# CHC Masternode Installation Instructions

-----------------------------------

##### Video Tutorial by Cliff On Crypto: https://www.youtube.com/watch?v=azBopV3Ldww 

##### Cliff On Crypto: https://www.youtube.com/channel/UC7aZpep7PnlRcvljRRwh0Gw

-----------------------------------

### Please create a new VPS using 64 bit Ubuntu 14.04

### After, please login as root, and create a new user.  Give that new user sudo rights

### run these commands
--------------------
#### adduser < newUsername >
######  (without the < >)
##### Example:
#### adduser awesomeUser101
--------------------
#### usermod -aG sudo < newUsername >
######  (without the < >)
##### Example:
#### usermod -aG sudo awesomeUser101
--------------------

### Success! Now log out of root, and log back into the VPS as your new user

### Now, download a FTP client such as fileZilla.  Upload the install file to your newUser directory located here:
##### /home/newUsername
##### Example:
##### /home/awesomeUser101

### Alternativly to fileZilla, run these commands:
#### sudo apt-get install git
### Now navigate to your users home directory:
##### cd /home/newUsername
##### Example:
##### cd /home/awesomeUser101
### Install the script by running:
##### sudo git clone https://github.com/jeffward01/Chaincoin-MN-SetupScript.git
##### cd Chaincoin-MN-SetupScript


--------------------
### Before we begin, lets ensure that the newly created user has the proper permission to run the MasternodeSetupScript, run these commands:
#### Ensure you are in the directory where you downloaded the MasternodeSetupScript.  You should not need to navigate away from your current directory. 
###### cd /home/myUserName/Chaincoin-MN-SetupScript
#### Grant permissions:
##### sudo chmod 777 MasternodeSetupScript
##### sudo chmod 777 username:sudo MasternodeSetupScript

### Example:
###### cd /home/awesomeUser101/Chaincoin-MN-SetupScript
##### sudo chmod 777 MasternodeSetupScript
##### sudo chmod 777 awesomeUser101:sudo MasternodeSetupScript

-----------------------



###  Now that you have uploaded the install file in your user's directory, go back to the VPS SSH terminal and run the tool:
##### ./MasternodeSetupScript (this starts the install process)


#### 1.) The swap file will now be edited to prevent the system from crashing

#####  (A nano editor will open up, append this to the last line and save)
######  /var/swap.img none swap sw 0 0

#####  To save, click CTRL+X and then after, CTRL + y



#### 2.) The dependencies will now be installed.  Press enter to continue and  please press y to all prompts



#### 3.) Chaincoin software will now be installed.  Press enter to continue


#### 4.) Next a nano editor will open.  Please replace the <\replaceThis\> tags with your information and paste the block into the code editor
##### Do not include the < > 
-----------------------

rpcuser=< any-username >

rpcpassword=< any-unique-password >

server=1

-----------------------

##### EXAMPLE:
-----------------------

rpcuser=testUser101

rpcpassword=password123

server=1

-----------------------

###### After you have pasted the text block save.
###### To save, click CTRL+X and then after, CTRL + y



#### 5.)
 ##### 5a.) Next you will see an output of your Masternode Wallet address.  Please it and save it to a text file on your local machine. You will need to fund this address with 1000.00 CHC

##### 5b.) Next you will see an output of your Masternode Private Key.  Please it and save it to a text file on your local machine.


#### 6.) Now you will see the nano text editor with your previous text block you have saved.  Please paste this text below your previous block 
##### Do not include the < > 

-----------------------

listen=1

masternode=1

masternodeprivkey=< masternode-wallet-private-key >

masternodeaddr=< your server ip >:11994

-----------------------
##### EXAMPLE:
-----------------------

listen=1

masternode=1

masternodeprivkey=554asd545asd454d5qw6d4qwd56qewfw23

masternodeaddr=55.555.55.555:11994

-----------------------

#### 7.) Now we need to fund your masternode and sync it.  Please send your 1000.00 CHC to your masternode address and click [ENTER] when that is complete
##### Note: Your masternode must recieve exactly 1000.00 CHC in the transaction.  If you are using the CHC Desktop wallet, please send 1000.00 CHC to the address
##### If you are using a different wallet such as an exchange wallet, please send 1000.001, where the .001 is the transcation fee incured from the transaction.

###### Note: This next step is syncing, and may take up to 4 hours.  You are downloading the CHC blockchain to your local masternode.  You are also incurring 15+ confirmations on your deposit of 1000.00 CHC.  After you have 15+ confirmations you may start your masternode.


##### Please complete the installer, and in 4 hours return and start your masternode by running this command:

### chaincoind masternode start
-------------------------------
# Installation Complete!

-------------------------------
### If you wish to start your masternode before the 4 hours (4 hours is suggested to ensure the masternode is finished syncing) please follow these directions:

##### run this command:

### watch chaincoind getinfo

###### Once your node finishes syncing, you will see the 1000.00 CHC in your balance. 
###### Press Ctrl + C to exit the ‘watch’ screen.

###### To check the transaction count please run this:

### chaincoind listtransactions

###### (once transaction count for the intial 1000.00 is over 15, start the masternode)


-------------------------
-------------------------


### Helpful commands:


-------------------------
#### Start ChainCoin
###### chaincoind -daemon
-------------------------

-------------------------
#### Stop ChainCoin
###### chaincoind stop
-------------------------


-------------------------
#### Start Masternode
###### chaincoind masternode start
-------------------------

-------------------------
#### Get Masternode Address:
###### chaincoind getaccountaddress 0
-------------------------

-------------------------
#### Get Masternode Private Key:
###### chaincoind masternode genkey
-------------------------

-------------------------
#### Get Masternode Status:
###### chaincoind getinfo
-------------------------


-------------------------
#### Get Masternode Status (continously update):
###### watch chaincoind getinfo
##### press Ctrl+C to exit
-------------------------








