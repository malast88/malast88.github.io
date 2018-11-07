---
layout: post
title: Liquid "where" filter
tags: [liquid, jekyll, filter, where]
---
# Liquid and Jekyll filters
[Liquid template engine](https://shopify.github.io/liquid/) provides some tools for control the flow of transformation.
I've just got deeper into one of them - filters, in particular, where filter actually [added by Jekyll](https://jekyllrb.com/docs/liquid/filters/).
There are already many awesome articles about extended Jekyll's filters, like [this](https://blog.webjeda.com/jekyll-filters/), 
but here I've documented my personal experience with them.

# An example from this blog
So in this blog I have created the data collection called [achievements](https://github.com/malast88/malast88.github.io/blob/master/_data/achievements.yaml),
which holds the various properties of certificates I've achieved, for example:
```
- date: 14 Oct 2018
  id: la-aws-essentials # keep id unique
  issuer: 
    title: Linux Academy
  # some data removed for the sake of readability
  filePNG: https://drive.google.com/uc?export=view&id=1Vjfj_Fz4yAuqphbX8MEecFCgsYONHGuD
```
This collection being processed in a for-loop which outputs the list of all the items.

But when I was adding the post about new certificate, I wanted to reuse some fields of the particular item from the collection.
The question was - how to get the particular item? Liquid allows indexing of arrays, but this is a bad approach.
So Jekyll's where filter to rescue: how it actually looks in the page's source code 
(used [this](https://stackoverflow.com/questions/3426182/how-to-escape-liquid-template-tags) answer to escape Liquid tags):
```
{{ "{%" }} assign achievement = site.data.achievements | where: "id","la-aws-essentials" | first "%}
[Certificate URl]({{"{{"}} achievement.url }})
![Certificate screenshot]({{"{{"}} achievement.filePNG }})
```
So I've introduced the new field id (do not want to filter on longer field title) and assigned a variable.
The only trick is that where filter returns the array, but I need a single object so apply another filter "first" to retrieve it.