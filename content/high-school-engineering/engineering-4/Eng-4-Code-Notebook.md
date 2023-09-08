---
title: "Engineering 4 Code Notebook"
date: 2023-08-28T11:34:44-0400
draft: false
tocopen: true
---
# The main code repository is located [here](https://github.com/rivques/Engr4Code).
## Media test:
![My profile picture](https://avatars.githubusercontent.com/u/38469076?s=400&u=3ce10d01190bcef83bee3d286e2c631144cc1ebc&v=4 "My profile picture")
![A previous project of mine running](/docs/WTPIDC/running.gif "A test GIF") 
## Launchpad part 1
This is the first in a series of assignments in which I build a simulated launchpad. For this assignment I just had to make the Pico count down from 10 to 1 in the console.
### Media
![A GIF of the console working.](/docs/eng-4/launch1.gif "A GIF of the countdown working. It was filmed very poorly for Reasons. Future gifs will be higher quality.")
### Wiring
No wiring was needed for this assignment.
### Reflection
This was a nice test project to make sure I had everything configured properly. (I didn't.) I ended up changing upload toolchains from MicroPython to my CPyProjectTemplate, remembering to change the board type from last year's Metro Express to the Pico W. There was also a good bit of fighting with Git over this change, and after running into errors tring to `git revert` a few times, I ended up deleting the repo and starting over from the template, which wasn't a huge problem because I hadn't done much work in the deleted repo.
## Launchpad part 2
This is the second assignment in the launchpad series. We had to add a red flashing light to the Pico that blinked in sync with the countdown, and a green light that turned on at liftoff.
### Media
![A GIF of the lights blinking in sync with the console](/docs/eng-4/launch2.gif)
### Wiring
![The schematic](/docs/eng-4/launch2schem.png "The schematic for this assignment.")
### Reflection
This went mostly without hitches, but there was one nuance: When a CircuitPython ends, all hardware is deinitialized and set to an input. This turns off all connected components.
Because of this, when my program immediately ended after turning on the green LED it turned right back off. To prevent this I added an infinite loop at the end of the program.
## Launchpad part 3
This is the third assignment in the launchpad series. We added a button that could start and stop the countdown.
### Media
![A GIF of the abort button being used](/docs/eng-4/launch3.gif "The launchpad being started and aborted.")
### Wiring
![The schematic](/docs/eng-4/launch3schem.png "The schematic for this assignment")
### Reflection
I did the spicy option here, which involved adding an abort button. This was non-trivial because I had to watch the button *while delaying.* A full async framework would have been overkill for this, so I just wait for 0.05 seconds then check the button for 20 times.
## Launchpad part 4
This is the fourth assignment in the launchpad series. We added a servo to "release the rocket" as the clock hit zero It had to start its move at T-3 and smoothly finish at T-0.
### Media
![A GIF of the abort button being used with the servo sweeping](/docs/eng-4/launch4.gif "The launchpad being aborted as the servo sweeps.")
### Wiring
![The schematic](/docs/eng-4/launch4schem.png "The schematic for this assignment")
### Reflection
Having to make the servo move smoothly made me realize the way I wrote part 3 was *really inextensible.* I had apparently forgotten about being able to use `time.monotonic()` instead of `time.sleep()` for doing stuff while delaying. With the help of Arduino's `map()` function, I was able to get the servo moving pretty smoothly.