# DPoVA-consensus
# coinnum: Delegated Proof of Verified Authority (DPoVA)

[![License: MIT/Apache-2.0](https://img.shields.io/badge/License-MIT%2FApache--2.0-blue.svg)]()
[![Language: Rust](https://img.shields.io/badge/Language-Rust-orange.svg)]()
[![Architecture: Wasm/CVM](https://img.shields.io/badge/Architecture-Wasm%2FCVM-purple.svg)]()

> A highly scalable, accountable, and capital insulated Byzantine Fault Tolerant (BFT) consensus protocol engineered for next generation digital financial infrastructure.

---

## 🏛️ Executive Overview

The **coinnum** introduces the **Delegated Proof of Verified Authority (DPoVA)** consensus mechanism. Traditional Proof of Stake (PoS) networks naturally degrade into oligopolistic plutocracies where absolute capital mass correlates directly to block verification power and governance vetoes. 

DPoVA elegantly breaks this "rich get richer" loop by completely decoupling a node's **Capital Alignment** from its **Operational Integrity**:
1. **Hard Gate Economic Alignment:** Nodes must stake a mandatory baseline minimum of **26 CNM** to enter the lifecycle state machine.
2. **Soft Weight Selection:** Actual consensus selection frequency and block proposal rights are governed by an independent, non linear, rapidly decaying **Reputation Engine**.
3. **Anti-Capture Ceiling:** A strict protocol enforced invariant ensures no single validator or colluded entity can ever wield more than **33% of the total network influence**.

---

## Key Technical Features

* **Dual Layer Deterministic Finality:** Seamlessly pipelines blocks through a 4-Phase BFT loop for rapid sub 5 second local finality, anchored by an immutable **Checkpoint Finality Certificate (CFC)** compiled every 100 blocks.
* **Modern Cryptographic Stack:** Leverages tree structured parallelized **BLAKE3** for blazingly fast state trie hashing, **Ed25519** for lightning quick transport/identity validation, and **BLS12-381** pairings for high density multi-signature consensus aggregation.
* **Dynamic Committee Sizing:** Automatically expands or compresses the active consensus sub committee ($C_d$) based on a real time hardware calculated *Partition Suspicion Score (PSS)* to survive active adversarial network splits.
* **Dual Phase VM Evolution:** Launches with a high performance WebAssembly (Wasm) runtime running a transparent EVM compatibility layer, with a planned upgrade path to a native, parallel processing **Coinnum Virtual Machine (CVM)**.
* **Ultra Light Clients:** Uses **Merkle Mountain Ranges (MMR)** to enable resource constrained environments (e.g., mobile wallets) to instantly verify historical transaction finality via logarithmic proof paths.

---

## Tokenomics: coinnum ($CNM$)

The native utility and security token **coinnum ($CNM$)** has a strictly fixed maximum supply established at genesis with a non inflationary, non burning layout. 

* **Gas Fee Dynamics:** Operates under a predictable `Base Fee + Priority Fee` schedule.
* **Velocity Preservation:** No portion of gas fees is burned. Transaction fees are entirely recycled into the ecosystem: **60%** to the Validator Reward Pool, **30%** directly to the active Block Proposer, and **10%** to the Network Treasury.

---

## Repository Software Directory Structure

```text
dpova-node/
├── Cargo.toml                  # Cargo project configuration manifest
├── src/
│   ├── main.rs                 # Node runtime initialization and kernel hook
│   ├── crypto/                 # Hashing (BLAKE3), Ed25519, and BLS12-381 pairings
│   ├── network/                # libp2p wire framing, gossip channels, and Protobufs
│   ├── consensus/              # 4-Phase BFT State Machine and view change loops
│   ├── storage/                # RocksDB Column Family isolated storage drivers
│   ├── reputation/             # Asynchronous non-linear decay scoring engine
│   ├── audit/                  # Real time anomaly, ring, and evidence generation modules
│   └── vm/                     # Wasm runtime sandbox and native CVM ISA compiler
