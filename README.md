Installation
Install the Aximeta SDK using npm or yarn to get started with real-time Solana data access.

npm install @aximeta/sdk
# or
yarn add @aximeta/sdk
Quick Start
Initialize the client and make your first API call to fetch wallet balances.

import { Aximeta } from '@aximeta/sdk';

const aximeta = new Aximeta({
  apiKey: process.env.AXIMETA_API_KEY
});

// Fetch wallet balance
const balance = await aximeta.wallet.getBalance('YOUR_WALLET_ADDRESS');
console.log(balance);


------------------------


API Reference
Wallet APIs
Access wallet balances, token holdings, NFTs, and transaction history.

// Get token balances
const tokens = await aximeta.wallet.getTokens(walletAddress);

// Get NFTs
const nfts = await aximeta.wallet.getNFTs(walletAddress);

// Get transaction history
const txs = await aximeta.wallet.getTransactions(walletAddress, {
  limit: 50,
  before: 'signature'
});
Market Data
Real-time market data including prices, depth, and trading activity.

// Get token price
const price = await aximeta.market.getPrice('SOL');

// Get order book depth
const depth = await aximeta.market.getDepth('SOL/USDC', {
  limit: 100
});

// Subscribe to price updates
aximeta.market.subscribe('SOL', (update) => {
  console.log('Price update:', update);
});
DeFi Protocols
Interact with DeFi protocols including lending, staking, and liquidity pools.

// Get staking positions
const stakes = await aximeta.defi.getStakes(walletAddress);

// Get LP positions
const lpPositions = await aximeta.defi.getLPPositions(walletAddress);

// Calculate APY
const apy = await aximeta.defi.calculateAPY('raydium', poolAddress);
