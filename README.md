# A completely from scratch 3D Renderer in Python

This is a 3d render in Python that takes a camera and cubes located in 3d space and creates the 2D image the camera should be displaying.
The renderer is not complete as some bugs exist within the rasterization. I intend to properly implement back culling to speed up rendering and many other optimizations within rasterization. 

## How to Use

**cam1 = camera(90,90,(1000,1000),(0,0,0),(0,0,0),(1,1000))**

(horizontal_fov: int, vertical_fov: int, resolution: tuple, location: tuple, direction: tuple, view_distance: tuple)
 First define your camera by inputting its FOV, resolution, location in 3d space, orientation in space, and view distance.

**canvas = initialize_2dimage((1000,1000),(100,100,100))**

(dimensions: tuple, background_color: tuple)
Create the canvas to your canvas size and background color as a RGB tuple.

**height_map = np.zeros([1000,1000])-1000**

Create a height map that is used to keep track of items in view order. It should simply be a Numpy array of -(camera view distance) that is the same size as your canvas size

**mesh = create_cube_mesh(200, (0,0,500),(86,45,26))**

(side_length: int, center: tuple, rotation: tuple)
This function gives you the mesh for a cube that you specify. You can do this as many times as you want for all the cubes you want.

**canvas = render(canvas, height_map, cam1, mesh, (200,200,200), (0,0,0))**

(canvas: np.ndarray, height_map: np.ndarray, cam: camera, mesh: mesh3D, border_color: tuple, fill_color: tuple)
This function will render a mesh onto a canvas by returning the canvas with the mesh rendered onto it. It also allows you to give an RGB tuple for the outline of each mesh face as well as the fill color for each mesh face.

**save_image(canvas, "perfect image")**

(pixels: list, image_name: str)
Saves and displays the image you just created to the given file name.
