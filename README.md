# Quantum Algorithms from First Principles — companion notebooks

Companion code for

> Muhammad Faryad, *Quantum Algorithms from First Principles: Derivations and
> Implementation Guides to Shor, Grover, Hamiltonian Simulation, Quantum Chemistry,
> Linear Algebra, and Block Encoding Algorithms* (2026).
> Paperback, hardcover and Kindle: [Amazon](https://www.amazon.com/dp/B0HKKHC6HP)
> Free PDF edition: [maven.com/faryad/o/05455f](https://maven.com/faryad/o/05455f)

One Jupyter notebook per implementation guide in Chapters 6–10. Each notebook follows its
guide in the book's order (register counts, the pieces, the assembled circuit, then the
tests in the order the book lists them) and every claim it prints was computed when the
notebook was run. The notebooks are self-contained: nothing is imported from elsewhere in
the repository.

## Notebooks

| Chapter | Guide | Notebook |
|---|---|---|
| 6 | Building Grover's algorithm | [06a_grover](notebooks/06a_grover.ipynb) |
| 6 | Building the counting circuit | [06b_quantum_counting](notebooks/06b_quantum_counting.ipynb) |
| 6 | Building amplitude amplification, derandomizing | [06c_amplitude_amplification](notebooks/06c_amplitude_amplification.ipynb) |
| 6 | Building the simulation-based search | [06d_search_by_hamiltonian_simulation](notebooks/06d_search_by_hamiltonian_simulation.ipynb) |
| 7 | Choosing and testing the Trotter parameters | [07a_trotter_suzuki](notebooks/07a_trotter_suzuki.ipynb) |
| 7 | Building the sparse (1-sparse) simulator | [07b_sparse_hamiltonian](notebooks/07b_sparse_hamiltonian.ipynb) |
| 7 | Building an LCU | [07c_lcu](notebooks/07c_lcu.ipynb) |
| 7 | Building a Pauli-sum simulator (`pauli_evolution`) | [07d_pauli_string_simulation](notebooks/07d_pauli_string_simulation.ipynb) |
| 8 | Building the whole chemistry pipeline (H₂, STO-3G) | [08_chemistry_pipeline](notebooks/08_chemistry_pipeline.ipynb) |
| 9 | Building QAOA | [09a_qaoa](notebooks/09a_qaoa.ipynb) |
| 9 | Building HHL | [09b_hhl](notebooks/09b_hhl.ipynb) |
| 10 | Maximum-likelihood amplitude estimation | [10a_mlae](notebooks/10a_mlae.ipynb) |
| 10 | Trotter-free simulation by qubitization | [10b_qubitization_simulation](notebooks/10b_qubitization_simulation.ipynb) |
| 10 | Linear systems beyond HHL (QSVT) | [10c_qsvt_linear_solver](notebooks/10c_qsvt_linear_solver.ipynb) |

Chapters 1–5 have no implementation guides; their circuits (QFT, phase estimation, period
finding) appear inside the notebooks above where they are needed.

## Conventions

The book writes a register as $|q_0 q_1 \cdots q_{n-1}\rangle$ with $q_0$ the most
significant bit on the top wire. Qiskit numbers qubits the other way round. Every
notebook maps book wire $j$ to Qiskit qubit `n - 1 - j` through a one-line helper `bq`,
so that Qiskit's printed bitstrings and statevector indices read exactly as in the book.
Pauli strings are written in book order (leftmost letter on wire 0). Appendix A of the
book collects the remaining conventions (rotation angles, occupation numbers, signs).

## Running

```
pip install -r requirements.txt
jupyter lab notebooks/
```

Tested with Qiskit 2.6, qiskit-aer 0.18, PySCF 2.15 (Chapter 8 only), NumPy 2.5,
SciPy 1.18 on Python 3.13. Everything runs on a laptop with the Aer simulator; no IBM
account is needed. The longest notebook (QSVT linear solver) takes about a minute, most
take seconds.

## Errata

Corrections to the printed book are listed in [ERRATA.md](ERRATA.md). Please report
anything you find through a GitHub issue.

## License

The code in this repository is released under the MIT License (see [LICENSE](LICENSE)).
The text of the book is copyright © Muhammad Faryad and is not covered by that license.
