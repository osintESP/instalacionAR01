# Tienes en este momento a la vista a una de las pocas distribuciones en Español de OSINT 
## Cada 6 meses estaremos realizando actualización de las versiones :)

## Brindamos alternativas para que lleves a cabo la instalación

## Opción A 

VAGRANT

La manera más fácil de tener tu distribución disponible en tu equipo!
Pre-Requisitos:

1) Instalar Vagrant

https://developer.hashicorp.com/vagrant/downloads

2) Instalar Virtual Box 

https://www.virtualbox.org/wiki/Downloads

3) Crear los siguientes archivos:

Ej: Path : /home/user/vm/osintesp

```
cd /home/user/vm/osintesp
```
```
vim Vagrantfile
```

Copiar y pegar el contenido de https://github.com/osintESP/instalacionAR01/blob/master/vagrantfile donde encontrarás la última versión del archivo responsable de la auto-instalación de la distro.


# Posibles ERRORES

URL: ["https://vagrantcloud.com/osintesp/osintesp-v1"]
Error: schannel: next InitializeSecurityContext failed: Unknown error (0x80092012) - La funci¾n de revocaci¾n no puede comprobar la revocaci¾n para el certificado.

Verifica si tienes Kaspersky deberás por un momento desactivar la verificación de https.



# Instalación de herramientas Osint modo Manual

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
chmod +x osintesp-desatendido
```
```
./osintesp-desatendido
```

# Información importante : 
## El usuario y contraseña de la distro por defecto.

```
Usuario: vagrant
```
```
Contraseña: vagrant
```

