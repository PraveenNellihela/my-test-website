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
> This post was [originally published ](https://medium.com/towards-data-science/clustering-algorithm-fundamentals-and-an-implementation-in-python-31a482592b04)in Medium under the Towards Data Science Publication.

# What is clustering?

Clustering is a method that can help machine learning engineers understand unlabeled data by creating meaningful groups or clusters. This often reveals patterns in data, which can be a useful first step in machine learning. Since the data you are working with is unlabeled, **clustering** is an unsupervised machine learning task.

Data is categorized into groups based on their similarity to each other through a metric known as the \*\*similarity measure, **which** \*\*is used to find out how similar the objects in the dataset are. To calculate this similarity measure, the **feature data** of the object in the dataset is used. A \*\*cluster ID \*\*is provided for each cluster, which is a powerful application of clustering. This allows large datasets to be simplified and also allows you to condense the entire feature set for an object into its cluster ID.

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

![](/images/clus2.webp)Hierarchical clustering and interactive dendrogram visualization in [Orange data mining suite](https://en.wikipedia.org/wiki/Orange_\(software\)).[ Blaž Zupan (Orange Data Mining)](https://commons.wikimedia.org/wiki/File:Orange-data-mining-hierarchical-clustering.png), [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0), via Wikimedia Commons


## Distribution-based Clustering

In these algorithms, it is assumed that data belongs to different distributions. Clusters are then defined as those that contain objects of similar distribution. One disadvantage is that distribution-based clustering is prone to overfitting. Therefore, constraints must be put on model complexity.

An example is shown in the image below where data is clustered into three Gaussian distributions. The darker colors are closer to the center of the distributions and the bands show the intensity of probability that data belongs to a cluster. As the distance to the center increases, the likelihood that the data belongs to that cluster will decrease.

If you do not have information on the type of distribution of the dataset, this algorithm might not be the best.


![](/images/clus3.webp)Gaussian distribution-based clustering. By Chire — Own work,[ CC BY-SA 3.0](https://commons.wikimedia.org/w/index.php?curid=17085713), via Wikimedia Commons



## Density-based Clustering

These algorithms create clusters by connecting areas that contain high densities of objects. It requires dense areas to be connectable, and by design, outliers are not assigned to clusters. A disadvantage is the difficulties density-based clustering algorithms face with higher dimensions as well as with data that have varying densities.

![](/images/clus4.webp)
Cluster analysis with [DBSCAN](https://en.wikipedia.org/wiki/DBSCAN) algorithm on a density-based data set. [Chire](https://commons.wikimedia.org/wiki/File:DBSCAN-density-data.svg), [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0), via Wikimedia Commons



## Centroid-based Clustering

This form of clustering groups data into non-hierarchical partitions. While these types of algorithms are efficient, they are sensitive to initial conditions and to outliers. The most commonly used centroid-based algorithm is known as k-means, where k is a hyperparameter defining the number of clusters.

K-means offer advantages such as the ability to scale to large data sets, ease of implementation, and adapt to new data. On the other hand, the *k* value must be found manually with some effort and the centroids can be dragged by outliers. It is beneficial to consider the removal of outliers prior to clustering.

Given a set of n data points, the objective of the k-means algorithm is to partition them into k groups, where each group contains similar data points. To do this, we first need to choose a number k. We then start by randomly assigning each point to its closest cluster center. Next, the distance between each data point and its assigned center is calculated. Then, we repeat the above steps until no further changes occur. Once we have finished calculating distances and centers, we go back to step 1 and recalculate the clusters. This continues until there are no changes to the clusters. At this point, we know that our clusters are stable.

# Implementation of the k-means algorithm

Now, let us implement one of the algorithms discussed above and visualize the resulting clusters. For this, we will use the k-means algorithm and scikit-learn. The code was inspired by and contains code found in the demo of K-Means clustering on the handwritten digits data provided by [scikit-learn examples](https://scikit-learn.org/stable/auto_examples/cluster/plot_kmeans_digits.html#sphx-glr-auto-examples-cluster-plot-kmeans-digits-py).




