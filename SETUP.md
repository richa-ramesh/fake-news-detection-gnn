# Quick Setup Guide

This guide will help you set up the project on your local machine.

## Prerequisites

- Python 3.7 or higher
- pip package manager
- (Optional) CUDA-compatible GPU for faster training

## Step-by-Step Setup

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/fake-news-detection-gnn.git
cd fake-news-detection-gnn
```

### 2. Create a Virtual Environment (Recommended)

**On Linux/Mac:**
```bash
python3 -m venv venv
source venv/bin/activate
```

**On Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

### 3. Install PyTorch

Visit [PyTorch website](https://pytorch.org/get-started/locally/) and install the appropriate version for your system.

**Example for CPU:**
```bash
pip install torch torchvision torchaudio
```

**Example for CUDA 11.8:**
```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```

### 4. Install PyTorch Geometric

```bash
pip install torch-geometric
pip install pyg-lib torch-scatter torch-sparse -f https://data.pyg.org/whl/torch-2.0.0+cu118.html
```

*Note: Adjust the CUDA version in the URL to match your PyTorch installation*

### 5. Install Other Dependencies

```bash
pip install -r requirements.txt
```

### 6. Launch Jupyter Notebook

```bash
jupyter notebook
```

Then open `TEAM_44.ipynb` in your browser.

## Verifying Installation

Run this in a Python shell to verify everything is installed:

```python
import torch
import torch_geometric
import networkx
import pandas
import sklearn

print("PyTorch version:", torch.__version__)
print("PyG version:", torch_geometric.__version__)
print("CUDA available:", torch.cuda.is_available())
```

## Troubleshooting

### Issue: PyTorch Geometric installation fails

**Solution**: Make sure your PyTorch version matches the PyG installation. Check compatibility at [PyG Installation Guide](https://pytorch-geometric.readthedocs.io/en/latest/install/installation.html)

### Issue: CUDA out of memory

**Solution**: Reduce the batch size in the notebook (currently 128) to a smaller value like 64 or 32.

### Issue: Dataset download fails

**Solution**: The dataset downloads automatically. If it fails, check your internet connection and try running the cell again.

## Running the Project

1. Open `TEAM_44.ipynb` in Jupyter
2. Run all cells sequentially (Shift + Enter)
3. The dataset will download automatically on first run
4. Training takes approximately 10-15 minutes (depending on your hardware)

## GPU vs CPU

- **With GPU**: Training is much faster (~2-3 minutes per epoch)
- **With CPU**: Training is slower (~5-10 minutes per epoch)

Both will produce the same results, GPU is just faster.

## Need Help?

- Check the [README.md](README.md) for more details
- Review [CONTRIBUTING.md](CONTRIBUTING.md) for collaboration guidelines
- Contact team members if you encounter issues

---

Happy coding! 🚀
