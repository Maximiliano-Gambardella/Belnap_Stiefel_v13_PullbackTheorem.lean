# A Formally Verified Pullback Theorem for Stiefel Manifolds (v13)

This repository contains the **Version 13** formalization in **Lean 4** of the Riemannian geometry on the complex Stiefel manifold $St(d, n)$ and its connection to the **Parameter-Shift Rule (PSR)** used in quantum circuit optimization.

## Overview

This 839-line Lean 4 artifact establishes a machine-checked bridge between the differential geometry of constrained matrix manifolds and hardware-compatible gradient evaluations. It specifically resolves the "Non-Claim 5.2" from Version 12, which declared the formal proof of the Pullback Theorem to be out of reach due to lack of library infrastructure.

## Main Formalized Results

The development is organized into seven sections mirroring the companion paper:

1.  **Automatic Tangency:** We prove that for any curve $\Phi(t)$ constrained to the Stiefel manifold ($\Phi(t)^\dagger \Phi(t) = I_d$), its derivative is automatically tangent to the manifold: $V^\dagger D + D^\dagger V = 0$ (Theorem 4.7).
2.  **Closed-Form Riemannian Gradient:** We derive and prove the exact expression for the Riemannian gradient of the loss functional $f(V) = \|V^\dagger MV - I_d\|^2_F$:
    $$\text{grad}_{St} f(V) = 4(I_n - VV^\dagger)MV(V^\dagger MV - I_d)$$
    This is achieved without relying on abstract manifold type classes, building the infrastructure directly from first principles.
3.  **The Pullback Theorem:** We establish that the pairing of the Riemannian gradient with any tangent direction $D$ equals the two-point PSR evaluation:
    $$\langle \text{grad}_{St} f(\Phi(t_0)), D \rangle_{tr} = \text{Re tr}(g(\Phi(t_0))(A_+ - A_-))$$
    This result confirms that the geometric gradient matches the quantity computable on quantum hardware.
4.  **Concrete Instantiation:** The abstract theorem is fully discharged via a layered-circuit construction and a concrete **Reconfigurable Beam Splitter (RBS)** gate instance.

## Key Hypotheses and Scope

*   **hPSR (Assumption 5.1):** The code explicitly isolates the "frequency-one" spectral fact (that $A$ admits an exact two-point PSR) as an external hypothesis. This is a fact of quantum-gate theory, not of the differential geometry formalized here.
*   **Self-Contained:** The development does not depend on unformalized results from Version 11 (such as Morse–Bott stratification).

## Reproducibility

To maintain the highest epistemological standards, this development is designed for **browser-based verification**.

1.  Copy the contents of `Belnap_Stiefel_v13_PullbackTheorem.lean`.
2.  Paste it into the [Lean 4 Playground](https://live.lean-lang.org/).
3.  Observe the absence of `sorry` placeholders and the confirmation of "No goals" at the end of each proof.

## References

*   **Version 11:** Zenodo record 19674923 (Theoretical foundations).
*   **Version 12:** Zenodo record 21354781 (Residual bound formalization).
*   **Version 13:** This artifact (Pullback Theorem formalization).

***

