# instalacionAR01

#!/bin/bash

# Instalación de herramientas básicas de OSINT
sudo pacman -S nmap wireshark-qt maltego theharvester shodan metasploit aircrack-ng sqlmap nikto cobaltstrike powersploit beef tor proxychains bleachbit meterpreter impacket-mssqlclient impacket-smbclient impacket-smbserver impacket-spray impacket-targeted-users impacket-ticketer impacket-wmiexec impacket-samrdump impacket-ntlmrelayx impacket-smbexec -y

# Instalación de Pivoting y Mimikatz
cd ~/Downloads/
git clone https://github.com/securestate/king-phisher.git
cd king-phisher/deps/
sudo pip install -r requirements.txt
sudo pacman -S mingw-w64-gcc mingw-w64-cmake mingw-w64-boost mingw-w64-zeromq
sudo pip install -r requirements-windows.txt
cd ..
sudo python3 setup.py install
rm -rf ~/Downloads/king-phisher/

cd ~/Downloads/
git clone https://github.com/gentilkiwi/mimikatz.git
cd mimikatz
make
cd ..

# Instalación de Shellter
cd ~/Downloads/
wget -q 'https://www.shellterproject.com/Downloads/Shellter/Latest/shellter.zip'
unzip shellter.zip
rm shellter.zip

# Fin del script
echo "Todas las herramientas han sido instaladas correctamente"
