# 🪄 Obscuro

> **Obscuro hides what must remain unseen.**

## 📖 Overview

Payroll is one of the most sensitive parts of business operations. Today’s systems (ADP, Gusto, Deel, etc.) handle
compliance and execution, but they require **full trust** in a central provider who sees every salary, schedule, and
adjustment.

With **Obscuro**, payroll shifts to a **neutral, verifiable blockchain layer** powered by FHE:

- Salaries and schedules are **encrypted**, visible only to employer and employee.
- The blockchain can still **enforce pay dates and rules** (e.g., _“pay $5,000 on the 30th of each month”_) **without
  ever learning the salary**.
- Payments are made in ERC-20 stablecoins (e.g., USDC, DAI), ensuring fast and global payouts.
- Employees receive **verifiable on-chain receipts**, while sensitive terms remain private.

This delivers payroll that is **confidential, trust-minimized, and borderless**.

## ⚖️ Why It Matters

| Feature                  | Web2 Payroll (e.g., ADP, Deel)          | Obscuro — Confidential Payroll                           |
| ------------------------ | --------------------------------------- | -------------------------------------------------------- |
| **Salary Privacy**       | Provider sees all salaries              | Salaries stored encrypted; only employer & employee know |
| **Trust Model**          | Centralized provider manages everything | Trustless: blockchain enforces rules on ciphertext       |
| **Audit Trail**          | Logs kept in provider’s DB              | Immutable, on-chain events (no sensitive info)           |
| **Cross-Border Pay**     | Complex bank integrations               | Instant ERC-20 stablecoin transfers                      |
| **Employee Proof**       | Payslip issued by provider              | On-chain verifiable receipt + optional decrypted payslip |
| **Selective Disclosure** | All-or-nothing reporting                | Reveal only what’s required (e.g., totals, not salaries) |

## 🔑 Key Features

- **Confidential Payroll Agreements** Encrypted salaries, schedules, and payout rules — visible only to employer and
  employee.

- **Automated Stablecoin Escrow** Employer funds escrow in ERC-20. Blockchain releases tranches on due dates, enforced
  privately by FHE.

- **Verifiable Receipts** Employees get immutable proofs of payment, useful for freelancers, DAOs, or compliance audits.

- **Selective Reveal** For disputes or regulators, decrypt only specific fields (e.g., “employee was paid $X in June”)
  without exposing everything.

## 🎯 MVP Scope

- **Smart Contracts**
  - **PayrollAgreementRegistry**: manages agreements, stores encrypted salaries/schedules.
  - **PayrollEscrowERC20**: holds ERC-20 funds, executes salary payouts on schedule.

- **Core Functions**
  - Create payroll agreement (HR).
  - Invite employee (wallet address).
  - Fund payroll vault with stablecoins.
  - Automated payout release (monthly/biweekly).
  - On-chain receipt + encrypted payslip export.

- **Frontend**
  - **HR Dashboard**: configure payroll, fund escrow, monitor payouts.
  - **Employee Portal**: decrypt payslip locally, view payment history, export receipts.

- **Backend**
  - Event indexer for payroll history.
  - API for HR and employees (no plaintext salary exposure).

## 🌍 Use Cases

- **Startups / SMEs** → Confidential payroll without relying on external providers.
- **DAOs / Web3 Orgs** → Pay contributors in stablecoins, keep salaries private.
- **Freelancers & Contractors** → Receive provable, borderless payments.
- **Enterprises** → Cross-border payroll compliance with privacy-first guarantees.

## 🛤 Roadmap

- [ ] MVP with ERC-20 escrow + confidential agreements.
- [ ] Batch payroll (one tx, multiple employees).
- [ ] Selective disclosure proofs for regulators/auditors.
- [ ] Fiat off-ramp integration (convert USDC → bank transfer).
- [ ] Enterprise connectors (Workday, QuickBooks, etc.).

## 📚 Tech Stack

- **Blockchain**: FHE-enabled EVM chain
- **Smart Contracts**: Solidity (PayrollAgreementRegistry, PayrollEscrowERC20)
- **Frontend**: React/Next.js (HR dashboard, employee portal)
- **Backend**: NestJS/FastAPI for orchestration & indexing
- **Storage**: Encrypted blobs in IPFS/S3 for payslip metadata

✨ With **Obscuro**, salaries stay hidden, payments stay on time, and trust shifts from providers to code.

## 🧪 Development Template

This repo is based on the **FHEVM Hardhat template** from Zama, supporting Solidity contracts with FHE primitives.

- [Quick Start Guide](https://docs.zama.ai/protocol/solidity-guides/getting-started/quick-start-tutorial)
- [FHEVM Documentation](https://docs.zama.ai/fhevm)

## ⚡ Quick Start

### Prerequisites

- Node.js ≥ 20
- npm / yarn / pnpm

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

- [FHEVM Docs](https://docs.zama.ai/fhevm)
- [Setup Guide](https://docs.zama.ai/protocol/solidity-guides/getting-started/setup)
- [Testing Guide](https://docs.zama.ai/protocol/solidity-guides/development-guide/hardhat/write_test)
- [FHEVM Hardhat Plugin](https://docs.zama.ai/protocol/solidity-guides/development-guide/hardhat)

## 📄 License

This project is licensed under the **BSD-3-Clause-Clear License**. See [LICENSE](LICENSE).

## 🆘 Support

- GitHub Issues: [Report bugs or request features](https://github.com/zama-ai/fhevm/issues)
- Documentation: [FHEVM Docs](https://docs.zama.ai)
- Community: [Zama Discord](https://discord.gg/zama)
