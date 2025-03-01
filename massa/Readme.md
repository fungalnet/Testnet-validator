## 1.0 Official Massa Document
* [Website](https://massa.net/)
* [Github](https://github.com/massalabs/massa/)
* [Discord](https://discord.gg/massa/)
* [Testnet Explorer](https://massexplo.io/stakers)

##  Hardware requirements：
* CPU: Recommend for ubuntu 20.4 , core number 4 core and above.
* Memory: 8 GB RAM
* Disk: Recommend 200 GB Disk

## Upgrade MASSA 19.2 
https://github.com/fatalbar/Testnet-validator/tree/main/massa/upgrade

## Detail testnet Massa 19.x
* The scoring will start at cycle 158, on Monday, February 13 2023, 07:53 UTC
* The scoring will end at cycle 703, on Sunday, February 26 2023, 05:55 UTC

##  Installation massa 19.1 Automatic (Latest version) 02.02.2023
```bash
wget -O massa.sh https://raw.githubusercontent.com/fatalbar/Testnet-validator/main/massa/massa.sh && chmod +x massa.sh && ./massa.sh
```
* install screen and make your log active on Background, `CTRL+A+D` to close without terminating proses
```bash
install apt screen
screen -dmS massa bash -c 'sudo tail -f /root/massa/massa-node/logs.txt'
```
* To back your massa screen
```bash
screen -x massa
```
* Check Massa Log ,`CTRL+C` to close
```bash
sudo tail -f /root/massa/massa-node/logs.txt
```
* Add custom port setup the firewall on your computer to allow incoming TCP connections on ports 31244 and 31245
```bash
ufw allow 31244 && ufw allow 31245
ufw allow 22
sudo ufw allow 31244/tcp
sudo ufw allow 31245/tcp
sudo ufw enable
```
* Check your firewall status
```bash
sudo ufw status
```
## automatic open port 31244 and 31245
```bash
. <(wget -qO- https://raw.githubusercontent.com/SecorD0/utils/main/miscellaneous/ports_opening.sh) \31244 31245
```
* Open Massa Client (please change `<passsword>` with your Client Password already created
```bash
cd massa/massa-client
./massa-client -p <passsword>
```

* please backup your wallet.dat on dir `$HOME/massa/massa-client/`, dont worry if you cant restore your old wallet because Bot already save your progress 
![Screenshot_11](https://user-images.githubusercontent.com/81378817/178314356-aaf68fae-4b9c-4833-ba83-8e86d2ae127c.jpg)

* check your wallet Address from massa_client, copy your address then go to [Discord](https://discord.gg/massa/) to get faucet
```bash
Wallet_info
```
* automatic Buy Rolls (Make sure your wallet have enough Balance before doing this Task) to close screen `CTRL+A+D` (proses already on background)
```bash
cd $HOME
wget -O buyrolls.sh https://raw.githubusercontent.com/fatalbar/Testnet-validator/main/massa/buyrolls.sh && chmod +x buyrolls.sh && screen -xR -S buyrolls ./buyrolls.sh
```
* Register Your Node on Discord Bot , Go to this channel `Testnet-reward-Registration` and click on the uptick emoji, and the bot will send you a message. 

![Screenshot_8](https://user-images.githubusercontent.com/81378817/178301191-6f28dd97-f7d3-4dfb-8a15-d58945931f89.jpg)

* change `ADDRESS` and `DISCORD_ID` with your own ID (example `node_testnet_rewards_program_ownership_proof A1J9dqvxxxx 998476373xxxx` ) To find your Discord ID you can following this step
![Screenshot_9](https://user-images.githubusercontent.com/81378817/178303191-5074221e-7f90-4934-960a-48a0f1873e75.jpg)
* After you got your address and discord ID, you can Register testnet registration Reward
```bash
node_testnet_rewards_program_ownership_proof ADDRESS DISCORD_ID
```
* Copy the code given into the discord bot
![Screenshot_14](https://user-images.githubusercontent.com/81378817/178324521-fa173df7-20c3-4e3d-8ed5-0ee4270c75fa.jpg)
* You will see like this
 ![Screenshot_15](https://user-images.githubusercontent.com/81378817/178324934-9e357e00-2eb8-448b-a0da-20efa8a99745.jpg)

* Now you can paste your IP Address on massa bot on Discord
![Screenshot_13](https://user-images.githubusercontent.com/81378817/178324194-653171e9-3bb5-459a-b49a-c8682ea6d110.jpg)

* register Node staking (change `<your private keys>` with your private keys)
```bash
node_add_staking_secret_keys <your private keys>
```

Congratulations you have successfully registered your node. check your node on explorer https://test.massa.net/v1/#explorer or https://massa.net/testnet/#wallet

You can check your node status on [Telegram](https://t.me/massacheck_bot),add your address on Bot


## Additional Command
* Remove old wallet 
```bash
wallet_remove_addresses <your address>
```
* Restore Wallet from previous wallet if you already have, change `your_key` with your key already backup
```bash
wallet_add_secret_keys <your_key>
```
* view your wallet
```bash
wallet_info
```
* Generate new Wallet
```bash
wallet_generate_secret_key
```
* Backup your Node,please save your DATA on safe placee
```bash
mkdir massa_backup
echo $HOME /massa/massa-node/config/node_privkey.key
echo $HOME /massa/massa-client/wallet.dat
cp $HOME/massa/massa-node/config/node_privkey.key $HOME/massa_backup/node_privkey.key
cp $HOME/massa/massa-client/wallet.dat $HOME/massa_backup/wallet.dat
```
* Restore old wallet 
```bash
mv $HOME/massa_backup/node_privkey.key $HOME/massa/massa-node/config/
mv $HOME/massa_backup/wallet.dat $HOME/massa/massa-client/
```

* Check Massa Log
```bash
sudo tail -f /root/massa/massa-node/logs.txt
```
* Get status massa, You can close with `CTRL+C`
```bash
systemctl status massad
```
* Restart Massa
```bash
systemctl restart massad
```
* Delete Node
```bash
sudo systemctl stop massad
sudo systemctl stop massad.service
sudo systemctl disable massad.service
sudo rm /etc/systemd/system/massa* -rf
sudo rm $(which massa) -rf
sudo rm $HOME/.massa* -rf
sudo rm $HOME/massa -rf
```

## source massacaptain, [Source](https://medium.com/@massacaptain/tutorial-running-node-massa-dengan-satu-command-line-32a9bc472b46)
