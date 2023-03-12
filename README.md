# Estas en una de las pocas distribuciones en Español de OSINT 

# Brindamos alternativas para que lleves a cabo la instalación

## Opción 1 
##Desatendida

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


