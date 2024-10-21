# Differential Gaussian Rasterization with Depth Forward and Backward Functionality

## About

An extension of the rasterization engine for the paper "3D Gaussian Splatting for Real-Time Rendering of Radiance Fields". 

We make two contributions: 
* Depth forward: render depth map, weight map, along with color map 
* Depth backward: backpropagate the graidents from depth loss to Gaussians.
* e3nn convention for sh coefficients.

Note that our method calculates depth values based on volume rendering, and  corrects the depth by **dividing it by the weights** of volume rendering. You can apply supervision to them, such as depth  monocular estimation. If you do not wish to correct the depth, you can obtain the uncorrected  depth map by multiplying the depth map with the weight map.

Note that our method calculates spherical harmonics in e3nn convention. Original 3D-GS's axis XYZ goes to ZYX. You can also refer the [issue](https://github.com/graphdeco-inria/gaussian-splatting/issues/176) for more details.

## Install

```shell
pip install git+https://github.com/Gynjn/diff-gaussian-rasterization-e3nn-depth
```



## Usage

```python
from diff_gaussian_rasterization_e3nn_depth import GaussianRasterizationSettings, GaussianRasterizer

...

raster_settings = ...
rasterizer = GaussianRasterizer(raster_settings=raster_settings)    

rendered_image, radii, depth_map, weight_map = rasterizer(
    means3D = means3D, 
    means2D = means2D,  
    shs = shs,          
    colors_precomp = colors_precomp,
    opacities = opacity, 
    scales = scales,   
    rotations = rotations,  
    cov3D_precomp = cov3D_precomp,
)

...
```



<section class="section" id="BibTeX">
  <div class="container is-max-desktop content">
    <h2 class="title">BibTeX</h2>
    <pre><code>@Article{kerbl3Dgaussians,
      author       = {Kerbl, Bernhard and Kopanas, Georgios and Leimk{\"u}hler, Thomas and Drettakis, George},
      title        = {3D Gaussian Splatting for Real-Time Radiance Field Rendering},
      journal      = {ACM Transactions on Graphics},
      number       = {4},
      volume       = {42},
      month        = {July},
      year         = {2023},
      url          = {https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/}
}
@misc{leofrank2024,
      author       = {Leo Frank (Wynn)},
      title        = {3D Gaussian Splatting Rasterizer with Depth},
      year         = {2024},
      publisher    = {github},
      url          = {https://github.com/leo-frank/diff-gaussian-rasterization-depth/}
}
@misc{charatan2023,
      author       = {David Charatan},
      title        = {3D Gaussian Splatting Rasterizer with e3nn convention},
      year         = {2023},
      publisher    = {github},
      url          = {https://github.com/dcharatan/diff-gaussian-rasterization-modified/}
}</code></pre>
  </div>
</section>

Thanks for open-sourcing the projects.

<!-- </code></pre>
  </div>
  <div class="container is-max-desktop content">
    <h2 class="title">BibTeX</h2>
    <pre><code>@misc{leofrank2024,
      author       = {Leo Frank (Wynn)},
      title        = {3D Gaussian Splatting Rasterizer with Depth},
      year         = {2024},
      publisher    = {github},
      url          = {https://github.com/leo-frank/diff-gaussian-rasterization-depth/}
}</code></pre>
  </div>
  <div class="container is-max-desktop content">
    <h2 class="title">BibTeX</h2>
    <pre><code>@misc{charatan2023,
      author       = {David Charatan},
      title        = {3D Gaussian Splatting Rasterizer with e3nn package convention},
      year         = {2023},
      publisher    = {github},
      url          = {https://github.com/dcharatan/diff-gaussian-rasterization-modified/}
}</code></pre>
  </div>  
</section> -->

<!-- 
<section class="section" id="BibTeX">
  <div class="container is-max-desktop content">
    <h2 class="title">BibTeX</h2>
    <pre><code>@misc{leofrank2024,
      author       = {Leo Frank (Wynn)},
      title        = {3D Gaussian Splatting Rasterizer with Depth},
      year         = {2024},
      publisher    = {github},
      url          = {https://github.com/leo-frank/diff-gaussian-rasterization-depth/}
}</code></pre>
  </div>
</section>


<section class="section" id="BibTeX">
  <div class="container is-max-desktop content">
    <h2 class="title">BibTeX</h2>
    <pre><code>@misc{leofrank2024,
      author       = {David Charatan},
      title        = {3D Gaussian Splatting Rasterizer with e3nn package convention},
      year         = {2023},
      publisher    = {github},
      url          = {https://github.com/dcharatan/diff-gaussian-rasterization-modified/}
}</code></pre>
  </div>
</section> -->