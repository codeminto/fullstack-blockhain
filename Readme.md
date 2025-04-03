## 🧠 **Full-Stack Blockchain Developer Interview Task**
**Reference: [superlend.xyz](https://superlend.xyz)**  
Create a simplified version inspired by **SuperLend** — enabling users to swap tokens and lend in **one smooth transaction**, across multiple chains.

---

### 🎯 **Objective**
Build a full-stack decentralized app (frontend + smart contract) that allows users to:
- Connect wallets across **3 EVM blockchains**
- **Swap a token** (e.g., USDC → DAI)
- **Lend the swapped token** on **Aave v3**
- All in a **single transaction**
- Delivered with a **clean, modern UI** inspired by [superlend.xyz](https://superlend.xyz)

---

## 🔗 PART 1: Multi-Blockchain Wallet UI

### ✅ Requirements
- Connect wallet on the following chains:
  - Ethereum (e.g., Sepolia)
  - Polygon (e.g., Mumbai)
  - Arbitrum (e.g., Arbitrum Goerli)
- Display:
  - Connected wallet address
  - Current chain
  - Native token balance
  - Token balances (e.g., USDC, DAI)
- Allow:
  - Chain switching
  - Wallet disconnection

### 💻 Tech Suggestions
- `wagmi`, `viem`, `web3modal` or `RainbowKit`
- `Next.js + React`
- `TailwindCSS` or `shadcn/ui`

### 🌟 Bonus
- Chain selector with logos
- Responsive layout
- Live token price display

---

## ⚒️ PART 2: Smart Contract – Swap + Lend

### ✅ Objective:
Create a Solidity smart contract that:
1. Receives `inputToken` from the user (e.g., USDC)
2. Swaps it to another token (e.g., DAI) via a DEX (Uniswap/1inch)
3. Lends the output token on **Aave v3**
4. Executes everything in **a single transaction**

### 🛠️ Requirements
- Handle:
  - ERC20 approvals
  - Slippage protection
  - Token transfers
- Return or log success + token lending amount

### 🔐 Security
- Use `SafeERC20` from OpenZeppelin
- Prevent reentrancy
- Validate swap and lending success

### 🧪 Bonus
- Use `permit()` (EIP-2612) for gasless approval
- Emit custom events for frontend tracking
- Fallback handling if swap fails

---

## 🖥️ PART 3: Frontend Integration

### ✅ Flow
1. User connects wallet & selects network
2. Chooses:
   - Input token (e.g., USDC)
   - Output token (e.g., DAI)
   - Amount to lend
3. Approve + call smart contract with values
4. Show:
   - Progress (swap/lend in progress)
   - Success confirmation (e.g., “You lent 100 DAI on Aave 🎉”)
   - Tx link to block explorer

### 🔧 Integration
- `ethers.js` / `viem`
- Use `wagmi` hooks for contract calls
- Deploy smart contract to at least one testnet

---

## 🧪 Evaluation Rubric

| Area                          | Weight | Evaluation Criteria |
|-------------------------------|--------|----------------------|
| **Smart Contract Quality**    | 30%    | Secure, modular, gas-efficient |
| **Frontend Design (UI/UX)**   | 25%    | Clean design like superlend.xyz, responsive |
| **Blockchain Integration**    | 20%    | Wallet, chain handling, token info |
| **End-to-End Flow**           | 15%    | Swap + Lend in one tx, works fully |
| **Code Quality & Structure**  | 10%    | Organized, commented, easy to review |
| **Bonus Points**              | +X%    | `permit()`, aToken tracking, slippage UI, analytics |

---

## 📦 Deliverables

- GitHub repo with:
  - `/frontend` (UI + logic)
  - `/contracts` (Solidity code)
- Clear `README.md` with:
  - Setup instructions
  - Deployed contract addresses (testnets OK)
  - Screenshots or demo link (optional)
- Properly commented code

---

## ✅ Extra Tips

- Testnet suggestions: **Sepolia**, **Mumbai**, **Arbitrum Goerli**
- Aave v3 deployments are available on Polygon, Arbitrum, Optimism
- Use free RPCs (Alchemy, Infura, QuickNode, etc.)

