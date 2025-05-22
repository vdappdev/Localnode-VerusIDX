# VerusIDX Marketplace Tauri App

## 🚀 Introduction

VerusIDX is a cross-platform desktop application built with Tauri, Svelte, and TypeScript. It allows users to interact with the Verus marketplace, connecting to local Verus nodes for both testnet and mainnet (& any pbaas chains on mainnet).

## 🛠 Prerequisites

- Node.js (v14.0.0 or later)
- npm (v6.0.0 or later)
- Rust (latest stable version)
- Git

## 🔧 Setup

1. Clone the repository: 

git clone https://github.com/yourusername/verusidx-marketplace.git cd verusidx-marketplace





2. Install dependencies:

npm install





3. Create a `.env` file in the root directory and add the following:

VITE_VERUS_RPC_USER=your_rpc_username VITE_VERUS_RPC_PASSWORD=your_rpc_password VITE_VERUS_RPC_HOST=127.0.0.1 VITE_VERUS_RPC_PORT_MAINNET=27486 VITE_VERUS_RPC_PORT_TESTNET=18843





Adjust the values according to your Verus node configuration.

- For testnet: Use port 18843
- For mainnet: Use port 27486

In your application code, you can access these environment variables like this:

```typescript
const network = import.meta.env.VITE_VERUS_NETWORK || 'testnet';
const rpcPort = network === 'mainnet' 
  ? import.meta.env.VITE_VERUS_RPC_PORT_MAINNET 
  : import.meta.env.VITE_VERUS_RPC_PORT_TESTNET;
const rpcHost = import.meta.env.VITE_VERUS_RPC_HOST || '127.0.0.1';

// Use rpcHost and rpcPort in your Verus RPC configuration
🏗 Project Structure



verusidx-marketplace/
├── src/
│   ├── lib/
│   │   ├── components/
│   │   ├── stores/
│   │   └── utils/
│   ├── routes/
│   ├── App.svelte
│   └── main.ts
├── src-tauri/
│   ├── src/
│   │   └── main.rs
│   └── tauri.conf.json
├── public/
│   └── index.html
├── package.json
├── svelte.config.js
├── vite.config.js
└── README.md
🚀 Running the App
For development:




npm run tauri dev
To build the app:




npm run tauri build
🧪 Testing
Run tests with:




npm test
📚 Available Scripts
npm run dev: Starts the app in development mode
npm run build: Builds the app for production
npm run preview: Locally preview production build
npm run check: Run svelte-check
npm run test: Runs the test suite
npm run tauri: Runs Tauri CLI commands
🔐 Security Considerations
Always use secure RPC credentials and never hardcode them
Implement proper input validation for all user inputs
Use Tauri's security features like CSP and allowlist
Regularly update Tauri and other dependencies
🤝 Contributing
Please read CONTRIBUTING.md for details on our code of conduct and the process for submitting pull requests.

📄 License
This project is licensed under the MIT License - see the LICENSE.md file for details.

🙏 Acknowledgments
Verus community and developers
Tauri team
Svelte team
📞 Support
For support, please open an issue in the GitHub repository or contact ejuliano on Verus Discord.