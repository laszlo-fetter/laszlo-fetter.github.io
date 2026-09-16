# GraphTreeBoost

**Soft Decision Tree-Based Graph Learning With Spectral Aggregation**

**László Fetter** and **András Gézsi**  
Department of Artificial Intelligence and Systems Engineering  
Budapest University of Technology and Economics

[GitHub Repository](https://github.com/laszlo-fetter/graphtreeboost)  
[Paper / DOI](https://doi.org/10.14428/esann/2026.ES2026-111)  
[PDF](https://www.esann.org/sites/default/files/proceedings/2026/ES2026-111.pdf)  
[DBLP](https://dblp.org/rec/conf/esann/FetterG26)

## Abstract

GraphTreeBoost is a gradient-boosted framework for graph-structured data that couples soft decision trees with spectral feature aggregation.

Each split operates on features filtered by truncated Chebyshev or Chebyshev–Bessel (heat-kernel) expansions of the normalized adjacency, enabling graph-aware learning without eigendecomposition.

Training combines analytic second-order leaf updates with AdamW for routing and filter parameters. Spectral operations are implemented in feature space using sparse graph primitives, making the approach practical on CPU hardware while retaining interpretable thresholds and per-node gain scores.

## Method

GraphTreeBoost is a node-classification method that combines gradient-boosted soft decision trees with graph-based feature aggregation. It uses Chebyshev and heat-kernel filters to incorporate information from neighboring nodes before the tree model makes its decisions. The graph filtering is implemented without explicitly computing the graph's eigenvectors.

### Why this combination?

Tree-based models are among the strongest and most widely used approaches for tabular data. Graph-structured datasets, however, contain additional information in the relationships between samples that standard tabular models cannot directly use.

GraphTreeBoost combines tree-based learning with graph-based feature aggregation. The graph is used to enrich the node features with information from neighboring nodes, and gradient-boosted soft decision trees are then trained on these features. This allows tree-based models to take advantage of both the original node features and the structure of the graph.

## Experimental results

The paper evaluates three variants on six benchmark datasets: feature-only, GraphTreeBoost with Chebyshev filtering (GTB-Cheby), and GraphTreeBoost with heat-kernel filtering (GTB-Heat).

Reported values are test accuracy (%) averaged over ten runs.

| Model | Cora | Citeseer | Texas | Cornell | Actor | Chameleon |
|---|---:|---:|---:|---:|---:|---:|
| GCN | 87.12 ± 1.38 | 76.50 ± 1.61 | 63.81 ± 5.27 | 59.35 ± 4.19 | 30.31 ± 0.98 | 67.96 ± 1.82 |
| No aggregation | 52.79 ± 0.96 | 53.56 ± 1.59 | 71.08 ± 2.56 | 57.30 ± 3.78 | 33.53 ± 1.06 | 38.55 ± 2.13 |
| GTB-Cheby | 74.09 ± 2.73 | 56.77 ± 1.22 | 72.43 ± 2.79 | 66.75 ± 4.42 | 31.05 ± 1.10 | 71.75 ± 2.13 |
| GTB-Heat | 71.27 ± 2.46 | 57.18 ± 1.03 | 73.24 ± 3.24 | 72.97 ± 8.55 | 33.34 ± 0.47 | 50.83 ± 1.87 |

The GCN values are taken from the evaluations reported in the paper. See Table 1 of the paper for the complete comparison and methodology.

## Code

The implementation is publicly available on GitHub under the MIT license. The repository includes the GraphTreeBoost implementation and the code used to run the benchmark experiments.

[View GraphTreeBoost on GitHub →](https://github.com/laszlo-fetter/graphtreeboost)

## Reproducing the experiments

The repository documents the required Python dependencies and provides `main.py` for running the experiments. For example:

```bash
python main.py <Dataset>
```

## Publication

*GraphTreeBoost: Soft Decision Tree-Based Graph Learning With Spectral Aggregation* appears in the proceedings of the 34th European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning (ESANN 2026), held 22–24 April 2026.

DOI: [10.14428/esann/2026.ES2026-111](https://doi.org/10.14428/esann/2026.ES2026-111)

## Citation

```bibtex
@inproceedings{fetter2026graphtreeboost,
  author    = {Fetter, László and Gézsi, András},
  title     = {GraphTreeBoost: Soft Decision Tree-Based Graph Learning With Spectral Aggregation},
  booktitle = {Proceedings of the 34th European Symposium on Artificial Neural Networks,
               Computational Intelligence and Machine Learning (ESANN 2026)},
  year      = {2026},
  doi       = {10.14428/esann/2026.ES2026-111}
}
```

GraphTreeBoost · László Fetter and András Gézsi · ESANN 2026
