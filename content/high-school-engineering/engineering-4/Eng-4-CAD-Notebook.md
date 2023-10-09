---
title: "Engineering 4 CAD Notebook"
date: 2023-10-03T12:49:28-0400
draft: false
tocopen: true
---
# FEA Beam Part 1
## Assignment
This assignment is the first part of our introduction to finite element analysis (FEA), a technique for simulating how strong a design will be. We were challenged to make a 180mm cantilevered beam that could support the most weight among the class without flexing more than 35mm. The beam would be 3D printed in PLA and weigh no more than 13 grams. For the first part of the assignment, we couldn't use FEA and had to design our best guess at a strong beam based off of our research and intuition. To start, my partner Jayden and I each designed our own beam; planning to use whoever's worked better.
## My Beam
### Images
![A wide view of my beam](/docs/eng-4/beamwide.png "A wide view of my beam. The grey part is the testing apparatus.")
![A top view of my beam](/docs/eng-4/beamtop.png "A top view of my beam.")
### Design Reasoning
I went with an inverted T-beam as the base shape because that design did well last year. I added lots of lightening holes down the T to stay underweight. While the loading at the end of the beam is ostensibly straight down, I knew a few beams failed in torsion last year so I added some struts to try and stiffen it in that axis. The struts are very light so they don't make much of an impact to the weight limit. One area where I know the beam could improve is in having more material near the mount point and less near the load to more efficiently handle the stress. 
## Jayden's Beam
### Images
![A wide view of Jayden's beam](/docs/eng-4/jaydenwide.png "A wide shot of Jayden's beam.")
![A translucent view of Jayden's beam](/docs/eng-4/jaydentransparent.png "A view of Jayden's beam with hidden edges showing. Note the supports inside the hollow structure.")
### Design Reasoning
Here's Jayden's reasoning for his design:
> I went with a triangular design mostly on a whim, but it wasn't completely silly. Triangles are strong, and I made it hollow to keep that strength while also making it as light as possible. I put tiny support beams inside of it because I figured that they *might* help, but I'm not completely sure what they'll do. Essentially, I made a big Toblerone and hoped for the best. The main issue is that the part where the weights will hang from looks like it'll just snap off.
# FEA Beam Part 2
## Assignment
This assignment is an FEA analysis of the beam designed in part one. It will inform our future designs and tell us where we need add material and where we can afford to lighten.
## FEA Images
![A screenshot of the FEA displacement simulation.](/docs/eng-4/displ.png "A screenshot of the FEA displacement simulation.")
![A screenshot of the FEA stress simulation.](/docs/eng-4/stress.png "A screenshot of the FEA stress simulation.")
## Analysis
The stress is much stronger at the base of the beam, so I'll move material there. I'll get the mass budget to do this by removing material near the tip of the beam. The lightenting hoels are also very stressed, so I'll remove those from areas that are already high-stress.