NOMP-MS-Access-database-and-json-generator
==========================================

This is a MS Access database that will create and maintain all of your coin configs and json files need for NOMP

In order to use this database you must create the following folder structure:

1. Main folder for databse, this can be named anything you like
The following folders need to be named as shown below
2. Coins  -- This is where the /nomp/coins/coin_name.json files will be stored
3. Pool_Configs  -- This is where the /nomp/pool_configs/coin_name.json files will be stored
4. Coin_Configs  -- This is where the main daemon conf file will be, example bitcoin.conf
5. Coin_Configs/Backup -- This is where the backup daemon conf fill will be if you are wanting to run two daemons

Once the folders are created launch NOMP.accdb - You may get a security error click on allow access or enable content. 
Please note this is a MS Access security warning for the VB code. Everything is stored on your PC 

Double click on the form labeled Main

Everything in here should be pretty easy to understand.

Coin Daemon Name - Please make sure to use the exact name that is compiled by the coin. This will be used in a upcoming release to have the database generate a "all in one" startup script for your server. 

Coin Display Name - No spaces, this is used to create both json files names. With the new NOMP update does not matter if there are any capital letters in the name. 

Scrypt-Jane/Scrypt-N/Keccak - Checking any one of these boxes will automatically add the additional configurations for these coins.

Wallet - Your daemon wallet address 

peerMagic - Use if P2P Enabled is checked. 

If P2P is NOT checked the following line will be added to your coin.conf file: 
"blocknotify=/usr/local/bin/blocknotify 127.0.0.1:17117 " & Display_Name & " %s"
Please note the file location it will look for blocknotify is /usr/local/bin -- make sure the file is there!

If you are only running one daemon you can leave the Backup RPC User/Password/Port blank -- if leaving blank do not click on the Generate Backup Daemon button ;) 
If you want to use the -datadir=/backup option for a second daemon make sure these are filled out with seperate RPC User/Password/Port information from your main config!

--When the config files are generated they will automatically add the following lines --
server = 1
daemon = 1
listen = 1
rpcconnect=127.0.0.1
rpcallow=*
gen = 0

Additional Coin Conf - For adding additional items such as addnode=, etc 

--Pool Config JSON file--
Any options not seen here the JSON file will be automatically created with the values from the NOMP example!

Recipient One - Wallet address for fee to go to.
Recipient One Fee - Percentage amount for fees.
Recipient Two - Same as above; if left blank it will not generate in the json file. 
NOMP Donation - Again if left blank will not generate in the json file. 

Stratum Ports

You do not need to use all three ports if Stratum Two or Three are left blank they will not generate in the JSON file. 
--Even though data auto-populates in some of the fields if there is no data entered in the PORTS they will not populate--

Now just click on your generate buttons and uplaod to your server!

If you find this database useful please donate BTC to 143xMaUgDzbaZkB5EQgJnQAgYvfN8ycA5m

