# APEX Protocol Thesis

## The Core Problem

Every blockchain deployed today inherits the security assumptions of classical cryptographic primitives — primarily ECDSA over elliptic curves. Those assumptions were not designed for environments where large-scale quantum computation is available.

Shor's algorithm, running on a sufficiently large fault-tolerant quantum computer, solves the discrete logarithm problem in polynomial time. This unconditionally breaks ECDSA, EdDSA, and all elliptic curve variants. The cryptographic guarantees underpinning every existing Layer 1 are time-limited.

## The Time Horizon Problem

Financial infrastructure is not replaced on short cycles. Systems deployed today will process capital through 2035, 2040, and beyond. The threat model for any long-lived system cannot be bounded by today's adversarial landscape.

NIST finalized its first post-quantum cryptographic standards in 2024. The window between "standards are ready" and "infrastructure is ready" must not be closed by a crisis.

## The Store-Now-Decrypt-Later Risk

Passive adversaries harvesting blockchain data today may decrypt it upon acquiring quantum capability. On a transparent blockchain, every account that has signed a transaction has permanently published its public key. That data is already in adversarial possession.

## The APEX Response

APEX is built from first principles for the post-quantum era:

1. All transaction authorization uses CRYSTALS-Dilithium3 (NIST FIPS 204).
2. All session key establishment uses CRYSTALS-Kyber-768 (NIST FIPS 203).
3. Addresses are SHA3-256 hash commitments to public keys — unspent accounts do not expose their public key on-chain.
4. Cryptographic agility is built into the protocol from genesis — primitives are upgradeable via governance.

APEX is not a response to a demonstrated attack. It is a response to a structural risk that prudent infrastructure design cannot ignore.
