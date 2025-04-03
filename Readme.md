## 🧠 **Full-Stack Blockchain Developer Interview Task**
**Reference: [superlend.xyz](https://superlend.xyz)**  
Create a simplified version inspired by **SuperLend** — enabling users to swap tokens and lend in **one smooth transaction**, across multiple chains.


### 📌 **Background**

SuperLend and similar platforms offer advanced DeFi flows where users can perform **complex financial actions (like swap + lend)** in a **single transaction**. The aim is to make DeFi more **gas-efficient, user-friendly, and seamless**.

In this challenge, you're asked to **replicate a simplified version** of SuperLend:

- Users connect their wallet on **any of 3 chains**
- They choose a token to **swap**
- The swapped token is **automatically deposited** into **Aave Lending Pools**
- All in a **single transaction**
- With a **clean, modern UI/UX** inspired by SuperLend

This tests your ability to **build full-stack dApps**, understand **DeFi protocols**, and deliver **real user value**.

---

## 🎯 **Core Objectives**

You are expected to:

1. Build a **responsive frontend UI** that allows users to connect their wallet across **Ethereum, Polygon, and Arbitrum**
2. Implement a **smart contract** that performs:
   - ERC20 **token swap**
   - Followed by **lending the swapped token on Aave v3**
   - All in **a single transaction**
3. Integrate your UI with the smart contract
4. Ensure your app is clean, easy to use, and works on testnets

---

## 🔗 PART 1: Multi-Chain Wallet UI

### ✅ Functional Requirements:
- Connect wallet using **Web3Modal, RainbowKit, or similar**
- Detect and display:
  - Chain name
  - Wallet address
  - Native token balance (e.g., ETH/MATIC/ARB)
  - Selectable chain switcher
- Show token balances:
  - USDC
  - DAI
- Highlight active chain
- Disable functions if wrong network is selected

### 💡 UX Inspiration:
- Single-screen experience
- Clear action flows: Connect → Select Token → Swap + Lend
- Smooth animations, status updates like on **SuperLend**
- Mobile responsive layout

---

## ⚒️ PART 2: Smart Contract – Swap + Lend (One Transaction)

### 🛠 Contract Responsibilities:
Write a Solidity contract that:
1. Accepts tokens (e.g., USDC) from the user
2. Swaps them into DAI using a DEX (Uniswap V3 or 1inch router)
3. Supplies the DAI to Aave’s Lending Pool
4. Wraps all of this in **one atomic transaction**

### 🔐 Security & Features:
- Use `SafeERC20` (OpenZeppelin)
- Validate slippage using `minOut` parameter
- Use Aave’s v3 interface for `supply()`
- Use reentrancy guards

### 🔧 Function Signature Example:
```solidity
function swapAndLend(
  address inputToken,
  address outputToken,
  uint256 amountIn,
  uint256 minAmountOut
) external;
```

### ✅ Bonus Features:
- Support **EIP-2612 permit()** approvals (gasless approval)
- Return `aToken` amount received
- Emit custom event `SwapAndLent(address user, uint256 amountIn, uint256 aTokenReceived)`

---

## 🖥️ PART 3: Frontend Integration

### ✅ UI Actions:
1. Show token selector (USDC → DAI)
2. Enter amount to swap/lend
3. On submission:
   - Approve token (if needed)
   - Call your contract’s `swapAndLend()` function
4. Display:
   - Transaction hash and status
   - Link to block explorer
   - Amount lent successfully

### 📦 Frontend Stack Suggestions:
- `Next.js + React`
- `ethers.js` or `viem`
- `wagmi` for hooks (connect, writeContract)
- `TailwindCSS` or `shadcn/ui` for design system

### 🌟 Optional Enhancements:
- Pull live prices from **Chainlink**
- Calculate estimated APY from Aave
- Add tx loading spinners and confetti on success 🎉

---

## 📦 DELIVERABLES

### You should submit:
- A GitHub repo with:
  - `/frontend` folder for the UI
  - `/contracts` folder with Solidity code
- A `README.md` file that includes:
  - Setup instructions
  - Smart contract addresses (deployed on testnets)
  - Screenshots or demo link (if possible)
  - A short explanation of your architecture decisions

---

## 🧪 Evaluation Rubric

| Area                          | Weight | Evaluation Criteria |
|-------------------------------|--------|----------------------|
| **Smart Contract Quality**    | 30%    | Safe, efficient, composable, and tested |
| **Frontend UI/UX**            | 25%    | Clean interface, similar feel to SuperLend |
| **Blockchain Integration**    | 20%    | Reliable wallet/chain handling, tx flow |
| **End-to-End Functionality**  | 15%    | Working Swap → Lend pipeline |
| **Code Quality & Structure**  | 10%    | Clean, documented, modular, scalable |
| **Bonus Points**              | +X%    | Gasless approval, analytics, APY UI, error handling |

---

## 🌐 Recommended Chains & Tools

- **Chains (testnets)**:
  - Sepolia (Ethereum)
  - Mumbai (Polygon)
  - Arbitrum Goerli (Arbitrum)

- **Infra**:
  - Alchemy / Infura RPCs
  - Uniswap V3 SDK or 1inch API
  - Aave V3 Lending Pool

- **Testing tools**:
  - Hardhat / Foundry for contracts
  - viem + wagmi for frontend

---

## ✅ Optional Enhancements (Bonus Points)
- Slippage tolerance UI slider
- Token list fetched from CoinGecko or 0x
- Transaction batching for better UX
- Multi-wallet support (e.g., MetaMask, Coinbase, WalletConnect)
- Track historical lending positions via The Graph

