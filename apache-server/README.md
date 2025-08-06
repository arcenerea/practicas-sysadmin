# Configuración de Servidor Apache en Ubuntu

Esta práctica consistió en la instalación, configuración y optimización de un servidor web Apache en un sistema Ubuntu 16.04. El objetivo principal fue entender el funcionamiento básico del servidor HTTP Apache, así como aplicar configuraciones esenciales para su correcto funcionamiento.

## 🧱 Objetivos

- Instalar Apache en Ubuntu.
- Verificar el estado del servicio.
- Configurar archivos principales (puertos, hosts virtuales).
- Optimizar el rendimiento básico del servidor.

## ⚙️ Pasos realizados

### 1. Instalación de Apache

Se instaló Apache mediante el gestor de paquetes `apt`:

```bash
sudo apt update
sudo apt install apache2


### 2. Comprobación del estado del servicio

Para verificar que Apache esté activo y funcionando, usa el siguiente comando:

```bash
sudo systemctl status apache2


###3. Comprobación de funcionamiento en el navegador
Se accedió al servidor desde el navegador introduciendo la IP local, confirmando que la página de bienvenida de Apache se mostraba correctamente.

###4. Archivos de configuración modificados
/etc/apache2/apache2.conf: Configuración general del servidor.

/etc/apache2/ports.conf: Para definir los puertos que escucha Apache.

/etc/apache2/sites-available/000-default.conf: Modificado para personalizar el host virtual por defecto.

###5. Reinicio del servicio
Después de los cambios se reinició Apache para aplicar la configuración:

bash
sudo systemctl restart apache2
🔧 Optimización básica
Se revisaron parámetros de rendimiento y módulos innecesarios para mejorar la eficiencia del servidor en entornos con recursos limitados.

📁 Resultado final
Servidor Apache funcional y personalizado, ejecutándose correctamente en una máquina virtual con Ubuntu 16.04.

✍️ Nota: Esta práctica forma parte del conjunto de ejercicios realizados durante mi formación como Administradora de Sistemas.
