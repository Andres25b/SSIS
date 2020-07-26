# Execute SQL Task

### **Descripción:**

<div style="text-align: justify">
La tarea Ejecutar SQL es uno de los componentes más útiles en los Servicios de Integración de SQL Server (SSIS) porque le permite ejecutar instrucciones Transact-SQL desde su flujo de control.
<div/>

<div style="text-align: justify">
La tarea es especialmente útil para devolver conjuntos de resultados que luego pueden ser utilizados por otros componentes en su paquete SSIS.  
<div/>

---

### **Ejercicios:**

1. Actualiza el Country de la tabla Customers a partir del CustomerID con el valor **'ALFKI'**.

    * Arrastramos al flujo de control la herramienta **'Tarea ejecutar SQL'**.
    * Hacemos doble click  para ver sus propiedades.
    * Asignamos el ResultSet a **Ninguno**.
    * Asignamos el tipo de conexion a **OLE DB**.
    * Asignamos la conexion. En el caso de no tener una conexion la creamos.
        * Para crear una conexion damos click en **nueva conexion**.
        * Asignamos el tipo de provedor, en este caso elegimos **OLE DB nativo\SQL Server Native Client 11.0**
        * Asignamos el Nombre del Servidor.
        * Elegimos el tipo de Autenticación.
        * Seleccionamos el nombre de la base de datos.
        * Probamos que la conexion se correcta.
    * Escibimos la sentencia SQL. En este caso seria: `UPDATE Customers SET Country = 'France' WHERE CustomerID = 'ALFKI';`.

2. Obtener el CustomerID de la tabla Customers,  donde el valor Country sea igual a **'France'** y el valor de  ContactName sea igual a **'Maria Anders'**.

    * Creamos una nueva variable con el **nombre: CustumerID**, **Tipo de dato: String**.
    * Arrastramos al flujo de control la herramienta **'Tarea ejecutar SQL'**.
    * Hacemos doble click  para ver sus propiedades.
    * Asignamos el ResultSet a **Fila Unica**.
    * Asignamos el tipo de conexion a **OLE DB**.
    * Asignamos la conexion. En el caso de no tener una conexion la creamos.
        * Para crear una conexion damos click en **nueva conexion**.
        * Asignamos el tipo de provedor, en este caso elegimos **OLE DB nativo\SQL Server Native Client 11.0**
        * Asignamos el Nombre del Servidor.
        * Elegimos el tipo de Autenticación.
        * Seleccionamos el nombre de la base de datos.
        * Probamos que la conexion se correcta.
    * Escibimos la sentencia SQL. En este caso seria: `SELECT customerID FROM Customers WHERE ContactName = 'Maria Anders' AND Country = 'France';`.
    * Nos dirigimos a la pestaña **Conjunto de resultados**.
    * Damos Click en agregar para que se asigne la variable antes creada y como nombre de resultado escribimos el valor de 0.
    
3. Actualiza de la tabla Customers, el Contry asignandole el valor de **'Francia'** a partir del CustomerID obtenido en el **paso 2**.

    * Arrastramos al flujo de control la herramienta **'Tarea ejecutar SQL'**.
        * Hacemos doble click  para ver sus propiedades.
        * Asignamos el ResultSet a **Ninguno**.
        * Asignamos el tipo de conexion a **OLE DB**.
        * Asignamos la conexion. En el caso de no tener una conexion la creamos.
            * Para crear una conexion damos click en **nueva conexion**.
            * Asignamos el tipo de provedor, en este caso elegimos **OLE DB nativo\SQL Server Native Client 11.0**
            * Asignamos el Nombre del Servidor.
            * Elegimos el tipo de Autenticación.
            * Seleccionamos el nombre de la base de datos.
            * Probamos que la conexion se correcta.
        * Escibimos la sentencia SQL. En este caso seria: `UPDATE Customers SET Country = 'Francia' WHERE CustomerID = ?;`.
        * Nos dirigimos a la pestaña **Asignación de parámetros**.
        * Damos click en agregar.
        * Selecionamos la variable que creamos anteriormente, con **Direccion: Input**, **tipo de dato: NVARCHAR**, **Nombre del parametro: 0**.

### **Resultado Final:**

<div style="text-align: center">

![Resultado Final - Tarea Ejecutar SQL](https://raw.githubusercontent.com/Andres25b/SSIS/master/Anexos/1.-TareaEjecutarSQL.png) "Resultado Final - Tarea Ejecutar SQL"

</div>





