---
Title: Vera Molnar
Date: 2024-05-02
---

## Vera Molnar

### Who is Vera Molnar
In class, we looked at an artist called Vera Molnar, who is known as a pioneer in the field of generative art, often using repetiton to make interesting effects.

### Examples of her work

## Recreating her works
We were tasked with thinking about how we would go about recreating some of the effects in her works. I decided to recreate her well known piece that consists of squares within squares, each having a slightly different tone.

(put code here)

## Making my own works like Molnar's
Once I had gotten the hang of making repetition and variation work together to make patterns, I made a piece similar to Vera's, but with a bit more freedom than the one where I just attempted to recreate her pieces. I decided to incorporate movement and colour changing into it to see what it looked like, as her works were mainly quite plain looking and I wanted to see what it would look like when mixing the simple style with a more visually noisy style.
I think that it turned out quite well, although I would like if it looped better, but I found it difficult to get the colour timings to line up so I settled with the effect it currently gives.

```
let step
let numAcross=10
let col = 50;

function setup() {
  createCanvas(windowWidth, windowHeight);
  step=width/numAcross;
   colorMode(HSB, 100);
}

function draw() {
  //draws tiles the amount of times numacross is set to
  //when it reaches the end, it moves down a line
  //repeats until it has gone down the amount that numacross is
for(let j=0; j<numAcross; j++){
  for (let i=0; i<numAcross; i++){
    drawTile(i,j,step)
    }
  }
}

function drawTile(across, down, step){
  push()
  noStroke()
  col = map(noise(step), 0, 1, frameCount%360, 100);
  translate((across+0.5)*step, (down+0.5)*step)
  rotate(frameCount/60 + across - step)
  rectMode(CENTER)
  let r=noise(across*0.1, down/10, frameCount/50)
  let r2=noise(across*0.1, down/10, frameCount/50)
  
  //makes the squares, each is smaller than the last
  fill(col-80, 100, 100)
  rect(0,0,r*step*2.25,r2*step*2,25)
  
  fill(col-70, 100, 100)
  rect(0,0,r*step*2,r*step*2)
  
  fill(col-60, 100, 100)
  rect(0,0,r*step*1.75,r2*step*1.75)
  
  fill(col-50, 100, 100)
  rect(0,0,r*step*1.5,r*step*1.5)
  
  fill(col-40, 100, 100)
  rect(0,0,r*step*1.25, r2*step*1.25)
  
  fill(col-30, 100, 100)
  rect(0,0,r*step,r2*step)
  
  fill(col-20, 100, 100)
  rect(0,0,r*step*3/4, r2*step*3/4)
  
  fill(col-10, 100, 100)
  rect(0,0,r*step*1/2, r2*step*1/2)
  
  fill(col,100,100)
  rect(0,0,r*step*1/4,r2*step*1/4)
  pop()
}

```
