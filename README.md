# A completely from scratch 3D Renderer in Python

This 3D render in Python takes a camera and 3D Meshes located in 3d space and creates the 2D image the camera should display. It can render any valid 3D mesh composed of given faces. The faces of these 3D Meshes can also be any nonconcave shape.
The renderer is not complete as some bugs exist within the rasterization. I intend to properly implement back culling to speed up rendering and many other optimizations within rasterization. 

## How to Use

**First define your camera by inputting its FOV, resolution, location in 3d space, orientation in space, and view distance.**
**(horizontal_fov: int, vertical_fov: int, resolution: tuple, location: tuple, direction: tuple, view_distance: tuple)**

EX: cam1 = camera(90,90,(1000,1000),(0,0,0),(0,0,0),(1,1000))

**Create the canvas to your canvas size and background color as a RGB tuple.**
**(dimensions: tuple, background_color: tuple)**
EX: canvas = initialize_2dimage((1000,1000),(100,100,100))

**Create a height map that is used to keep track of items in view order. It should simply be a Numpy array of -(camera view distance) that is the same size as your canvas size**
EX: height_map = np.zeros([1000,1000])-1000

**Use "create_cube_mesh" function to give an example mesh to use. You can do this as many times as you want for all the cubes you want.**
**(side_length: int, center: tuple, rotation: tuple)**
mesh = create_cube_mesh(200, (0,0,500),(86,45,26))

**Render any mesh you want on to a canvas. The "render" function allows you to give an RGB tuple for the outline of each mesh face and the fill color for each mesh face.**
**(canvas: np.ndarray, height_map: np.ndarray, cam: camera, mesh: mesh3D, border_color: tuple, fill_color: tuple)**
canvas = render(canvas, height_map, cam1, mesh, (200,200,200), (0,0,0))



**save_image(canvas, "perfect image")**

(pixels: list, image_name: str)
Saves and displays the image you just created to the given file name.
