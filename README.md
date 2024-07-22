# Juneo Validator Node - Socotra Testnet 

 ![Screenshot 2024-07-22 110316](https://github.com/user-attachments/assets/25e02dca-6ce9-47a2-922f-076651e62c0d)

- You must need to buy a VPS for running Juneo Validator
- You can buy from : Contabo
- You should buy VPS which is fulfilling all these requirements : 
```bash
Operating System : Ubuntu 22.04
CPU: 4 core.
Memory: 8 GB.
Storage: SSD or NVMe with at least 160GB of space.
```

### Deployment - Read Carefully! 
#### Step 1:  Fill Out the Form
- You need to fill out the form provided by the project. Make sure to complete all required fields, including Website or Twitter Profile, Email, Telegram ID, Additional Inquiries, and select your role in the Testnet, which will be “Validator.” Ensure the email address you provide is one you frequently use.

Form link: https://juneo.com/forms

#### Step 2: Update & Upgrade
```bash
sudo apt update && sudo apt upgrade -y
```

#### Step 3: Install Allora ( This will take time )
```bash
sudo apt install curl git wget build-essential jq screen -y
```

#### Step 4: Clone the Juneo Binaries Repository
```bash
cd ~

git clone https://github.com/Juneo-io/juneogo-binaries
```

#### Step 5: Set File Permissions:
```bash
chmod +x ~/juneogo-binaries/juneogo
chmod +x ~/juneogo-binaries/plugins/jevm
chmod +x ~/juneogo-binaries/plugins/srEr2XGGtowDVNQ6YgXcdUb16FGknssLTGUFYg7iMqESJ4h8e
```
#### Step 6: Move the Files:
```bash
mv ~/juneogo-binaries/juneogo ~

mkdir -p ~/.juneogo/plugins

mv ~/juneogo-binaries/plugins/jevm ~/.juneogo/plugins
mv ~/juneogo-binaries/plugins/srEr2XGGtowDVNQ6YgXcdUb16FGknssLTGUFYg7iMqESJ4h8e ~/.juneogo/plugins
```
------------------------------------------------------------------------------

#### Step 7: Install Screen 
```bash
apt install screen
```

#### Step 8: Create Screen 
```bash
screen -S JUNEO
```

#### Step 9: Start the Juneo node:

```bash
cd ~ && ./juneogo --network-id="socotra"
```

- Once the node is running, you can view the log to ensure it is functioning correctly. To detach from the screen session without stopping the node, press `CTRL + A + D`

#### You may check if the node has boostrapped with the following call:
```bash
curl -X POST --data '{
    "jsonrpc":"2.0",
    "id"     :1,
    "method" :"info.isBootstrapped",
    "params": {
        "chain":"JUNE"
    }
}' -H 'content-type:application/json;' 127.0.0.1:9650/ext/info
```
-  Response | `TRUE` is fully Sync - `False` is still syncing. 
```bash
{
  "jsonrpc": "2.0",
  "result": {
    "isBootstrapped": true
  },
  "id": 1
}
```
- After the bootstrapping process has completed, you may proceed to the next step 10.

#### Step 10: Join as a Validator and Participate in the Rewards Program
With your node running, gather its information to sync with your wallet and start validating the network.

Open the Required Ports:
```bash
sudo ufw allow 9650
sudo ufw allow 9651
```

#### Retrieve Node Information: Run the following command to get your nodeID:
```bash
curl -X POST --data '{
    "jsonrpc":"2.0",
    "id"     :1,
    "method" :"info.getNodeID"
}' -H 'content-type:application/json' 127.0.0.1:9650/ext/info
```

- After running the command, make sure to save your NodeID, BLS Key (publicKey), and BLS Signature (proofOfPossession) for the next steps.

#### Step 7: Create a Wallet and Stake Your Node
Next, go to https://mcnwallet.io/ to create a wallet and securely store your private key.

- Join the Discord Channel at:https://discord.gg/juneosupernet
- Open a ticket in the Faucet channel at:https://discord.com/channels/1109824729453432953/1207338712388862013

In the ticket, send your email address (the one you used in the form), your wallet address, and NodeID.

####  Stake Your Node:

- In the mcnwallet.io, navigate to the Stake page and click on the Validate card.
- Enter your NodeID, BLS Key (publicKey), and BLS Signature (proofOfPossession).
- Set the staking amount to 1 JUNE and the validation period to 14 days
- Ensure all information is correctly entered to enable your node for validation.
- Then, Click “Validate” to add your node to the Validator set.

Note: In order to stake, you must have funds on *Platform-Chain*. Use the *Cross-Chain* page to transfer the desired amount from *JUNE-Chain* to *Platform-Chain*.

![image](https://github.com/user-attachments/assets/9912062f-6d12-493f-a2ff-839bc513578e)


### Check Node Status:
- After the transaction is complete, go to https://mcnscan.io/validator/validator-list.
- Enter your NodeID in the search bar to check the status of your node.


Congratulations! Your node should now be part of the validator set and actively participating in the network validation process.

Having problem with the setup? Join us on discord: at:https://discord.gg/QTAqpuRDhP





