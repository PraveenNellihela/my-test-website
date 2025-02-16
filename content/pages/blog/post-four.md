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
> This post was
>
> [ originally published](https://medium.com/towards-data-science/feature-selection-choosing-the-right-features-for-your-machine-learning-algorithm-379bda9f3e05)
>
>  in the Towards Data Science Publication on Medium.

## Why should we select some features and ignore the rest? Isn’t having more features good for the accuracy of our model?

Choosing the right features, and ignoring unsuitable ones, is a vital step in any machine learning project. This can result in good model performance and save you time down the line. It can also help you interpret the output of your model more easily. But having more features will mean the model has more data to train on, and should mean the model will be more accurate, right? Well, not exactly.

Having too many features can cause the algorithm to be prone to **overfitting. **Overfitting is when the model generalizes to irrelevant data or outliers. Another good reason to choose features carefully is something called **the curse of dimensionality. **Typically each feature is stored in a dimension.** **Algorithms become harder to design in high dimensions as the running time often grows exponential with the number of dimensions. So it makes sense, and offers a benefit, when we select the most suitable features and ignore the rest.

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

We can select a specific species using **‘iris.target’ **for example, in the above code:** iris.data\[iris.target == 0, dim] **gives us the data of the Iris Setosa species **and** the feature: sepal length.

By looking at the resulting histogram, we realize that the features overlap. This means that the feature we selected (sepal length), given by **dim = 0**, may not be good enough to seperate the different types of iris flowers (Setosa, Versicolor and Virginica).

<p align="center">
![](/images/iris1.webp)
<em>The results of the above code, the features are overlapping.</em>
</p>


