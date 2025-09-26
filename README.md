# 🔐 Confidential Smart Legal Contracts (FHE-DocuSign)

> A next-generation DocuSign built on a blockchain with **Fully Homomorphic Encryption (FHE)**.
> Store contracts confidentially, enforce signing rules automatically, and prove outcomes without revealing sensitive terms.

## 📖 Overview

Traditional e-signature apps like DocuSign work well but require **trust in a central provider**. They store documents in plaintext on their servers, manage audit logs internally, and control the whole process.

With **FHE-powered smart contracts**, we flip this model:

* Contracts and sensitive fields (price, dates, clauses) are always **encrypted**.
* The blockchain itself can still **enforce rules** (e.g., “all parties signed before deadline”) **without ever seeing the data**.
* Results are **verifiable on-chain**, audit logs are immutable, and only signers can decrypt.

This creates a **neutral, privacy-first alternative** to Web2 e-signature apps.

## ⚖️ Why It Matters

| Feature                  | Web2 DocuSign                           | FHE-DocuSign                                                 |
| ------------------------ | --------------------------------------- | ------------------------------------------------------------ |
| **Document Privacy**     | Stored in plaintext on provider servers | Stored encrypted (AES + FHE), never revealed on-chain        |
| **Audit Trail**          | Centralized logs in DocuSign’s DB       | Immutable, tamper-proof, on-chain event history              |
| **Trust Model**          | Trust DocuSign to secure data           | Trustless: validators compute on ciphertext, can’t see terms |
| **Selective Disclosure** | All or nothing access                   | Reveal only what’s needed (e.g., “salary ≥ $80k”)            |
| **Composability**        | Isolated e-signature system             | Auto-trigger payments, escrow, workflows                     |
| **Neutral Ground**       | Vendor-controlled                       | Shared blockchain layer, no single party in control          |

## ⚙️ How It Works

1. **Create Document**

   * PDF is encrypted with AES-GCM.
   * Only signers hold decryption keys.
   * A document fingerprint (hash) is anchored on-chain.

2. **Encrypt Key Facts**

   * Critical fields (e.g., required signatures, expiry date) are encrypted with the contract’s **FHE public key**.
   * The blockchain processes these fields without seeing them.

3. **Invite & Sign**

   * Signers decrypt and review the doc locally.
   * When signing, the blockchain increments an **encrypted counter** inside FHE.

4. **Finalize**

   * Blockchain checks, inside ciphertext:

     * “Has required number of signers signed?”
     * “Is current time ≤ expiry date?”
   * If true → state changes to **Finalized**.

5. **Optional Escrow**

   * Smart contracts can hold funds, royalties, or assets.
   * Release is tied to the contract’s encrypted final status.

6. **Amend or Reveal**

   * Amendments = new encrypted version linked to the old one.
   * For disputes, a threshold of parties can **decrypt specific fields** or the whole doc.

## 🔑 Key Benefits

* **Confidentiality** – only signers see the contract.
* **Verifiable Workflow** – existence & state visible, terms hidden.
* **Legal Disputes Supported** – selective reveal via threshold decryption.
* **Programmable Agreements** – tie signatures to escrow, royalties, governance.
* **Future-Proof** – works for regulated, enterprise, and cross-org use.

## 🎯 Example Use Cases

* **NDAs & MSAs** → enforce signatures before a deadline, keep clauses private.
* **Employment Offers** → prove “salary ≥ X” without exposing entire contract.
* **Vendor Contracts** → confidential tiered pricing, escrow releases at milestones.
* **Royalty Agreements** → splits remain secret, payouts auto-execute.
* **Board / DAO Votes** → votes encrypted, tally homomorphic, only outcome visible.

## 🚀 MVP Scope

* Contract registry for agreements.
* Encrypted counters (`sign_count`, `required_signers`).
* Encrypted deadlines (`expiry`).
* Core functions: `create`, `invite`, `sign`, `finalize`, `amend`.
* Off-chain storage (IPFS/S3) for encrypted PDFs.
* Client app for PDF encryption/decryption & signing.

## 🛤 Roadmap

* [ ] Threshold key management (multi-party decryption for disputes).
* [ ] Escrow integration for conditional payouts.
* [ ] Selective disclosure (decrypt only certain clauses).
* [ ] Enterprise connectors (Salesforce, Workday, etc.).
* [ ] Compliance mapping (ESIGN, UETA, eIDAS).

## 🧪 Development Template

This repo is based on the **FHEVM Hardhat template** from Zama, supporting Solidity contracts with FHE primitives.

* [Quick Start Guide](https://docs.zama.ai/protocol/solidity-guides/getting-started/quick-start-tutorial)
* [FHEVM Documentation](https://docs.zama.ai/fhevm)

## ⚡ Quick Start

### Prerequisites

* Node.js ≥ 20
* npm / yarn / pnpm

### Setup

```bash
# Install deps
npm install

# Configure env vars
npx hardhat vars set MNEMONIC
npx hardhat vars set INFURA_API_KEY
npx hardhat vars set ETHERSCAN_API_KEY   # optional
```

### Commands

```bash
npm run compile        # Compile contracts
npm run test           # Run tests
npm run coverage       # Coverage report
npm run lint           # Lint checks
npm run clean          # Clean artifacts
```

### Local Deploy

```bash
npx hardhat node
npx hardhat deploy --network localhost
```

### Testnet Deploy (Sepolia)

```bash
npx hardhat deploy --network sepolia
npx hardhat verify --network sepolia <CONTRACT_ADDRESS>
npx hardhat test --network sepolia
```

---

## 📁 Project Structure

```
fhevm-hardhat-template/
├── contracts/           # Smart contracts
├── deploy/              # Deployment scripts
├── tasks/               # Custom Hardhat tasks
├── test/                # Tests
├── hardhat.config.ts    # Config
└── package.json
```

## 📚 Resources

* [FHEVM Docs](https://docs.zama.ai/fhevm)
* [Setup Guide](https://docs.zama.ai/protocol/solidity-guides/getting-started/setup)
* [Testing Guide](https://docs.zama.ai/protocol/solidity-guides/development-guide/hardhat/write_test)
* [FHEVM Hardhat Plugin](https://docs.zama.ai/protocol/solidity-guides/development-guide/hardhat)

## 📄 License

This project is licensed under the **BSD-3-Clause-Clear License**. See [LICENSE](LICENSE).

## 🆘 Support

* GitHub Issues: [Report bugs or request features](https://github.com/zama-ai/fhevm/issues)
* Documentation: [FHEVM Docs](https://docs.zama.ai)
* Community: [Zama Discord](https://discord.gg/zama)
