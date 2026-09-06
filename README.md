# Hack for Business

![Node.js](https://img.shields.io/badge/Node.js-Express-339933?logo=nodedotjs&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248?logo=mongodb&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-14-000000?logo=nextdotjs&logoColor=white)
![Blockchain](https://img.shields.io/badge/Blockchain-custom-8A2BE2)

A hackathon team project ("Spartans") building a blockchain-backed local business platform — individuals and businesses each get a wallet, transact peer-to-peer or with businesses, and businesses can issue/redeem loyalty credits, all recorded on a custom-built blockchain.

This is a team effort — see the `karma`, `piyush`, and `rohan` branches on this repo for individual contributors' work in progress.

## Repo layout note

This repository was committed as-is during/after the hackathon and still contains scratch files from the event (loose notes, an accidentally-committed `Downloads/` folder, etc.) at the root. **`Downloads/final/` is the most complete, working version of the project** and is what this README describes. Everything else at the root is left untouched.

## What it does

- **Auth** — separate registration/login for individual users and businesses (JWT + bcrypt), role-based route protection.
- **Wallets** — each user/business gets a wallet with a generated address and private key; balance tracking, peer-to-peer transfers, starting balance on creation.
- **Custom blockchain** — a from-scratch blockchain (`blockchain/`: block, chain, miner, wallet, transaction) that mines and persists transactions to MongoDB, with chain validation and stats endpoints.
- **Transactions** — create, list, and verify transactions between wallets, with QR code generation for payments (`utils/qrCode.js`, QR scan/generate components in the frontend).
- **Business features** — business registration/profile, product listings (with geo "nearby products" lookup), and a credit/loyalty system (purchase, spend, and track credits with bronze/silver/gold/platinum membership tiers).
- **Frontend** — a Next.js 14 + TypeScript app (`front/`) with shadcn/ui components: dashboard, explore/discovery page, QR payment flow, wallet manager, auth forms, and transaction history.

## Tech stack

- **Backend**: Node.js, Express, MongoDB + Mongoose, JWT, bcryptjs, custom blockchain implementation
- **Frontend**: Next.js 14, TypeScript, Tailwind CSS, shadcn/ui (Radix primitives), Axios

## Setup

Backend (`Downloads/final/`):

```bash
cd Downloads/final
npm install
# create a .env with MONGO_URI, JWT_SECRET, PORT
npm run dev
```

Frontend (`Downloads/final/front/`):

```bash
cd Downloads/final/front
npm install
npm run dev
```

The backend listens on the port set by `PORT` (defaults to 5000 in `server.js`); the frontend is a standard Next.js dev server.
