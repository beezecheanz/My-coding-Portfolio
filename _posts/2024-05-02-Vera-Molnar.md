## Vera Molnar

### Who is Vera Molnar
In class, we looked at an artist called [Vera Molnar](https://ropac.net/artists/231-vera-molnar/#), who is known as a pioneer in the field of generative art, often using repetiton to make interesting effects. Her pieces often include limited colours, usually only consisting of different types of greys, which draw more attention to the patters being created as there isn't much else going on visually.

### Examples of her work
![vera molnar piece 1, black and white squares](https://dam.org/museum/wp-content/uploads/2020/09/Molnar1974DesOrdres.jpg)
![vera molnar piece 2, square scribbles](https://dam.org/museum/wp-content/uploads/2020/08/molnar1985StructureDeQuadrilateres-2000x2000.jpg)
![vera molnar piece 3, squiggles](https://dam.org/museum/wp-content/uploads/2021/07/MolnarInterruptions28x28cm1968-69.jpg)

## Recreating her works
We were tasked with thinking about how we would go about recreating some of the effects in her works and shown how to replicate the looks of her [classic pieces involving black and white squares](https://dam.org/museum/artists_ui/artists/molnar-vera/des-ordres/#lightbox[rel-13052-1738219330]-4) , which are shown in the examples of her work above.
We created this code in class, following along with a demo, but changing things like variables to fit what we wanted the creation to look like.

![veramolnarsquaresexample](https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/425ef421-040b-4973-9ccc-ef48b856a210)

```
let step;
let numAcross=17; //amount of tiles across

function setup() {
  createCanvas(500, 500);
  step=width/numAcross;
  frameRate(1); //so that it doesn't run too fast
}

function draw() {
  background(220);
  
  //goes across the amount decided by numAcross
  //then goes down one and starts again
  //until it has gone down the amount that it goes across
  for(let j=0; j<numAcross; j++){
    for(let i=0; i<numAcross; i++){
      drawTile(i,j,step)
    } 
  }
}

function drawTile(across, down, step){
  let numSquares=10 //number of squares inside
  push()
  translate((across+0.5)*step, (down+0.5)*step)
  rectMode(CENTER) //draws squares from their centre
  for(let k=numSquares-1; k>=0; k--){
    let r=random(10)
    fill(random(40,150)) //fill with random grey
    if(r<5){
      rect(0,0,step*k/numSquares)
    }
  }
  
  pop()
}
```

## Experimentation
I then went and found [this YouTube tutorial](https://www.youtube.com/watch?v=kjB_3pWmTR8) to create a similar piece of code, this time with offset quadrilaterals of different colours. I did one test where I precisely followed the tutorial, then I played around with changing variables to make interesting results. These are there results.

### Exactly following tutorial
Here is the result I got from following the tutorial
![squares](https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/0d86518f-e89d-4eae-9d61-1c12af51eba1)

### Changing colour
Here are the results from where I tried to make it look more appealing to me, by changing the colour scheme to be more coherent and increasing the number of cells so that they begin to overlap, which I think looked quite interesting.
![overlappingsquares](https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/26f109c1-ff16-4f28-8d6a-dc7935c83440)

### Changing everything
I then just went through and changed variables until it created interesting effects.
![booksqaure](https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/00fa134c-6801-4e7e-8ec3-7147da0fb6e2)
![crazysquares](https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/b85d2a6d-169d-4171-9787-c1cd7c6612f8)
![squigglesquare](https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/94994516-dd5d-4f67-b515-9089d7284713)

## Making my own works like Molnar's
Once I had gotten the hang of making repetition and variation work together to make patterns, I made a piece similar to Vera's, but with a bit more freedom than the one where I just attempted to recreate her pieces. I decided to incorporate movement and colour changing into it to see what it looked like, as her works were mainly quite plain looking and I wanted to see what it would look like when mixing the simple style with a more visually noisy style.
[Rainbow Squares Sketch](https://editor.p5js.org/beezecheanz/sketches/mzh8PAEoo)
![rainnbowsqures](https://github.com/beezecheanz/My-coding-Portfolio/assets/83460384/674b7d41-c6e0-4f9e-8739-28c4b4f35138)

