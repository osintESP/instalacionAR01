# Tienes en este momento a la vista a una de las pocas distribuciones en Español de OSINT 
# En Abril y Octubre estaremos realizando actualización de las versiones :)
# Brindamos alternativas para que lleves a cabo la instalación

## Opción 1 
##Desatendida

### Configuración de idioma y zonas horarias
locales locales-gen
keyboard-layouts keyboard-layouts/laoutcode string es
keyboard-layouts keyboard-layouts/variantcode string 
keyboard-configuration keyboard-configuration/unsupported_layout boolean true
keyboard-configuration keyboard-configuration/layout select Spanish (SP)
keyboard-configuration keyboard-configuration/layoutcode string es
keyboard-configuration keyboard-configuration/variantcode string 

### Información de usuario y contraseñas
user-setup-udeb username string manjaro
user-setup-udeb full-name string Manjaro User
user-setup-udeb password-crypted password hash
user-setup-udeb password-again-crypted password hash
user-setup-udeb encrypt-home boolean false
 
### Configuración de partición
partman-auto/init_automatically_partition select Guided - use entire disk
partman-auto/method string regular
partman-auto/choose_recipe select All files in one partition (recommended for new users)

### Configuración de red
network-console network-console/enable boolean true
network-console network-console/password password remote installation password
network-console network-console/start select continue

Es importante que en la sección de informacion de usuario y contraseñas incluyas la contraseña en formato hash (optativo pero importante).

Abre una ventana de terminal / línea de comandos y navega a la ubicación de VirtualBox en tu computadora.

Ejecuta el siguiente comando para crear una nueva máquina virtual en VirtualBox:

VBoxManage createvm --name "Manjaro" --ostype ArchLinux_64 --register

Luego, agrega un disco duro virtual a la máquina virtual con el siguiente comando:

VBoxManage storagectl "Manjaro" --name "SATA Controller" --add sata --controller IntelAHCI
VBoxManage createhd --filename Manjaro.vdi --size 8192 --format VDI
VBoxManage storageattach "Manjaro" --storagectl "SATA Controller" --port 0 --device 0 --type hdd --medium Manjaro.vdi

## Opción 2 
##A manopla :S

a )Descarga e instala VirtualBox en tu sistema operativo en https://www.virtualbox.org/wiki/Downloads.

b) Descarga la imagen ISO de Manjaro Gnome 22.0.4 desde https://download.manjaro.org/gnome/22.0.4/manjaro-gnome-22.0.4-230222-linux61.iso a una carpeta en tu computadora.

c) Abre VirtualBox e inicia la creación de una nueva máquina virtual presionando el botón "Nuevo" en la barra de herramientas.

d) Agrega un nombre para la máquina virtual (osintesp) y selecciona "Linux" como tipo de sistema operativo. Selecciona "Arch Linux (64-bit)" como versión.

e) Selecciona la memoria RAM que quieras asignar a la máquina virtual, según las especificaciones de tu computadora.

f) Selecciona crear un disco duro virtual.

g) Elige "VDI (VirtualBox Disk Image)" como tipo de disco duro virtual.

h) Selecciona "Dinámicamente asignado" como tamaño del disco duro virtual.

i) Elige el tamaño que quieras asignarle al disco duro virtual y presiona "Crear".

j) Selecciona la máquina virtual que acabas de crear y presiona "Configuración".

k) En la sección "Almacenamiento", selecciona el controlador "Controlador IDE".

l) Selecciona "Agregar un disco óptico" y luego selecciona la imagen ISO de Manjaro que descargaste previamente.

Presiona "OK" para guardar la configuración.

Inicia la máquina virtual, te preguntará si quieres arrancar desde la imagen ISO de Manjaro, confirma y comenzará la instalación.

ll) Sigue los pasos del instalador de Manjaro para completar la instalación del sistema operativo en la máquina virtual.


Instalación de herramientas básicas de OSINT

## Sobre la distro Manjaro

cd Descargas 

git clone https://github.com/osintESP/instalacionAR01.git

cd instalacionAR01

chmod +x manja         
./manja 


