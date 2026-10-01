# iXaio · Prototipo web

Abre `index.html` en tu navegador. Todo el diseño y los controles están en ese archivo, sin instalación ni dependencias externas. También puedes servir la carpeta con `python -m http.server 8000`.

## Logo y fotografía

1. Copia el logo a `assets/logo.png` y la fotografía a `assets/israel.jpg`.
2. En `index.html`, busca `const CONFIG` y cambia:

```js
logo: 'assets/logo.png',
portrait: 'assets/israel.jpg',
```

Puedes utilizar otros nombres o extensiones: ajusta las rutas. El logo debería tener fondo transparente; la foto puede ser vertical. Si una imagen falta, permanece la composición de reemplazo.

## Servicios y precios

Busca `const SERVICES`. Cada entrada contiene nombre, duración, precio, modalidades, descripción y detalles. Los precios son CLP sin separadores (23000). Estos datos alimentan tanto las tarjetas como el selector de consulta. Las tarifas corporales recibidas corresponden a Lo Prado: en Providencia se pide confirmación. El seguimiento no tiene duración definida todavía.

No publicar acreditación MINSAL hasta contar con el documento y verificar su alcance. `CONFIG.credential` está pendiente y no se muestra. Las cifras de personas atendidas tampoco se muestran hasta definir período, fuente y personas únicas. No hay testimonios inventados ni logos institucionales.

## Agenda: conexión pendiente

El prototipo NO reserva, bloquea horarios, envía correos ni mensajes automáticamente. WhatsApp abre un borrador que el visitante envía voluntariamente. No se recogen datos en el sitio ni se almacenan consultas en el navegador.

1. Crear una cuenta de agenda propiedad de Israel y un calendario dedicado en Google Calendar u Outlook.
2. Probar Cal.com individual gratuito. Revisar funciones disponibles al configurar, especialmente aprobación, correo de respuesta y avisos. No se garantiza que los correos automáticos permanezcan en una única cadena.
3. Crear eventos por servicio/sede, con un único calendario de conflictos. No ofrecer acupuntura online.
4. Resolver el solapamiento: Lo Prado lunes a sábado 10–18; Providencia lunes, miércoles y jueves 10–15; solidaria martes 10–17 en Lo Prado. Un mismo terapeuta no puede tener esas disponibilidades simultáneas. Asignar bloques efectivos por sede, incluir traslado, preparación y pausas. El martes solidario debe descontarse de la disponibilidad ordinaria.
5. Definir duración del seguimiento, anticipación mínima, límite diario y plazos de solicitudes pendientes. Probar si una solicitud pendiente bloquea efectivamente el cupo y cómo se libera.
6. Acordar monto/porcentaje de abono y plazo para pagar. No se han inventado datos bancarios, porcentajes ni políticas de inasistencia.
7. Completar `CONFIG.calendarLinks`, por ejemplo:

```js
calendarLinks: {
  'acupuntura|Lo Prado': 'https://cal.com/TU-USUARIO/TU-EVENTO',
  'tarot-foco|Online': 'https://cal.com/TU-USUARIO/OTRO-EVENTO'
},
```

El botón de agenda aparecerá solamente para combinaciones configuradas. Los enlaces son externos; este prototipo no incluye un calendario ficticio. Una futura inserción del calendario puede implementarse tras disponer de enlaces y reglas verificadas.

## Flujo operativo a validar

Solicitud → condiciones y pago acordados → comprobante por correo → revisión de transferencia por Israel → confirmación → recordatorio → atención realizada.

No confirmar por la mera recepción de un comprobante. Verificar ingreso efectivo. Asegurar que las solicitudes vencidas o rechazadas liberen el cupo y que los recordatorios solo se envíen a reservas confirmadas. Para pagos online falta aclarar cuánto debe estar pagado antes de comenzar: el saldo presencial no aplica a una sesión totalmente online.

El sitio recoge la política informada de 24 horas y descuento del atraso. Las excepciones se conversan con Israel. Los pagos por tarjeta e internacionales no se anuncian como integraciones operativas del sitio.

WhatsApp automático tres horas antes queda pendiente de proveedor, consentimiento, plantilla y costos. Un enlace WhatsApp no equivale a automatización. Empezar con recordatorio humano si no hay integración. La web no ha creado cuentas ni enviado comunicaciones.

## Publicación

Se puede mantener el código en GitHub. Elegir alojamiento apto para una web comercial y revisar el plan vigente antes de publicar. GitHub Pages restringe sitios destinados principalmente a facilitar transacciones comerciales: https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits

Sin dominio propio se puede usar el subdominio del alojamiento elegido. Esta entrega es local; no se ha publicado.

## Registro de actividad

`registro_actividad.csv` es una plantilla vacía para registros administrativos privados. Nunca subir registros reales al repositorio web. Un ID de persona pseudónimo sigue requiriendo resguardo. Usar un único ID interno para contar personas únicas y un ID de solicitud para seguir el flujo. No ingresar diagnósticos, identidad de género, datos de nacimiento ni situación económica en la tabla administrativa.

Estados propuestos: consulta, cotizada, pendiente_pago, pendiente_revision, confirmada, realizada, cancelada, reprogramada, inasistencia, rechazada, vencida. Definir denominadores y períodos antes de calcular conversiones; solicitudes y sesiones son unidades diferentes. Continuidad requiere fijar un período de seguimiento. No interpretar satisfacción como eficacia clínica.

## Pendientes de contenido

- Certificado y formación verificable; permiso para mencionar colaboraciones con Tao Vital y Acupuntura Hoy.
- Logo, retrato y fotos reales de los espacios.
- Accesibilidad física por sede.
- Tarifas de Providencia y comuna/recargo de domicilio.
- Reiki independiente, si se desea incluir.
- Consentimiento separado para audio y publicación de testimonios.
- Revisar la encuesta actual; no pudo leerse desde el enlace disponible.

El diseño es adaptable a móvil, con contraste alto, foco de teclado, filtros con estado accesible y detalles nativos. La sintaxis JavaScript, las anclas HTML y las interacciones se comprobaron con Node y JSDOM: filtros, selector, modalidades, enlaces de WhatsApp, cotización y agenda pendiente. La revisión visual con navegador quedó pendiente porque no se pudo instalar Chromium en este entorno.
