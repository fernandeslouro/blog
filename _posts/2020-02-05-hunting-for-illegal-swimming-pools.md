---
layout: post
title: Hunting for Illegal Swimming Pools
tags: [machine-learning]
---

Cascais is a municipality in the Lisbon District of Portugal, located on the Portuguese Riviera. An important tourist destination, the municipality is one of the wealthiest in the Iberian Peninsula. It has one of the most expensive real estate markets and one of the highest costs of living in the country and is consistently ranked highly for its quality of life. A common form of tax evasion in wealthy, sunny areas is to delay the building of swimming pools when constructing new houses until after their evaluation for taxation. The municipality of Cascais set out to end this phenomenon using data-driven approaches.

### Data

This project shares some similarities with the one previously described. Since the project was developed in collaboration with the municipality, access to proprietary data was offered. We were also provided with high-definition aerial images, but this time only in the RGB bands. Additionally, we had access to polygons outlining the land parcels in which houses and other buildings are contained. These polygons contain information on the existence of a swimming pool inside the land parcel, as well as information about the parcel’s owner.

### Approach

Our approach starts by finding swimming pool ’candidate’ shapes in our RGB imagery. These amount to blobs of the blue color typical of swimming pools found in the aerial image. This was done by setting a threshold on the band obtained by subtracting the values of the red band to the blue band, an approach that showed success in previous work @blue. The pool ’candidates’ correspond to the aggregations of blue color inside a range of sizes. In the figure below we can see in yellow an example of a pool ’candidate’.

![A pool ’candidate’.](/assets/images/pool.png =250x)

Some of these shapes were labeled by the team, and a classification model was trained on this trained data. Features were extracted both from the ’candidate’ shape and the area around it. The classifications were then crossed with the land parcel polygons. If a shape was classified with high certainty as a swimming pool and was contained in a parcel without any declared pools, a report was generated, aggregating all the images available in the dataset of the parcel, and the location of the swimming pool.

### Results

As in the previous project, the chosen model was a Logistic Regression, which achieved 90% accuracy in our validation dataset. The initial iteration of the tool provided actionable insights for the municipality. Further action is facilitated by the fact that the tool provides what is in essence a report of tax avoidance with photographic proof. The developed tool also has the benefit of being able to capture new instances of tax avoidance as soon as new imagery is provided. The developed tool is also scalable, and the trained model could be applied to other cities, since most pools have bottoms colored in similar shades of blue, in the range of what is detected by our tool. Due to the nature of this tool, it was not open sourced.

## Conclusion

Despite their proof-of-concept status, both these projects have had significant impact. This is due to the fact that they produce actionable insights.

It was interesting to note that, despite the simplicity of the models, their performance was enough to make them very useful in assisting public policy. This is partly due to the fact that the features being detected in the images are striking relatively to the rest of the environment, which makes them particularly suitable to this kind of approach.
