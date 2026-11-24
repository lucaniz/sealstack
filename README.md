# Sealstacking: How a Prover Can Fake Storage by Encoding Its Own Encodings

**Luca Nizzardo** ([l.nizzardo@gmail.com](mailto:l.nizzardo@gmail.com)) · **Irene Giacomelli** ([irene.giacomelli29@gmail.com](mailto:irene.giacomelli29@gmail.com)) · November 2026

A self-contained explainer of the Sealstack attack.

📄 **[Read the PDF](Sealstacking%20-%20Nizzardo%2C%20Giacomelli.pdf)**

## TL;DR

- A prover that chooses its own data can seal it, declare the result as the data of the next unit of storage, seal again, and keep only the outermost layer. If decoding is fast, it can claim c = ⌈T_chal / T_unseal⌉ times more storage than it holds, and every check the verifier runs still passes.
- In Filecoin (where the attack was identified in the design phase) the storage a prover can claim is unbounded. In AI verification, memory is bounded by the accelerator, and model weights committed before the verifier reveals the sealing randomness cannot be stacked: only the part of memory filled with data the prover chooses stays exposed.
Note that Filecoin does not suffer Sealstacking as it relies on symmetric sealing.
- **Potential Defences:** periodic re-sealing with fresh randomness, or symmetric encodings, at the cost of losing fast decoding.

No knowledge of Filecoin or of any specific proof system is needed to follow the note. Sealstack is not an attack on Filecoin: it is a generic attack on proofs of storage in which the prover chooses its own data and decoding is fast.

## Related work

- [SEAL Stacking Attack (SEALSTACK), Filecoin research issue #71](https://github.com/filecoin-project/research/issues/71)
- [Seal-Stack Attack and Dynamic PoRep, CryptoNet](https://cryptonet.org/research/seal-stack-attack-and-dynamic-porep)
- [Sealstack modeling (HackMD)](https://hackmd.io/@LIRa8YONSwKxiRz3cficng/rymp9wCfa)
- [PIEs: Public Incompressible Encodings for Decentralized Storage (Cecchetti, Fisch, Miers, Juels, CCS 2019)](https://eprint.iacr.org/2018/684)
- [Proofs of Catalytic Space (Pietrzak, ITCS 2019)](https://eprint.iacr.org/2018/194)

---

*This document was written with the support of AI.*
