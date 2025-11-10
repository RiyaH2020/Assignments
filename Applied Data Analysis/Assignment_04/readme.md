# 🧠 Community Detection on the Enron Email Network

This project explores **community detection algorithms** applied to the **Enron email dataset**, focusing on identifying structural patterns and communication clusters among employees.  

---

## 📁 Dataset

The Enron email network was represented as an **undirected weighted graph**, where:
- **Nodes** → Individuals (email addresses)
- **Edges** → Email exchanges between individuals
- **Edge Weights** → Number of emails exchanged  

---

## ⚙️ Preprocessing

- Filtered out **isolated nodes** and **extreme-degree nodes** (too high or too low degree) to construct meaningful subgraphs.
- Generated a **moderate-degree subgraph (H_gn)** to ensure fair comparison across algorithms.
- Used **NetworkX** for graph manipulation and community detection.

---

## 🧩 Algorithms and Results

### 1. Louvain Community Detection

The **Louvain algorithm** was applied to the entire Enron network to detect hierarchical modular structures.

**Results:**
- **Modularity:** 0.5237  
- **Number of Communities:** 144  
- **Largest Community Size:** 6,112  
- **Smallest Community Size:** 4  
- **Average Community Size:** 832.75  

**Observations:**
- Louvain achieved the **highest modularity**, indicating **strong community structure**.
- Efficient and scalable — ideal for large graphs.
- However, it can **get trapped in local optima**, producing slightly inconsistent results across runs.

---

### 2. Girvan–Newman on Degree-Filtered Subgraph

Applied the **Girvan–Newman algorithm** on a **moderate-degree subgraph (H_gn)** due to its high computational cost.

**Results:**
- **Modularity:** 0.0423  
- **Number of Communities:** 2  
- **Largest Community Size:** 3,377  
- **Smallest Community Size:** 55  
- **Average Community Size:** 1,716.00  

**Observations:**
- Produces **clear hierarchical splits**, but suffers from **poor scalability**.
- Not suitable for large networks like Enron.
- Best used for **visual analysis** or small subgraphs where interpretability matters.

---

### 3. Spectral Clustering on Moderate-Degree Subgraph

Applied **Spectral Clustering** using the **graph Laplacian** on the same subgraph used for Girvan–Newman.

**Results:**
- **Number of Communities:** 5  
- **Modularity:** 0.3332  
- **Community Sizes:** 31 – 2,932 nodes  
- **Average Size:** 686.40 nodes  

**Observations:**
- Captures **global structural patterns** via eigen-decomposition.
- Performs well on **moderate-sized subgraphs**.
- Computationally heavier than Louvain but more stable than Girvan–Newman.

---

### 4. Label Propagation

The **Label Propagation algorithm** was applied to the **entire network**.

**Results:**
- **Modularity:** 0.3433  
- **Number of Communities:** 1,679  
- **Largest Community Size:** 18,589  
- **Smallest Community Size:** 2  
- **Average Community Size:** 20.07  

**Observations:**
- Extremely **fast and scalable**, ideal for large graphs.
- However, results can be **unstable** since label updates are random.
- Captures **local clusters** effectively but lacks global interpretability.

---

## 📊 Summary Comparison

| Algorithm           | Modularity | # Communities | Scalability | Strengths | Weaknesses |
|---------------------|-------------|----------------|--------------|------------|-------------|
| **Louvain**         | **0.5237**  | 144            | ✅ Excellent | High modularity, efficient, robust | Can get trapped in local optima |
| **Girvan–Newman**   | 0.0423      | 2              | ❌ Poor      | Hierarchical splits, interpretable | Computationally expensive |
| **Spectral Clustering** | 0.3332  | 5              | ⚙️ Moderate  | Captures global structure | High complexity (eigendecomposition) |
| **Label Propagation** | 0.3433    | 1,679          | ✅ Excellent | Very fast, automatic cluster formation | Unstable, random label convergence |

---

## 🚀 Key Insights

- **Louvain** provides the **best modularity** and most interpretable community structure.  
- **Label Propagation** is **fastest**, making it suitable for very large-scale graphs.  
- **Spectral Clustering** serves as a balanced choice between **accuracy** and **interpretability**.  
- **Girvan–Newman** is mainly valuable for **academic demonstration**, not large graphs.  

---

## 🔮 Future Scope

- Develop a **hybrid Louvain + Girvan–Newman (L+GN)** approach:
  - Use Louvain for coarse clustering.
  - Apply GN locally within large communities to refine substructures.
- Explore **temporal community detection** (since Enron emails are time-stamped).
- Investigate **embedding-based clustering** using GNNs or Node2Vec for deeper representation learning.

---



## 🏁 Conclusion

The **Louvain algorithm** emerged as the **most effective** for uncovering meaningful communities within the Enron email network.  
Future hybrid approaches combining **efficiency (Louvain)** with **precision (Girvan–Newman)** could further enhance detection in large-scale communication networks.

---

