# ZKPay: Confidential Payroll & Splits Protocol

[![CI/CD Tests](https://github.com/efekrbas/zkpay-midnight/actions/workflows/test.yml/badge.svg)](https://github.com/efekrbas/zkpay-midnight/actions/workflows/test.yml)

ZKPay is a privacy-preserving dApp built on the **Midnight Network** using the Compact language. It enables organizations to manage payroll and allocate funds without exposing individual salaries or payee addresses to the public ledger.

## 🚀 Important Links

- **Live Demo**: https://zkpay-midnight.vercel.app/
- **Demo Video**: https://drive.google.com/file/d/1X7AJxKcSCwDkNOpzykNxdYLIWc8uCzoT/view?usp=drive_link
- **Product Proposal**: Confidential Payroll and Splits Protocol

---

## Deploy
<img width="878" height="871" alt="image" src="https://github.com/user-attachments/assets/dc99dc0d-fa0d-452c-b925-a4530378a1ff" />

## UI Screenshot
<img width="1449" height="840" alt="image" src="https://github.com/user-attachments/assets/bac6e4ba-3b07-4381-a74e-ffbd3b7f9880" />
<img width="1439" height="833" alt="image" src="https://github.com/user-attachments/assets/7eff5167-7e80-474a-b46d-a2787e96040e" />
<img width="283" height="623" alt="image" src="https://github.com/user-attachments/assets/a13a65d1-7c80-453f-95a2-444df257c8e1" />

## 🛡️ Privacy Model

ZKPay leverages Zero-Knowledge proofs to create a hybrid state (public ledger + private cell state) that perfectly balances transparency for the organization with strict privacy for the employees.

### What an observer CAN learn (Public State):
- **Total Pool Liquidity (`total_pool_value`)**: Observers can verifiably see the total amount of tokens allocated to the smart contract.
- **Transaction Validity**: Observers can see that a mathematical proof was submitted and validated, and that the total pool decreased by the claimed amount.

### What an observer CANNOT learn (Private Witness State):
- **Payee Identity**: The 32-byte address of the person claiming the funds remains completely hidden.
- **Allocated Salary**: Observers cannot see how much a specific individual was allocated.
- **Cryptographic Commitments**: The `ShieldedPayee` struct acts as a commitment. Hackers cannot brute-force or scrape the ledger to find out who is registered in the shielded set, as it requires the exact `Address`, `Amount`, and `Secret Key` (entropy) to generate a valid ZK circuit proof.

---

## 🧪 Testing & CI/CD

We have built a robust Mocha + Chai testing suite that leverages the `@midnight-ntwrk/compact-runtime` to simulate the ZK environment locally. The tests guarantee that:
1. The contract initializes properly.
2. Valid ZK claims correctly decrement the public pool.
3. Fraudulent claims (wrong secret keys or excessive amounts) fail silently without exposing data or altering the public state.

### Test Output Screenshot
*(Passing all hackathon criteria)*

![Test Output](images/test.png)

## 💻 Tech Stack
- **Smart Contracts**: Midnight Compact Language (v0.2.0)
- **Testing**: TypeScript, Mocha, Chai, ts-node
- **Frontend**: React, Vite, Tailwind CSS, GSAP (Glassmorphism UI)
- **CI/CD**: GitHub Actions

---
*Built with ❤️ for the Midnight Network Hackathon.*
