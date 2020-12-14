    npm install
    npm start

### How to compress assets and turn them into JSX components

1. `npx gltf-pipeline -i model.gltf -o model.glb --draco.compressionLevel=7`
1. `npx gltfjsx model.glb`

### How to include them into a real project

1. Set up [react-three-fiber](https://github.com/pmndrs/react-three-fiber)
1. Put `model.glb` into `/public`
1. Copy Model.js into the project

<div align="center">
  <br>
  <img src="readme.svg" width="800" height="400">
  <br>
</div>
