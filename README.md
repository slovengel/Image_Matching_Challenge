# VRDL_Final_IMC2023

This repository contains the implementation for the Image Matching Challenge 2023.

## Prerequisites

- Python 3.x
- PyTorch
- CUDA-capable GPU
- Required Python packages (will be listed in requirements.txt)

## Setup

1. Clone this repository:
```bash
git clone https://github.com/chuchunchi/VRDL_Final_IMC2023.git
cd VRDL_Final_IMC2023
```

2. Install required dependencies:
```bash
pip install -r requirements.txt
```

3. Download required model weights:
   - HardNet weights
   - LoFTR weights
   - Other model weights as specified in the notebook

## Running the Notebook

1. Open `final-imc2023.ipynb` in your preferred Jupyter environment.

2. Configure the notebook settings:
   - Set `MODE` to either "train" or "test" depending on your needs
   - Set `is_local` to `True` for local testing or `False` for Kaggle environment
   - Adjust `NUM_CORES` based on your system's capabilities
   - Set `DEBUG` to `True` for debugging or `False` for full execution

3. For local testing, ensure your directory structure is as follows:
```
VRDL_Final_IMC2023/
├── kaggle/
│   └── input/
│       ├── image-matching-challenge-2023/
│       └── kornia-local-feature-weights/
├── final-imc2023.ipynb
└── README.md
```

4. For Kaggle environment, the paths are automatically configured.

## Configuration Options

The notebook includes several configurable parameters:

- `MODE`: Set to "train" or "test"
- `hardnet_res`: Resolution for HardNet processing (default: 1600)
- `MATCH_FILTER_RATIO`: Filter ratio for matches (default: 0.005)
- `DEBUG_SCENE`: List of scenes to process in debug mode
- `FM_PARAMS`: Parameters for fundamental matrix calculation

## Model Configuration

The notebook supports multiple feature detection and description models that can be configured through the `MODEL_CONFIG` dictionary:

```python
MODEL_CONFIG = {
    "model_type": "hardnet_plus_plus",  # Options: "hardnet", "hardnet_plus_plus", "sosnet"
    "patch_size": 32,
    "grayscale_descriptor": True
}
```

### Available Models:
1. **HardNet** (`"hardnet"`)
   - Original HardNet8 implementation
   - Uses HardNetLib weights

2. **HardNet++** (`"hardnet_plus_plus"`)
   - Enhanced version of HardNet
   - Uses hardnet++ weights
   - Default configuration

3. **SOSNet** (`"sosnet"`)
   - SOSNet implementation
   - Uses sosnet_32x32_liberty weights

### Model Parameters:
- `patch_size`: Size of patches for descriptor computation (default: 32)
- `grayscale_descriptor`: Whether to use grayscale for descriptor computation (default: True)

### Feature Detection Models:
The notebook also includes multiple feature detection models that can be enabled/disabled in the `MODEL_DICT`:
- Keynet
- GFTT
- DoG
- Harris
- Hessian

Each model can be configured with:
- `enable`: Enable/disable the model
- `resize_long_edge_to`: Target resolution for processing
- `pair_only`: (Keynet only) Whether to process image pairs only


