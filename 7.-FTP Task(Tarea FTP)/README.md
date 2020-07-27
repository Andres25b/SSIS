# FTP Task

### **Descripción:**

<div style="text-align: justify">

La tarea FTP descarga y carga archivos de datos y administra directorios en servidores. Por ejemplo, un paquete puede descargar archivos de datos de un servidor remoto o una ubicación de internet como parte de un flujo de trabajo del paquete de Integration Services.

</div>

---

### **Ejercicio:**

<b>1.</b> Se requiere que el proceso automatizado envíe y descargue archivos del servidor SFTP, para ello debe utilizar la herramienta FTP Task.

##### Crear Enviar archivo CSV

* Arrastramos al flujo de control la herramienta **'Tarea FTP'**.
* Hacemos doble click para ver sus propiedades.
* Creamos un nueva conexión FTP.
* Nos dirigimos a la pestaña de **Transferencia de archivo**.
* Asignamos el valor de **Enviar archivos** a Operation.
* Establecemos el LocalPath por un archivo exitente.
* Establecemos el RemotePath a la carpeta donde se enviara el archivo.

##### Crear Descargar archivo TXT

* Arrastramos al flujo de control la herramienta **'Tarea FTP'**.
* Hacemos doble click para ver sus propiedades.
* Creamos un nueva conexión FTP.
* Nos dirigimos a la pestaña de **Transferencia de archivo**.
* Asignamos el valor de **Recibir archivos** a Operation.
* Establecemos el LocalPath por un directorio existente.
* Establecemos el RemotePath como el archivo que mandara.

#### **Resultado Final:**

<div style="text-align: center">

![Resultado Final - File System Task](https://raw.githubusercontent.com/Andres25b/SSIS/master/Anexos/7.-FTP.Task.png "Resultado Final - File System Task")

"Resultado Final - File System Task"

</div>