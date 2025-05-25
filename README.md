# Aztec Sequencer Guide 🔥
# 🖥️ Device/System Requirements
![1000531868](https://github.com/user-attachments/assets/2dfe6f9f-58fd-4790-8f10-7e6a80d584ce)
# Pre-Requirements 🛠
• Docker & Docker Compose

🔺(Let run your docker in background if u are using local Device)

• Aztec Tool

• Sepolia Rpc URL
# Install All Require Dependecies
```
sudo apt-get update && sudo apt-get upgrade -y
```
• Install Node.js
```
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo apt update && sudo apt install -y nodejs
```
• Other Packages
```
sudo apt install curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev screen ufw -y
```
# Install Docker & Docker Compose
```
sudo apt update && sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```
sudo apt update && sudo apt install -y docker-ce && sudo systemctl enable --now docker
```
```
sudo usermod -aG docker $USER && newgrp docker
```
```
sudo curl -L "https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | jq -r .tag_name)/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose
```
• Verify installation
```
docker --version && docker-compose --version
```
# Install the Aztec CLI 👇
```
bash -i <(curl -s https://install.aztec.network)
```
• Lets Config it to your corrent Shell/Path
```
echo 'export PATH="$HOME/.aztec/bin:$PATH"' >> ~/.bashrc
```
```
source ~/.bashrc
```
• Verify the Installation with- 👇
```
aztec -h
```
• Set the correct version for the testnet 👇
```
aztec-up alpha-testnet
```
# Load your wallet with Sepolia Faucet
https://www.alchemy.com/faucets/ethereum-sepolia
https://www.alchemy.com/faucets/ethereum-sepolia
# Allow Incoming connections on Ports
```
sudo ufw allow 22
sudo ufw allow ssh
sudo ufw enable
```
```
sudo ufw allow 40400
sudo ufw allow 8080
```
# Get Seapolia and Beacon API Key's Free of Cost 👇
Go to - https://tinyurl.com/y8v7tm2d

Manually Sign up with Email address- u will rcvd 100$ voucher- (Dont sign up with Google)

Select Ethereum Sepolia
![1000532064](https://github.com/user-attachments/assets/6e3fb6d1-252e-43ea-9685-08fe3a366902)


Scroll Down and Select the Growth Plan for which RPC u need, (Sepolia or Beacon)
![1000532067](https://github.com/user-attachments/assets/03554452-4b25-4541-8055-c5d3da8a4df0)

Click on Select Voucher

Select 50$ Voucher
![1000532069](https://github.com/user-attachments/assets/71d0d24e-b1e3-4358-a3bd-ae6288a6514c)


Now Click on Pay with Balance

Here we go... U got your API key for free!

U can see your Api key on API section!
![1000532071](https://github.com/user-attachments/assets/13fe46c3-0420-4c2d-8041-cd1348a1e2c1)
# More Other Sites!
https://drpc.org/dashboard

https://developer.metamask.io/key/active-endpoints

https://www.alchemy.com
# Paid RPC Purchase From Me
If not works from Free You can purchase it from me your own RPC just pay by 10$ Both RPC i will give you 
dm on Telegram @sandeepkum21 it will work 101% 
# Start Your Sequencer 🍥
```
screen -S aztec
```
👇 Execute below given command to Start Your node & Dont forget to make changes in it- 👇
```
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls Eth_Sepolia_RPC \
  --l1-consensus-host-urls Eth-beacon_sepolia_RPC \
  --sequencer.validatorPrivateKey 0xYourPrivateKey \
  --sequencer.coinbase YourAddress \
  --p2p.p2pIp Your_ip
```
Replace Eth_Sepolia_RPC with your actual one! -follow above steps

Replace Eth-beacon_sepolia_RPC with your actual one -follow above steps

Replace 0xYourPrivateKey with your actual EVM wallet pvt key 🔺 (dont forget to add 0x at starting)

Replace YourAddress with your actual evm wallet address

Replace Your_ip with your External IP ...

-U can get External IP by running curl ifconfig.me

It will take few times to download and Sync! 🥶
![1000532073](https://github.com/user-attachments/assets/6255303d-04c2-4526-b220-772e1680a4c1)
The Successfull Running Should Look like this 👇
![1000532075](https://github.com/user-attachments/assets/56b2c075-8ebf-4e68-9314-3a17b94520cf)
# Detached and Attached From the Screen
• For detached from screen session - ctrl , a + d
For Attach -
```
screen -r aztec
```
# Get Apprentice Role In dc- 😍
Note : open it new tab with Same IP
📋 Step 1: Get the latest proven block number
```
curl -s -X POST -H 'Content-Type: application/json' \
-d '{"jsonrpc":"2.0","method":"node_getL2Tips","params":[],"id":67}' \
http://localhost:8080 | jq -r ".result.proven.number"
```
• Save this block number for the next steps

•Example output: 1234

🔍 Step 2: Generate your sync proof
```
curl -s -X POST -H 'Content-Type: application/json' \
-d '{"jsonrpc":"2.0","method":"node_getArchiveSiblingPath","params":["BLOCK_NUMBER","BLOCK_NUMBER"],"id":67}' \
http://localhost:8080 | jq -r ".result"
```
Replace both BLOCK_NUMBER with your: (check step1)

This will output a long base64-encoded string - (Copy it completely)

✅ Step 3: Register with Discord

join dc- https://discord.gg/aztec

Go to #operators│start-here Channel

Type /operator start
![1000532080](https://github.com/user-attachments/assets/96fa57f9-6b04-43c6-a12a-383f4ac9f5c5)
Now it will promt u to enter address , block number , proof

Place your evm wallet address in address section

Place block-number From the Step-1

Place sync Proof from Step-2

Success message should look like this! & U will get the role!
![1000532082](https://github.com/user-attachments/assets/31471260-8387-4676-908e-80e28732f91d)
# Register as a Validator 🔗⛓️
Replace Eth_Sepolia_Rpc with your actual sepolia rpc url from Metamask developer.

Replace your-private-key with your evm wallet pvt key! Dont forget to add 0x at starting

Replace your-validator-address with your evm wallet address

Replace your-validator-address with your evm wallet address
```
aztec add-l1-validator \
  --l1-rpc-urls Eth_Sepolia_Rpc \
  --private-key your-private-key \
  --attester your-validator-address \
  --proposer-eoa your-validator-address \
  --staking-asset-handler 0xF739D03e98e23A7B65940848aBA8921fF3bAc4b2 \
  --l1-chain-id 11155111
```

# 👇🎈 Use this Template for saving data:
Aztec Sequencer Node 

• Ethereum sepolia rpc :

• Beacon_sepolia_RPC :

• PVT KEY :

• MM Public Address :

• IP ( cloud vps) :

• Block Number :

• Base64 encoded string :

👉 Join Twitter for more Updates: 
https://x.com/bdggts

If U have any issue then open a issue on this repo or Dm me on TG~ @sandeepkum21

Thank You Guys 🙌
