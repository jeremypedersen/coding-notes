---
id: zrzuso1wjne88yp1b9wtm8v
title: 'Computer Vision'
desc: 'Computer Vision'
updated: 1725517663182
created: 1725513444786
---

Resources related to computer vision. For me this means everything from image processing to stitching panoramas to photogrammetry and even creating and editing NeRF models. 

For now it's just sort of a brain dump where I collect tools I want to play with. Here are a few I'm researching now.

## Focus stacking

- [focus-stack](https://github.com/PetteriAimonen/focus-stack), plus [this blog post](https://peterfalkingham.com/2024/04/29/an-excellent-free-and-open-source-focus-stacking-solution/) talking about how to use it. 

## 3D Reconstruction and Photogrammetry

- [micmac](https://github.com/micmacIGN/micmac), open source photogrammetry.
- [meshroom](https://github.com/alicevision/Meshroom?tab=readme-ov-file), open source 3D reconstruction software
- A quick [survival guide](https://moviola.com/courses/meshroom-survival-guide/) to using meshroom
- [nerfstudio](https://docs.nerf.studio/) for building NeRFs.
- [CloudCompare](https://www.danielgm.net/cc/) open source software for working with 3D point clouds and meshes.
- [MeshLab](https://www.meshlab.net/) open source system for processing and editing 3D triangular meshes.
- [Open3D](https://www.open3d.org/), open source software for 3D data processing, with [documenatation here](https://www.open3d.org/docs/release/).
- [Regard3D](https://www.regard3d.org/index.php/documentation/tutorial) open source software to go from a set of images to a 3D model. 
- [openMVG](http://imagine.enpc.fr/~moulonp/openMVG/index.html) tool for "multiple view geometry" targeted to developers. Looks like it makes it easy to solve for geometry using 2 to "N" different views of a scene. 
- [openMVS](https://github.com/cdcseacave/openMVS) stereo view reconstruction software. Looks like it can do a ton of cool stuff but I'm mostly interested in the ability to do mesh reconstruction (to make 3D models).
- [PMVS (Patch-based Multi-vew Stereo)](https://www.di.ens.fr/pmvs/), a tool for doing the 3D reconstruction from a set of images. Apparently it is included inside [CVMS (Clustering Views for Multi-vew Stereo)](https://www.di.ens.fr/cmvs/).

While looking for open source photogrammetry solutions, I ran across [this cool blog post from an archaeology team](https://arc-team-open-research.blogspot.com/2016/12/comparing-7-photogrammetry-systems.html) talking about reconstructions done for scientific purposes. 

Wildly enough, the quality of these models can be quite good. Good enough to [print replacement teeth for dogs](https://www.dailymail.co.uk/sciencetech/article-3678651/Animal-avengers-rescue-Adorable-puppy-eat-3D-printed-tooth-replaces-one-broke-chewing.html), at least.

They looked at a couple different solutions and chose openMVS + openMVG as their general favorite.

It looks like for simple 3D reconstructions from a set of photographs Meshlab may also work (not tested in their blog).

As for **sharing the resulting models** it seems [Thingiverse](https://www.thingiverse.com/) is the go-to for 3D printing, and [Sketchfab](https://sketchfab.com) for general 3D models.  

Apparently [Three.js](https://threejs.org/examples/#webgl_animation_keyframes) can also display reconstructions, up to and including animation! 

## Panoramas

- [Hugin](https://hugin.sourceforge.io/), which appears to be the leading open source toolkit for making panoramic images, and is based on [Panorama tools](https://panotools.sourceforge.net/). Both seem to be working just fine but are quite old and seem to mostly just be receiving maintenance updates. The releases on the Hugin site indicate that no major new features are being added, but the software is being actively maintained.
- [Xpano](https://krupkat.github.io/xpano/) looks like a simpler alternative to Hugin, will autodetect related images in a folder, stitch them, and export.

## AI/ML Stuff

There are some really, really cool demos that mix photography and generative AI. Most of them are hosted on HuggingFace. Here are a couple I've looked at: 

- [InstantMesh](https://huggingface.co/spaces/TencentARC/InstantMesh) takes a single photo, generates best-guesses for multiple views of the object, and then uses those to create an actual colorized 3D model in OBJ or GLB format.
- [StableDesign](https://huggingface.co/spaces/MykolaL/StableDesign) submit an image of a bare interior and a description of the interior design aesthetic you are interested in, and the system generates a concept image showing the space redesigned to meet your needs.
- [Minecraft skin generator](https://huggingface.co/spaces/Nick088/Stable_Diffusion_Finetuned_Minecraft_Skin_Generator) Use a prompt to generate 3D models which can be used as "skins" for player characters in Minecraft.
- [multimodalart](https://huggingface.co/multimodalart), a really interesting collection of spaces for generating AI art, including spaces to help you [easily create and train LoRAs](https://huggingface.co/spaces/multimodalart/lora-ease) and space to [re-style selfies](https://huggingface.co/spaces/multimodalart/face-to-all).

