# taller-robotica-uno

## Proceso de instalacion

### Configuracion del raspberry pi
1. Descargar la herramienta de instalacion de systemas operativos del sitio oficial de raspberry pi.
2. Installar la version completa de rasbianOS 32 bits.
3. Mediante el uso de un monitor, teclado y raton, conectate al raspi y sigue todos los pasos iniciales para la instalacion del systema operativo.
	1. asegurate que la contrasena del admin sea tambien "holamundo" 
	2. wifi ssd "tallerRoboticaUno"; passwd "holamundo"
	3. Deja que el sistema instale todas las actualizaciones pendientes. Al treminar, reinicia el equipo.
4. Accede el menu de configuracion de tu github y genera un token.
	1. Este token tiene que tener acceso a "repo" y "read:repo_hooks" y ademas dar un tiempo suficiente para su caducidad.
	2. Solo una persona debe de configurar git con su cuenta por cada robot. 
5. Ejecuta los siguientes comandos en la tarminal

```
sudo apt-get upgrade
sudo apt-get update
sudo apt-get install git screen xrdp
sudo vi /boot/config.txt
--->
#disable bluetooth
dtoverlay=disable-bt
<--- Ctrl+X, y, Enter

mkdir basura
cd basura
git config --global user.name "myuser"
git config --global user.email "myuser@email.com"
git config --global credential.helper cache
git clone https://github.com/alberto-bortoni/myrcfiles
[insert username]
[insert token]

cd myrcfiles
cp -f .bashrc ~/
cp -f .gitconfig ~/
cp -f .nanorc ~/
cp -f .screenrc ~/
cd ~
source .bashrc

sudo raspi-config
``` 
6. En este menu cambiaremos varias cosas
	1. System Options
		1. hostname
		2. "robotUno"..."robotDos"
	2. Interface options
		1. SSH -> Si
		2. SPI -> Si
		3. I2C -> Si
		4. Remote GPIO -> Si
	3. Finish. Reiniciar
7. Usando otra computadora, trada te acceder a este PI mediante la aplicacion "Remote Desktop" en windows
	1. Adquiere la direccion IP de este dispositivo en el sitio del ruter, o
	2. En tu rasberri pi ejecuta "ifconfig"
	3. En el router asegurate de reservar esta direccion para esta unidad en perpetuidad.
	4. user: pi@robotUno pass: holamundo
	5. No pasa nada si no se ve bien lo importante es tener una coneccion por ahora.
8. Apaga el equipo por completo (sudo shutdown now) 
9. Usando putty
	1. Copiar la plantilla 
	2. pi@DIRECCIONIP pass: holamundo
10. Installar las bases del PiCar
	1. git clone --recursive https://github.com/alberto-bortoni/sun-founder.git
	2. cd sun-founder
	3. sudo ./install_dependencies
	4. reboot
	5. deja pasar un minuto y vuelve a acceder al robot mediante Putty
	6. cd sun-founder
	7. picar servo-install
		1. con esto terminas de installar el servo de direccion
	8. picar front-wheel-test 0
	9. picar rear-wheel-test
	

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


nota:
python-smbus no instalo