# Hey, I'm Vlad Episk 👋

Senior Solidity Engineer with 5+ years crafting secure Ethereum/DeFi contracts. TypeScript pro for bulletproof dApps. Based in PST—hunting remote web3 gigs!

## Skills
- ![Solidity](https://img.shields.io/badge/Solidity-5%2B%20Years-purple)
- ![TypeScript](https://img.shields.io/badge/TypeScript-Expert-yellow)
- ![Ethereum](https://img.shields.io/badge/Ethereum-DeFi%20Specialist-green)
- Python 3.11 for automation scripts.

## Key Projects
- **X**: My latest Solidity playground—check the code!
- **Decentralized Exchange (DEX) with Staking**: 

# Decentralized Exchange (DEX) with Staking

This repository showcases a production-grade Decentralized Exchange (DEX) with an Automated Market Maker (AMM) mechanism and staking for liquidity providers. As a Senior Solidity Developer with 5+ years of experience, this project demonstrates expertise in secure, gas-optimized smart contracts, including ERC-20 standards, liquidity pools, constant-product AMM (x * y = k, where k is the invariant ensuring price stability through reserve balances), multi-hop swaps, and time-weighted reward staking. The code adheres to best practices like the Checks-Effects-Interactions (CEI) pattern (validate inputs first, update state second, interact externally last to prevent reentrancy attacks) and formal verification readiness.

[![CI](https://github.com/1337niy/DEX/workflows/Hardhat%20CI/badge.svg)](https://github.com/1337niy/DEX/actions)

## Project Overview

This DEX enables token creation, pair factories, liquidity provision/removal with LP tokens, token swaps with slippage controls, and staking of LP tokens for rewards. It's fully functional out-of-the-box, deployable to any EVM-compatible chain, and optimized for low gas costs (e.g., using immutable variables and native overflow checks in Solidity 0.8.30).

### Key Features

- **ERC-20 Tokens**: Custom tokens with mint/burn, role-based access, permits for gasless approvals, and pausability.
- **Factory & Pairs**: Dynamic pair creation with sorted tokens; AMM pools with invariant checks and 0.3% swap fees (deducted from input, added to reserves for LP incentives).
- **Router**: User-friendly for adding/removing liquidity, exact-input/output swaps, multi-hop paths, and deadline enforcement.
- **Staking**: Yield farming with accumulator pattern (cumulative rewards per staked unit for O(1) efficiency, avoiding loops), APY calculations, and emergency functions.
- **Security**: ReentrancyGuard, Pausable, flash loan resistance (post-swap invariant checks), and role separation (e.g., MINTER_ROLE).
- **Testing**: 100% coverage with Hardhat/Chai, including edge cases like zero liquidity and reentrancy simulations.

### Smart Contracts

1. **Token.sol**: Extensible ERC-20 with permits and roles.
2. **Factory.sol**: Pair factory with event indexing and feeTo control.
3. **Pair.sol**: Core AMM with optimized math (Babylonian sqrt for roots) and fee-on-transfer support.
4. **Router.sol**: Routing for swaps and liquidity with multi-path efficiency.
5. **Staking.sol**: Proportional rewards with time multipliers and pause/emergency withdraw.

## Prerequisites

- Node.js v22+: Install from nodejs.org (Windows 11 compatible).
- Hardhat ^2.22.10: Global install with `npm i -g hardhat`.
- MetaMask: For testnet interactions.
- Ethereum Testnet: Sepolia recommended; use Alchemy for RPC (free key at alchemy.com).
- Windows 11 Notes: Use VS Code terminal; no issues with TS/Python 3.11 env for scripts.

## Installation

1. Clone the repo: `git clone https://github.com/1337niy/DEX.git` then `cd DEX`.
2. Install dependencies: `npm install`.
3. Initialize Hardhat (if not done): `npx hardhat init` (select TypeScript).
4. Configure .env`: Add PRIVATE_KEY, ALCHEMY_API_KEY, ETHERSCAN_API_KEY (never commit!).
5. Update hardhat.config.ts if needed: Solidity 0.8.30 with optimizer enabled.

## Testing

Run full suite: `npm run test` (or `npx hardhat test`).

- Covers deployment, liquidity ops, swaps, staking accrual, and security simulations.
- CI/CD: Automated on every push via GitHub Actions (see badge above).

## Deployment

1. Compile: `npx hardhat compile`.
2. Deploy: `npm run deploy` (updates scripts/deploy.ts to handle all contracts sequentially on Sepolia).
3. Verify: `npm run verify` for Etherscan (public code transparency).

## Usage

1. **Add Liquidity**: Approve router, call `addLiquidity` with tokens/amounts/min/deadline.
2. **Swap Tokens**: Approve input, call `swapExactTokensForTokens` with amountIn/minOut/path/deadline.
3. **Stake LP**: Approve staking, call `stake(amount)`.
4. **Claim Rewards**: Call `claimReward()`; withdraw with `withdraw(amount)`.

Interact via ethers.js (TS compatible) or Remix.

## Security Considerations

- **Audits**: Code audit-ready with OZ libraries; CEI pattern, no external calls in critical paths.
- **Risks Mitigated**: Reentrancy (guards), overflow (native checks), flash loans (invariant validation), MEV (deadlines).
- **Best Practices**: Immutable state, events for off-chain monitoring, role-based access.

## Contract Interaction Diagram

![Diagram](https://github.com/user-attachments/assets/e3e6a508-35b7-4e16-acfc-ef7dd139fc77)

- Token → Base assets.
- Factory → Creates pairs.
- Pair → AMM logic.
- Router → User gateway.
- Staking → Rewards engine.

## Potential Improvements

- Integrate React frontend with ethers.js (TS).
- Add 0.3% fees customization.
- Support ERC-721 for NFT staking.
- Formal verification with Certora.

## License

MIT License.

Contribute or connect—let's build DeFi innovations!

## About Me
Seasoned Solidity dev with 5+ yrs shipping audited DeFi protocols that handle $100M+ TVL—cut gas by 50% in prod swaps, thwarted exploits via CEI mastery. Bring battle-tested Ethereum smarts to your crypto crew: optimize, secure, and scale your dApp game. Remote-ready—let's crush web3!

Connect: [LinkedIn](your-link) | [Twitter](your-link)
