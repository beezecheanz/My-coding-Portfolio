---
Title: Interaction
Date: 2024-05-20
---

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


### Blob Game
In class, we also went further with this simple interaction of clicking the mouse, and made a simple game,
where there are blobs on screen that can be clicked on. I went away and added a a few features to make it more game like,
including a score that increases with each successful click and a timer so the player can attempt to get a high score.
I also added easing on the movement of the blobs, I learnt how to do that from a [website I found](https://cratecode.com/info/p5js-easing-functions).

```
let clickBlob1, clickBlob2;
let score = 0;
let ease = 0.2; //how potent the easing is
let timer = 10;

function setup() {
  createCanvas(400, 400);
  //creating the blobs in their starting places
  clickBlob1=new clickBlob(200,100,50)
  clickBlob2=new clickBlob(200,300,50)
}

function draw() {
  background(220);
  clickBlob1.update()
  clickBlob2.update()
  clickBlob1.show()
  clickBlob2.show()
  
  text(score, 20,25)
  text(timer, 50, 25)
  
  //if a second has passed
  if (frameCount % 60 == 0 && timer > 0) {
    timer --;
  }
  if (timer == 0) {
    
    push() //so it doesn't change the numbers at the top
    textSize(35);
    noStroke();
    fill(230,50,50)
    text("GAME OVER", 100, 200);
    text(score, 200, 250)
    pop()
  }
  
}

function mousePressed(){ //when mouse is clicked
  clickBlob1.click()
  clickBlob2.click()
}

class clickBlob{
  constructor(x,y,s){
    this.x=x
    this.y=y 
    this.s=s
    this.hover=false
    
    //where they are being eased to
    this.targetY = y;
    this.targetX = x;
  }
  
  click(){
    if(this.hover){     
      //getting random place for them to go to
      this.targetX=random(width)
      this.targetY=random(height)
      score++
    }
  }
  
  show(){
    stroke(0)
    fill(128)
    if(this.hover){
      fill(0,200,100)
    }
    ellipse(this.x,this.y,this.s)
  }
  
  update(){
    let d=dist(this.x,this.y,mouseX,mouseY)
    this.hover=d<this.s/2
    
    // easeing towards the target positions
    this.x = lerp(this.x, this.targetX, ease);
    this.y = lerp(this.y, this.targetY, ease);
    
    if (timer == 0) {
      this.x=10000;
      this.y=10000;
    }
  }
}
```

### Art Program
I thought that a good way of having interaction in a simple way is to have something like an art program, where there are 
different brushes and colours the user can use to make things on the page. It is a fairly simple set up but gives the user a
lot of freedom and ability to experiment. It also has the opportunity to be added to, such as interesting brushes or filters.
