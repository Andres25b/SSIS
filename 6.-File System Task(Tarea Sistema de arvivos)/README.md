# File System Task

### **Descripción:**

<div style="text-align: justify">

La tarea del sistema de archivos se utiliza para minipular operaciones en archivos y directorios en un servidor o de manera local. Por ejemplo, puede crear la tarea para crear, copiar, eliminar o mover un archivo o un directorio. Todas las operaciones en la tarea usan una fuente y algunas de ellas, como copiar y mover, tamien necesitan un destino.

</div>

---

### **Ejercicio:**

<b>1.</b> Mediante la herramienta File System Task se debe crear un directorio(carpeta) para que se pueda copiar el archivo desde un origen, para luego procedes a cortar el archivo y finalmente poder eliminarlo. Conociendo asi las funcionalidades del File System Task.

##### Creacion de variables.

* Creamos dos variables.
    | Nombre      | Ambito                   | Tipo de dato| Valor                                                                 | Expresión                                     |
    | :---------- | :----------------------- | :-----------| :---------------------------------------------------------------------| :---------------------------------------------|
    |dDestino     | Nombre del paquete actual| String      |C:\SQL Service Integration Services\Tarea Sistema de Archivo\Destino   |                                               | 
    |dOrigen      | Nombre del paquete actual| String      |C:\SQL Service Integration Services\Tarea Sistema de Archivo\Origen\   |                                               | 

##### Crear directorio origen.

* Arrastramos al flujo de control la herramienta **'Tarea Sistema de Archivos'**.
* Hacemos doble click para ver sus propiedades.
* Especificamos la Operation a **Crear directorio**.
* Cambiamos el IsSourcePathVariable a **True**.
* Asignamos el valor de la variable **dOrigen** a SourceVariable .
* Cambiamos el valor de UseDirectoryIfExists a **True**.

##### Crear directorio destino.

* Arrastramos al flujo de control la herramienta **'Tarea Sistema de Archivos'**.
* Hacemos doble click para ver sus propiedades.
* Especificamos la Operation a **Crear directorio**.
* Cambiamos el IsSourcePathVariable a **True**.
* Asignamos el valor de la variable **dDestino** a SourceVariable .
* Cambiamos el valor de UseDirectoryIfExists a **True**.

##### Crear copiar archivo

* Arrastramos al flujo de control la herramienta **'Tarea Sistema de Archivos'**.
* Hacemos doble click para ver sus propiedades.
* Especificamos la Operation a **Copiar archivo**.
* Configuramos el origen:
    * IsSourcePathVariable va a se igual a **False**.
    * SourceConnection va a ser igual a la nueva conexion con un archivo existente.
* Configuramos el destino:
    * IsDestinationPathVariable va a ser igual a **False**
    * DestinationConnection va a ser igual a la nueva conexión con una carpeta existente.
* Para sobrescribir el archivo le asignamos el valor de **True** a OverwriteDestination.

##### Crear mover un archivo

* Arrastramos al flujo de control la herramienta **'Tarea Sistema de Archivos'**.
* Hacemos doble click para ver sus propiedades.
* Especificamos la Operation a **Mover archivo**.
* Configuramos el origen:
    * IsSourcePathVariable va a se igual a **False**.
    * SourceConnection va a ser igual a la nueva conexion con un archivo existente.
* Configuramos el destino:
    * IsDestinationPathVariable va a ser igual a **False**
    * DestinationConnection va a ser igual a la nueva conexión con una carpeta existente.
* Para sobrescribir el archivo le asignamos el valor de **True** a OverwriteDestination.


##### Crear eliminar un archivo

* Arrastramos al flujo de control la herramienta **'Tarea Sistema de Archivos'**.
* Hacemos doble click para ver sus propiedades.
* Especificamos la Operation a **Eliminar archivo**.
* Configuramos el origen:
    * IsSourcePathVariable va a se igual a **False**.
    * SourceConnection va a ser igual a la nueva conexion con un archivo existente.


# Script Task

### **Descripción:**

<div style="text-align: justify">

La tarea Script proporciona código para realizar funciones que no están disponible en las tareas integradas y las tranformaciones que proporciona SQL Server Integration Services. La tarea Script también puede combinar funciones en un script en lugar de usar multiples tares y transformaciones.

</div>

---

### **Ejercicio:**

<b>1.</b> }Finalizado el proceso anteriormente diseñado se requiere que un archio de texto plano(txt) se especifique si el proceso termino correctamente o si hubo algún error al momento que se ejecutó el package.

##### Creacion de variables.

* Creamos dos variables.
    | Nombre         | Ambito                   | Tipo de dato| Valor                                                                 | Expresión                                       |
    | :------------- | :----------------------- | :-----------| :---------------------------------------------------------------------| :-----------------------------------------------|
    |Directorio      | Nombre del paquete actual| String      | C:\SQL Service Integration Services\Tarea Sistema de Archivo\Mensaje\ |                                                 | 
    |MensajeCorrecto | Nombre del paquete actual| String      |                                                                       | `@[User::Directorio]+"MensajeCorrecto.txt"`     |
    |MensajeError    | Nombre del paquete actual| String      |                                                                       | `@[User::Directorio]+"MensajeError.txt"`        |

##### Crear mensaje correcto

* Arrastramos al flujo de control la herramienta **'Tarea Script'**.
* Hacemos doble click para ver sus propiedades.
* Configuramos variables de solo lectura en este caso: **Directorio** y **MensajeCorrecto**.
* Editamos el Script: 

        String Directorio = Dts.Variables["Directorio"].Value.ToString();
        String MensajeCorrecto = Dts.Variables["MensajeCorrecto"].Value.ToString();

        String Contenido = "El proceso a terminado corretamente";

        if (!Directory.Exists(Directorio))
        {
            Directory.CreateDirectory(Directorio);
        }

        File.WriteAllText(MensajeCorrecto ,Contenido);

		Dts.TaskResult = (int)ScriptResults.Success;

##### Crear mensaje Error

* Arrastramos al flujo de control la herramienta **'Tarea Script'**.
* Hacemos doble click para ver sus propiedades.
* Configuramos variables de solo lectura en este caso: **Directorio** y **MensajeError**.
* Editamos el Script: 

        String Directorio = Dts.Variables["Directorio"].Value.ToString();
        String MensajeError = Dts.Variables["MensajeError"].Value.ToString();

        String Contenido = "El proceso a terminado en error";

        if (!Directory.Exists(Directorio))
        {
            Directory.CreateDirectory(Directorio);
        }

        File.WriteAllText(MensajeError, Contenido);

		Dts.TaskResult = (int)ScriptResults.Success;


#### **Resultado Final:**

<div style="text-align: center">

![Resultado Final - File System Task](https://raw.githubusercontent.com/Andres25b/SSIS/master/Anexos/5.-FileSystemTask.png "Resultado Final - File System Task")

"Resultado Final - File System Task"

</div>