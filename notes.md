# 22 IMPORTED MODELS 

## FORMATS
- OBJ 
- FBX
- STL
- PLY
- COLLADA
- 3DS
- GLTF
Different criteria:
    - dedicated to 1 software
    - light but lacks specific data
    - all data but heavy
    - open source
    - not open source
    - binary
    - ASCII
    - etc.
- can create own format 
### GLTF
- is becomming the standard format that covers most needs
- supports different sets of data like: 
    - geometries
    - materials
    - camera
    - lights
    - scene graph
    - animations
    - skeletons
    - morphing
    - etc. 
- various formats like 
    - json
    - binary
    - embed texture
- don't have to use GLTF in all cases, question data, weight and time to decompress
### FINA A MODEL
- GLTF team provised models for testing
- need to downnload/clone whole repo and take files needed

## GTLF FILE FORMATS
- 4 main formats
### glTF
- default format
- multiple files
- `.gltf` is JSON that contains cameras, lights, scenes, materials, object transformations, but no geometries or textures
- `.bin` in binary that contains geometries 
- `.png` is the texture
### glTF-Binary
- 1 file
- binary
- usually lighter
- easier to load
- hard to alter data
### glTF-Draco
- like glTF default but buffer data is compressed using `Draco algorith`
### glTF-Embedded
- one file
- JSON
- heavier 
### CHOOSING
- how you want to handle assets
- alter files - glTF-default
- loading multiple files can be faster
- draco compression or no?

## ADD LOADED MODEL TO SCene
- multiple ways of adding duck to scene:
    - add whole scene 
    - add children of the scene and ignore `PerspectiveCamera`
    - filter the children before adding to scene
    - add only the `Mesh` and have duck with wrong scale/position/rotation
    - open file in 3d software, clean it and export again 
- add the `Object3D` to scene and ignore the unused `PerspectiveCamera`

## DRACO COMPRESSION
- much lighter than default version
- compression is applied to the buffer data (usually geometry)
- not exclusive to glTF 
- google develops the algorithm under the open-source Apache License

### WHEN TO USE DRACO COMPRESSION
- geometries are lighter but user has to load the `DRACOLoader` class and the decoder
- takes time and resources for computer to decode the compressed file
- need to adap accordingly to the project 
- use for huge geometries not for small ones 

## ANIMATIONS
- glTF supports animations and Three.js can handle them
- loaded gltf object contains an animations property composed of multiple `AnimationClip` 
- need to create an `AnimationMixer` which is like a player associated with an object that can contain one or many `AnimationClips`

## THREE.JS EDITOR
- https://threejs.org/editor/
- like a tiny online 3D software
- good way to test models
- only works with models composed of one file 