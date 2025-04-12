# Bitz Node Miner Run Full Guide (PC and VPS and Mac)

### Offical Docs Guide - still searching..................

----

## 🧰 Prerequisites
### Before getting started, make sure you have the following:
	
 * A Backpack wallet (or another Eclipse-compatible wallet) [Download](https://chromewebstore.google.com/detail/backpack/aflkmfhebedbjioipglgcbcmnbpgliof)
 * 0.005+ ETH on the Eclipse network
---

1️⃣ Dependencies for WINDOWS & LINUX & VPS & Mac

For WSL or VPS
```
sudo apt update && sudo apt upgrade -y
sudo apt install curl nano build-essential -y
```
For Mac
```
brew install git curl wget nano tmux htop jq make gcc autoconf automake pkg-config openssl leveldb lz4 coreutils
```

2️⃣ Install Rust & Node Js & Yarn

For WSL or VPS
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
rustc --version
```
- Just Press Enter to Proceed it
```
sudo apt-get update && curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash - && sudo apt-get install -y nodejs && node -v && npm -v && sudo npm install -g yarn && yarn -v
```

For Mac
```
brew install curl node yarn rust
```

3️⃣ Install Solana CLI

For WSL or VPS
```
curl --proto '=https' --tlsv1.2 -sSfL https://solana-install.solana.workers.dev | bash
```
```
source $HOME/.bashrc
```
```
solana --version
```
If you get Solana: command not found RUN
```
echo 'export PATH="/root/.local/share/solana/install/active_release/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

For Mac
```
sh -c "$(curl -sSfL https://solana-install.solana.workers.dev)"
```
```
source $HOME/.bash_profile
solana --version
```

For VPS Only
- If using VPS, and Solana not found, REBOOT it
```
reboot
```

4️⃣ Configue RPC for Eclipse
```
solana config set --url https://mainnetbeta-rpc.eclipse.xyz/
```

5️⃣ Wallet Setup (Solana Keypair)
```
solana-keygen new
```
Press ENTER and save the passphrase

6️⃣ Exporting Private Key from ID.json
```
cat ~/.config/solana/id.json
```
* Copy the output (a list of numbers) and import it into Backpack Wallet under “Private Key”.
* Fund the wallet with 0.005+ ETH on Eclipse to activate mining.



7️⃣ Install Bitz CLI
```
cargo install bitz
```

For VPS Only
```
apt install screen -y
```
```
screen -S bitz
```

8️⃣ 🅰️ Start Miner
```
bitz collect
```

OR

8️⃣ 🅱️ Start Miner (using multiple core) 
```
bitz collect --cores 4
```

For VPS Only
- PRESS CTRL+A+D (to run ur miner continuously)
- To check ur Node Again
```
screen -r bitz
```

### Claim Mined tokens 
```
bitz claim
```

### Check Wallet status 
```
bitz account
```


## 🔶For Next Day Run This Command (Windows or Mac)

#1 Open WSL or HomeBrew and Put this Command 
```
bitz collect
```

## Delete Node File
```
rm -rf ~/.config/solana
```
