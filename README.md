# particle-array
game

//SKETCH.JS
var person;

var obstacle;

function setup() {
  createCanvas(640, 360);
  person = new Person();
  
}

function keyPressed(){
   if (key == ' ') {
       var jump = createVector(0,-5);
     person.applyForce(jump);
   }
 }

function draw() {
  background(51);
  translate(-person.pos.x + 50, 0);
  var gravity = createVector(0,0.1);
  person.applyForce(gravity);
  if(mouseIsPressed) {
  var force = createVector(-0.1,0);
  person.applyForce(force);

  }


  person.update();
  person.edges();
  person.display();
  //trasnslate(-person.pos.x,0);

  fill(225, 0, 100);
  rect(400, height-50,50,50);
 }



//INDEX.HTML
 html, body {
  margin: 0;
  padding: 0;
}
canvas {
  display: block ;
}


//STYLE.CSS
html, body {
  margin: 0;
  padding: 0;
}
canvas {
  display: block ;
}


//PERSON.JS
function Person() {
  this.pos = createVector(50, 250);
  this.vel = createVector(1, 0);
  this.acc = createVector(0, 0);
  this.mass = 10;

  this.applyForce = function(force) {
    this.acc.add(force);
  }

  this.update = function() {
    this.vel.add(this.acc);
    this.pos.add(this.vel);
    this.acc.set(0, 0);
  }

  this.display = function() {
    fill(255, 150);
    stroke(255);
    rect(this.pos.x, this.pos.y, this.mass*10, this.mass*10);
  }

  this.edges = function() {
    if (this.pos.y > 250) {
      this.vel.y *= 0;
      this.pos.y = 250;
   
    }
  }
}
