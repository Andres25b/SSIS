# Data Flow

### **Descripción:**

<div style="text-align: justify">
La tarea Flujo de datos encapsula el motor de flujo de datos que mueve datos entre orígenes y destino, y permite al usuario tranformar, limpiar y modificar datos a medida que se mueven.
<div/>

<div style="text-align: justify">
La adición de una tarea de flujo de datos a un flujo de control de paquete hace posible que el paquete extraiga, tranforme y cargue datos.
<div/>

---

### **Ejercicio:**

<b>1.</b> Se desea exportar de la base de datos **NORTHWND** la tabla **Customers** a un archivo con el nombre  Reporte Clientes.txt.

##### Configuración de la herramienta Tarea de flujo de datos.
* Arrastramos al flujo de control la herramienta **'Tarea flujo de datos'**.
* Hacemos doble click para acceder a la pestaña **'Flujo de datos'**.

<div style="text-align: center">

![Herramienta Data Flow Task](https://raw.githubusercontent.com/Andres25b/SSIS/master/Anexos/2.1-DataFlowTask.png "Herramienta Data Flow Task")

"Herramienta Data Flow Task"

</div>

##### Configuración del origen.

* Arrastramos la herramienta de origen **'Origen de OLE DB'**.
* Hacemos doble click para ver las propiedades del origen.
* Creamos una nueva conexion a la base de datos **NORTHWND**.
* Asignamos **'Tabla o vista'** como modo de acceso a datos.
* Asignamos el nombre de la tabla a ocupar en este caso **'Customers'**.
* En la **'pestaña columnas'** podemos configurar las columnas que se exportaran.
* Damos click en aceptar.

##### Configuración del destino.
* Arrastramos la herramienta de destino **'Destino de archivo plano'**.
* Hacemos doble click para ver las propiedades del origen.
* Creamos una nueva conexion de archivo plano.
    * Asignamos un nombre de administrador de conexion. En esta caso le ponemos **'Reporte Cliente'**.
    * Buscamos el archivo de destino.
    * Permitimos que la primera fila sea el nombre de las columnas de los datos.
    * Aceptamos para continuar.
* Nos dirigimos a la pestaña de **asignaciones** y establecemos los elementos de entrada y salida que se generaran en el archivo plano.
* Podemos permitir o no que los dato se sobrescriban cuando se ejecute la tarea.
* Damos click en aceptar para terminar.

<b>2.</b> Diariamente la gerencia necesita el reporte de los clientes que se encuentran en la base de datos SQL Server, también se requiere que se deposite el reporte en una ruta especifica y el nombre del archivo tiene que estar con la fecha que se genera dicho reporte. Cabe señalar que la elaboración del reporte debe ejecutarse de manera automática de manera diaria.(**NOTA:** Usa de base el ejercicio anterior)

* Creamos dos variables.
    | Nombre      | Ambito                | Tipo de dato| Valor                               | Expresión                                     |
    | :---------- | :-------------------- | :-----------|:-------------------------------------|:----------------------------------------------|
    |NombreArchivo| 2 Tarea Flujo De Datos| String      | Reporte Cliente                      |                                               | 
    |Ruta         | 2 Tarea Flujo De Datos| String      | C:\SQL Service Integration Services\ |                                               | 
    |FechaSistema | 2 Tarea Flujo De Datos| String      | Fecha es automatica                  | `SUBSTRING( (DT_WSTR, 90)  GETDATE(), 1, 10 )`|
* Seleccionamos **Reporte Cliente**, el cual se encuentra ubicado en el panel de administracion de conexiones.
* Damos click derecho sobre dicha conexión y seleccionamos propiedades.
* Seleccionamos en el panel de propiedades el apartado de **Expressions**.
* Le asignamos como propiedad **'ConnectionString'** y como Expresión: `@[User::Ruta]+ @[User::NombreArchivo]+ @[User::FechaSistema]+".txt"`


#### **Resultado Final:**

<div style="text-align: center">

![Resultado Final - Origen y Destino](https://raw.githubusercontent.com/Andres25b/SSIS/master/Anexos/2.2-OrigenyDestino.png "Resultado Final - Conexion del origen y el destino")

"Resultado Final - Conexion del origen y el destino"

</div>