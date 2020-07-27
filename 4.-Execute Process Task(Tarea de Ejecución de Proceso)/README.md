# Execute Process Task

### **Descripción:**

<div style="text-align: justify">

La tarea Ejecutar proceso se puede usar para ejecutar una aplicación o un archivo por lotes como uno de los pasos en un paquete SSIS. La entrada, la salida y los argumentos de la aplicacion se pueden establecer en el editor de la tarea y se pueden usar en tiempo de ejecución.

</div>

---

### **Ejercicio:**

<b>1.</b> Diariamente se genera una base de datos de los clientes que son extraídos de la base de datos SQL Server hacia un archivo de texto plano (txt), se solicita que dichas bases se envíen comprimidas en el formato ".gz".

##### Configuración del proceso Comprimir.

* Arrastramos al flujo de control la herramienta **'Tarea Ejecutar proceso'**.
* Hacemos doble click para acceder a sus propiedades. 
* Nos dirigimos a la pestaña de **Proceso**.
* En Executable pondremos el ejecutable que se ejecuta como parte del paquete. En esta ocación utilizares el .exe de python para posteriormente ejecutar un programa.
* En Arguments pondremos la dirección del programa a ejecutar.
        
        #Este es el contenido del programa para comprimir un archivo a ".gz"

        import gzip

        input = open("C:/SQL Service Integration Services/Execute Process Task/Reporte Cliente.txt",'rb')
        s=input.read()
        input.close()

        output = gzip.GzipFile("C:/SQL Service Integration Services/Execute Process Task/Comprimido/Reporte Cliente.txt.gz",'wb')
        output.write(s)
        output.close()

        print("Done")

##### Configuración del proceso Eliminar reporte cliente.

* Arrastramos al flujo de control la herramienta **'Tarea Ejecutar proceso'**.
* Hacemos doble click para acceder a sus propiedades. 
* Nos dirigimos a la pestaña de **Proceso**.
* En Executable pondremos el ejecutable que se ejecuta como parte del paquete. En esta ocación utilizares el .exe de python para posteriormente ejecutar un programa.
* En Arguments pondremos la dirección del programa a ejecutar.
        
        #Este es el contenido del programa para Eliminar el reporte de cliente
        
        import os

        if os.path.exists("C:/SQL Service Integration Services/Execute Process Task/Reporte Cliente.txt"):
            os.remove("C:/SQL Service Integration Services/Execute Process Task/Reporte Cliente.txt")
        else:
            print("El archivo no existe")


<div style="text-align: center">

![Resultado Final - Execute Process Task](https://raw.githubusercontent.com/Andres25b/SSIS/master/Anexos/3.-TareaEjeutarProceso.png "Resultado Final - Execute Process Task")

"Resultado Final - Execute Process Task"

</div>

