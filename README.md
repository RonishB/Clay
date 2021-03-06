# Clay: 3D Graphics Engine
**Experimental Beta (Cross-Platform Coming Soon!)**

``` 
$ 3D Graphics Engine with built-in movement functionality 
$ Written from scratch without the use of external libraries
 ```
 
## Startup
#### Requirements
* Windows OS
* VisualStudio 2017/2019 (Or any C++ compiler)
#### Launch
//note: can put in numbered list
* Clone the repository
* In OnUserUpdate(), instantiate an instance of an object by either passing in the path to your object file, or constructing an object(s) yourself

To test, two obj files are provided (teapot/teddy), and sample obj files are freely available on the internet. Optionally, models in tools such as Blender easily export to obj format

Passing in obj file:
```
object o("path/to/objfile");
```

Constructing object manually (this will construct a cube):
```
object o;
o.tris = {
 { Vertex(0.0f, 0.0f, 0.0f), Vertex(0.0f, 1.0f, 0.0f), Vertex(1.0f, 1.0f, 0.0f) },
 { Vertex(0.0f, 0.0f, 0.0f), Vertex(1.0f, 1.0f, 0.0f), Vertex(1.0f, 0.0f, 0.0f) },                                                  
 { Vertex(1.0f, 0.0f, 0.0f), Vertex(1.0f, 1.0f, 0.0f), Vertex(1.0f, 1.0f, 1.0f) },
 { Vertex(1.0f, 0.0f, 0.0f), Vertex(1.0f, 1.0f, 1.0f), Vertex(1.0f, 0.0f, 1.0f) },                                                  
 { Vertex(1.0f, 0.0f, 1.0f), Vertex(1.0f, 1.0f, 1.0f), Vertex(0.0f, 1.0f, 1.0f) },
 { Vertex(1.0f, 0.0f, 1.0f), Vertex(0.0f, 1.0f, 1.0f), Vertex(0.0f, 0.0f, 1.0f) },                                               
 { Vertex(0.0f, 0.0f, 1.0f), Vertex(0.0f, 1.0f, 1.0f), Vertex(0.0f, 1.0f, 0.0f) },
 { Vertex(0.0f, 0.0f, 1.0f), Vertex(0.0f, 1.0f, 0.0f), Vertex(0.0f, 0.0f, 0.0f) },                                                  
 { Vertex(0.0f, 1.0f, 0.0f), Vertex(0.0f, 1.0f, 1.0f), Vertex(1.0f, 1.0f, 1.0f) },
 { Vertex(0.0f, 1.0f, 0.0f), Vertex(1.0f, 1.0f, 1.0f), Vertex(1.0f, 1.0f, 0.0f) },                                               
 { Vertex(1.0f, 0.0f, 1.0f), Vertex(0.0f, 0.0f, 1.0f), Vertex(0.0f, 0.0f, 0.0f) },
 { Vertex(1.0f, 0.0f, 1.0f), Vertex(0.0f, 0.0f, 0.0f), Vertex(1.0f, 0.0f, 0.0f) },
};
```
  
### 

## API Implementation

### Construct Console

Constructs the console window given the width and height of the screen as well as the width and height of each character. The below code will initialize the console in the main cpp file. 

```
 int main()
 {
   App clay;
   if (clay.ConstructConsole(300, 300, 1, 1))
   {
     clay.Start();
   }
 }
```

| Parameter  | Type | Required  | Default Value | Description  |
|---|---|---|---|---|
| width  |  int  |  |  | The desired width of the window  | 
|  height | int  |   |  | The desired height of the window  |
|  fontw | int  |   |  | The desired number of pixels in the width of each character |
|  fonth | int  |   |  | The desired number of pixels in the height of each character  |



### Draw Line

Draws a line using a combination of the Bressenham and the Digital Differential Analyzer (DDA) algorithm. The below code draws a line from the top right of the screen to (250, 350).

```
 DrawLine(0, 0, 250, 350);
```


| Parameter  | Type | Required  | Default Value | Description  |
|---|---|---|---|---|
| x0  |  int  |  |  | The X coordinate of the beginning of the line  | 
|  y0 | int  |   |  | The Y coordinate of the beginning of the line   |
|  x1 | int  |   |  | The X coordinate of the end of the line  |
|  y1 | int  |   |  | The Y coordinate of the end of the line  |
|  c | short  |  optional  | 0x2588 | The shading of the line (SOLID/THREEQUARTERS/HALF/QUARTER) |
|  col | short  | optional  | 0x000F | The color of the line |




### Rotate

Rotates the object by the given angle around any axis. The below code demonstrates how to use the Rotate function by 1.4 radians around the X and Z axis, with the rotation around the X and Y axes sped up 2.5x and 1.3x respectively. However, fTheta is also computed for you, and passing in fTheta in OnUserUpdate() will continuously rotate the given object.

```
 Object.Rotate(1.4f, true, false, true, 2.5f, 1.3f);
```

| Parameter  | Type | Required  | Default Value | Description  |
|---|---|---|---|---|
| fTheta  |  float  |  |  | The angle of rotation in radians  | 
|  X | bool  |   |  | True if the rotation is in the X-axis  |
|  Y |  bool |   | |True if the rotation is in the Y-axis   |   
|  Z |  bool |   | |True if the rotation is in the Z-axis   |  
|  xSpeed |  float |  Optional | 1.0 | The speed of movement in the X direction   | 
|  ySpeed |  float |  Optional | 1.0 | The speed of movement in the Y direction   | 
|  zSpeed |  float |  Optional | 1.0 | The speed of movement in the Z direction   




### Translate

Translates the object in any direction. The below code will move the object 15 characters to the right at 2x the speed, and 2.5 characters up in the Y-axis.

```
 Object.translate(15.0f, 2.5f, 0.0, 2.0f);
```

| Parameter  | Type | Required  | Default Value | Description  |
|---|---|---|---|---|
| x  |  float  | Optional | 0.0 | The distance translated in the X-axis | 
|  y | float  | Optional  | 0.0 | The distance translated in the Y-axis  |
|  z |  float |  Optional |0.0 | The distance translated in the Z-axis   |   
|  xSpeed |  float |  Optional | 1.0 | The speed of movement in the X direction   | 
|  ySpeed |  float |  Optional | 1.0 | The speed of movement in the Y direction   | 
|  zSpeed |  float |  Optional | 1.0 | The speed of movement in the Z direction   |

onUsercreate on userupdate


## Acknowledgments
 `Ishan Ghimire, Erfan Huq, and Rakin Mohammed`
