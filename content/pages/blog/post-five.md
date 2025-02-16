---
type: PostLayout
title: What is K-fold Cross Validation?
colors: colors-a
date: '2022-07-01'
author: content/data/team/doris-soto.json
excerpt: More context that may or may not be helpful
featuredImage:
  type: ImageBlock
  url: /images/featured-Image5.jpg
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
> This post was [originally published ](https://medium.com/towards-data-science/what-is-k-fold-cross-validation-5a7bb241d82f)in Medium, under the Towards Data Science publication

# Introduction

Let’s say that you have trained a machine learning model. Now, you need to find out how well this model performs. Is it accurate enough to be used? How does it compare to another model? There are several evaluation methods to determine this. One such method is called K-fold cross validation.

Cross validation is an evaluation method used in machine learning to find out how well your machine learning model can predict the outcome of unseen data. It is a method that is easy to comprehend, works well for a limited data sample and also offers an evaluation that is less biased, making it a popular choice.

The data sample is split into ‘k’ number of smaller samples, hence the name: K-fold Cross Validation. You may also hear terms like four fold cross validation, or ten fold cross validation, which essentially means that the sample data is being split into four or ten smaller samples respectively.

# How is k-fold cross validation performed?

The general stratergy is quite straight forward and the following steps can be used:

1.  First, shuffle the dataset and split into k number of subsamples. (It is important to try to make the subsamples equal in size and ensure k is less than or equal to the number of elements in the dataset).

2.  In the first iteration, the first subset is used as the test data while all the other subsets are considered as the training data.

3.  Train the model with the training data and evaluate it using the test subset. Keep the evaluation score or error rate, and get rid of the model.

4.  Now, in the next iteration, select a different subset as the test data set, and make everything else (including the test set we used in the previous iteration) part of the training data.

5.  Re-train the model with the training data and test it using the new test data set, keep the evaluation score and discard the model.

6.  Continue iterating the above k times. Each data subsamples will be used in each iteration until all data is considered. You will end up with a k number of evaluation scores.

7.  The total error rate is the average of all these individual evaluation scores.

<div style="text-align: center">![](https://preview--nellihela-0a1b8.stackbit.dev/_static/app-assets/public/images/K-fold_cross_validation_EN.svg)
Diagram of k-fold cross validation By Gufosowa — Own work, CC BY-SA 4.0, <https: commons.wikimedia.org="" w="" index.php?curid="82298768">
</https:></div>

# How to determine the best value for ‘k’ in K-Fold Cross Validation?

<div style="text-align: left">Chosing a good value for k is important. A poor value for k can result in a poor evaluation of the model’s abilities. In other words, it can cause the measured ability of the model to be overestimated (high bias) or change widely depending on the training data used (high variance).Generally, there are three ways to select k:\*   Let k = 5, or k =10. Through experimentation, it has been found that selecting k to be 5 or 10 results in sufficiently good results.</div>

*   Let k = n, where n is the size of the dataset. This ensures each sample is used in the test data set.

*   Another way is to chose k so that every split data sample is sufficiently large, ensuring they are statistically represented in the larger dataset.# Types of cross validationCross validation can be divided into two major categories:\*   Exhaustive, where the method learn and test on every single possibility of dividing the dataset into training and testing subsets.

*   Non-exhaustive cross validation methods where **all** ways of splitting the sample are **not** computed.</div>

## Exhaustive cross-validation

Leave-p-out cross validation is a method of exhaustive cross validation. Here, p number of observations (or elements in the sample dataset) are left out as the training dataset, everything else is considered as part of the training data. For more clarity, if you look at the above image, p is equal to 5, as shown by the 5 circles in the ‘test data’.

Leave-one-out cross validation a special form of leave-p-out exhuastive cross validation method, where p = 1. This is also a specific case for k-fold cross validation, where k = N(number of elements in the sample dataset).

## Non-exhaustive cross-validation

K-fold cross validation where k is not equal to N, Stratified cross validation and repeated random sub-sampling validation are non-exhaustive cross validation methods.

*Stratified cross validation*: partitions are selected such that each partition contains roughly the same amount of elements for each class label. For example, in binary classification, every split has elements of which roughly 50% belongs to class 0 and 50% that belongs to class 1.

*Repeated random sub-sampling validation (Monte Carlo cross validation):* Data is split into multiple random subsets and the model is trained and evaluated for each split. The results are averaged over the splits. Unlike the k-fold cross validation, proportions of the training and test set size are not dependent on the size of the data set, which is an advantage. However, a disadvantage is that some data elements will never be selected as a part of the test set, while some may be selected multiple times. When the amount of random splits are increased and approach infinity, the results tend to be similar to that of leave-p-out cross validation.

# Conclusion

Cross validation is used to evaluate how well a model perfoms and compare different models objectively. For example, we can determine if a support vector machine (SVM) performs better than a K-nearest neighbors (KNN) model on the same set of data. It is a straight forward and less biased, making cross validation a popular evaluation tool. However, there are some disadvantages to cross validation, such as having to rerun training algorithms k times, which can take up significant computation and time.
