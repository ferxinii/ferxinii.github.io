---
name: 3D Voronoi diagrams
tools: [geometry, C]
image: /assets/images/projects/voronoi/front.png
description: Construct bounded 3D Voronoi diagrams in an arbitrary polyhedron.
---
## Robust Delaunay triangulation
Given a set of seeds, to find its Voronoi diagram we first construct the associated Delaunay triangulation. To do so, we have implemented in C the algorithm described in the paper *Computing the 3D Voronoi Diagram Robustly: An Easy Explanation* by Hugo Ledoux ([link](https://gdmc.nl/publications/2007/Computing_3D_Voronoi_Diagram.pdf){:target="_blank"}).

The idea of the algorithm is to iteratively add each seed and at each step restore local Delaunayness by using *Pachner flips* (or *bistellar flips*).

<div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 10px;">
<img src="/assets/images/projects/voronoi/pachner.png" alt="Pachner flips" width="700" height="auto" />
</div>


When the Delaunay triangulation is constructed, extracting the corresponding Voronoi diagram is trivial due to the duality relationships between the Delaunay and Voronoi constructions. However, the resulting Voronoi diagram is unbounded.

## Bounding polyhedron
In order to bound the diagram appropriately with an arbitrary polyhedron, we use a *mirroring* appraoch. The idea is to enlarge the set of seeds by mirroring the necessary sites accross each face of the bounding polyehdron. Then, the Delaunay triangulation of this extended set of seeds is computed. Finally, we extract the dual Voronoi cells in the interior of the polyhedron, which will be naturally bounded. 

The next figure (from [this](https://stackoverflow.com/questions/28665491/getting-a-bounded-polygon-coordinates-from-voronoi-cells) StackOverflow discussion, comment by *Flabetvibes*) shows an example of this principle in the plane, with the goal of bounding the cells corresponding to the points inside the red box.

<div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 10px;">
<img src="/assets/images/projects/voronoi/mirroring.png" alt="Mirroring in 2D" width="400" height="auto" />
</div>

## Example in lung geometry
This code has been used to construct secondary pulmonary lobules inside a lung geometry. By playing with the distribution of seeds inside the lung, we can obtain different morphologies and distributions of lobule volumes.

<div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 10px;" markdown="0">
<img src="/assets/images/projects/voronoi/R_v2.png" alt="Example right lung" width="400" height="auto" />
<img src="/assets/images/projects/voronoi/L_v4.png" alt="Example left lung" width="400" height="auto">
</div>

<center>
{% include elements/button.html link="https://github.com/ferxinii/voronoi_3d" text="GitHub" %}
</center>
