---
type: PostLayout
title: 'Clustering Algorithm Fundamentals and an Implementation in Python '
colors: colors-b
date: '2022-09-01'
author: content/data/team/doris-soto.json
excerpt: >-
  The unsupervised process of creating groups of data containing similar
  elements
featuredImage:
  type: ImageBlock
  url: /images/aldebaran-s-A8tFlXQzRXg-unsplash.jpg
  altText: >-
    Foto de <a
    href="https://unsplash.com/es/@aldebarans?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Aldebaran
    S</a> en <a
    href="https://unsplash.com/es/fotos/galaxia-negra-y-roja-con-estrellas-A8tFlXQzRXg?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>      
  caption: >-
    Foto de <a
    href="https://unsplash.com/es/@aldebarans?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Aldebaran
    S</a> en <a
    href="https://unsplash.com/es/fotos/galaxia-negra-y-roja-con-estrellas-A8tFlXQzRXg?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>      
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
media:
  type: ImageBlock
  url: /images/aldebaran-s-A8tFlXQzRXg-unsplash.jpg
  altText: altText of the image
  caption: Caption of the image
  elementId: ''
backgroundImage:
  type: BackgroundImage
  url: /images/bg2.jpg
  backgroundSize: cover
  backgroundPosition: center
  backgroundRepeat: no-repeat
  opacity: 40
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

<p align="center">
![](/images/clus1.webp)
<em>The result of cluster analysis. Source: hellisp, Public domain, via [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cluster-2.png)</em>

# Clustering Algorithms

Now that we understand the concepts of clustering, let us look at some common clustering algorithms. For an exhaustive list, you can refer to [this paper](https://link.springer.com/article/10.1007/s40745-015-0040-1).

## Hierarchical Clustering

This approach is suited for hierarchical data and it creates a tree of clusters. The standard algorithm is too slow for most datasets, as it has a time complexity of O(n³) with a memory requirement of Ω(n²). However, the runtime can be decreased at the cost of memory requirements, although memory overhead makes it difficult to use practically in most cases.

<p align="center">
![](/images/clus2.webp)
<em>Hierarchical clustering and interactive dendrogram visualization in [Orange data mining suite](https://en.wikipedia.org/wiki/Orange_\(software\)).[ Blaž Zupan (Orange Data Mining)](https://commons.wikimedia.org/wiki/File:Orange-data-mining-hierarchical-clustering.png), [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0), via Wikimedia Commons </em>

## Distribution-based Clustering

In these algorithms, it is assumed that data belongs to different distributions. Clusters are then defined as those that contain objects of similar distribution. One disadvantage is that distribution-based clustering is prone to overfitting. Therefore, constraints must be put on model complexity.

An example is shown in the image below where data is clustered into three Gaussian distributions. The darker colors are closer to the center of the distributions and the bands show the intensity of probability that data belongs to a cluster. As the distance to the center increases, the likelihood that the data belongs to that cluster will decrease.

If you do not have information on the type of distribution of the dataset, this algorithm might not be the best.

<p align="center">
![](/images/clus3.webp)
<em>Gaussian distribution-based clustering. By Chire — Own work,[ CC BY-SA 3.0](https://commons.wikimedia.org/w/index.php?curid=17085713), via Wikimedia Commons
</em>

## Density-based Clustering

These algorithms create clusters by connecting areas that contain high densities of objects. It requires dense areas to be connectable, and by design, outliers are not assigned to clusters. A disadvantage is the difficulties density-based clustering algorithms face with higher dimensions as well as with data that have varying densities.

<p align="center">
![](/images/clus4.webp)
<em>Cluster analysis with [DBSCAN](https://en.wikipedia.org/wiki/DBSCAN) algorithm on a density-based data set. [Chire](https://commons.wikimedia.org/wiki/File:DBSCAN-density-data.svg), [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0), via Wikimedia Commons</em>
## Centroid-based Clustering

This form of clustering groups data into non-hierarchical partitions. While these types of algorithms are efficient, they are sensitive to initial conditions and to outliers. The most commonly used centroid-based algorithm is known as k-means, where k is a hyperparameter defining the number of clusters.

K-means offer advantages such as the ability to scale to large data sets, ease of implementation, and adapt to new data. On the other hand, the *k* value must be found manually with some effort and the centroids can be dragged by outliers. It is beneficial to consider the removal of outliers prior to clustering.

Given a set of n data points, the objective of the k-means algorithm is to partition them into k groups, where each group contains similar data points. To do this, we first need to choose a number k. We then start by randomly assigning each point to its closest cluster center. Next, the distance between each data point and its assigned center is calculated. Then, we repeat the above steps until no further changes occur. Once we have finished calculating distances and centers, we go back to step 1 and recalculate the clusters. This continues until there are no changes to the clusters. At this point, we know that our clusters are stable.

# Implementation of the k-means algorithm

Now, let us implement one of the algorithms discussed above and visualize the resulting clusters. For this, we will use the k-means algorithm and scikit-learn. The code was inspired by and contains code found in the demo of K-Means clustering on the handwritten digits data provided by [scikit-learn examples](https://scikit-learn.org/stable/auto_examples/cluster/plot_kmeans_digits.html#sphx-glr-auto-examples-cluster-plot-kmeans-digits-py).

```
import numpy as np
import matplotlib.pyplot as plt

from sklearn.datasets import load_digits
from sklearn.cluster import KMeans
from sklearn.decomposition import PCA

data, labels = load_digits(return_X_y=True)
(n_samples, n_features), n_digits = data.shape, np.unique(labels).size

reduced_data = PCA(n_components=2).fit_transform(data)
kmeans = KMeans(init="k-means++", n_clusters=n_digits, n_init=4)
kmeans.fit(reduced_data)

# Step size of the mesh. Decrease to increase the quality of the VQ.
h = 0.02  # point in the mesh [x_min, x_max]x[y_min, y_max].

# Plot the decision boundary. For that, we will assign a color to each
x_min, x_max = reduced_data[:, 0].min() - 1, reduced_data[:, 0].max() + 1
y_min, y_max = reduced_data[:, 1].min() - 1, reduced_data[:, 1].max() + 1
xx, yy = np.meshgrid(np.arange(x_min, x_max, h), np.arange(y_min, y_max, h))

# Obtain labels for each point in mesh. Use last trained model.
Z = kmeans.predict(np.c_[xx.ravel(), yy.ravel()])

# Put the result into a color plot
Z = Z.reshape(xx.shape)
plt.figure(1)
plt.clf()
plt.imshow(
    Z,
    interpolation="nearest",
    extent=(xx.min(), xx.max(), yy.min(), yy.max()),
    cmap=plt.cm.Paired,
    aspect="auto",
    origin="lower",
)

plt.plot(reduced_data[:, 0], reduced_data[:, 1], "k.", markersize=2)
# Plot the centroids as a white X
centroids = kmeans.cluster_centers_
plt.scatter(
    centroids[:, 0],
    centroids[:, 1],
    marker="x",
    s=169,
    linewidths=3,
    color="w",
    zorder=10,
)
plt.title(
    "K-means clustering on the digits dataset (PCA-reduced data)\n"
    "Centroids are marked with white cross"
)
plt.xlim(x_min, x_max)
plt.ylim(y_min, y_max)
plt.xticks(())
plt.yticks(())
plt.show()
```

The output is shown in the image below.

<p align="center">
![](/images/clus5.webp)
<em>The resulting plot is produced from the above code.</em>
</p>

In addition to the k-means algorithm, scikit-learn library offers several other algorithms that can be used based on the data you have. Some of these algorithms include:

*   Affinity Propagation

*   Agglomerative Clustering

*   BIRCH

*   DBSCAN

*   K-Means

*   Mini-Batch K-Means

*   OPTICS

*   Spectral Clustering

*   Mixture of Gaussians

Keep in mind that there is no fixed algorithm that will offer the best results. You will have to run controlled experiments to identify the most suitable algorithm for the dataset you are working with.

If you want to dive deeper into the algorithms provided, the [scikit-learn clustering API](https://scikit-learn.org/stable/modules/clustering.html) is a good place to start.

# Conclusion

In this article, we looked at clustering, its uses, and some commonly used types of clustering algorithms. We also had a look at their advantages and disadvantages, and where some algorithms shine compared to others. We finished by looking at a coded example of how k-means clustering can be done. I hope you found this information useful. Feel free to let me know your thoughts and questions in the comment section below.
