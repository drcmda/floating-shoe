# gltf

- what is gltf, how is it usually loaded
- why is it so hard to make the data dynamic, what are the current solutions (scene traversal + mutation, KHR_variants etc)
  - GLTFJSX changes that by extracting a virtual tree, linking up geometries and materials
  - now everything can be altered, made conditional or interactive, hooked to state

# process of using GLTF's in react

- having a model (sketchfab, google poly), or making one (for instance blender)
- draco compressing it into a single glb
  - `npx gltf-pipeline -i model.gltf -o model.glb --draco.compressionLevel=10`
- creating a JSX component
  - `npx gltfjsx model.glb`
- drop glb into the /public folder, add the component
- et voila, it displays

# example of making a simple configurator

- state model is critical, bc it bridges the two worlds: canvas and dom. every app should start from state, this will make everything easier.
  - we use valtio, a really simple proxy base state manager that doesn't need much learning. proxy an object, read from snapshots, write to the source object.
- create colors in the state model, wire them into the gltfjsx.
- use events to change the state model. r3f has real event bubbling, so we can have events on a group and stop-propagate to only work with the closest mesh underneath the cursor.
- use a colorpicker to set the color for the current-active mesh

# making stuff look nice

- the biggest secret is proper gamma encoding. r3f does this by default for all colors and textures.
- lights: fill (ambientLight, spotLight)
  - the main light in this case is a HDRI environment, bc it's more realistic. the drei component makes that super easy.
- contact shadows give it some depth.
