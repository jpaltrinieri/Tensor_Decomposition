# Tensor Decomposition

Form-factor (tensor) decomposition of scattering amplitudes with FeynCalc and FeynArts.

## Contents

- `ee_pipi_FF_Tree.nb` — e⁺e⁻ → π⁺π⁻ in scalar QED at tree level. The amplitude is projected onto the
  basis {v̄(p1) p̸3 u(p2), v̄(p1) u(p2)}; the form factors follow from solving G·F = B with G the Gram
  matrix of the basis and B the projection of the amplitude. Result: F1 = −2e²/s, F2 = 0.
- `ee_pipi_FF_1L.nb` — the same at one loop (bare 1PI amplitude, ten diagrams, D dimensions). The form
  factors are obtained in two independent ways: projecting first and tensor-reducing the traces with TID,
  and tensor-reducing the open amplitude first and reading the coefficients off with the Dirac equation.
  Both are reduced to the fifteen scalar A0/B0/C0/D0 integrals and shown to agree. UV poles are extracted
  per diagram class, and alternative strategies (IBP reduction to master integrals, helicity amplitudes,
  numerical evaluation) are discussed.

- `ee_pipi/` — the resulting form factors as Mathematica expressions, one file per form factor
  (`FF_Tree_1.m`, `FF_Tree_2.m`, `FF_1L_1.m`, `FF_1L_2.m`) plus the Gram matrix of the basis. Both notebooks
  write here; the one-loop files are in the scalar A0/B0/C0/D0 basis with D kept symbolic.

## Requirements

Mathematica 13+, FeynCalc 10 with the FeynArts add-on. Scalar QED is obtained from the FeynArts SM
model by keeping only the charged Goldstone boson S[3], the electron and the photon, with m_W renamed
to m_π. At one loop the muon and tau and the quartic Goldstone self-coupling are excluded as well.
Running the one-loop notebook takes about a minute.
