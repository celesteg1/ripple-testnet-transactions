![Version](https://img.shields.io/github/v/release/celesteg1/ripple-testnet-transactions)
![License: MIT](https://img.shields.io/github/license/celesteg1/ripple-testnet-transactions)
![Last Commit](https://img.shields.io/github/last-commit/celesteg1/ripple-testnet-transactions)

# Ripple (XRP) Testnet App

A simple demo app built with Vue.js (Vue 3) to interact with the Ripple Testnet. This app currently allows users to check the balance of a given XRP Testnet wallet address.

## ✅ Current Features

- View the XRP balance of a wallet on the Ripple Testnet
- Auto-load wallet address from environment variable (`.env`)
- Toggle visibility of wallet address input (mask/unmask)
- Basic error handling for failed requests

## 🧪 Getting Started

### 1. Clone the repository:

```bash
git clone https://github.com/celesteg1/ripple-testnet-app.git
cd ripple-testnet-app
```

### 2. Install dependencies:

```bash
npm install
```

### 3. Set your environment variables

- Rename .env.example to .env
- Open the .env and add your testnet wallet address 

```.env
VITE_XRP_TESTNET_WALLET_ADDRESS=your_testnet_wallet_address
```

- Save the file

### 4. Run the app:

```bash
npm run dev
```

### 5. Open your browser and navigate to http://localhost:5173 (or the port shown in your terminal).

```example
  VITE v6.3.4  ready in 702 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h + enter to show help
```

## Get your own XRP testnet wallet address

1. Navigate to: [https://xrpl.org/resources/dev-tools/xrp-faucets](https://xrpl.org/resources/dev-tools/xrp-faucets)
2. Under `Choose Network`, select: `Testnet: Mainnet-like network for testing applications.`
3. Click the `Generate Testnet Credentials` button
4. The wallet address is the one starting with an `r` e.g., `rabCd1e23fGHiJKlMnOPQrstuVWX45zAbc`

## 🤝 Contributing
If you'd like to contribute to this project:

- Fork the repository: This will create a copy of the project on your GitHub account, where you can make changes freely.
- Make your changes: Add new features, fix bugs, or improve documentation in your forked repository.
- Submit a pull request: Once you're happy with your changes, submit a pull request to propose merging your changes into the original repository. I’ll review and discuss your changes before deciding whether to merge them.
- Open an issue: If you encounter any bugs or have suggestions for improvements, feel free to open an issue in this repository. This helps track tasks or problems with the project.

## License
MIT License. See LICENSE for more details.
