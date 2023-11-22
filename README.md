# Crear-y-configurar-certificado-SSL-en-Apache-Windows-Server
# Paso 1: Descargar e instalar OpenSSL

1. Descarga OpenSSL para Windows 
2. Instala OpenSSL siguiendo las instrucciones del instalador.

# Paso 2: Generar un certificado autofirmado

Abre una terminal y navega a la ubicación donde instalaste OpenSSL. Luego, ejecuta los siguientes comandos:

1. Generar una clave privada:
   
   `openssl genrsa -out claveprivada.key 2048`
   

2. Generar una solicitud de firma de certificado (CSR):
   
   `openssl req -new -key claveprivada.key -out solicitud.csr`
   

3. Completar la solicitud de CSR con la información solicitada.

4. Generar un certificado autofirmado a partir del CSR:
   
   `openssl x509 -req -days 365 -in solicitud.csr -signkey claveprivada.key -out certificado.crt`

# Paso 3: Configurar Apache para usar el certificado SSL

1. Copia los archivos `claveprivada.key` y `certificado.crt` a la carpeta donde Apache está configurado para buscar los certificados SSL.

2. Abre el archivo de configuración de Apache (`httpd.conf`).

3. Busca las líneas que contienen configuraciones de SSL y modifica o agrega las siguientes líneas:

![image](https://github.com/jooseeruu/Crear-y-configurar-certificado-SSL-en-Apache-Windows-Server/assets/120745808/af9f1805-e647-4fd1-a4f7-8a7eb2dd31d5)


4. Guarda los cambios y reinicia el servicio de Apache para aplicar la configuración.

# Paso 4: Verificar la configuración

Reinicia Apache y verifica si no hay errores en el reinicio. Luego, accede a tu sitio web utilizando `https://` y verifica si el certificado SSL está funcionando correctamente.

Recuerda que este es un certificado autofirmado y puede no ser válido para su uso en producción. En producción, debes obtener un certificado SSL de una Autoridad de Certificación (CA) reconocida.


