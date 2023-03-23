# Tienes en este momento a la vista a una de las pocas distribuciones en Español de OSINT 
## Cada 6 meses estaremos realizando actualización de las versiones :)

## Brindamos alternativas para que lleves a cabo la instalación

## Opción 0 

##Vagrant

La manera más fácil de tener tu distribución disponible en tu equipo!
Pre-Requisitos:
1) Instalar Vagrant https://developer.hashicorp.com/vagrant/downloads

Crear los siguientes archivos:

Vagrantfile

```
Vagrant.configure("2") do |config|
  config.vm.box = "generic/arch"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
  config.vm.provision "shell", path: "vagrant-install.sh"
end
```

vagrant-install.sh
```
#!/bin/bash

# instalar el entorno gráfico GNOME
sudo pacman -S --noconfirm gnome

# clonar el repositorio de GITHUB e instalar las aplicaciones de OSINT
sudo pacman -S --noconfirm git
git clone https://github.com/osintESP/instalacionAR01.git
cd instalacionAR01
sudo bash install.sh

```


vagrant cloud auth login --token IHLHO7R2K4gaVQ.atlasv1.Jn3pHr76oYEdio57Q9ZNZPTtM6PfyUPYKXFJE6lrw09P0uBBa9vyeab1vqemXDoBfAo


# Posibles ERRORES

URL: ["https://vagrantcloud.com/osintesp/osintesp-v1"]
Error: schannel: next InitializeSecurityContext failed: Unknown error (0x80092012) - La funci¾n de revocaci¾n no puede comprobar la revocaci¾n para el certificado.

Verifica si tienes Kaspersky deberás por un momento desactivar la verificación de https.

## Opción 1 

##Desatendida

Crea un archivo de respuesta en un editor de texto que incluya información sobre las configuraciones de la instalación, como el idioma, la zona horaria, el hostname, el usuario y la contraseña, y guardarlo como "manjaro-preseed.cfg" en una carpeta en tu computadora. Este archivo especificará los ajustes que se utilizarán durante la instalación y evitará que tenga que responder manualmente durante el proceso de instalación.

## LINUX 

```
vim osintesp-preseed.cfg
```
Copiar y Pegar lo siguiente:

```
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
```

## WINDOWS 10/11 o Posteriores


```
echo locales locales/default_environment_locale select es_MX.UTF-8 >> manjaro-preseed.cfg && ^
echo keyboard-configuration keyboard-configuration/layout select Latin American >> manjaro-preseed.cfg && ^
echo keyboard-configuration keyboard-configuration/variantcode select >> manjaro-preseed.cfg && ^
echo keyboard-configuration keyboard-configuration/modelcode select pc105 >> manjaro-preseed.cfg && ^
echo keyboard-configuration keyboard-configuration/xkb-keymap select latam >> manjaro-preseed.cfg && ^
echo user-setup-udeb user-setup/allow-password-weak boolean true >> manjaro-preseed.cfg && ^
echo user-setup-udeb username string manjaro >> manjaro-preseed.cfg && ^
echo user-setup-udeb full-name string Manjaro User >> manjaro-preseed.cfg && ^
echo user-setup-udeb password password password >> manjaro-preseed.cfg && ^
echo user-setup-udeb password-again password password >> manjaro-preseed.cfg && ^
echo user-setup-udeb encrypt-home boolean false >> manjaro-preseed.cfg && ^
echo partman-auto-crypto partman-auto-crypto/erase_disks boolean true >> manjaro-preseed.cfg && ^
echo partman-auto-crypto partman-auto-crypto/key_size string 256 >> manjaro-preseed.cfg && ^
echo partman-auto-crypto partman-auto-crypto/algorithm select aes-cbc-essiv:sha256 >> manjaro-preseed.cfg && ^
echo partman-auto-crypto partman-auto-crypto/passphrase password password >> manjaro-preseed.cfg && ^
echo partman-auto-crypto partman-auto-crypto/passphrase-again password password >> manjaro-preseed.cfg && ^
echo partman-auto-lvm partman-auto-lvm/new_vg_name string vg00 >> manjaro-preseed.cfg && ^
echo partman-auto-lvm partman-auto-lvm/no_boot boolean true >> manjaro-preseed.cfg && ^
echo partman-auto-lvm partman-auto-lvm/confirm boolean true >> manjaro-preseed.cfg && ^
echo partman-auto-lvm partman-auto-lvm/encryption_passphrase password password >> manjaro-preseed.cfg && ^
echo partman-auto-lvm partman-auto-lvm/encryption_passphrase-again password password >> manjaro-preseed.cfg && ^
echo partman-auto-lvm partman-auto-lvm/new_lv_name string lv_root >> manjaro-preseed.cfg && ^
echo partman-auto-lvm partman-auto-lvm/guided_size string max >> manjaro-preseed.cfg && ^
echo partman-auto-lvm partman-auto-lvm/new_lv_size string 100%VG >> manjaro-preseed.cfg && ^
echo partman-basicfilesystems partman-basicfilesystems/choose_label string gpt >> manjaro-preseed.cfg && ^
echo partman-partitioning partman-partitioning/confirm_write_new_label boolean true >> manjaro-preseed.cfg && ^
echo partman-partitioning partman-partitioning/confirm boolean true >> manjaro-preseed.cfg && ^
echo partman-basicfilesystems partman-basicfilesystems/default_filesystem string ext4 >> manjaro-preseed.cfg && ^
echo ubiquity ubiquity/summary note >> manjaro-preseed.cfg
```

Es importante que en la sección de informacion de usuario y contraseñas incluyas la contraseña en formato hash (optativo pero importante).

Abre una ventana de terminal / línea de comandos y navega a la ubicación de VirtualBox en tu computadora.

Ejecuta el siguiente comando para crear una nueva máquina virtual en VirtualBox:

```
VBoxManage createvm --name "Manjaro" --ostype ArchLinux_64 --register
```

Luego, agrega un disco duro virtual a la máquina virtual con el siguiente comando:

```
VBoxManage storagectl "Manjaro" --name "SATA Controller" --add sata --controller IntelAHCI
VBoxManage createhd --filename Manjaro.vdi --size 8192 --format VDI
VBoxManage storageattach "Manjaro" --storagectl "SATA Controller" --port 0 --device 0 --type hdd --medium Manjaro.vdi
```

## Opción 2 

## Manual

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

## Deploy instalación desatendida

``` cd Descargas 
```
```
git clone https://github.com/osintESP/instalacionAR01.git
```
```
cd instalacionAR01
```
```
chmod +x *
```
```
./desatendido-simplificado
```

