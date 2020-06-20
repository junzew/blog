---
layout: post
title:  "Conway's Game of Life"
categories: Python
---

# Conway's Game of Life
In honor of [John Horton Conway](https://en.wikipedia.org/wiki/John_Horton_Conway), the inventor of [Game of Life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life), who recently passed away due to COVID-19 complications.

## Game Rules
Given a board with *m* by *n* cells, each cell has an initial state *live* (1) or *dead* (0). Each cell interacts with its eight neighbors (horizontal, vertical, diagonal) using the following four rules:

1. Any live cell with fewer than two live neighbors dies, as if caused by under-population.
2. Any live cell with two or three live neighbors lives on to the next generation.
3. Any live cell with more than three live neighbors dies, as if by over-population..
4. Any dead cell with exactly three live neighbors becomes a live cell, as if by reproduction.


## Example
Glider
![sieve animation]({{ "/assets/Sieve_of_Eratosthenes_animation.gif" | absolute_url }})

## Running Pygame in a Browser

It turns out that you can run a pygame application in the browser by compiling it to JavaScript.

There is a library called Pyjsdl that does this. It is built on top of the PyJs compiler. I managed to convert a Conway's game of life written with pygame into an [HTML web page](https://junzew.github.io/game-of-life/game.html).

## Steps
* Install Ubuntu Linux in VirtualBox
I am using a Mac but pyjsdl works on Linux so I installed an Ubuntu VM on my machine

* Install `Python` and `pip`
```
sudo apt update
sudo apt install python3-pip
sudo apt install python2
curl https://bootstrap.pypa.io/get-pip.py --output get-pip.py
sudo python2 get-pip.py
```
* Install `git`
```
sudo apt install git
```
* Install [`Pyjs`](https://github.com/pyjs/pyjs/wiki/GettingStarted) from source
```
git clone https://github.com/pyjs/pyjs.git
cd pyjs
sudo python2 setup.py install
```
Now you should have the  `pyjsbuild` tool installed.
* Install pygame
```
sudo apt install python-pygame
```
* Download the [Pyjsdl](https://gatc.ca/2013/07/31/deploy-javascript-application-using-pyjsdl/) module and unpack into the folder containing your game python script
```
wget https://s3.gatc.ca/files/pyjsdl-0.22.zip
unzip pyjsdl-0.22.zip
```
* Modify python game script
  * Replace `import pygame` with `import pyjsdl as pygame`
  * Move the code inside the main loop to a `run()` function and get rid of the while loop. Call `
pyjsdl.display.setup(run)` to start executing the `run()` function in a loop automatically
* Compile the python script to JavaScript
```
pyjsbuild game.py
``` 
This generates a `game.html` file in the folder named `output` that can be run in a browser.

## Reference
* http://bearums.github.io/games/pyjsdlguide.html

Note: This guide contains a mistake in Step 2: Install PyJsdl that tripped me up. The URL for downloading the zip file is wrong. It is not the actual PyJsdl library but just an exmple script you can use to test everything is set up properly.

* https://leetcode.com/problems/game-of-life/

