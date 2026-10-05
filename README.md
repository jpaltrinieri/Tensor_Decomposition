# Tensor Decomposition

Form-factor (tensor) decomposition of scattering amplitudes with FeynCalc and FeynArts.

## Contents

- `ee_pipi_FF_Tree.nb` — e⁺e⁻ → π⁺π⁻ in scalar QED at tree level. The amplitude is projected onto the
  basis {v̄(p1) p̸3 u(p2), v̄(p1) u(p2)}; the form factors follow from solving G·F = B with G the Gram
  matrix of the basis and B the projection of the amplitude. Result: F1 = −2e²/s, F2 = 0.

## Requirements

Mathematica 13+, FeynCalc 10 with the FeynArts add-on. Scalar QED is obtained from the FeynArts SM
model by keeping only the charged Goldstone boson S[3] and the photon, with m_W renamed to m_π.
