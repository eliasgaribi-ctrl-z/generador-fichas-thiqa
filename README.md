<div align="center">

# 🏠 Generador de Fichas THIQA

**Crea fichas imprimibles (PDF) de casas en recuperación directo desde un Excel — sin instalar nada.**

[![Ver la app en vivo](https://img.shields.io/badge/%E2%96%B6%20Ver%20la%20app-en%20vivo-1E4A72?style=for-the-badge)](https://eliasgaribi-ctrl-z.github.io/generador-fichas-thiqa/)
![Estático](https://img.shields.io/badge/100%25-est%C3%A1tico-F07E22?style=for-the-badge)
![Sin instalación](https://img.shields.io/badge/sin-instalaci%C3%B3n-1E4A72?style=for-the-badge)

</div>

---


<div align="center">
<img src="docs/screenshot.png" alt="Vista previa del Generador de Fichas THIQA" width="800">
</div>

## ¿Qué hace?

Este proyecto es una sola página web (`index.html`) que lee un archivo Excel con el listado de domicilios y genera, para cada uno, una **ficha lista para imprimir o guardar como PDF**: dirección, datos de la cartera, folio, y demás información de seguimiento.

No requiere servidor, cuenta ni instalación — se abre directo en el navegador.

## 🚀 Usar la app

1. Entra a **[eliasgaribi-ctrl-z.github.io/generador-fichas-thiqa](https://eliasgaribi-ctrl-z.github.io/generador-fichas-thiqa/)**
2. Sube tu archivo Excel con el listado de domicilios.
3. Revisa el empate de columnas que la app propone (el paso 3 marca en naranja lo que reconoció).
4. Elige la casa o casas que quieras y genera su ficha.
5. Imprime o guarda como PDF desde el navegador (`Ctrl/Cmd + P`).

## ✨ Características

- **Un solo archivo** (`index.html`) — no depende de librerías externas ni de instalación.
- **Lee Excel directamente** en el navegador, sin subir datos a ningún servidor.
- **Encuentra sola la hoja y la fila de encabezados**: de un libro con varias pestañas
  (respaldos, catálogos, instrucciones) abre la que trae los domicilios, aunque el
  encabezado no esté en la primera fila.
- **Empata las columnas automáticamente** contra los campos de la ficha, y recuerda las
  correcciones que hagas para la próxima vez.
- **Conserva las ligas del Sheet**: los enlaces de Google Maps y las carpetas de Drive que
  cuelgan de una celda quedan como enlaces vivos dentro del PDF.
- **Filtro por estatus de ruta**: como los líderes mueven el estatus desde la app de campo,
  cada estatus es una casilla que puedes apagar para dejarlo fuera de la corrida. Las casas
  ya **Recuperada** se descartan al leer el archivo y no llegan a la lista.
- **Liga de Google Maps en cada ficha**, sin costo y sin salir del navegador: se respeta la
  del Sheet cuando existe y, si no, se arma con el domicilio, colonia, C.P. y municipio.
- **Edición por domicilio** antes de generar la ficha final.
- **Exportación a PDF** usando la función de impresión del navegador.

## 🎙️ Dictar fichas sin Excel

En la pestaña **Dictar** hablas de corrido, incluso de varias casas seguidas —*“Boulevard
República de Honduras 134, Hacienda Santa Fe, Tlajomulco, cuadrilla de Teófilo, monto sesenta
mil, bono quinientos”*— y la IA separa cada domicilio y llena los campos de la ficha. Puedes
corregir el texto antes de crearlas, o escribirlo/pegarlo si tu navegador no dicta.

Las fichas dictadas se juntan con las del Excel: se filtran, se editan y se imprimen igual, y
entran con el estatus `Dictada` para distinguirlas. Quedan guardadas en el navegador aunque
cierres la página. El dictado por voz usa la API del navegador (Chrome o Edge).

## 🤖 IA opcional (tu propia API key)

Se usa para dos cosas: **convertir el dictado en campos de la ficha** y **desenredar las
direcciones que llegan pegadas** del tipo `AV BOGOTA275SANTA FE00630TLAJOMULCO DE ZUNIGA45653STMJL`.
Todo lo demás —incluida la liga de Maps— se resuelve sin IA, gratis y sin llamadas.

Como el proyecto es un archivo estático en GitHub Pages, **no existe un servidor donde
esconder una API key**: cualquier key en el código sería pública. Por eso la pones tú y se
guarda únicamente en el `localStorage` de tu navegador. Nunca hay una key en este repositorio.

Proveedores soportados, priorizando lo gratuito:

| Proveedor | Costo | Nota |
|---|---|---|
| **Google Gemini** | capa gratuita permanente | key en `aistudio.google.com/apikey`; tope por minuto |
| **OpenAI y compatibles** | según proveedor (Groq y OpenRouter tienen modelos gratis) | pones URL base y modelo |
| **Anthropic Claude** | de paga, centavos por corrida | único con llamada directa desde navegador verificada |

El botón **Probar mi key** hace una llamada mínima y dice de una vez si el proveedor la
acepta, sin tener que dictar algo primero. Como el campo se ve de contraseña, el navegador a
veces lo rellena solo con una contraseña guardada: por eso está el **ver** de al lado, y por
eso el encabezado de la tarjeta dice cuántos caracteres tiene la key que va a salir —una de
Google Gemini empieza con `AIza` y mide 39.

Qué sale del navegador, según la tarea:

- **Desenredar direcciones del Excel**: solo dirección, colonia, C.P., municipio y estado.
  Nunca el nombre del acreditado, el crédito, el expediente ni los montos.
- **Dictado**: el texto que dictaste, completo — de ahí salen los datos de la ficha.

Lo que la IA escriba queda marcado como edición tuya y se puede deshacer en bloque.

## 📋 Qué lleva la ficha

Encabezado (folio, cartera, ruta, orden de visita, estatus), domicilio completo
(calle, colonia, C.P., municipio, entidad y cómo llegar), acreditado, datos del expediente
(exp. judicial y digital, juzgado, etapa judicial, folio real, crédito, carta poder, predial),
fechas clave (asignación, desalojo, convenio), el desglose de dinero y las seis etapas de
seguimiento con sus firmas. Los campos que tu archivo no traiga salen como línea en blanco
para llenarse a mano.

## 🛠️ Uso local

Si prefieres correrlo en tu computadora en vez de usar la versión en línea:

```bash
git clone https://github.com/eliasgaribi-ctrl-z/generador-fichas-thiqa.git
cd generador-fichas-thiqa
```

Y abre `index.html` con cualquier navegador.

## 🏗️ Stack

HTML + CSS + JavaScript vanilla — sin frameworks, sin build step.

---

<div align="center">
<sub>Proyecto interno THIQA · Seguimiento de rutas y recuperación de casas</sub>
</div>
