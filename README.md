# Tensor Decomposition

Form-factor (tensor) decomposition of scattering amplitudes with FeynCalc and FeynArts.

## Contents

- `ee_pipi_FF_Tree.nb` — e⁺e⁻ → π⁺π⁻ in scalar QED at tree level. The amplitude is projected onto the
  basis {v̄(p1) p̸3 u(p2), v̄(p1) u(p2)}; the form factors follow from solving G·F = B with G the Gram
  matrix of the basis and B the projection of the amplitude. Result: F1 = −2e²/s, F2 = 0. Then the
  polarised amplitudes M(λa, λb) = FF1 T1 + FF2 T2 in the brackets ⟨ij⟩, [ij] only: every massive momentum
  is split along a light-like reference ξ as in CEEX (p = p♭ + k, k ∝ ξ, u(p) = u(p♭) + u(k), p̸₃ = Σ |·⟩[·| + |·]⟨·|),
  and brackets of two k's vanish, so e.g. M(−,−) = FF1 (⟨1♭3♭⟩[3♭k₂] − [k₁3♭]⟨3♭2♭⟩) + FF2 ⟨1♭2♭⟩; λ = 2S_z along the e⁺ beam (e⁺ helicity λa, e⁻ −λb).
- `ee_pipi_FF_1L.nb` — the same at one loop (bare 1PI amplitude, ten diagrams, D dimensions). The form
  factors are obtained in two independent ways: projecting first and tensor-reducing the traces with TID,
  and tensor-reducing the open amplitude first and reading the coefficients off with the Dirac equation.
  Both are reduced to the fifteen scalar A0/B0/C0/D0 integrals and shown to agree. UV poles are extracted
  per diagram class, and alternative strategies (IBP reduction to master integrals, helicity amplitudes,
  numerical evaluation) are discussed.

- `ee_pipi_check_CEEX.nb` — checks CEEX's numerical spin tensors (`T_pipi`) against the tree decomposition.
  Step 1, the Gram check: Σ_spins T_i T_j^* from CEEX at one CMD point (`ee_pipi/CEEX_point.m`, written by
  CEEX's `TESTS/TESTS_DRIVERS/gram_pipi_dump.f90`) against `ee_pipi/Gram_Matrix.m`, and the Born spin sum with
  `FF_Tree_*.m`: agreement to 2×10⁻¹² (double precision). Step 2, per helicity: CEEX's spinor construction
  (`Spinors.f`, `Weyl.f`: chiral γ's, massive spinors on the reference ξ = (1,0,0,−1)) rebuilt in Mathematica;
  in double it reproduces CEEX's T to 10⁻¹⁶ per helicity with phases, at 50 digits it satisfies the Gram
  matrix exactly; CEEX's 10⁻¹² is the cancellation in p₂·ξ = E − p_z for the e⁻ (parallel to ξ). Step 3: the
  saved polarised amplitudes (brackets evaluated on CEEX's spinors) equal CEEX's `amp_pipi_LO` complex-conjugated, per helicity. Plain Mathematica, no FeynCalc. CEEX's e line is
  ū(p2)…v(p1), the complex conjugate of the notebook's v̄(p1)…u(p2).

- `ee_pipi/` — the resulting form factors as Mathematica expressions, one file per form factor
  (`FF_Tree_1.m`, `FF_Tree_2.m`, `FF_1L_1.m`, `FF_1L_2.m`) plus the Gram matrix of the basis. Both notebooks
  write here, and the tree notebook also writes the polarised amplitudes `Pol_Amp_<λa><λb>.m` (m/p = −1/+1):
  FF[1] T1 + FF[2] T2 in ang[a,b] = ⟨ab⟩, sq[a,b] = [ab] of "1b", "2b", "3b", "k1", "k2", "k3",
  the same at every order (FF from FF_Tree_i.m or FF_1L_i.m). The form-factor files are expressed in s, t, m12 = me² and m32 = mpi² (odd powers of the masses appear as
  Sqrt[m12], Sqrt[m32]); the one-loop files are in the scalar A0/B0/C0/D0 basis with D kept symbolic.

## Requirements

Mathematica 13+, FeynCalc 10 with the FeynArts add-on. Scalar QED is obtained from the FeynArts SM
model by keeping only the charged Goldstone boson S[3], the electron and the photon, with m_W renamed
to m_π. At one loop the muon and tau and the quartic Goldstone self-coupling are excluded as well.
Running the one-loop notebook takes about a minute.
