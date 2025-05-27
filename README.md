# Equation Learner (EQL) with L₀ Regularization

## Overview

This repository implements a symbolic regression model based on the **Equation Learner (EQL)** framework. The goal is to train neural networks that **output interpretable mathematical expressions**, bridging data-driven models with symbolic reasoning.

This work:

* Is **inspired by the MIT paper** by Kim et al. (2019) \[[arXiv:1912.04825](https://arxiv.org/abs/1912.04825)]
* Explores **L₀ regularization** to promote sparsity (following Louizos et al., 2017)
* Serves as a **prerequisite to future NOMTO-style developments**, focusing purely on symbolic expression recovery (not Neural Operators)

>  This project **does not implement NOMTO**, but includes a comparative study and roadmap in the attached theory documents.

---

## Repository Contents

```
.
├── EQLs_EPFL_Training0.ipynb                    # Main implementation (PyTorch)
├── EQL Model Mind Map.png                       # Graphical overview of model components
├── Theory - Focus on L0 Regularization.pdf       # Notes on sparsity and regularization
├── Theory - Symbolic Regression and NOMTO.pdf    # Notes on Neural Operators (not implemented)
├── Presentation - From Symbolic Regression to Neural Operators.pdf
├── Paper - Kim et al., Equation Learner (MIT).pdf
```

---

## Features

* ✅ Symbolic regression with trainable neural network
* ✅ Interpretable basis functions: `sin`, `log`, `sign`, `square`, `identity`, `product`
* ✅ L₀ regularization using the hard-concrete distribution
* ✅ Final symbolic equation extraction using SymPy
* ✅ Multi-run benchmarks with stability analysis

---

## Example: Fitting sin(x)

```python
bench = Benchmark(
    n_layers=2,
    reg_weight=5e-6,
    learning_rate=1e-2,
    n_epochs1=2001,
    n_epochs2=2001
)
bench.benchmark(lambda x: np.sin(x), func_name="sin(x)", trials=5)
```

Resulting expression (example):

```latex
y(x) = 0.05x + 0.92\sin(1.04x)
```

---

## Mind Map

To aid understanding, a complete [**mind map**](./EQL%20Model%20Mind%20Map.png) is included, covering:

* Symbolic function definitions
* EQL architecture (with/without L₀)
* Symbolic expression extraction
* Testing loop and benchmarks

---

## Inspirations and Comparisons

| Concept                   | Implemented? | Source                                                   |
| ------------------------- | ------------ | -------------------------------------------------------- |
| Symbolic Regression (EQL) | ✅            | [Kim et al., 2019](https://arxiv.org/abs/1912.04825)     |
| L₀ Regularization         | ✅            | [Louizos et al., 2017](https://arxiv.org/abs/1712.01312) |
| NOMTO Operator Extraction | ❌            | [Garmaev et al., 2024](https://arxiv.org/abs/2501.08086) |

---

## Requirements

* Python 3.8+
* PyTorch
* NumPy
* SymPy
* matplotlib
* tqdm

Optional: Run in Google Colab for easy GPU access.

---

## Limitations

* ❌ No PDE rediscovery
* ❌ No function-to-function learning (Neural Operators)
* ❌ No NOMTO symbolic tree parser
* ❌ Limited to 1D/2D symbolic functions (future upgrade planned)

---

## Next Steps

Planned upgrades:

* ✅ Switch between L₁ and L₀/HardConcrete regularization
* 🔄 Integrate Neural Operators (FNO/CNO)
* 🔄 Benchmark against KANs and NOMTO
* 🔄 Automatic symbolic tree extraction

---

## References

* Samuel Kim et al., [*Equation Learner for Symbolic Regression*](https://arxiv.org/abs/1912.04825)
* Christos Louizos et al., [*L₀ Regularization*](https://arxiv.org/abs/1712.01312)
* Sergei Garmaev et al., [*NOMTO*](https://arxiv.org/abs/2501.08086)

---

## Author

**Yasser El Kouhen**
* AI Research Intern @ EPFL IMOS Lab
* GitHub: [@Yasser-EL-KOUHEN](https://github.com/Yasser-EL-KOUHEN)
* Contact: [yasserelkouhen5@gmail.com](mailto:yasserelkouhen5@gmail.com)

