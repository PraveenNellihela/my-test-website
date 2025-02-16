---
type: PostLayout
title: "Clustering Algorithm Fundamentals and an Implementation in Python \U0001F5C2️"
colors: colors-a
date: '2022-09-01'
author: content/data/team/doris-soto.json
excerpt: More context that may or may not be helpful
featuredImage:
  type: ImageBlock
  url: /images/featured-Image6.jpg
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
> [originally published](https://medium.com/towards-data-science/clustering-algorithm-fundamentals-and-an-implementation-in-python-31a482592b04)
>
>  in Medium under the Towards Data Science Publication. 

# What is clustering?

Clustering is a method that can help machine learning engineers understand unlabeled data by creating meaningful groups or clusters. This often reveals patterns in data, which can be a useful first step in machine learning. Since the data you are working with is unlabeled, **clustering** is an unsupervised machine learning task.

Data is categorized into groups based on their similarity to each other through a metric known as the **similarity measure, **which** **is used to find out how similar the objects in the dataset are. To calculate this similarity measure, the **feature data** of the object in the dataset is used. A **cluster ID **is provided for each cluster, which is a powerful application of clustering. This allows large datasets to be simplified and also allows you to condense the entire feature set for an object into its cluster ID.

A simple real-life example of this principle is collecting data about household size and household income to create clusters of users such as small family high spenders, small family low spenders, large family high spenders, and large family low spenders.

# Uses of clustering

Today, clustering is used for a wide variety of use cases in the industry. Some of these include the grouping of search results, analysis of social networks, and market segmentation. Clustering is also used in image segmentation, anomaly detection, and in medical imaging.

Expanding on the advantage of cluster IDs mentioned above, clustering can be used to group objects by different features. For example, stars can be grouped by their brightness or music by their genres.

In organizations like Google, clustering is used for:

*   Generalization: when objects in clusters have missing feature data, they can be inferred from other objects in their cluster.

*   Data compression: feature data can be entirely replaced by the cluster ID. This saves storage and simplifies the feature space. This can help make ML model training simpler and faster.

*   Preserve privacy: clustering groups of users and associating their data with cluster IDs prevent associating user data with specific users, ensuring user privacy.

![](/images/clus1.webp)

The result of cluster analysis. Source: hellisp, Public domain, via [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cluster-2.png)


# Clustering Algorithms

Now that we understand the concepts of clustering, let us look at some common clustering algorithms. For an exhaustive list, you can refer to [this paper](https://link.springer.com/article/10.1007/s40745-015-0040-1).

## Hierarchical Clustering

This approach is suited for hierarchical data and it creates a tree of clusters. The standard algorithm is too slow for most datasets, as it has a time complexity of O(n³) with a memory requirement of Ω(n²). However, the runtime can be decreased at the cost of memory requirements, although memory overhead makes it difficult to use practically in most cases.




