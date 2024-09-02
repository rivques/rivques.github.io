---
title: "Labyrinth for Sprig"
date: 2024-09-02T00:01:00-0400
draft: false
aliases: [/lbrnth]
---
This is a port of the [Labyrinth board game](https://boardgamegeek.com/boardgame/1219/labyrinth) to the Sprig.

## How to Play
This is designed as a pass-and=play game where the goal is to collect all of your artifacts from the shifting labyring before your opponents do. The game is played on a grid of maze tiles, many of which can be moved around. On your turn you'll shift the labyrinth, then move your player within the maze, trying to collect your target artifact. Once you've collected all of your artifacts, you win!

### Game Pieces
* Tiles: These are the pieces that make up the labyrinth. Many can be moved around the board. They are black with white passages, with a light grey dotted line at the boundary of the tile.
* Players: Each player is a small hollow square of their color.
* Cursor: This is a large hollow square of your color.
* Artifacts: These are small patterns (plus, circle, U, bars, square, checkers) in one of four colors (brown, pink, purple, orange). These are your targets. Your current target artifact is shown on the left of the screen. Once you collect an artifact, it'll be removed from the board and your score will go down by one. Once your score hits zero, you win!

### Moving the Labyrinth
When it's your turn, you'll first move the labyrinth. You'll have a tile in your hand that you can insert into some rows and columns of the labyrinth. Use W/S to change where you'll insert the tile, use A/D to rotate it, then press L to insert it. Some tiles can never move. These tiles are framed in dark grey arrows. Once you insert your tile, the row or column you inserted it into will shift, pushing the last tile in the row or column out. This tile will become the next held tile.

If you push a player off the board, they'll wrap around to the other side. 

You can't directly undo the move of the person before you.

### Moving Your Player
After you've moved the labyrinth, you'll move your player. Use the WASD keys to move your cursor to where you want to move, then press L to confirm. You can only move to tiles you can reach by travelling through the labyrinth. If you land on a tile with your target artifact, you'll collect it.