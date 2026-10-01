# TRELLIS Lite for MLinPL 2026

This is a reduced fork of [Microsoft TRELLIS](https://github.com/microsoft/TRELLIS) for the MLinPL 2026 tutorial **“Build Your Own 3D Scene: An Introduction to Gaussian Splatting.”** It retains the image-to-3D inference code used by `src/4_TRELLIS.ipynb` and `src/benchmark_trellis_memory.py` in the [workshop repository](https://github.com/MikolajZielinski/MLinPL-2026), including mesh and Gaussian output and mesh preview rendering. Training, Gradio, and large upstream demo assets are omitted.

Use this repository as the workshop's `modules/TRELLIS` Git submodule. After cloning the workshop, initialize its submodules:

```bash
git submodule update --init --depth 1
```

The two vendored FlexiCubes source files are required for mesh extraction; they include a small compatibility change that avoids installing Kaolin just for shape checks. Their original license is included beside them. The workshop's prepared Python/CUDA runtime supplies PyTorch, xFormers, spconv, CUDA rasterizers, `rembg`, `utils3d`, and other TRELLIS inference dependencies; this fork does not install or bundle those binaries. Run the workshop notebook rather than the original Gradio demo. Model weights (`microsoft/TRELLIS-image-large`), DINOv2, and U²-Net live under the parent workshop's `models/trellis/` directory and are **not stored in Git**. See the workshop's `setup.md` for the download commands. The notebook, memory benchmark, and `example.py` all use this local layout.

The Gaussian renderer includes a compatibility fix for rasterizer variants used with the workshop's CUDA/PyTorch stack. The retained `assets/example_image/T.png` is the default image for the memory benchmark. For the original full project, training code, and attribution, see [upstream TRELLIS](https://github.com/microsoft/TRELLIS). Original license: [MIT](LICENSE).
