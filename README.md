# Sparse Octree

[![Build status](https://travis-ci.org/vanruesc/sparse-octree.svg?branch=master)](https://travis-ci.org/vanruesc/sparse-octree) 
[![npm version](https://badge.fury.io/js/sparse-octree.svg)](http://badge.fury.io/js/sparse-octree) 
[![Dependencies](https://david-dm.org/vanruesc/sparse-octree.svg?branch=master)](https://david-dm.org/vanruesc/sparse-octree)

A sparse octree data structure.  

*[Extensive Demo](http://vanruesc.github.io/sparse-octree/public/index.html) &there4;
[API Reference](http://vanruesc.github.io/sparse-octree/docs)*


## Installation

```sh
npm install sparse-octree
``` 


## Usage

##### Custom Octrees

```javascript
import { Octree, CubicOctant } from "sparse-octree";

export class CubicOctree extends Octree {

	constructor(min, size) {

		this.root = new CubicOctant(min, size);

	}

}
```

##### Helper

```javascript
import { Scene } from "three";
import { Octree, OctreeHelper } from "sparse-octree";

const scene = new Scene();

const octree = new Octree();
const octreeHelper = new OctreeHelper(octree);

scene.add(octreeHelper);
```

##### Points

```javascript
import { Vector3 } from "three";
import { PointOctree } from "sparse-octree";

const min = new Vector3(-1, -1, -1);
const max = new Vector3(1, 1, 1);

const octree = new PointOctree(min, max);

octree.add(new Vector3(0, 0, 0), {});
octree.fetch(new Vector3(0, 0, 0)); // => {}
```

A full point octree example can be found [here](https://jsfiddle.net/6gt9fjmq/3/).


## Features

- Base Functionality
	- Pointer-based structure
  - Handles octant splitting
  - Adheres to a [common octant layout](http://vanruesc.github.io/sparse-octree/docs/classes/Octant.html#property_PATTERN)
  - Supports raycasting
  - Supports culling
  - Supports cubic octrees
  - Can be extended to manage any data
- Provides a point management implementation
- Provides a helper that can visualise octrees


## Contributing

Maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code.
