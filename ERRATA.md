# Errata

Corrections to the first printing of *Quantum Algorithms from First Principles*
(September 2026). Page numbers are the printed folios, identical in the paperback,
hardcover and Kindle editions. Entries are listed by page.

To report a correction, open an issue on this repository with the page number, the
printed text, and what it should say.

## Chapter 4

**Page 116, box "This is a feature, not a workaround", last paragraph; page 121,
table "QPE versus IPE", row "Superposition of eigenvectors".**

Printed: the iterative method of Section 4.3 "does not give a clean answer" on a
superposition of eigenvectors, because "different rounds can collapse onto different
eigenvectors"; the table marks IPE as "unreliable" for such inputs.

Correction: this is wrong for the procedure the book actually describes. In Section
4.3 the eigenvector register is kept in place through all rounds and only the ancilla
is measured and reset (Fig. 4.11). That construction is the semiclassical Fourier
transform of Griffiths and Niu (Phys. Rev. Lett. 76, 3228, 1996), and it is unitarily
identical to standard phase estimation followed by measuring the counting qubits one
at a time. On a superposition input it therefore returns eigenphase θ_j with
probability |c_j|², exactly as QPE does, and the measurements progressively condition
the retained register, which ends in the corresponding eigenvector |u_j⟩. The table
row should read "works (samples spectrum), provided the eigenvector register is kept
between rounds".

The printed warning is correct only for a different implementation, in which the
eigenvector register is freshly prepared at the start of every round. Then each
round's bit may come from a different eigenvector and the assembled bits describe no
single eigenphase. Numerically, with eigenphases 1/8 and 6/8 at weights 0.3 and 0.7,
IPE with the register kept returns m = 1 and m = 6 with probabilities 0.30 and 0.70;
with the register re-prepared each round the outcome spreads over all eight values
of m. Readers applying phase estimation to approximate eigenstates in quantum
chemistry (Chapter 8) should note the distinction.

Reported by James Weaver.

## Chapter 6

**Page 184, box "Building the simulation-based search", paragraph "Testing".**

Printed: "plot the error against Δt: it should fall as Δt². If it falls as Δt, you
have a bug in the splitting order."

Correction: the statement conflates two quantities. The error of a *single* first-order
step falls as Δt², but the accumulated error of the whole evolution to t* at fixed t*
falls as Δt for the first-order split (as the same box says two paragraphs earlier,
O(t* Δt)) and as Δt² only for the symmetric split of Chapter 7. A slope of 1 at fixed
t* with the first-order split is therefore correct, not a bug. Chapter 7's testing box
(page 194) states the slopes correctly. The companion notebook
`06d_search_by_hamiltonian_simulation` measures all three slopes.

## Chapter 8

**Page 238, worked example (H₂ in STO-3G), Step 3.**

Printed: "Parity encoding plus the two-qubit tapering of §8.6.6 reduces this to
2 qubits and six terms: I, Z₀, Z₁, Z₀Z₁, X₀X₁ and Y₀Y₁."

Correction: carried out as §8.6.6 describes (parity encoding with spin-blocked
ordering, qubits M/2−1 and M−1 replaced by their eigenvalues), the result has five
terms: I, Z₀, Z₁, Z₀Z₁ and X₀X₁, the four XXYY-type strings of the four-qubit
Hamiltonian all landing on X₀X₁ with coefficient 0.1809 Hartree. The six-term form
with X₀X₁ and Y₀Y₁ of equal weight (about 0.0905 each) is the reduction of O'Malley
et al., Phys. Rev. X 6, 031007 (2016), which uses a different symmetry argument. Both
operators agree on the physical subspace, and Step 4 is unaffected: the ground state
is −1.1373 Hartree either way. The companion notebook `08_chemistry_pipeline`
performs the tapering and prints the five terms.
