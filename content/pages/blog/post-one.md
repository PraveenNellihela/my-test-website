---
type: PostLayout
title: K-Nearest Neighbors Algorithm - A simple overview
date: '2022-05-13'
excerpt: >-
  K-Nearest Neighbors (KNN) is one of the simplest machine learning algorithms
  to understand. Let's try to do that in this post.
featuredImage:
  type: ImageBlock
  url: /images/xavi-cabrera-kn-UmDZQDjM-unsplash.jpg
  altText: Post thumbnail image
  caption: Caption of the image
  elementId: ''
media:
  type: ImageBlock
  url: /images/xavi-cabrera-kn-UmDZQDjM-unsplash.jpg
  altText: Post image
  caption: >-
    Caption of theFoto de <a
    href="https://unsplash.com/es/@xavi_cabrera?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Xavi
    Cabrera</a> en <a
    href="https://unsplash.com/es/fotos/bloques-de-lego-amarillos-rojos-azules-y-verdes-kn-UmDZQDjM?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>      
    image
  elementId: ''
addTitleSuffix: true
colors: colors-b
backgroundImage:
  type: BackgroundImage
  url: /images/bg2.jpg
  backgroundSize: cover
  backgroundPosition: center
  backgroundRepeat: no-repeat
  opacity: 37
author: content/data/team/doris-soto.json
---
> This post was [originally posted ](https://medium.com/towards-artificial-intelligence/k-nearest-neighbors-algorithm-a-simple-overview-e0114059d19c)under Medium, published under the Towards AI publication.

K-Nearest Neighbors (KNN) is one of the simplest machine learning algorithms to understand. Like many other algorithms, KNN was inspired by human reasoning.

Imagine, for a moment, that you are holding in your hand a blue glass bottle that you have never seen before. You slip and suddenly drop it from about 5 feet to the concrete floor below. Before the bottle hits the ground, you know one thing with the utmost certainty, the bottle is going to break. How did you know this, even though you have never seen “this” bottle before? You have experienced in the past most types of glass brakes easily. Your mind made an instant connection between past experiences and this incident as the bottle slipped your hand.

If the bottle fell from a height of fewer than 2 feet to the grass-covered ground outside, you might have predicted that the glass would not break. Your mind compares the situation with similar past experiences and picks the condition that occurred the most, which is what happens in KNN as well.

# How does KNN work?

It is fairly straightforward. The algorithm checks for the closest “k” number of neighbors around a given object and predicts the most repeated class from this selection. Take a look at the image below. We let k = 4.

<p align="center">
![](/images/scatter-plot.webp)
<em>Scatter plot of different species of Iris flowers against their sepal length and sepal width.</em>
</p>

<div style="text-align: center"></div>

Here, different species of Iris flowers are plotted against their sepal lengths and widths. Observing the plot, you can see a clear distinction between species based on these two features. Now, we are given a new flower (purple point in the plot) and need to identify the species.

K-NN looks for the nearest points of data. If K = 4, the closest 4 issues are identified based on their distance to the new point, as shown, and the maximum occurring class is given as the prediction. In this instance, 2 out of 4 are virginica and one each of Setosa and Versicolor. Thus, the new point is predicted as a flower belonging to Virginica species.

*Note*: Unlike most machine learning algorithms that do the training work when training data is supplied, KNN just stored that data without doing any actual training. It is only during the prediction stage that computation is done to identify the closest neighbors and determine the class. Because of this, KNN is called a “**lazy learner**”.

# How is the distance calculated?

There are several methods of calculating the distance. Euclidean distance is a popular method, while Manhattan, Minkowski, and Hamming distance methods can also be used. The formula for calculating Euclidean distance is given below.

<p align="center">
![](/images/euq.webp)
</p>

<div style="text-align: center">Euclidean distance formula.</div>

Let us now consider our iris example and apply the Euclidean formula to calculate the distance between two points.

<p align="center">
![](/images/iris.webp)
</p>

Euclidean distances between the new point (purple) and the closest sample for Versicolor (red) can be calculated as shown below.

<p align="center">
![](/images/dist.webp)How do we find the best value for k?
</p>

The best value for K cannot be predetermined and requires some trial and error. It depends, for each case, on the data being used.

Typically, having larger K values result in less distinct boundaries between classes, but it also reduces the effect of noise on classification. Having large K values also makes computation more intensive and can increase bias.

Some ways of selecting K are to choose an odd number if the number of classes (n) is 2 or to set k=sqrt(n). A good value for K can also be determined by cross-validation.

# Pros and Cons of KNN algorithm

KNN is quite advantageous as it is easy to implement and does not require the building of a model, tuning several parameters, or making additional assumptions. It can be used well with classification, regression as well as for search. However, as the volume of data increases, this algorithm becomes significantly slower.
