# Fake News Detection Using Graph Neural Networks

A Graph Neural Network (GNN) based approach to detect fake news by analyzing propagation patterns on Twitter using PyTorch Geometric.

## Team Members 

- **Richa Ramesh** 
- **Apoorva Sarvade** 
- **Gurukiran** 
- **Tushar J** 

## Project Overview

This project implements a fake news detection system using Graph Attention Networks (GAT) to analyze how news propagates through social networks. Unlike traditional text-based approaches, this method leverages the graph structure of news propagation to identify fake news based on how it spreads across Twitter.

### Key Features

- **Graph-based Analysis**: Models news propagation as directed graphs
- **Graph Attention Networks (GAT)**: Uses attention mechanisms to weigh node importance
- **Hybrid Features**: Combines Word2Vec embeddings with user profile features
- **Binary Classification**: Distinguishes between real and fake news

## Dataset

The project uses the **UPFD (User Preference-aware Fake news Dataset)** with the GossipCop subset:

- **Source**: [FakeNewsNet](https://github.com/KaiDMML/FakeNewsNet)
- **Preprocessing**: Based on [this paper](https://arxiv.org/pdf/2104.12259.pdf)
- **Features**: Spacy Word2Vec embeddings + Twitter user profile features
- **Structure**: News propagation graphs extracted from Twitter

## Model Architecture

The GNN model consists of:

1. **Three GAT Convolutional Layers**: Extract hierarchical graph features
2. **Global Max Pooling**: Aggregate node features to graph-level representation
3. **Readout Layer**: Combines pooled features with root node embeddings
4. **Binary Classification**: Outputs probability of news being fake

### Architecture Details

```
Input: Node features (310 dimensions) + Edge connections
├── GATConv Layer 1 (310 → 128)
├── GATConv Layer 2 (128 → 128)  
├── GATConv Layer 3 (128 → 128)
├── Global Max Pooling
├── Linear Layer (128 → 128)
├── Concatenate with News Embeddings
└── Output Layer (256 → 1)
```

## Installation

### Prerequisites

- Python 3.7+
- CUDA-compatible GPU (recommended)

### Setup

1. Clone the repository:
```bash
git clone https://github.com/yourusername/fake-news-detection-gnn.git
cd fake-news-detection-gnn
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Install PyTorch Geometric (adjust CUDA version as needed):
```bash
pip install torch-scatter -f https://pytorch-geometric.com/whl/torch-${TORCH}+${CUDA}.html
pip install torch-sparse -f https://pytorch-geometric.com/whl/torch-${TORCH}+${CUDA}.html
pip install torch-geometric
```

## Usage

### Running the Notebook

```bash
jupyter notebook fake_news.ipynb
```

### Training the Model

The notebook includes complete training pipeline:

1. **Data Loading**: Automatically downloads UPFD dataset
2. **Data Exploration**: Visualize propagation graphs and analyze features
3. **Model Training**: Trains GAT model for 40 epochs
4. **Evaluation**: Reports accuracy and F1-score on test set

### Expected Results

The model typically achieves:
- **Test Accuracy**: ~85-90%
- **F1-Score**: ~0.85-0.90

## Project Structure

```
fake-news-detection-gnn/
├── fake_news.ipynb          # Main notebook with complete implementation
├── README.md              # Project documentation
├── requirements.txt       # Python dependencies
├── .gitignore            # Git ignore file
└── data/                 # Dataset (auto-downloaded)
```

## Methodology

### 1. Data Preprocessing
- News articles collected from Twitter
- Propagation graphs constructed from retweets and replies
- Node features: Word2Vec embeddings + user profile data

### 2. Model Training
- **Optimizer**: Adam (lr=0.01, weight_decay=0.01)
- **Loss Function**: Binary Cross-Entropy Loss
- **Batch Size**: 128
- **Epochs**: 40

### 3. Evaluation Metrics
- Accuracy
- F1-Score
- Binary Cross-Entropy Loss

## Technical Details

### Graph Attention Networks (GAT)

The model uses GAT convolutions which apply attention mechanisms to aggregate neighbor information:

```python
h = GATConv(in_channels, out_channels)(x, edge_index)
```

This allows the model to learn which nodes are more important for classification.

### Root Node Integration

Following the UPFD paper methodology, the model incorporates raw news embeddings:

```python
news = x[root]  # Extract root node features
out = concat([graph_features, news_features])
```

This combines both propagation patterns and original news content.

## Results Visualization

The notebook includes:
- Propagation graph visualizations
- Class distribution histograms
- Training/testing loss curves
- Prediction analysis

## References

- **UPFD Dataset**: [Paper](https://arxiv.org/pdf/2104.12259.pdf)
- **FakeNewsNet**: [GitHub Repository](https://github.com/KaiDMML/FakeNewsNet)
- **PyTorch Geometric**: [Documentation](https://pytorch-geometric.readthedocs.io/)

## Future Improvements

- Experiment with different GNN architectures (GraphSAGE, GCN)
- Implement attention visualization
- Add cross-dataset evaluation
- Deploy as web service
- Incorporate temporal features

## License

This project is for academic purposes.

## Acknowledgments

- UPFD dataset creators
- PyTorch Geometric team
- FakeNewsNet contributors

---

**Note**: This project was developed as part of an academic assignment. The dataset is automatically downloaded when running the notebook.
