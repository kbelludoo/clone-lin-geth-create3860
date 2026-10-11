# clone-lin-geth-create3860

LIN clone of [ethereum/go-ethereum](https://github.com/ethereum/go-ethereum) tag `v1.16.9` `gasCreateEip3860` / `gasCreate2Eip3860` (EIP-3860 initcode word gas, LGPL-3.0).

This repository holds **only the LIN copy**. Auditable proofs live in [kbelludoo/lin-open](https://github.com/kbelludoo/lin-open):

- Kernel: `src/lin_geth_create3860.lin`
- Proofs: `examples/geth_create3860/`
- Event: `docs/events/EVENT_GETH_CREATE3860_CLONE_LIN.rulel`
- Harness: `python3 test/prove_geth_create3860_external.py`

## Class

**EXPERIMENTAL** i64-scale. Not a Geth node. `stack.Back(2)` is lifted to an integer `size`. `size > MaxInitCodeSize` (49152) fail-closes to 0.

## Goldens

| size | CREATE | CREATE2 |
|---|---:|---:|
| 0 | 0 | 0 |
| 1 | 2 | 8 |
| 32 | 2 | 8 |
| 33 | 4 | 16 |
| 49152 | 3072 | 12288 |

Formula: `InitCodeWordGas * ((size+31)/32)` with `InitCodeWordGas=2`. CREATE2 adds `Keccak256WordGas=6`.

## License

Algorithm: LGPL-3.0 (go-ethereum). This LIN transcription is published so auditors can hash the clone independently of lin-open proofs.
