# Práctica 4.4 – Bot "¿Reparo o compro?"

**Instituto Tecnológico de Mazatlán** · Ingeniería en Sistemas Computacionales
**Asignatura:** Desarrollo Sustentable (ACD-0908) · **Unidad 4:** Escenario económico
**Tema:** 4.4 Obsolescencia planificada y percibida
**Alumno:** Christian Paul Lizárraga Oronia
**Profesor:** Miguel Ángel Barrón Hernández

---

## 🤖 Bot

Bot de Telegram: **Reparo o Compro Equipo #** ([@ReparoCompro_Christian_bot](https://t.me/ReparoCompro_Christian_bot))
Escenario de Make: **Reparo_Compro_Equipo#**

---

## Objetivo

Distinguir la obsolescencia planificada de la percibida en casos reales, valorar la reparación como alternativa de consumo y verificar con información real las recomendaciones de una IA.

## ¿Cómo funciona?

```
Usuario en Telegram: "laptop de 5 años que se calienta y se apaga"
   │
   ▼
Telegram Bot: Watch Updates
   │  Filtro "Solo texto, sin comandos": el texto existe y no empieza con /
   ▼
Make AI Agent (asesor de reparación)
   │
   ▼
Telegram Bot: Send a Text Message or a Reply → respuesta con causa probable,
tipo de obsolescencia, costos aproximados, impacto y recomendación
```

El bot responde si conviene **REPARAR**, **REEMPLAZAR** o **DONAR O RECICLAR**, con rangos de costo en pesos mexicanos. El filtro evita gastar créditos con stickers, fotos o comandos como `/start`.

## Tecnologías

- Telegram (BotFather)
- Make: Telegram Bot (Watch Updates, Send a Text Message or a Reply), Make AI Agent

## Estructura del repositorio

| Carpeta | Contenido |
|---------|-----------|
| `Código/` | `Reparo_Compro_Equipo#.blueprint.json` (blueprint exportado de Make) y `configuracion_make.md` (módulos, filtro e instrucciones de la IA) |
| `Imágenes/` | Capturas del escenario, del historial, de las 6 respuestas del bot y de los precios oficiales consultados |
| `Video/` | `enlace.txt` con el enlace al video en YouTube |
| `Resultados/` | Informe en PDF con investigación, tabla de casos y preguntas |

> El token del bot no está en este repositorio por seguridad.

## Resultados

Casos enviados al bot el 11 de noviembre de 2026:

| # | Aparato y falla | Recomendación de la IA | Costo según la IA | Precio real consultado |
|---|-----------------|------------------------|-------------------|------------------------|
| 1 | iPhone 11 de 5 años, batería al 74 % | REPARAR (batería) | $2,500 – $5,000 | $1,949 + IVA (Apple México) |
| 2 | Huawei Y9 2019 de 6 años, se apaga al 20 % | REPARAR (batería) | $1,000 – $2,500 | $299 – $359 (Huawei México) |
| 3 | Laptop HP 15 de 5 años, se calienta y se apaga | REPARAR (limpieza y pasta térmica) | $1,500 – $5,000 | — |
| 4 | Licuadora Oster de 8 años, las cuchillas no giran | REEMPLAZAR | $1,500 – $5,000 | — |
| 5 | Ventilador de pedestal de 4 años, gira lento | REPARAR (capacitor o motor) | $500 – $1,500 | — |
| 6 | Control de Xbox de 4 años, drift en el joystick | REPARAR (cambio del stick) | $500 – $1,500 | — |

- **5 de 6** aparatos tenían reparación; solo la licuadora se recomendó reemplazar.
- En los dos casos comparados con precios oficiales, la IA **acertó en reparar** pero **sobrestimó el costo** (en el Huawei, de 3 a 7 veces).
- Las fuentes de los precios son [Apple México](https://support.apple.com/es-mx/iphone/repair/battery-replacement) y [Huawei México](https://consumer.huawei.com/mx/support/battery-service/), consultadas el 11/11/2026.

El informe completo está en [`Resultados/`](Resultados/).

## Preguntas de reflexión

**1. ¿Cuántos de los 6 aparatos tenían reparación? ¿Cuántos se habrían desechado sin necesidad?**

De los 6 aparatos que probamos, **5** tenían reparación según el bot (los dos celulares, la laptop, el ventilador y el control) y solo **1**, la licuadora, se recomendaba reemplazar. Eso significa que **5** aparatos se habrían tirado sin necesidad si hubiéramos comprado uno nuevo sin preguntar. Las fallas más comunes, como una batería que dura poco, un cable o un botón dañado, tienen arreglos relativamente baratos comparados con el precio de un aparato nuevo. Esto muestra que muchas veces el problema no es que el aparato ya no sirva, sino que no sabemos que se puede reparar ni dónde hacerlo.

**2. ¿Qué tan cercanas fueron las estimaciones de la IA a las cotizaciones reales? ¿Por qué creen que difieren?**

No fueron muy cercanas: en los dos casos la IA **sobrestimó** el costo. Para el iPhone 11 calculó entre $2,500 y $5,000, y el precio oficial de Apple es $1,949 más IVA (unos $2,261), por debajo de su rango. Para el Huawei Y9 2019 calculó entre $1,000 y $2,500, pero Huawei México cobra entre $299 y $359 en sus centros autorizados, es decir, de 3 a 7 veces menos. Aun así, la recomendación (reparar) sí fue correcta en ambos casos. Las estimaciones de la IA sirven como referencia, pero no son exactas, porque la IA no conoce los precios actuales de las refacciones en Mazatlán ni el costo de la mano de obra de cada taller. Además, el precio depende de la marca y el modelo exacto, de si la pieza es original o genérica, y de que el técnico revise el aparato y encuentre otra falla. Por eso el bot aclara que sus costos son aproximados y que conviene pedir una cotización.

**3. ¿Qué casos fueron de obsolescencia planificada y cuáles de percibida?**

La IA clasificó casi todo como obsolescencia percibida y el ventilador como ninguna. Nosotros lo vemos distinto: el **iPhone 11** tiene algo de obsolescencia planificada, porque la batería viene sellada y el usuario no la puede cambiar, y en 2018 Apple fue multada en Italia por actualizaciones que hacían más lentos los teléfonos viejos [2]. El **control de Xbox** también es discutible, porque el drift es una falla tan común que Microsoft enfrentó una demanda colectiva en Estados Unidos por esa causa [9]. El Huawei, la laptop, la licuadora y el ventilador no muestran obsolescencia: su falla viene del desgaste normal, del polvo o de una pieza gastada. Ninguno de los 6 fue un caso de obsolescencia percibida, porque en todos había una falla real y no solo el deseo de tener un modelo nuevo. En general, consideramos planificada la obsolescencia cuando el aparato falla por diseño: baterías que no se pueden cambiar, piezas pegadas, actualizaciones que vuelven lento el equipo o falta de refacciones. Fue percibida cuando el aparato todavía funcionaba bien o tenía una falla menor, pero el dueño quería cambiarlo porque ya se veía viejo o había un modelo nuevo. También hubo casos sin obsolescencia, por ejemplo cuando la falla se debía a un golpe o al desgaste normal de muchos años de uso.

**4. ¿Qué impide que más personas reparen sus aparatos (costo, falta de talleres, diseño del producto)?**

Lo que más lo impide es el diseño del producto: muchos aparatos vienen pegados con adhesivos, usan tornillos especiales o tienen la batería soldada, y los fabricantes no venden piezas ni manuales. Otro factor es el costo: cuando un aparato nuevo y barato cuesta casi lo mismo que la reparación, la gente prefiere comprarlo. También influye la falta de información, porque muchas personas no saben qué talleres hay ni si pueden confiar en ellos, y temen perder la garantía. Por último, la publicidad y la costumbre de “usar y tirar” hacen que reparar se vea como algo pasado de moda.

**5. ¿Qué alternativas proponen para cambiar las pautas de consumo de su familia?**

Proponemos que, antes de tirar un aparato, en casa primero se revise si tiene reparación, usando el bot o preguntando en un taller de la colonia. También daremos mantenimiento a los aparatos que ya tenemos, como limpiar el ventilador de la laptop, cuidar la carga de la batería y usar fundas. Al comprar algo nuevo, elegiremos marcas que vendan refacciones y tengan garantía más larga, y no cambiaremos de celular solo porque salió un modelo nuevo. Los aparatos que ya no sirvan los llevaremos a un centro de acopio de residuos electrónicos o los donaremos si todavía funcionan, en lugar de tirarlos a la basura.
