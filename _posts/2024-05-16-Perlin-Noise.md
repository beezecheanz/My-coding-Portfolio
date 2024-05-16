---
layout: post
title:  "Perlin Noise"
date:   2024-05-16 22:17:57 
---

# Perlin Noise

In class we looked into "random walkers", using Perlin noise and randomness to make things move around in an area.
In the session, we worked towards making interesting patterns and effects using these techniques. I mainly focused on using Perlin Noise over actual randomness.

### Simple Random Walker

(put example of code here >:D)


### More Complex Random Walker

(put example of more interesting one here)

I then went away and decided to use this movement to make a scene of a bee flying around in some flowers as I thought that the way Perlin Noise makes an object move was often quite similar to how insects fly. I also used this as a way to practice functions, as I used them to create the flowers, instead of individually making each flower. 

### Bee Flying
```
let c1,c2;

function setup() {
  createCanvas(1000, 1000);
}

function draw() {
 
  c1 = color(20,101,180);
  c2 = color(150, 230, 250);
  
  for(let y=0; y<height; y++){
    n = map(y,0,height,0,1);
    let newc = lerpColor(c1,c2,n); //makes a gradient
    stroke(newc);
    line(0,y,width, y);
    
  }
  
  stroke(0,0,0)

  let y = frameCount/2
  let x = 1000*noise(0.006*y)
  let z = 1000*noise(0.004*y)
  
  //background flowers
  flowers(45,840,180)
  flowers(180,870,150)
  flowers(420,860,190)
  flowers(600,850,100)
  flowers(750,840,120)
  flowers(975,870,120)
  
  //foreground flowers
  flowers(100,800,130) //draws a flower with a centre at 100, 800, 130 changes shade of petals
  flowers(500,800,150)
  flowers(300,850,160)
  flowers(650,850,160)
  flowers(900,850,140)
  flowers(800,750,180)
  
  clouds() //draws a cloud in the background
  
  bee(x,z,y) //draws a bee
}

function bee(x,z,y){
  
  push()
  translate(x,z+100) //makes the centre a semi random place
  
  fill(200,200,75)
  ellipse(0,0, 30, 25) //makes body of bee
  
  fill(100,100,100)
  triangle(14, -2, 14, 4, 25, 1) //stinger
  circle(-9,-3,4)
  
  fill(100,100,100, 80) //flapping wings
  rotate(-(y%10/50)*0.9,0) //rotates the wings a small amount for 10 frames,then resets
  ellipse(-6,-16,10,15)
  rotate(-(y%10/50)*0.7,0)
  ellipse(-1,-16,10,15)
  pop()
  
}


function flowers(a,b,c){

  push()
  translate(a,b) //changed centre to be where yellow circle is
    
  fill(130,220,130)
  rect(-15,0,30,300)
  
  fill(255,255,100)
  circle(0,0,60) //flower centre
 
  fill(220, 150, c)
  
  for (let i = 0; i < 16; i++) {

  rotate(0.4)
  ellipse(0,75,40,100)
    
  }
  
  pop() 
  
}

function clouds(){
  push()
  noStroke()
  
  let y = frameCount%1300 //reset after 1500 frames to make it a loop, making it look like multiple clouds

  //lots of circles, moving right based on frames
  circle(y-90,90,80)
  circle(y-70,120,100)
  circle(y-70,80,100)
  circle(y-160,160,80)
  circle(y-180,100,80)
  circle(y-160,100,100)
  circle(y-100,160,80)
  circle(y-200,160,90)
  circle(y-230,160,70)
  
  pop()
}

```
