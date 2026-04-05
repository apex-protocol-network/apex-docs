# APEX Architecture

## Layer Model

| Layer | Responsibility |
|-------|---------------|
| Consensus | Block ordering and finalization |
| Execution | State transition computation |
| Settlement | Value transfer and account state |

Each layer evolves independently.

## Consensus

Tendermint-derived BFT. Deterministic finality upon 2/3+ supermajority Precommit. All validator signing uses CRYSTALS-Dilithium3. Active set: up to 128 validators.

## State

Merkle Patricia Trie. Each block header commits to the post-execution state root.

## Cryptographic Primitives

| Operation | Primitive |
|-----------|-----------|
| Transaction signing | CRYSTALS-Dilithium3 (NIST FIPS 204) |
| Key encapsulation | CRYSTALS-Kyber-768 (NIST FIPS 203) |
| Address derivation | SHA3-256 |
| Merkle tree | BLAKE3 |
| Emergency signing | SPHINCS+-SHA2-256f (NIST FIPS 205) |

## Repository Map

| Repository | Role |
|------------|------|
| apex-core | Protocol types, interfaces, consensus logic |
| apex-crypto | PQC primitive implementations |
| apex-node | Node software, P2P, RPC |
| apex-wallet | CLI wallet |
| apex-explorer | Block explorer |
| apex-docs | Specifications |
