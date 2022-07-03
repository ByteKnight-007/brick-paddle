let ball_x,ball_y,ball_dx,ball_dy,ball_radius;
let paddle_x,paddle_y,paddle_width,paddle_height,paddle_dx;
let brick_x,brick_y,brick_width,brick_height;
let lives,scores;
let b,v,x,y,w,h;
let grid = [];
let bol;
function setup() {
  createCanvas(400, 400);
  
  //paddle's properties
  paddle_x =(width/2) - 40;
  paddle_y = height -20;
  paddle_height =15;
  paddle_width =80;
  paddle_dx= 3;
  
  //ball's property
  ball_x = width/2-40;
  ball_y = height/2-10;
  ball_dx = 2;
  ball_dy = 2;
  ball_radius =25;
  
  //brick's property
  brick_x =(width/2)-180;
  brick_y =height-350;
  brick_height= 20;
  brick_width = 60;
  
  //parameters
  lives =3;
  scores = 0;
  bol = true;
  
  //brick setup
  for(let i=0;i<=4;i++){
    let brick = [];
    for(let j=0;j<=3;j++){
      brick.push({x:(i*80)+10,y:(j*35)+20,w:brick_width,h:brick_height,v:true})
    }
    grid.push(brick);
  }
  }


function draw() {
  
  background('rgb(37,88,47)');
  ball_x += ball_dx;
  ball_y += ball_dy;
  if(keyIsDown(RIGHT_ARROW)){
    paddle_x += paddle_dx;
  }
  if(keyIsDown(LEFT_ARROW)){
    paddle_x -= paddle_dx;
  }

  fill('rgb(231,217,145)');
  circle(ball_x,ball_y,ball_radius);
  fill("rgb(116,119,236)")
  rect(paddle_x,paddle_y,paddle_width,paddle_height)

  
  //right and left boundary constraints for ball
  if(((ball_x + (ball_radius)/2)>width) || ((ball_x - (ball_radius)/2)<0)){
    ball_dx = -(ball_dx);
  }
  //bottom boundary constraints for ball
  if((ball_y + (ball_radius)/2)>height) {
    //ball = -(ball_dx)
    ball_dy = -ball_dy;
    if(lives!==0){
       lives -= 1;
     }
    if(scores===20){
      ball_dx =0;
      ball_dy=0;
      fill('yellow');
      text("You have won!",width/2-50,height/2);
    }
    if (lives === 0){
      ball_dx = 0;
      ball_dy = 0;
      fill('red')
      text("GAME OVER",width/2-50,height/2);
      
    }
    
  }
  
  //top boundary constraints for ball
  if ((ball_y - (ball_radius)/2)<0){
    ball_dy = -(ball_dy)
  } 
  
  //  Boundary constraint for paddle
  if (paddle_x<0){
      paddle_x = 0;
  }
  if(paddle_x+80>width){
    paddle_x = width-paddle_width;
  }
  
  //ball bouncing from paddle
  let y_constraint = ball_y + (ball_radius)/2;
  if((y_constraint>=paddle_y)&&(ball_x>=paddle_x)&&(ball_x<=paddle_x+paddle_width)){
    if(bol===true){
      ball_dy = -(ball_dy);
      bol = false;
    }
  }
  else{
    bol = true;
  }
  
  
  //conditions for dissapearence of the brick
  for(var i=0;i<=4;i++){
    for(var j=0;j<=3;j++){
      fill('rgb(160,205,220)')
      rect(grid[i][j].x,grid[i][j].y,grid[i][j].w,grid[i][j].h);
      if(ball_x-(ball_radius/2) < grid[i][j].x + grid[i][j].w &&
        ball_y > grid[i][j].y && ball_y <grid[i][j].y + grid[i][j].h && ball_x + (ball_radius/2) > grid[i][j].x){
        ball_dx = -ball_dx;
        scores++;
        grid[i][j].h=0;
        grid[i][j].w=0;
      }
      
       if(ball_y-(ball_radius/2) < grid[i][j].y + grid[i][j].h &&
        ball_x > grid[i][j].x && ball_x <grid[i][j].x + grid[i][j].w && ball_y + (ball_radius/2) > grid[i][j].y){
        ball_dy = -ball_dy;
        scores++;
        grid[i][j].h=0;
        grid[i][j].w=0;
      } 
    }
  }
  
  fill('rgb(231,132,132)')
  text(`Scores:${scores}`,width-100,20);
  text(`Lives:${lives}`,width-380,20);
  
}
