# Configuración del escenario en Make: `Reparo_Compro_Equipo#`

Flujo: **Telegram (Watch Updates) → Filtro → Make AI Agent → Telegram (respuesta)**

## 1. Crear el bot

1. En Telegram abrir **@BotFather**, enviar `/newbot` y nombrarlo **Reparo o Compro Equipo #**.
2. Copiar el token.

> ⚠️ El token es la llave del bot. No se comparte ni se sube a GitHub.

## 2. Módulos

| # | Módulo | Configuración |
|---|--------|---------------|
| 1 | Telegram Bot → Watch Updates | Crear la conexión con el token y guardar el webhook. Vincular el bot abriendo en el navegador la URL de `setWebhook` (igual que en la práctica del chatbot de Gobernanza). |
| — | Filtro (entre 1 y 2) | `Message → Text` *Exists* **y** `Message → Text` *Does not start with* `/`. Así no se gastan créditos con stickers, fotos o comandos. |
| 2 | Make AI Agent | Connection: Make's AI Provider (créditos del plan Pro, sin API key). Input: `Aparato y falla: {{1.message.text}}` (mapear desde el panel). Instructions: ver abajo. |
| 3 | Telegram Bot → Send a Text Message or a Reply | Chat ID: `Message → Chat → ID` (del Watch Updates). Text: la respuesta del AI Agent. |

Guardar y activar el escenario (**ON**).

### Formato de la URL de setWebhook

```
https://api.telegram.org/botTOKEN/setWebhook?url=URL_DEL_WEBHOOK_DE_MAKE
```

Cambiar `TOKEN` por el token del bot y `URL_DEL_WEBHOOK_DE_MAKE` por la dirección que muestra el módulo Watch Updates.

## 3. Instructions del AI Agent

```
Eres un asesor de reparacion de aparatos para alumnos de Desarrollo Sustentable del TecNM en Mazatlan, Sinaloa.
El usuario describe un aparato y su falla. Responde en texto plano (sin asteriscos, sin markdown), en espanol, con este formato:

Aparato: [que es]
Causa probable: [1 linea]
Tipo de obsolescencia: [planificada / percibida / ninguna, con 1 linea de explicacion]
¿Tiene reparacion?: [si / no / depende]
Costo aproximado de reparacion: [rango en pesos mexicanos]
Costo aproximado de uno nuevo: [rango en pesos mexicanos]
Impacto si se desecha: [materiales que contiene y por que contamina]
RECOMENDACION: [REPARAR / REEMPLAZAR / DONAR O RECICLAR, con 1 linea de razon]
Que hacer: [donde repararlo o a donde llevarlo si se desecha]

Aclara que los costos son aproximados y que conviene pedir una cotizacion.
Si el mensaje no describe un aparato con falla, responde: "Describe el aparato y su falla, por ejemplo: laptop de 4 años que se calienta y se apaga."
```

## 4. Mensajes de prueba sugeridos

Usa aparatos **reales** (tuyos, de tu familia o vecinos). Ejemplos del tipo de descripción que entiende el bot:

1. Celular de 3 años, la batería dura menos de medio día y se apaga solo.
2. Laptop de 5 años que se calienta mucho y se apaga cuando abro varias pestañas.
3. Licuadora que hace ruido pero las cuchillas ya no giran.
4. Ventilador de pedestal que gira muy lento aunque lo pongo en el 3.
5. Audífonos inalámbricos: el lado izquierdo ya no suena.
6. Control de consola que se mueve solo (drift en el joystick).
