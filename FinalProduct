import processing.video.*;      // required to get webcam access
Cell[][] grid;

// Number of columns and rows in the grid
int cols;
int rows;
int index;
int dx;
int dy;
int spacing = 10;    // grid spacing 
color spore1, spore2, spore3, spore4;
Capture camera;      // instance of the Capture class, used 
                     // to get frames from the camera


void setup() {
  spore1 = 250;
  spore2 = 200;
  spore3 = 100;
  spore4 = 0;
  // make our sketch always run fullscreen
  // note! this means our code below all has to be relative to
  // the width and height variables
  size(displayWidth, displayHeight);
  
  // alternatively, set your sketch to run fullscreen (similar to Present Mode)
  // fullScreen();

  // get a list of all available cameras
  // (if there are none, it means no camera was detected)
  String[] cameras = Capture.list();
  if (cameras.length == 0) {
    println("Couldn't detect any cameras!");
    exit();
  } 
  else {
    println("Available cameras:");
    printArray(cameras);
  }

  // instead of selecting from the list, we can specify the width and
  // height of the camera's input (this will be faster than resizing
  // the image below)
  camera = new Capture(this, width,height);
  
  // for external cameras, you may need to specify the camera's name,
  // which you can get from the list we printed earlier
  // camear = new Capture(this, width,height, "FaceTime HD Camera", 30);
  
  // start the camera input!
  camera.start();
}


void draw() {
  
  // only draw if there's a new frame available from the
  // camera (saves unecessary processing)
  if (camera.available()) {
   background(random (220),random (220),random (220));
    
    // read the frame from the camera
    camera.read();
    
    // draw the camera's frame, stretched to fit the screen
    image(camera, 0,0);
    filter(POSTERIZE, 4);
    // set(0,0, camera);      // does the same thing and is sometimes faster than image()
  //   tempAdj = map(mouseX, 0,width, -100,100);
  //hueAdj = map(mouseY, 0,height, -100,100);
    // go through the frame's pixel values in a grid
    rows = height;
    cols = width;
    grid = new Cell[cols][rows];
    loadPixels(); 
    makeCells();
    //runCells();
    

    //     for (int i=0; i<pixels.length; i++) {
    //float r = pixels[i] >> 16 & 0xFF;
    //float g = pixels[i] >> 8 & 0xFF;
    //float b = pixels[i] & 0xFF;
    
    //r += tempAdj;
    //r = constrain(r, 0,255);
    //g += hueAdj;
    //g = constrain(g, 0, 255);
    //b -= tempAdj;
    //b = constrain(b, 0,255);
    
    //pixels[i] = color(r, g, b);
    
    //  }
    }
  }
  
  
  
  void makeCells(){
  for (int y=0; y<height; y+=spacing) {
      for (int x=0; x<width; x+= spacing) {
        
        // get the index in the pixel array for this x/y point
        // (note that normally we'd use y*width+x, but that gives
        // us an image that is flipped horizontally and wouldn't
        // feel natural – the equation below makes the input look 
        // like a normal mirror)
        
        index = (width-x-1) + y*width;
        // set the fill color to the current pixel and draw a 
        // circle there
   if (index > spore1)
    {
      dx = (int)random(-10,10);
      dy = (int)random(-10,10);
    }
    else if (index > spore2)
    {
      dx = (int)random(-2,2);
      dy = (int)random(-5,5);
    }
   else if (index > spore3)
    {
       dx = (int)random(-1,1);
        dy = (int)random(-2,2);
    }
    else if (index > spore4)
    {
      dx = (int)random(-1,1);
      dy = (int)random(-1,1);
    }
        grid[x][y] = new Cell(x+spacing/4 + dx,y+spacing/4 + dy, spacing,spacing,index);
  }
  }
  }
  // A Cell object

// A Cell object
class Cell {
  // A cell object knows about its location in the grid 
  // as well as its size with the variables x,y,w,h
  float x,y;   // x,y location
  float w,h;   // width and height
  float angle; // angle for oscillating brightness

  // Cell Constructor
  Cell(float tempX, float tempY, float tempW, float tempH, int index) {
    x = tempX;
    y = tempY;
    w = tempW;
    h = tempH;
    fill(pixels[index]);
        strokeWeight(.2);
        
    rect(x,y,w,h); 
 
  } 
  
  // Oscillation means increase angle
  void oscillate() {
    angle += 0.02; 
  }


//  The World class simply provides two functions, get and set, which access the
//  display in the same way as getPixel and setPixel.  The only difference is that
//  the World class's get and set do screen wraparound ("toroidal coordinates").
}
 
