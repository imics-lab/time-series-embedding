## A Comprehensive Evaluation of Time Series Embedding Methods for Classification Tasks

[![Python 3.12](https://img.shields.io/badge/python-3.12+-blue.svg)](https://www.python.org/downloads/release/python-312/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![DOI](https://img.shields.io/badge/DOI-10.1111/exsy.70148-blue.svg)](https://doi.org/10.1111/exsy.70148)
[![arXiv](https://img.shields.io/badge/arXiv-2501.13392-b31b1b.svg)](https://arxiv.org/abs/2501.13392)

**Published in:** *Expert Systems* (Wiley)

This repository implements various time series embedding methods and provides a framework for quantitative evaluation of these methods on classification tasks. It allows researchers to compare different embedding techniques based on their theoretical foundations and empirical performance.

## Description
This repository contains code for the quantitative evaluation of different time series embedding methods based on their theoretical foundations and application contexts. Unlike previous work, this study quantitatively compares these methods by testing their performance on various classification tasks across different datasets. The results reveal that embedding methods perform differently depending on the dataset and classification algorithm, emphasizing the need for careful model selection and experimentation. 


## Key Findings

**🏆 Top Performing Methods:**
- **C-Transformer**: Best overall performance with average rank 1.6
- **FFT**: Strong classical method with average rank 2.7
- **Wavelet Transform**: Excellent for bioelectrical signals with average rank 3.1
- **PCA**: Robust baseline with average rank 3.5

**📊 Performance Summary:**
- C-Transformer achieves best performance on 7 out of 10 datasets
- Classical methods (FFT, Wavelet, PCA) remain highly competitive
- Domain-specific patterns: Wavelet excels for biomechanical signals (77.7% accuracy)
- Computational efficiency: Classical methods offer excellent performance-to-cost ratios

**⚙️ Computational Efficiency on ElectricDevices dataset**

| Method | Training Time | Inference Time | Memory | GPU Benefit |
|--------|---------------|----------------|---------|-------------|
| PCA | 0.443s | 0.064s | Low | Low |
| Wavelet | 0.010s | 0.005s | Low | Moderate |
| FFT | 0.103s | 0.090s | Low | High |
| LLE | 23.377s | 1.604s | Moderate | Low |
| UMAP | 21.719s | 15.000s | Moderate | Low |
| Graph | 364.340s | 309.867s | High | Low |
| TDA | 204.619s | 176.771s | High | Low |
| Autoencoder | 38.609s | 1.181s | Moderate | High |
| C-CNN | 680.504s | 0.139s | High | Very High |
| C-RNN | 703.063s | 0.150s | High | High |
| C-Transformer | 579.639s | 0.157s | High | Very High |

**Key Insights:**
- **Fastest training**: Wavelet Transform (0.010s) and FFT (0.103s)
- **Fastest inference**: Wavelet Transform (0.005s) and PCA (0.064s)
- **Most resource-intensive**: C-RNN (703s training) and Graph methods (365s training)
- **Best GPU acceleration**: Deep learning methods (C-CNN, C-Transformer, C-RNN)
- **Memory efficient**: Classical methods (PCA, Wavelet, FFT)


## Repository Structure

- `/data`: Scripts for downloading and processing datasets
- `/results`: Results from experiments
- `/utils`: Utility functions for data augmentation and visualization
- `/notebooks`: Jupyter notebooks for experiments
- `/src`: Implementation scripts



## Dependencies

The main dependencies for this project include:
- **Python 3.12** (required for compatibility with all packages)
- NumPy
- Pandas  
- TensorFlow
- Scikit-learn
- UMAP
- Matplotlib
- Optuna
- **Specialized packages**: giotto-tda, ts2vg, gudhi, keras-tuner
- And more scientific computing packages

All dependencies are specified in the `requirements.txt` file.

## Installation

### Prerequisites

**Important**: This project requires **Python 3.12** for full compatibility with all packages, especially the topological data analysis libraries (gtda, ts2vg, gudhi).

#### Option 1: Using Conda (Recommended)
```bash
# Install/create Python 3.12 environment with conda
conda create -n timeseries_py312 python=3.12 -y
conda activate timeseries_py312
```

#### Option 2: Using pyenv
```bash
# Install Python 3.12 with pyenv
pyenv install 3.12.11
pyenv local 3.12.11
```

### Setting up the environment

```bash
# Clone the repository
git clone https://github.com/imics-lab/time-series-embedding.git
cd time-series-embedding

# Create virtual environment using Python 3.12
python3.12 -m venv venv
# OR if using conda Python 3.12:
# /path/to/conda/envs/timeseries_py312/bin/python -m venv venv

# Activate the virtual environment
source venv/bin/activate  # On Windows use: venv\Scripts\activate

# Verify Python version (should be 3.12.x)
python --version

# Upgrade pip
pip install --upgrade pip

# Install all dependencies
pip install -r requirements.txt

# Verify installation (quick test)
python -c "import gtda, ts2vg, gudhi; print('✅ All packages installed successfully!')"

# Run comprehensive environment test
python test_environment.py
```

### Troubleshooting

If you encounter issues:

1. **Python version**: Ensure you're using Python 3.12.x:
   ```bash
   python --version  # Should show Python 3.12.x
   ```

2. **Package conflicts**: If packages fail to install, try:
   ```bash
   pip install --upgrade pip setuptools wheel
   pip install -r requirements.txt --force-reinstall
   ```

3. **Missing system dependencies**: On Ubuntu/Debian, you may need:
   ```bash
   sudo apt-get update
   sudo apt-get install python3.12-dev python3.12-venv build-essential
   ```

### Key Package Notes

This project includes several specialized packages for topological data analysis and time series processing:

- **giotto-tda (gtda)**: Topological data analysis toolkit for machine learning
- **ts2vg**: Time series to visibility graph conversion  
- **gudhi**: Geometry Understanding in Higher Dimensions library
- **keras-tuner**: Hyperparameter tuning for Keras models (replaces kerashypetune)

These packages require Python 3.12 for optimal compatibility and have been tested to work together seamlessly.

## Dataset Compatibility

The framework is designed to work with multiple time series datasets, including:
- Human Activity Recognition (HAR)
- ECG/EEG signal classification
- Industrial sensor data
- Environmental monitoring time series



## Environment Testing

After installation, you can verify that your environment is properly set up by running:

```bash
python test_environment.py
```

This script will:
- Check that you have Python 3.12.x
- Verify all required packages are installed and importable
- Test basic functionality of key packages (gtda, ts2vg, gudhi)
- Provide a comprehensive report of your environment status

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

<!-- CITATION -->
## Citation

```bibtex
@article{irani2025time,
   title={Time series embedding methods for classification tasks: A review},
   author={Irani, Habib and Ghahremani, Yasamin and Kermani, Arshia and Metsis, Vangelis},
   journal={Expert Systems},
   volume={42},
   number={11},
   pages={e70148},
   year={2025},
   publisher={Wiley Online Library}
}
```

**Paper Links:**
- Journal Article: https://onlinelibrary.wiley.com/doi/full/10.1111/exsy.70148
- arXiv Preprint: https://arxiv.org/abs/2501.13392