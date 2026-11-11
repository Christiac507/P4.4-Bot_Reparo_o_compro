# Práctica 4.4 – Bot "¿Reparo o compro?"

**Instituto Tecnológico de Mazatlán** · Ingeniería en Sistemas Computacionales
**Asignatura:** Desarrollo Sustentable (ACD-0908) · **Unidad 4:** Escenario económico
**Tema:** 4.4 Obsolescencia planificada y percibida
**Alumno:** Christian Paul Lizárraga Oronia
**Profesor:** Miguel Ángel Barrón Hernández

---

## 🎥 Video

[▶ Ver el video de la práctica en YouTube](https://www.youtube.com/watch?v=PEGA_AQUI_EL_ID_DEL_VIDEO)

## 🤖 Bot

Bot de Telegram: **Reparo o Compro Equipo #**

---

## Objetivo

Distinguir la obsolescencia planificada de la percibida en casos reales, valorar la reparación como alternativa de consumo y verificar con información local las recomendaciones de una IA.

## ¿Cómo funciona?

```
Usuario en Telegram: "laptop de 4 años que se calienta y se apaga"
   │
   ▼
Telegram Bot: Watch Updates
   │  Filtro: el mensaje tiene texto y no empieza con /
   ▼
Make AI Agent (asesor de reparación)
   │
   ▼
Telegram Bot: Send a Text Message → respuesta con causa probable,
tipo de obsolescencia, costos aproximados, impacto y recomendación
```

El bot responde si conviene **REPARAR**, **REEMPLAZAR** o **DONAR O RECICLAR**, con un rango de costos en pesos mexicanos. Después, al menos 2 casos se verifican con un taller de reparación de Mazatlán.

## Tecnologías

- Telegram (BotFather)
- Make: Telegram Bot (Watch Updates, Send a Text Message or a Reply), Make AI Agent

## Estructura del repositorio

| Carpeta | Contenido |
|---------|-----------|
| `Código/` | `configuracion_make.md` (módulos, filtro e instrucciones de la IA) |
| `Imágenes/` | Capturas del escenario, del chat con el bot y de la cotización del taller |
| `Video/` | Video de la práctica (enlace arriba) |
| `Resultados/` | Informe en PDF con investigación, tabla de casos y preguntas |

> El token del bot no está en este repositorio por seguridad.

## Resultados

La tabla con los 6 aparatos, la recomendación de la IA, la cotización del taller y el tipo de obsolescencia está en [`Resultados/`](Resultados/).
