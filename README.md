# Catching a Bit Flip

This quantum error correction internship project demonstrates how two parity checks locate a deliberately injected bit flip in a three-qubit repetition code. The notebook reconstructs the experiment described in the final presentation and runs locally with a Python state-vector simulation.

![Five-wire circuit showing preparation, encoding, a D1 bit flip, syndrome extraction, and Toffoli correction](bit_flip_circuit.png)

The three data wires are D0, D1, and D2. Two ancilla wires, A0 and A1, store the adjacent parity checks. A filled dot marks a control and a circled plus marks the target. The red X is the injected error.

## Experiment

| Stage | Data (D0 D1 D2) | Ancillas (A0 A1) |
| --- | --- | --- |
| Encode logical 1 | 111 | 00 |
| Inject X on D1 | 101 | 00 |
| Extract syndrome | 101 | 11 |
| Apply correction | 111 | 11 |

The syndrome 11 activates a Toffoli gate with A0 and A1 as controls and D1 as the target. The corrected data returns to 111, and the ancillas retain the syndrome. The ideal simulation gives the final joint basis state with probability 1.

The circuit identifies which data qubit suffered a single X error. Its recovery gate acts on D1 only. The notebook also checks that D1 recovery preserves the amplitudes of a superposition. The diagram and notebook represent the correction as one Toffoli gate.

## Run the notebook

Open [bit_flip_correction.ipynb](bit_flip_correction.ipynb) in JupyterLab or another Jupyter-compatible editor, select a Python 3 kernel, and run all cells. The simulation uses the Python standard library. The saved outputs show the four checkpoints and the syndrome checks.
