---
type: PostLayout
title: "Feature Selection: Choosing the Right Features for Your Machine Learning Algorithm \U0001F30E"
colors: colors-a
date: '2022-07-13'
author: content/data/team/doris-soto.json
excerpt: 'Sometimes, less is more'
featuredImage:
  type: ImageBlock
  url: /images/featured-Image4.jpg
  altText: Post thumbnail image
bottomSections:
  - elementId: ''
    type: RecentPostsSection
    colors: colors-f
    variant: variant-d
    subtitle: Recent posts
    showDate: true
    showAuthor: false
    showExcerpt: true
    recentCount: 2
    styles:
      self:
        height: auto
        width: wide
        margin:
          - mt-0
          - mb-0
          - ml-0
          - mr-0
        padding:
          - pt-12
          - pb-56
          - pr-4
          - pl-4
        justifyContent: center
      title:
        textAlign: left
      subtitle:
        textAlign: left
      actions:
        justifyContent: center
    showFeaturedImage: true
    showReadMoreLink: true
  - type: ContactSection
    backgroundSize: full
    title: Stay up-to-date with my words ✍️
    colors: colors-f
    form:
      type: FormBlock
      elementId: sign-up-form
      fields:
        - name: firstName
          label: First Name
          hideLabel: true
          placeholder: First Name
          isRequired: true
          width: 1/2
          type: TextFormControl
        - name: lastName
          label: Last Name
          hideLabel: true
          placeholder: Last Name
          isRequired: false
          width: 1/2
          type: TextFormControl
        - name: email
          label: Email
          hideLabel: true
          placeholder: Email
          isRequired: true
          width: full
          type: EmailFormControl
        - name: updatesConsent
          label: Sign me up to recieve my words
          isRequired: false
          width: full
          type: CheckboxFormControl
      submitLabel: "Submit \U0001F680"
      styles:
        submitLabel:
          textAlign: center
    styles:
      self:
        height: auto
        width: narrow
        margin:
          - mt-0
          - mb-0
          - ml-4
          - mr-4
        padding:
          - pt-24
          - pb-24
          - pr-4
          - pl-4
        alignItems: center
        justifyContent: center
        flexDirection: row
      title:
        textAlign: left
      text:
        textAlign: left
---
> This post was [originally published ](https://medium.com/towards-data-science/feature-selection-choosing-the-right-features-for-your-machine-learning-algorithm-379bda9f3e05)in the Towards Data Science Publication on Medium.

## Why should we select some features and ignore the rest? Isn’t having more features good for the accuracy of our model?

Choosing the right features, and ignoring unsuitable ones, is a vital step in any machine learning project. This can result in good model performance and save you time down the line. It can also help you interpret the output of your model more easily. But having more features will mean the model has more data to train on, and should mean the model will be more accurate, right? Well, not exactly.

Having too many features can cause the algorithm to be prone to \*\*overfitting. \*\*Overfitting is when the model generalizes to irrelevant data or outliers. Another good reason to choose features carefully is something called \*\*the curse of dimensionality. **Typically each feature is stored in a dimension.** \*\*Algorithms become harder to design in high dimensions as the running time often grows exponential with the number of dimensions. So it makes sense, and offers a benefit, when we select the most suitable features and ignore the rest.

# How can we select the best features for training?

There are two ways to select features. First, one can manually observe features by representing them graphically though histograms etc. The second way is through automatic selection of best features.

## Doing things manually…

We can manually observe features by representing them graphically though histograms etc. Then, by identifying the features that can be distinguished from each other and those that overlap each other, we can decide which ones will be the best. Let us look at an example.

We are going to have a look at the [iris dataset](https://www.kaggle.com/datasets/uciml/iris). It has data for 150 iris flowers, consisting of 3 species (Iris setosa, Iris virginica and Iris versicolor). Four features of the flowers are available in the dataset (the width and length of sepals and petals of the flowers). An excerpt of the dataset is shown below.

```
Here, you can see the 
```

The code to lead the Iris data set is shown below:

```

# In this code, we load up the iris data set 
# and try to visualize the features using a histogram

from sklearn import datasets
import matplotlib.pyplot as plt

iris = datasets.load_iris()

dim = 0  # the feature we want to compare

# each dataset is seperated into 5 intervals (by giving 5 to the bins variable)
plt.hist(iris.data[iris.target==0,dim], bins=5, histtype='stepfilled', color='b', alpha=0.5, label='Setosa')
plt.hist(iris.data[iris.target==1,dim], bins=5, histtype='stepfilled', color='r', alpha=0.5, label='Versicolor')
plt.hist(iris.data[iris.target==2,dim], bins=5, histtype='stepfilled', color='g', alpha=0.5, label='Virginica')

plt.title("Histogram")
plt.xlabel("Value")
plt.ylabel("Occurances")
plt.legend()

plt.show()
```

With the above code, we draw a histogram for each of the three species of the iris data set, for a specific feature selected using the variable ‘**dim’**.

We can select a specific species using \*\*‘iris.target’ **for example, in the above code:** iris.data\[iris.target == 0, dim] \*\*gives us the data of the Iris Setosa species **and** the feature: sepal length.

By looking at the resulting histogram, we realize that the features overlap. This means that the feature we selected (sepal length), given by **dim = 0**, may not be good enough to seperate the different types of iris flowers (Setosa, Versicolor and Virginica).

<p align="center">
![](/images/iris1.webp)
<em>The results of the above code, the features are overlapping.</em>
</p>

Now, let us select a different feature. We will select feature 4 (petal width) by using dim=3. The image below shows the resulting histogram.

<p align="center">
![](/images/iris2.webp)
<em>The results of the above code, the features are overlapping.</em>
</p>

As you can see, this feature provides a good enough seperation between the three types of flowers, compared to the other feature that we observed. Observing the histograms in this way can help us gain a better feeling or an intuition for the data that we are working with and identify suitable features as well as features that are not so useful.

The manual method of doing things might not be suitable when we are working with more features. In such situations, we can make use of automatic feature selection methods.

*Note: In the dataset we used, lengths were used for features. Every feature has the same units (centimeters). But some datasets can have features that differ from each other. For example, one feature may be in meters, while another feature might be color. This can introduce its own set of complications and we will need to **scale** features, which we will look at, at the end of this article.*

## Automatic feature selection

The general procedure for feature selection is:

*   Calculate the quality of each feature by comparing with ground truth or by comparing variance among the classes for each feature.

*   Next, sort the features according to the calculated quality and keep only the best. The best features can be selected by using a quality threshold or by simply selecting the best *n* number of features.

To select a subset of features we can perform either \*\*\*forward feature selection, \*\*\*where we add the best dimension or feature step by step, or perform ***backward feature selection,*** where we start with all features and continue to delete the feature with the worst quality.

**How can we calculate the *quality* of a feature?**

The first quality index we will look at is called the *Correlation Coefficient* (aka *Pearson correlation*). Correlation Coefficient is the ratio between **covariance and standard deviation** between two variables. As a result of the ratio, we get a result between -1 and 1.

*What is **covariance**?*

> If the greater values of one variable mainly correspond with the greater values of the other variable, and the same holds for the lesser values (that is, the variables tend to show similar behavior), the covariance is positive.
>
> In the opposite case, when the greater values of one variable mainly correspond to the lesser values of the other, covariance is negative.
>
> [- Weisstein, Eric W.](https://en.wikipedia.org/wiki/Eric_W._Weisstein) [“Covariance”](https://mathworld.wolfram.com/Covariance.html). [*MathWorld*](https://en.wikipedia.org/wiki/MathWorld).

This can be understood clearly by observing the image below.
<p align="center">
![](/images/1_8jws5-3rAmaRyNyN01MzDg.webp)
<em>[The sign of the covariance of two random variables *X* and *Y*](https://en.wikipedia.org/wiki/Covariance)</em>
</p>

