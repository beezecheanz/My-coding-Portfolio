---
Title: Interaction
Date: 2024-05-20
---

## Interaction

### First Tests
In class, we began a piece that would create a firework when the user clicked, which is one of the simplest forms of 
interaction a user can do. To push this idea further, a classmate and I added to this with randomising the 
colours and making it so that the colours slowly change over time.
I myself then added a few extra features, such as making the screen flash when the firework "explodes".

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
