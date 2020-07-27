# Send Mail Task

### **Descripción:**

<div style="text-align: justify">

La tarea Enviar correi envía un mensaje de correo electrónico. Al usar la tarea Enviar correo, un paquete puede enviar mensajes si las tareas en el flujo de trabajo del paquete tienen exito o fallan, o enviar mensajes en respuesta a un evento que el paquete genera en tiempo de ejecución, Por  ejemplo, la tarea puede notificar a un administrador de base de datos sobre  el éxito o el fracaso de la tarea Copia de seguridad de la base de datos.

</div>

---

### **Ejercicio:**

<b>1.</b> Se necesita que el proceso automatizado envíe un correo electrónico donde especifique si el proceso finalizo correctamente o si finalizo en error.

**NOTA:** Para este ejercicio ocuparemos el [pakage 6.-Send Mail Task(Tarea Sistema de arvivos)](https://github.com/Andres25b/SSIS)

##### Crear scrip E-mail correcto

* Arrastramos al flujo de control la herramienta **'Tarea Script'**.
* Hacemos doble click para ver sus propiedades.
* Editamos el Script:

        --Librerias a importar
        using System.Net;
        using System.Net.Mail;

        --Código para enviar correo electrónico
        String emailOrigen = "andres24b.ha@gmail.com";
        String emailDestino = "andres24b.ha@gmail.com";
        String contrasena = "15106077b";

        MailMessage oMailMessage = new MailMessage();

        oMailMessage.From = new MailAddress(emailOrigen);

        foreach (var address in emailDestino.Split(new[] { ";" }, StringSplitOptions.RemoveEmptyEntries))
        {
            oMailMessage.To.Add(emailDestino);
        }

        oMailMessage.Subject = "PROCESO EXITOSO";
        oMailMessage.Body = "<p>El proceso termino correctamente</p>";
            oMailMessage.IsBodyHtml = true;

        SmtpClient oSmtpClient = new SmtpClient("smtp.gmail.com");
        oSmtpClient.EnableSsl = true;
        oSmtpClient.UseDefaultCredentials = false;
        // oSmtpClient.Host = "smtp.gmail.com";
        oSmtpClient.Port = 587;
        oSmtpClient.Credentials = new NetworkCredential(emailOrigen, contrasena);

        oSmtpClient.Send(oMailMessage);
        oSmtpClient.Dispose();
        
##### Crear scrip E-mail correcto

* Arrastramos al flujo de control la herramienta **'Tarea Script'**.
* Hacemos doble click para ver sus propiedades.
* Editamos el Script:

        --Librerias a importar
        using System.Net;
        using System.Net.Mail;

        --Código para enviar correo electrónico
        String emailOrigen = "andres24b.ha@gmail.com";
        String emailDestino = "andres24b.ha@gmail.com";
        String contrasena = "15106077b";

        MailMessage oMailMessage = new MailMessage();

        oMailMessage.From = new MailAddress(emailOrigen);

        foreach (var address in emailDestino.Split(new[] { ";" }, StringSplitOptions.RemoveEmptyEntries))
        {
            oMailMessage.To.Add(emailDestino);
        }

        oMailMessage.Subject = "PROCESO ERROR";
        oMailMessage.Body = "<p>El proceso termino con errores</p>";
        oMailMessage.IsBodyHtml = true;

        SmtpClient oSmtpClient = new SmtpClient("smtp.gmail.com");
        oSmtpClient.EnableSsl = true;
        oSmtpClient.UseDefaultCredentials = false;
        // oSmtpClient.Host = "smtp.gmail.com";
        oSmtpClient.Port = 587;
        oSmtpClient.Credentials = new NetworkCredential(emailOrigen, contrasena);

        oSmtpClient.Send(oMailMessage);
        oSmtpClient.Dispose();


#### **Resultado Final:**

<div style="text-align: center">

![Resultado Final - Send Mail Task](https://raw.githubusercontent.com/Andres25b/SSIS/master/Anexos/8.-TareaEnviarCorreo.png "Resultado Final - Send Mail Task")

"Resultado Final - Send Mail Task"

</div>