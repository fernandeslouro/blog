---
layout: post
title: Hunting for Illegal Swimming Pools
tags: [machine-learning]
---

This is the second in a series of two posts on my early work applying machine learning approaches to public policy problems. You can also read the [first post](http://blog.louro.xyz/2020/02/03/detecting-green-rooftops-in-rotterdam) or a [pdf version](http://louro.xyz/ml-public-policy.pdf) complete with citations. Each of the posts goes over a separate project. On this second one, I'll explain our method for detecting swimming pools in aerial images, and how that helped fight tax avoidance.

***

Cascais is a municipality in the Lisbon District of Portugal, located on the Portuguese Riviera. An important tourist destination, the municipality is one of the wealthiest in the Iberian Peninsula. It has one of the most expensive real estate markets and one of the highest costs of living in the country and is consistently ranked highly for its quality of life. A common form of tax evasion in wealthy, sunny areas is to delay the building of swimming pools when constructing new houses until after their evaluation for taxation. The municipality of Cascais set out to end this phenomenon using data-driven approaches.

# Data

This project shares some similarities with the one described in the [previous post](http://blog.louro.xyz/2020/02/03/detecting-green-rooftops-in-rotterdam). Since the project was developed in collaboration with the municipality, access to proprietary data was offered. We were also provided with high-definition aerial images, but this time only in the RGB bands. Additionally, we had access to polygons outlining the land parcels in which houses and other buildings are contained. These polygons contain information on the existence of a swimming pool inside the land parcel, as well as information about the parcel’s owner.

# Approach

Our approach starts by finding swimming pool ’candidate’ shapes in our RGB imagery. These amount to blobs of the blue color typical of swimming pools found in the aerial image. This was done by setting a threshold on the band obtained by subtracting the values of the red band to the blue band, an approach that showed success in previous work @blue. The pool ’candidates’ correspond to the aggregations of blue color inside a range of sizes. In the figure below we can see in yellow an example of a pool ’candidate’.
<center>
<div style="text-align:center; width:400px; max-width:device-width"><img src="/assets/images/pool.png" /></div>
</center>
Some of these shapes were labeled by the team, and a classification model was trained on this trained data. Features were extracted both from the ’candidate’ shape and the area around it. The classifications were then crossed with the land parcel polygons. If a shape was classified with high certainty as a swimming pool and was contained in a parcel without any declared pools, a report was generated, aggregating all the images available in the dataset of the parcel, and the location of the swimming pool.

# Results

As in the previous project, the chosen model was a Logistic Regression, which achieved 90% accuracy in our validation dataset. The initial iteration of the tool provided actionable insights for the municipality. Further action is facilitated by the fact that the tool provides what is in essence a report of tax avoidance with photographic proof. The developed tool also has the benefit of being able to capture new instances of tax avoidance as soon as new imagery is provided. The developed tool is also scalable, and the trained model could be applied to other cities, since most pools have bottoms colored in similar shades of blue, in the range of what is detected by our tool. Due to the nature of this tool, it was not open sourced.

# Conclusion

As in the previous project, this work provided actionable insights to public officials. The tool is still in use by the municipality, and has contributed to reductions in tax evasion. It was interesting to note that, even with a simple model, detection of swimming pools in aerial images with good performance is an achievable task. After all, there aren't a lot of things that are light blue when seen from the sky :). Our model also did a good job at not flagging blue cars, which was a problem in the earliest iterations.

**Note:** This project was developed in partnership with the [Municipality of Cascais](https://www.cascais.pt/) under a [Data Science for Social Good Europe](http://www.dssgfellowship.org/europe/) initiative.
