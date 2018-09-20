# VAPEX
Shell script to install a [VAPEX Masternode](https://www.vapecoinshop.com/) on a Linux server running Ubuntu 16.04.
***

## VPS installation
If you require a VPS check out [Vultr](https://www.vultr.com/?ref=7170618/) and start up a Linux Ubuntu 16.04 server
```
wget -N https://raw.githubusercontent.com/VapeCoinDev/VapeX-Masternode-Script/master/vapexmn_install.sh
bash vapexmn_install.sh
```
***

## Desktop wallet setup

After the Masternode is up and running, you need to configure the desktop wallet accordingly. Here are the steps:
1. Open the VAPEX Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **2500** VAPEX to **MN1**. You need to send all 2500 coins in one single transaction.
4. Wait for 15 confirmations.
5. Go to **Help -> "Debug Window - Console"**
6. Type the following command: **masternode outputs**
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
```
Alias Address Privkey TxHash TxIndex
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* TxIndex:  **Second value from Step 6**
9. Save and close the file.
10. Go to  **Tools -> "Open Wallet Configuration File"**
11. Insert the following into that file:
```
rpcuser=AnyUsername
rpcpassword=Any Password
txindex=1
listen=1
server=1
daemon=1
logtimestamps=1
maxconnections=256
masternode=1
masternodeprivkey=Masternode Private Key
masternodeaddr=VPS IP:8259
```
12. Save and close the file.
13. **Restart your wallet**
14. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
15. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
16. Select your MN and click **Start Alias** to start it.
17. Alternatively, open **Debug Console** and type:
```
startmasternode alias 0 MN1
```
18. Login to your VPS and check your masternode status by running the following command to confirm your MN is running:
```
vapex-cli masternode status
```

***

## Usage:
```
vapex-cli masternode status #To check your MN status
vapex-cli getinfo #To get general info such as VapeX version and current block numnber
vapex-cli mnsync status #To check if your MN is synced.
```
Also, if you want to check/start/stop **vapex**, run one of the following commands as **root**:

```
systemctl status vapex #To check if VapeX service is running
systemctl start vapex #To start VapeX service
systemctl stop vapex #To stop VapeX service
systemctl is-enabled vapex #To check if VapeX service is enabled on boot
```
***

## Donations	
Any donation is highly appreciated
```
**BTC**: 3Mi9fUVroHYSds6Dsu66eGtsP2EVba8Mm3
**ETH**: 0x94E27a1DF0fbc3E694c8B995EBF7F75277cAe7fd
```
