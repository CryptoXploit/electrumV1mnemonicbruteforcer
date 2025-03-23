Brute-force Mnemomonic old Electrum (V1)
config.cfg file
"folder_database": "C:\database" - path to the folder with tables of the sought addresses. The addresses in the tables must be in hash160 format and sorted by the program https://github.com/Houzich/Convert-Addresses-To-Hash160-For-Brute-Force
"cuda_grid": 1024 - setting for the video card
"cuda_block": 256 - setting for the video card The number of generated mnemonics per round is equal to cuda_grid*cuda_block
Description
When the program is launched, the settings are read from the config.cfg file. The console displays the message

Detected 3 CUDA Capable device(s)

where the number 3 is the number of NVIDIA video cards found. The characteristics of each card are displayed below:

Device 0: "NVIDIA GeForce GTX 1050 Ti"

...

Device 1: "NVIDIA GeForce GTX 1050 Ti"

Enter the number of the used video card:

You need to enter the number of the card you are using. Reading and converting the database files with addresses begins:

PROCESSED 2168134 ROWS IN FILE C:\database\A0.csv .....

Where 2168134 is the number of addresses in the file. The addresses in the file are stored in 20-byte format as a hex string. And sorted in ascending order.

Enter number of generate mnemonic:

The number of mnemonics we want to generate. This is entered to check the generation speed. If we want it infinite, then we set the maximum value to 18000000000000000000.

Enter num cycles save data in file:

How many rounds do we want to write to the file? Entered to check the correctness of the generation. The mnemonic and the corresponding addresses are written to the Save_Addresses.csv file. The writing is very slow. Since the conversion of the 20-byte format to the WIF format is performed on the CPU. When checking the speed, select the number of cycles 0.

!!!FOR TEST!!! Enter num bytes for check BIP44 6...8:

You can enter the number of bytes by which additional verification will be performed. To skip this step, enter 0. If you enter a number, the addresses will be checked for a match also by the specified number of bytes.

Next, the number of wallets generated per round is displayed. And the generation process begins. During the program's operation, the inscription is constantly updated

SPEED: 250,234 MNEMONICS/SECOND AND 2,500,340 ADDRESSES/SECOND, ROUND: 9

Number of mnemonics and number of addresses generated per second. In this case, 10 addresses were generated for each generated wallet. 5 addresses of patch m/0/x and five addresses of patch m/1/x

Check for byte matches
If you enter when starting the program

!!!FOR TEST!!! Enter num bytes for check BIP44 5...8:

for example, 5. Then periodically the following messages will appear on the screen:

!!!FOUND BYTES: blossom window trouble everyday return use dot reflect sweat midnight cost made,14FtUvN1BHV4kto2t1V3pkAkZnLwrmat9f,14FtUvN14hVyyXJFDcwTkz5vkDyYWYBRCN,23B 92CE0FF27BD38A6D7E1B8C8EED9D4F372E295,23B92CE0FF03C3AF18CF8A182D9B791CD260D8D0

Mnemonic of the generated wallet. Its address. The address in the database, which coincided by the first bytes with the address of the mnemonic. And accordingly, their representation in the 20-byte hash160 format. You can count the same bytes and verify this. All these addresses are saved in the log file Found_Bytes.csv. In the file, the lines are stored as: usual disagree error juice gap renew jacket toe circle goose tank prefer,15JMEsfkJSE1BJ3FjyMFZheAtpn7qLyHUs,15JMEsfjbTyHN6Wf9x2HA7XnqfVqdgD4kD,2F28782544E96EBEC694FFF37AC20FD2B6389ABD,2F2878254409A3E553D017294757CC2DDF4A2E99,Fri Feb 3 11:40:56 2023

If you found a wallet
The following message will appear in the console:

!!!FOUND!!! !!!FOUND!!! !!!FOUND!!! !!!FOUND!!! !!!FOUND: emotion first beard escape shield rough flame carefully handle dish really dad, 17oaREDuDrWg1ECCyQZHwNJJyWTp3Bfnw1 !!!FOUND!!! !!!FOUND!!! !!!FOUND!!! !!!FOUND!!!*
Accordingly, the mnemonic and the address that we found. And the information will be added to the file Found_Addresses.csv. In the file, the lines are stored as follows: emotion first beard escape shield rough flame carefully dish handle really dad, 17oaREDuDrWg1ECCyQZHwNJJyWTp3Bfnw1,Fri Feb 3 12:21:27 2023

The BruteForceMnemonicOld.exe file is located in the exe folder