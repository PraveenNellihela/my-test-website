---
type: PostLayout
title: A Comprehensive Guide to Python Lists
colors: colors-b
date: '2022-08-20'
author: content/data/team/doris-soto.json
excerpt: >-
  Everything a coder need to know about Python lists, from beginner to advanced
  levels.
featuredImage:
  type: ImageBlock
  url: /images/featured-Image3.jpg
  altText: Post thumbnail image
backgroundImage:
  type: BackgroundImage
  url: /images/bg4.jpg
  backgroundSize: cover
  backgroundPosition: center
  backgroundRepeat: no-repeat
  opacity: 10
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
        width: wide
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
Lists are a one of the four built in data structures found in Python. Data structures can be considered as “containers” that help organize, manage and store data in a unique way. In addition to the built in data structures, Python also offers developers the ability to create their own. These are known as user-defined data structures. Today, we will look at the built in data structure, lists. We will dive deeper into the other data structures in future guides in this series.

## Table of Contents

*   List creation and indexing

*   The methods of list objects

*   List Slicing

*   List Comprehension

*   Other useful tips

<p align="center">
![](/images/python1.webp)
<em>Data structures found in Python.</em>
</p>

## List creation and indexing

### How to create a list

There are different ways to create a list in Python. You can add elements by putting them in-between square brackets and separated by a comma. The elements can be of different types, such as strings, integers, floats and even data structures such as lists.

```
# create a list by adding elements within square brackets: 
list_a = ["banana", 42, [], 24.08, True]  

# create a new empty list with the list function (items can be appended later):
list_b = list()

# different data types such as integers, bolean, strings, lists etc.
# are allowed. duplicates are also allowed, as shown below. 
list_types = ["apple", True, list_a, 42, True] 
```

