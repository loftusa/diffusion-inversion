# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a research project implementing DDIM (Denoising Diffusion Implicit Models) Inversion techniques for precise image editing using Stable Diffusion. The main implementation is in `experiments/DDIM Inversion.py`, which is a converted Jupyter notebook from Hugging Face's diffusion models course.

## Development Commands

### Setup
```bash
# Install dependencies (once pyproject.toml is updated)
pip install -e .

# Or install required packages directly
pip install torch diffusers transformers accelerate pillow matplotlib tqdm requests
```

### Running the Code
```bash
# Execute the main experiment
python "experiments/DDIM Inversion.py"
```

## Architecture

The project implements DDIM inversion for controlled image editing:

1. **Core Algorithm**: The DDIM inversion process (`invert()` function) converts images back to their latent noise representation deterministically
2. **Editing Pipeline**: The `edit()` function combines inversion with prompt-based re-sampling to make targeted changes
3. **Key Functions**:
   - `sample()`: DDIM sampling for image generation
   - `invert()`: Converts images to latent noise (lines 87-145)
   - `edit()`: Main editing interface (lines 269-289)

## Important Implementation Details

- The code uses Stable Diffusion v1.5 from Hugging Face
- DDIM inversion requires the same random seed and number of steps for consistency
- The `guidance_scale` parameter controls how strongly the model follows text prompts
- Higher `num_inference_steps` (50-100) gives better inversion quality but is slower

## Dependencies Not Yet in pyproject.toml

The following packages are used but need to be added to pyproject.toml:
- torch
- diffusers
- transformers
- accelerate
- pillow
- matplotlib
- tqdm
- requests

## Python Version

This project requires Python 3.12 as specified in `.python-version`.