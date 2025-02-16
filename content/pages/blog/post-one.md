---
type: PostLayout
title: K-Nearest Neighbors Algorithm - A simple overview
date: '2022-05-13'
excerpt: >-
  Nunc rutrum felis dui, ut consequat sapien scelerisque vel. Integer
  condimentum dignissim justo vel faucibus.
featuredImage:
  type: ImageBlock
  url: 'https://assets.stackbit.com/components/images/default/post-4.jpeg'
  altText: Post thumbnail image
  caption: Caption of the image
  elementId: ''
media:
  type: ImageBlock
  url: 'https://assets.stackbit.com/components/images/default/post-4.jpeg'
  altText: Post image
  caption: Caption of the image
  elementId: ''
addTitleSuffix: true
colors: colors-a
backgroundImage:
  type: BackgroundImage
  url: /images/bg2.jpg
  backgroundSize: cover
  backgroundPosition: center
  backgroundRepeat: no-repeat
  opacity: 100
---
> This post was 
>
> [originally posted](https://medium.com/towards-artificial-intelligence/k-nearest-neighbors-algorithm-a-simple-overview-e0114059d19c)
>
>  under Medium, published under the Towards AI publication.

K-Nearest Neighbors (KNN) is one of the simplest machine learning algorithms to understand. Like many other algorithms, KNN was inspired by human reasoning.

Imagine, for a moment, that you are holding in your hand a blue glass bottle that you have never seen before. You slip and suddenly drop it from about 5 feet to the concrete floor below. Before the bottle hits the ground, you know one thing with the utmost certainty, the bottle is going to break. How did you know this, even though you have never seen “this” bottle before? You have experienced in the past most types of glass brakes easily. Your mind made an instant connection between past experiences and this incident as the bottle slipped your hand.

If the bottle fell from a height of fewer than 2 feet to the grass-covered ground outside, you might have predicted that the glass would not break. Your mind compares the situation with similar past experiences and picks the condition that occurred the most, which is what happens in KNN as well.

# How does KNN work?

It is fairly straightforward. The algorithm checks for the closest “k” number of neighbors around a given object and predicts the most repeated class from this selection. Take a look at the image below. We let k = 4.

<p align="center">
![](/images/scatter-plot.webp)
</p>





