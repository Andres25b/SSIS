# Bulk Insert Task

### **Descripción:**

<div style="text-align: justify">

La tarea de inserción masiva proporciona una forma eficiente de copiar grandes cantidades de datos en una tabla o vista de SQL Server.

</div>

<div style="text-align: justify">

Para garantizar la copia de datos a alta velocidad, no se pueden realizar tranformaciones en los datos mientras se mueven del archivo de origen a la tabla o vista.

</div>

---

### **Ejercicio:**

<b>1.</b> Diariamente se necesita que se cargue un archivo csv que contiene millones de registros y de suma importancia que se realice la carga en el menor tiempo posible(Utilizando Bulk Insert). (**Nota:** Para fines practicos se realizara un TRUNCATE al inicio del proceso).

##### Configuración del proceso Truncate.

* Arrastramos al flujo de control la herramienta **'Tarea Ejecutar SQL'**.
* Hacemos doble click  para ver sus propiedades.
* Asignamos el ResultSet a **Ninguno**.
* Asignamos el tipo de conexión a **OLE DB**.
* Asignamos la conexión. En el caso de no tener una conexión la creamos.
    * Para crear una conexión damos click en **nueva conexión**.
    * Asignamos el tipo de proveedor, en este caso elegimos **OLE DB nativo\SQL Server Native Client 11.0**
    * Asignamos el Nombre del Servidor.
    * Elegimos el tipo de Autenticación.
    * Seleccionamos el nombre de la base de datos.
    * Probamos que la conexión se correcta.
* Escribimos la sentencia SQL. En este caso seria: `TRUNCATE TABLE Cliente;`.

##### Configuración del Bulk.

* Arrastramos al flujo de control la herramienta **'Tarea Inserción masiva'**.
* Hacemos doble click  para ver sus propiedades.
* Nos dirigimos a la pestaña **Conexión**.
* Configuramos la conexión de destino.
* Configuramos la conexión de origen.
* Modificamos el ColumnDekimiter segun sea necesario.
* Nos dirigimos a la pestaña **Opciones** y configuramos el FirtRow para indicar el inicio de los datos.

#### **Resultado Final:**

<div style="text-align: center">

![Resultado Final - Bulk Insert Task](https://raw.githubusercontent.com/Andres25b/SSIS/master/Anexos/4.-BulkInsertTask.png "Resultado Final - Bulk Insert Task")

"Resultado Final - Bulk Insert Task"

</div>

