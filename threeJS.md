# Three JS

![3d cube](https://cloud.githubusercontent.com/assets/7386478/23084724/d556a074-f531-11e6-8325-511ac6a9e78a.png)

Three.js is a cross-browser JavaScript library/API used to create and display animated 3D computer graphics in a web browser. Three.js uses WebGL. The source code is hosted in a repository on GitHub. The main components create an app are a camera, a renderer, and a scene. Think of it this way, we are rendering a scene with a camera.

### Uses

Thress.js is used in adding layers and graphics to online media, advetising, games, and apps, especially in VR and AR. Threejs relies on either HTML5 canvas or WebGL.

The Canvas element can be used with either a 2D context or a WebGL context. threejs can use either the WebGL or the 2D context.

Most mobile phones support the 2D context. Few support WebGL context yet. Firefox for mobile supports WebGL and is available for at least some android builds, and the BlackBerry PlayBook can use it too.

[webGl](http://caniuse.com/#feat=webgl);
[canvas](http://caniuse.com/canvas)



### To Get started

Paste the following into an index.html file in the root directory. 
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <title>My first three.js app</title>
        <style>
            body { margin: 0; }
            canvas { width: 100%; height: 100% }
        </style>
    </head>
    <body>
        <script src="js/three.js"></script>
        <script>
            // Our Javascript will go here.
        </script>
    </body>
</html>
```

Then we will create the directory the three.js file will go into. 
- `mkdir js`
- `cd js`
- `touch three.js`
- `touch shape.js`
Then follow this link to the [three.js build] and paste the library for our index.html to reference. 

That's it for local setup! We will provide code from the official documentation which can either be imported directly into your HTML file, or you can change the script tags to link to a separate javascript file. 


## Basics

Creating a scene
 1. set a scene variable on the THREE object calling the scene method
 2. set a camera var on the THREE object calling the PerspectiveCamera method with specified porperties
 3. set a renderer on the THREE object calling the WebGlrender method
    ```renderer.setSize( window.innerWidth, window.innerHeight );```
    ```document.body.appendChild( renderer.domElement );```


[codepen](http://codepen.io/super996/pen/jyowjR?editors=1010)

## Shapes

There are dozens of geometries to choose from. The takeaway here is that a buffer geometry is different from a regular geometry is that this class is an efficient alternative to Geometry, because it stores all data, including vertex positions, face indices, normals, colors, UVs, and custom attributes within buffers; this reduces the cost of passing all this data to the GPU.

Also...

[stackoverflow](http://stackoverflow.com/questions/35058389/three-js-questions-about-the-use-of-three-buffergeometry)

## Resources

[reddit](https://www.reddit.com/r/threejs/)
[stackoverflow](https://stackoverflow.com/questions/tagged/three.js)
[learnthreejs](http://learningthreejs.com/)
[treehouse](https://teamtreehouse.com/community/the-beginners-guide-to-threejs)

### Commented Code


# Three JS

Three.js is a cross-browser JavaScript library/API used to create and display animated 3D computer graphics in a web browser. Three.js uses WebGL. The source code is hosted in a repository on GitHub.

### Local Installation
- mkdir 3js_practice
- cd 3js_practice

Paste the following into an index.html file in the root directory. 
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <title>My first three.js app</title>
        <style>
            body { margin: 0; }
            canvas { width: 100%; height: 100% }
        </style>
    </head>
    <body>
        <script src="js/three.js"></script> 
        <script src="js/shape.js"></script>
    </body>
</html>
```

Then we will create the directory the three.js file will go into. 
- `mkdir js`
- `cd js`
- `touch three.js`
Then follow this link to the [three.js build] and paste the library for our index.html to reference. Alternatively, replace the first script with the CDN script
```javascript
<script src="js/three.min.js"></script>
```

That's it for local setup! We will provide code from the official documentation which can either be imported directly into your HTML file, or you can change the script tags to link to a separate javascript file. 

#### Add to the shape.js file!
```javascript
// initializes the scene, camera and renderer. three vital spects in 3D modeling
let scene, camera, renderer;
let geometry, material, mesh;

init();
animate();

function init() {
    // Scenes are one of 3 things required to display in three.js
    scene = new THREE.Scene();
    // There are many cameras in three.js - for now we'll use PerspectiveCamera
    // The first attribute is field of view. You can zoom in or out for a wider
    // perspective of the scene. Try changing 25 to 75, and pay close attention
    // to !
    // The second is aspect ratio. Convention suggests we use the width of the
    // element divided by the height, otherwise your scene will look squished.
    // The next two attributes (1 & 10000) are the "near" and "far" clipping plane.
    // Objects further away from the camera than the value of "far" or closer
    // than "near" won't be rendered, of course!
    camera = new THREE.PerspectiveCamera( 25, window.innerWidth / window.innerHeight, 1, 10000 );
    // As you can imagine, the position of the camera in a 3D space zooms in and
    // out. Try positioning the z-index closer or further than our object (3000)!
    camera.position.z = 1500;

    // we can set the shape itself to a variable - there are many shapes out there!
    geometry = new THREE.BoxGeometry( 150, 150, 150, 5, 5 );
    material = new THREE.MeshBasicMaterial( { color: 0xff0000, wireframe: true } );
    // The second vital piece for shapes are meshes. A mesh is an object that takes a shape and applies a material to it. This is what we inject into our scene to manipulate.
    // Below we rotate our object.
    mesh = new THREE.Mesh( geometry, material );
    scene.add( mesh );

    // alternative renderer could be Canvas, but here we use WebGL
    // a renderer is another of the three things required to.. render!
    renderer = new THREE.WebGLRenderer();
    // setting size of the window and appending to the html
    renderer.setSize( window.innerWidth, window.innerHeight );
    document.body.appendChild( renderer.domElement );

}

function animate() {
    // adds speed to the rotation of the object
    requestAnimationFrame( animate );
    // rotates around the X axis
    mesh.rotation.x += 0.01;
    // rotates around the Y axis
    mesh.rotation.y += 0.02;

    renderer.render( scene, camera );

}

```
Submitted by *Kevin* and *Jerel*
