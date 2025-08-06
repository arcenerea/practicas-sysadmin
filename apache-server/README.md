Práctica: Compartición de archivos entre dos máquinas virtuales (Windows y Linux)
Realizado por: Nerea Arce Hernández

Introducción
En esta práctica configuré la compartición de archivos entre dos máquinas virtuales con sistemas operativos diferentes: Windows y Linux. El objetivo fue configurar correctamente las redes y compartir archivos utilizando métodos específicos para cada sistema operativo.

Para Windows, usé la compartición avanzada en red NAT. Para Linux, configuré Samba y SSP para compartir archivos. Durante el proceso, se presentaron algunos problemas de configuración y conectividad que resolví.

1. Configuración de redes en VirtualBox
Máquinas con Windows
Configuradas en modo NAT para usar la conexión de red del equipo anfitrión.

Máquinas con Linux
Inicialmente con adaptador puente (bridge), pero surgieron problemas de conexión.

Finalmente configuradas en modo NAT, lo que solucionó el acceso a internet.

Problema detectado:
Las máquinas Linux no accedían a internet con el adaptador puente. La solución fue cambiar a modo NAT y renovar la IP con sudo dhclient.

2. Compartición de archivos
En Windows (Compartición avanzada)
Activé la compartición de archivos e impresoras.

Compartí carpetas con permisos adecuados para acceso desde Linux.

En Linux (Samba)
Instalé Samba con:
sudo apt update
sudo apt install samba samba-common-bin

Configuré /etc/samba/smb.conf para compartir la carpeta:

bash
Copiar
Editar
[Compartida]
path = /home/usuario/compartida
available = yes
valid users = usuario
read only = no
browsable = yes
public = yes
writable = yes
Reinicié Samba con:
sudo systemctl restart smbd

Acceso desde Windows usando la ruta:
\\10.0.2.15\Compartida

Problema detectado:
Revisar permisos y firewall para evitar bloqueo de conexiones SMB.

3. Compartición entre máquinas Linux (SSP)
Instalé sshfs:
sudo apt install sshfs

Monté carpeta remota:
sshfs usuario@10.0.2.15:/home/arcenerea/carpeta /mnt/carpeta

Para desmontar la carpeta:
fusermount -u /mnt/carpeta

Conclusión
La práctica permitió entender cómo funcionan diferentes protocolos y configuraciones para compartir archivos entre sistemas heterogéneos. Se resolvieron problemas típicos de redes virtuales y permisos, reforzando el conocimiento en administración básica de sistemas.
