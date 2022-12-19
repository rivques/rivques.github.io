---
title: "Fun With Overhangs"
date: 2022-12-19T17:16:29-0500
draft: true
math: true
---
Overhangs are annoying. When 3D printing, you must be cautious to avoid
having an overhang of more then a few dozen degrees, and if you do, you must support it
with extra support material. This material is annoying to remove and makes the print
take longer.

Recently, a few new techniques to print overhangs without support have been
popularized. Conical slicing and arc overhangs are two new ideas that allow the printing of
overhangs basically by always pulling filament against an already printed surface. I discovered
these ideas from [two](https://www.youtube.com/watch?v=1i-1TEdByZY) excellent [videos](https://www.youtube.com/watch?v=B0yo-o47688) by [CNC Kitchen](https://www.youtube.com/@CNCKitchen).

For one of my high school engineering projects, I needed a roller, which was basically a stack of
differently-sized circles on top of each other:
![A CAD model of a roller, with 4 large wheels on a thinner axle](/docs/fun-with-overhangs/roller-cad.png "A roller.")
Normally, this would be a massive pain to print, necessitating the use of a large amount of support material.
However, this model is an ideal candidate for support material elimination via arc overhangs. In fact, it's even easier then that,
because while arc overhangs need to glue many arcs together to form a shape, a simple circle can be printed easily.
![A visualization of how arc overhangs would need to fill a polygon](/docs/fun-with-overhangs/arc-overhang-preview.png "A visualization of how arc overhangs would need to fill a polygon. From github.com/stmcculloch/arc-overhang.")
![A circle filled by a spiral path](/docs/fun-with-overhangs/circle-spiral-gen.png "A toolpath to fill a circle with a spiral. Note how the outer edge of the spiral approaches the red circle.")
# The Journey
This project was nicely timed so that I could take on this challenge over winter break and put a lot of time into it.
I decided to try to write this G-code generator is Rust, because I've been meaning to learn the language for a while.
I really enjoyed the experience and found Rust a joy to use. The compiler feedback is impeccable, the integration
with VS code works great, and the speed is a nice bonus when I'm trying to get working code and don't want to spend
time optimizing my algorithms. My code is available at [github.com/rivques/FunWithOverhangs](https://github.com/rivques/FunWithOverhangs)
and should be pretty plug and play.
## Simple beginnings
I started by just trying to extrude a line across the build plate. I was initially using the [`gen_gcode`](https://docs.rs/gen_gcode/latest/gen_gcode/index.html)
crate, but I quickly realized that it would not be sufficient enough for my needs. Its `Point3d` type didn't support
any linear algebra operations, so it was a pain to do things like get the distance between two points, and it
didn't support all the G-code that I wanted to use. I suspect its author wrote it to support exactly as much as they
needed and no more, and they needed less than me. To fix this, I wrote my own module to handle G-code generation that does
exactly as much as *I* need and fixes a few of the issues I was having with `gen_gcode`. Even after I was generating coherent
G-code, I still wasn't able to get any extrusion. I figured my math to find how much I should extrude per millimeter I moved
was off. Even after fixing a confusion of the radius of the filament with the diameter, it still wasn't working. I had a hunch that
it might have something to do with the long Bowden cable not having enough time to build up the pressure to extrude filament.
Sure enough, longer lines worked enough that I was willing to push ahead.
![A thin extrusion of plastic](/docs/fun-with-overhangs/line.jpg "One of the first things I extruded with the G-code generator.")
## Cylinders
I next tried to generate a circle. A quick bit of research confirmed that there was a spiral with a consistent distance between its
lines. The Archimedean Spiral, with the conveniently simple formula $r=aθ$, has a consistent inter-line spacing of $2πb$. It
was fairly simple to plug my line width of $0.4$mm into this, then loop over $θ$ for however many rings were needed
to achieve the desired diameter. One issue I ran into was that Rust doesn't support iterating over a range with a non-integer
step, so instead of iterating in radians I iterated in degrees then immediately converted them to radians. Here's my code for
this, with a few modifications for clarity (again, the whole program is on my Github):
```rust
for theta_deg in (0..(360*(diameter/2.0/line_width).floor() as i32)).step_by(5) {
    let theta = theta_deg as f64 * PI / 180.0; // convert theta to radians
    let r = (spacing / (2.0*PI)) * theta; // compute r
    let point = point3!(r*theta.cos() + starting_location.x, r*theta.sin() + starting_location.y, printer.position.z);
    printer.extrude_to(point) // automatically calculate the needed extrusion
}
```
After I had a circle, it was easy to stack a few on top of each other, and now I was making cylinders!
![A small blue circle of plastic and a larger cylinder](/docs/fun-with-overhangs/first-circle.jpg "The first circle I printed next to a cylinder of stacked circles.")
