## Interaction

### First Tests
In class, we began a piece that would create a firework when the user clicked, which is one of the simplest forms of interaction a user can do. We implemented a simple version of gravity, where the particles of the firework would slowly move downwards over time, adding to the realism of what was created.

#### Original Result
<img width="150" alt="thumbnail_image" src="https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/72338be0-2706-4ed7-a2e6-3a24b2621d31">

#### Additional Result
To push this idea further, a classmate and I added to this with randomising the 
colours and making it so that the colours slowly change over time.
I myself then added a few extra features, such as making the screen flash when the firework "explodes".
![fireworkshow](https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/25128b58-c6df-4b9f-9f39-85020e985c2b)

```
let firework
let r
let g 
let b 
let fc

function setup() {
  createCanvas(1000, 1000);
}

function draw() {
  background(5, 10);
  
  if(firework){
    firework.update()
  }
}

function mousePressed(){
    r = random(0,255); //generating random colours, a different set each time mouse pressed
    g = random(0,200); 
    b = random(0,200);
  
  firework=new Firework(mouseX, mouseY, random(20,200))
  background(r+150,g+150,b+150) //makes bg flash tint of white on click
    
}

class Firework{ 
  constructor(x,y,n){
    this.p=[]
    this.numParticles=n
    for(let i=0; i<this.numParticles; i++){ 
      this.p.push(new Particle(x,y))
    }
  }
  
  update(){

    
    for(let i=this.p.length-1; i>=0; i--){
      if(this.p[i].update()){
        this.p[i].show()
      } else {
        // remove it if particle off of screen
        this.p.splice(i,1)
      }
    }
    fill(255)

  }
  
}


class Particle{ //properties of the particles
  constructor(x,y){
    this.x=x
    this.y=y
    this.a=random(TWO_PI)
    this.speed=random(2.5,4.5) //randomises particle speed
    this.fall=0
    this.gravity=0.05
    this.moveX=cos(this.a)*this.speed
    this.moveY=sin(this.a)*this.speed
    this.lifeSpan=60 //how many updates the particles exist for
    this.ttl=this.lifeSpan //time to live
  }
  
  update(){
    this.x+=this.moveX
    this.y+=this.moveY
    this.y+=this.fall
    this.fall+=this.gravity
    
    this.ttl-- //takes one from time to live
    this.size=this.ttl
    return this.ttl>0 
    
  }
  
  show(){
     fill(r/this.ttl*this.lifeSpan,g/this.ttl*this.lifeSpan,b/this.ttl*this.lifeSpan) //fills with random colours that get lighter over time
    noStroke()
    ellipse(this.x, this.y, this.size/9) //gets smaller over time
    
  }
}
```

#### Experimental Results
I then experimented with changing variables in an attempt to make interesting results. I started with changing the background to white and opaque, so that the fireworks would stay on screen after having gone off. This made an interesting effect that looked like paint spattered across the page.
![loadsafirewrosk](https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/936ef4bb-851d-4fff-8bfe-ba2a222dbc56)

My next experiment was to see if I could make it so that multiple fireworks would spawn at the same time. I used the technique of just copying and pasting the part of the code that makes a firework and changing the variables so the colour and location were different. I could have looked into doing this in a more compact way but I thought that just for seeing how it looks, this way of doing it was good enough.
![download (2)](https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/34243ac4-ff87-461f-a7f1-6cdf117b72b3)

I then added a feature where, if the user drags the mouse after clicking, the firework explodes somewhat in the direction of the drag, making it much more interactive and interesting to play with.
[Interactive firework sketch](https://editor.p5js.org/beezecheanz/sketches/R7d7PKrej)


### Blob Game
In class, we also went further with this simple interaction of clicking the mouse, and made a simple game,
where there are blobs on screen that can be clicked on. I went away and added a a few features to make it more game like,
including a score that increases with each successful click and a timer so the player can attempt to get a high score.
I also added easing on the movement of the blobs as I thought that it made the game easier to follow and just looked nicer generally, I learnt how to do that from a [website I found](https://cratecode.com/info/p5js-easing-functions).
I added feedback when a blob is clicked by adding [a sound](https://freesound.org/people/fordps3/sounds/186669/) that plays after a successful click. I used [this sketch](https://editor.p5js.org/k1518155@students.katyisd.org/sketches/B1z411R3X) as an example to figure out how to implement it.
[click blob sketch](https://editor.p5js.org/beezecheanz/sketches/y6_r1Pqhn)

### Ink Blobs
We were introduced to [The Coding Train]((https://www.youtube.com/@TheCodingTrain), who makes video tutorials on different techniques that can be used in coding. I followed the [marbling algorithm tutorial](https://thecodingtrain.com/challenges/183-mathematical-marbling), that shows you how to make interesting marbled effects with "ink blobs" on a canvas. Thesse are the results I got from following the tutorial and looking at the code examples provided. I found the calculations kind of complicated so I basically [copied them line for line](https://editor.p5js.org/codingtrain/sketches/HtEtm1vii), however, for the actual creation of the blobs, I changed a few things while writing it. For example, I changed the colour palette to be a more muted one, as I thought it would look nice. I also changed the speed at which the blobs grow, as I thought it was more fun to play with when it goes faster.
![blobs](https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/a3dfc242-c498-420b-8533-0d87ee97f86a)
![blobbyblobs](https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/22c1833c-bdcf-4212-8935-ef761686f0e5)
[marbling.zip](https://github.com/beezecheanz/My-coding-Portfolio/files/15416208/marbling.zip)

