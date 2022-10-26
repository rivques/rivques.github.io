---
title: "Engineering 3 CAD Notebook"
date: 2022-10-25T11:34:49-04:00
draft: false
---
## Propeller Toy/Collaborative Onshape
### Assignment
For this assignment, two students were to create a small toy that would launch a propeller when you
pulled a cord, learning about Onshape's collaboration features along the way. Partners were assigned
different tasks by the assignment that could be done in parallel. For example, one student might be
designing the propeller while the other designed the pull cord.
### Document
The document is available for viewing [here](https://cvilleschools.onshape.com/documents/28913ae2144b614eeb24c495/w/1f8daf7a81eecfe2384f967e/e/f1940db3c9019138372953fc?renderMode=0&uiState=6357f406d023a50894606873).
### Media
![An animation of the toy](/docs/propdemo.gif "An animation of the key being pulled")
![A close-up of the spinner part](/docs/helix.png "The spinner part, which holds the prop on. Note the highlighted helix, which defines the groove the prop rests in.")
### Reflection
I learned a lot here. First of all, Onshape's collaboration tools are much more advanced than I thought they were, providing something akin to Google Docs CAD. In addition, I really got a change to explore the branching features because I ended up doing some of my partner's work on a separate branch while they were absent. Also, because the part was designed for Metric M2 bolts, I had to adapt it to  use the imperial #4-40 bolts that the lab stocks. Because the part's design intent was implemented well, this was pretty painless. In addition, I explored the helix tool for the first time. I've used a parametric featurescript before when I needed a curve, but it's good to know that Onshape has some of these tools natively.
## Swing Arm
### Assignment
This was the class's first attempt at designing a part only from drawings. We were given a PDF of drawings of a part and once we had designed it, we checked to see if it weighed the correct amount. If it didn't weigh the correct amount, we had made a mistake, so we would then have to fix it. In addition, we were encouraged to design as much of the part as possible by only constraining things to each other instead of explicitly dimensioning them. This helps preserve design intent.
### Document
The document is available for viewing [here](https://cvilleschools.onshape.com/documents/2b2aafa427dfcb0424d54032/w/95d27a735581fd5fcf29e4b5/e/b58931bb013e6270ef59e632?renderMode=0&uiState=6357fc5a7381901e6cad6dda).
### Media
![A screenshot of the part](/docs/swing_arm.png "An image of the full part.")
![The part, not looking quite right](/docs/broken_swing_arm.png "The bottom hole was set to “through all”, causing the extra hole in the top.")
### Reflection
All things considered, this went fairly well. I only had one thing go wrong, and it was easily fixed (an extrude that was set to "through all" should have been "up to face," see the image for how this broke). I discovered that almost everything can be constrained in a sketch if you really think about your design intent.
## Multi-Part Design
### Assignment
This was another "Here's the drawings, good luck!" assignment. This one, however, had 9 parts instead of just one. Again, the assignment was checked by making sure the part had the right mass. Then, a dimension would be changed, and the mass would be checked again to make sure the part responded according to the design intent.
### Document
The document is available for viewing [here](https://cvilleschools.onshape.com/documents/ed3c96f86e2a8535b5e9c77b/w/da4a5a12cce6f82fbe864f02/e/842bff9739f4eecb64808e88?renderMode=0&uiState=6358002ab7948a2d7b5ab2d2).
### Media
![A screenshot of the part](/docs/multipart.png "An image of the full part.")
![A section view of the part](/docs/multipart_section.png "A cross-section of the part. Note the plunger in the middle of the cylinder.")
### Reflection
I really enjoyed this project. The big challenge here was designing the parts in the correct order to make it easiest to preserve design intent. For example, the bolts holding the part together needed to extend 15 mm past each end, so it made sense to design them after the cap parts to enforce this relationship. Then, when a revision pushed the caps farther apart, the bolts automatically expanded to preserve design intent.
