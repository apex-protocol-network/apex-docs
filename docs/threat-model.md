# APEX Threat Model

## Adversary Classes

### Classical Adversary
Polynomial-time algorithms on classical hardware. Against this model, ECDSA is computationally secure.

### Quantum Adversary
Access to a large-scale fault-tolerant quantum computer. Against this model:
- Shor's algorithm breaks ECDSA and EdDSA unconditionally.
- Grover's algorithm halves hash function security to ~128 bits at 256-bit output. Considered sufficient.

APEX's threat model does not require such a computer to exist today.

## Primary Attack Surface: Signature Forgery

Recovering private keys from exposed public keys.

**Mitigation:** All signing uses CRYSTALS-Dilithium3. Security reduces to MLWE and MSIS. No polynomial-time quantum algorithm known for either.

## Secondary Attack Surface: Channel Compromise

Decrypting inter-node session traffic retroactively.

**Mitigation:** CRYSTALS-Kyber-768 for all session key encapsulation. Forward secrecy via ephemeral key generation per session.

## Store-Now-Decrypt-Later (SNDL)

Harvesting on-chain data today for future quantum decryption.

**Mitigation:** Addresses are SHA3-256 hashes of public keys. Unspent accounts do not expose public keys on-chain. Signed-from accounts should be treated as potentially exposed in the long-horizon model.

## Out of Scope

- Validator collusion via economic means
- Physical key compromise
- Supply chain attacks on client software
