# Configuración de EmailJS para Joch Transportes

## 📧 Configuración del Envío de Emails

Para que el formulario de contacto envíe emails a `chavezjose251100@gmail.com`, necesitas configurar EmailJS siguiendo estos pasos:

### 1. Crear cuenta en EmailJS
1. Ve a [EmailJS.com](https://www.emailjs.com/)
2. Regístrate para una cuenta gratuita
3. Verifica tu email

### 2. Configurar el Servicio de Email
1. En el dashboard de EmailJS, ve a "Email Services"
2. Haz clic en "Add New Service"
3. Selecciona "Gmail" o "Outlook" (recomendado Gmail)
4. Conecta tu cuenta de email (puede ser la misma: chavezjose251100@gmail.com)
5. Guarda el servicio y copia el **Service ID**

### 3. Crear Template de Email
1. Ve a "Email Templates"
2. Haz clic en "Create New Template"
3. Usa este template:

```html
Nuevo mensaje de contacto desde Joch Transportes

Nombre: {{from_name}}
Email: {{from_email}}
Teléfono: {{from_phone}}
Servicio solicitado: {{service}}

Mensaje:
{{message}}

---
Este mensaje fue enviado desde el formulario de contacto de Joch Transportes.
```

4. Guarda el template y copia el **Template ID**

### 4. Obtener la Clave Pública
1. Ve a "Account" → "API Keys"
2. Copia tu **Public Key**

### 5. Actualizar el Código
Reemplaza en el archivo `script.js` las siguientes líneas:

```javascript
// Línea 6: Reemplaza YOUR_PUBLIC_KEY
emailjs.init("TU_CLAVE_PUBLICA_AQUI");

// Línea 47: Reemplaza YOUR_SERVICE_ID y YOUR_TEMPLATE_ID
emailjs.send('TU_SERVICE_ID', 'TU_TEMPLATE_ID', templateParams)
```

### Ejemplo de configuración completa:
```javascript
// Initialize EmailJS
(function() {
    emailjs.init("user_abc123def456"); // Tu clave pública
})();

// En el envío del email:
emailjs.send('service_xyz789', 'template_contact', templateParams)
```

## 🔧 Configuración Alternativa (Sin EmailJS)

Si prefieres no usar EmailJS, puedes usar otras opciones:

### Opción 1: Formspree
1. Ve a [Formspree.io](https://formspree.io/)
2. Crea una cuenta gratuita
3. Crea un nuevo formulario
4. Reemplaza el `<form>` en el HTML con:

```html
<form action="https://formspree.io/f/TU_FORM_ID" method="POST" class="contact-form">
    <!-- mismos campos -->
</form>
```

### Opción 2: Netlify Forms
Si subes el sitio a Netlify, puedes usar sus formularios nativos agregando `netlify` al form:

```html
<form class="contact-form" netlify>
    <!-- mismos campos -->
</form>
```

## 📱 Prueba del Formulario

Una vez configurado:
1. Abre el sitio web
2. Ve a la sección de contacto
3. Llena el formulario
4. Envía el mensaje
5. Verifica que recibas el email en `chavezjose251100@gmail.com`

## ⚠️ Notas Importantes

- **Cuenta gratuita de EmailJS**: Permite 200 emails por mes
- **Spam**: Los emails pueden ir a spam inicialmente
- **Verificación**: Asegúrate de verificar tu cuenta de email
- **Pruebas**: Siempre prueba el formulario antes de publicar

## 🆘 Soporte

Si tienes problemas con la configuración:
1. Revisa la consola del navegador para errores
2. Verifica que las claves sean correctas
3. Asegúrate de que el servicio de email esté conectado
4. Consulta la documentación de EmailJS

