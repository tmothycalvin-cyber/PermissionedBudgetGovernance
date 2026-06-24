# SmartBudgeting-Blockchain

> **"Governing Public Budgets Across Sectors with Permissioned Blockchain:
> A Multi-Sector Information Systems Framework for
> Stakeholder-Differentiated Accountability"**

*Nimbo, T.C., Alamsyah, A., & Irawan, H.*
*Telkom University, Bandung, Indonesia*

---

## 📂 Repository Structure

```
SmartBudgeting-Blockchain/
│
├── contracts/
│   └── SmartBudgeting.sol        ← Solidity smart contract deployed on Sepolia testnet
│
├── simulation/
│   ├── simulate.js               ← 600-cycle automated simulation (Node.js + Ethers.js v6)
│   ├── adversarial_test.js       ← RBAC isolation and AND-join adversarial tests
│   ├── package.json              ← Node.js dependencies
│   └── .env.example              ← Environment variable template
│
├── verification/
│   └── etherscan_links.md        ← On-chain verification references (Sepolia Etherscan)
│
├── results.csv                   ← Full simulation results (600 cycles, 2,400 transactions)
├── LICENSE                       ← MIT License
└── README.md
```

---

## 📘 Project Overview

This repository contains the implementation artifact for a Design Science
Research (DSR) study constructing a permissioned blockchain IS artifact
for multi-sector public financial governance across six public service sectors.

The artifact jointly satisfies three IS design requirements derived from
Agency Theory and Sociotechnical Systems Theory (STS):

- **Requirement 1 (Agency Theory):** Accountability enforcement must be algorithmic and tamper-resistant, operating independently of any individual actor integrity.
- **Requirement 2 (STS — Technical):** The system must maintain a deterministic, immutable record of every fund movement across all lifecycle states.
- **Requirement 3 (STS — Social):** Role-differentiated access and authority boundaries must be encoded directly within the technical subsystem.

Three IS design contributions are demonstrated:

1. A unified multi-sector ledger with Role-Based Access Control (RBAC) and departmentID isolation across six sectors: Defense (DEF), Education (EDU), Public Health (HLT), ICT and Digital Government (ICT), Infrastructure and Transport (INF), and Social Assistance (SOC).
2. A lifecycle-aware smart contract encoding budget phase transitions (PENDING → VALIDATED → REALIZED) as tamper-resistant technical properties.
3. A stakeholder-differentiated Public Observer Node delivering citizen-facing transparency through selective disclosure.

---

## 🔗 Smart Contract

| Item              | Detail                                                                                               |
|-------------------|------------------------------------------------------------------------------------------------------|
| Contract Address  | `0x6034F9Cc959ea5F49Be2ac133382AFE6Ef5d6AB0`                                                         |
| Network           | Sepolia Testnet (Chain ID: 11155111)                                                                 |
| Compiler          | Solidity ^0.8.20                                                                                     |
| Framework         | Ethers.js v6                                                                                         |
| Etherscan         | [View on Etherscan](https://sepolia.etherscan.io/address/0x6034F9Cc959ea5F49Be2ac133382AFE6Ef5d6AB0) |

> **Note:** This repository contains the implementation version of the smart contract used for simulation and evaluation. The deployed contract is a lean execution version consistent with the artifact evaluated in the paper. The full theoretical specification is presented in Algorithm 1, 2, and 3 of the manuscript.

---

## 📁 Simulation Results

### Overview

| Parameter                     | Value                                      |
|-------------------------------|--------------------------------------------|
| Total simulation cycles       | 600 (100 per sector × 6 sectors)           |
| Total on-chain transactions   | 2,400                                      |
| Completed cycles              | 597                                        |
| Failed cycles                 | 3 (network interruptions, not contract faults) |
| Cycle completion rate         | 99.5%                                      |
| RBAC isolation violations     | 0                                          |
| Cross-sector access violations| 0                                          |

### Gas Consumption (N = 597 cycles)

| Function                    | Mean Gas  | SD   | CV (%)  |
|-----------------------------|-----------|------|---------|
| `submitBudgetAnchor()`      | 122,518   | 4.83 | 0.004   |
| `validateBudgetAnchor()`    | 34,842    | 3.82 | 0.011   |
| `recordBudgetRealization()` | 171,133   | 5.93 | 0.003   |

### Average Response Time per Lifecycle Stage (seconds)

| Stage          | Average (s) |
|----------------|-------------|
| Submission     | 14.13       |
| BAV Validation | 13.94       |
| ICV Validation | 13.72       |
| Realization    | 13.41       |

Full results available in `results.csv`.

---

## ⚙️ How to Run

```bash
# Clone the repository
git clone https://github.com/tmothycalvin-cyber/SmartBudgeting-Blockchain.git
cd SmartBudgeting-Blockchain/simulation

# Install dependencies
npm install

# Configure environment
cp .env.example .env
# Edit .env with your RPC_URL, PRIVATE_KEY, PRIVATE_KEY_BAV, and CONTRACT_ADDRESS

# Run 600-cycle simulation
node simulate.js

# Run adversarial tests (RBAC isolation + AND-join verification)
node adversarial_test.js
```

---

## ✅ On-Chain Verification

All 2,400 on-chain transactions generated during the simulation are
independently and publicly verifiable via Sepolia Etherscan at the
contract address above without administrative mediation.

See `verification/etherscan_links.md` for the end-to-end proof of concept
transaction reference and deployment details.

---

## 👥 Authors

| Role | Contributor |
|------|-------------|
| Conceptualization, Methodology, Software, Formal Analysis, Investigation, Writing (original draft), Visualization | T.C. Nimbo |
| Writing (review and editing), Supervision, Validation | A. Alamsyah |
| Writing (review and editing), Supervision | H. Irawan |

*Smart Computing, Blockchain and Data Science Laboratory (LAB SCBD),
School of Computing, Telkom University, Bandung, Indonesia*

---

## ⚖️ License

MIT License. See `LICENSE` for details.

---

## 📬 Contact

For questions about the code or simulation data, please open a
[GitHub issue](https://github.com/tmothycalvin-cyber/SmartBudgeting-Blockchain/issues)
or contact the corresponding author indicated in the manuscript.

---

## 🙏 Acknowledgements

This research was conducted as part of the research program of the Smart
Computing, Blockchain and Data Science Laboratory Telkom University, Bandung, Indonesia. No external funding was received.
