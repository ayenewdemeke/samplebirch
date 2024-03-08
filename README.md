# BIRCH Clustering Implementation

This project provides a Python implementation of the BIRCH (Balanced Iterative Reducing and Clustering using Hierarchies) clustering algorithm without relying on external machine learning libraries. It includes the core BIRCH clustering components (`CFNode`, `CFLeaf`, `CFBranch`), the main clustering function `birch_cluster`, utility functions like `collect_leaf_centroids`, and an implementation of the k-means algorithm to further process the clustering results.

## Features

- Pure Python implementation of BIRCH clustering.
- K-means clustering for further refinement of BIRCH results.
- Utility functions for working with cluster features and centroids.

## Getting Started

### Prerequisites

- Python 3.x

### Installation

1. Clone the repository:
git clone <repository-url>

2. Navigate to the project directory and install the required dependencies:
cd BIRCH
pip install -r requirements.txt


### Usage

Here's a simple example of how to use the BIRCH clustering implementation with your data:

```python
from BIRCH import birch_cluster, collect_leaf_centroids, k_means
import numpy as np

# Example data points
points = np.array([[1.0, 2.0], [2.5, 4.5], [2.0, 2.0], [3.0, 3.0], [5.0, 7.0]])

# Perform BIRCH clustering
branching_factor = 2
threshold = 1.5
root = birch_cluster(points, branching_factor, threshold)

# Extract centroids and perform k-means clustering
centroids = collect_leaf_centroids(root)
initial_centroids = np.array(centroids[:2])  # Initial centroids for k-means
clusters = k_means(points, initial_centroids, 100)  # 100 iterations

print("Cluster assignments:", clusters)

Developed by Lemlem Asaye, as part of a comprehensive exam at NDSU.
