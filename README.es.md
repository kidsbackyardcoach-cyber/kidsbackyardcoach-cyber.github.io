# Backyard Coach — Entrenador de Patio

[English](README.md) · [中文](README.zh.md) · **Español**

**Planes de práctica de 12 semanas para papás y mamás que entrenan fútbol, t-ball, flag football y básquetbol a niños de 3 a 5 años — aunque nunca hayas jugado el deporte.**

Disponible en inglés, 中文 (chino simplificado) y español.

[**→ Abrir la app**](https://kidsbackyardcoach-cyber.github.io/)

---

## Qué es esto

Casi todos los recursos de deporte infantil dan por hecho dos cosas: que ya conoces el deporte y que ya sabes dirigir una sesión. Esta app no asume ninguna de las dos. Responde las dos preguntas que un papá realmente tiene un sábado por la mañana:

1. **¿Qué compro?** — listas por prioridad, con precios aproximados y una lista explícita de "esto todavía no lo compres"
2. **¿Qué hacemos exactamente los próximos 25 minutos?** — una temporada completa de sesiones, con cronómetro

Todo está construido alrededor de una sola restricción: **la atención de un niño de cuatro años dura entre dos y cinco minutos por actividad.** Cada decisión de diseño sale de ahí.

---

## Qué incluye

| | |
|---|---|
| **Básicos del deporte** | ¿Nunca jugaste? Cada deporte tiene una explicación en lenguaje sencillo con diagramas — el campo, cómo funciona un partido, cómo se anota, las reglas que importan y ocho palabras que vas a oír. Más una descripción honesta de cómo se ve el juego de verdad a los 4 años. |
| **Temporadas de 12 semanas** | Cuatro deportes. Dos sesiones de 25 minutos por semana, en cuatro fases, desde el primer toque hasta un partido reducido real. Cada semana tiene un enfoque y una meta concreta que observar. |
| **56 ejercicios** | Cada uno trae montaje, cómo se juega, la frase exacta que decir y cómo hacerlo más fácil o más difícil sobre la marcha. |
| **Cronómetro de práctica** | Modo de pantalla completa con un reloj legible a un brazo de distancia bajo el sol. |
| **Listas de equipo** | Tres niveles de prioridad, ilustraciones dibujadas, total del presupuesto en vivo y una lista de lo que *no* comprar. |
| **Kit de movimiento** | Juegos opcionales de escalera, vallas y conos que se intercambian en el calentamiento de cualquier semana. |
| **Guía para entrenar** | Ocho reglas, expectativas de desarrollo y soluciones para el que se va, el que colapsa y el que domina a todos. |
| **Seguimiento** | Marca las sesiones hechas; el progreso se guarda en tu navegador. |

---

## Los principios detrás de todo esto

Estos sostienen el resto. Si cambias el contenido, consérvalos:

- **25 minutos en total.** Una práctica corta que sigue divertida vale más que una hora que se desmorona.
- **Un balón por niño.** Dos niños compartiendo un balón significa un niño tocando el balón.
- **Sin filas, sin vueltas, sin sermones.** Un niño formado en una fila es un niño que no está practicando.
- **Juegos, no ejercicios.** La misma habilidad con otra envoltura — a esta edad solo una de las dos funciona.
- **Nadie se queda fuera nunca.** Los juegos de eliminación producen un niño llorando y una práctica arruinada. Aquí cada juego está diseñado para que ser atrapado signifique volver a entrar de inmediato.
- **Termina cuando todavía quieren más.** La meta de la práctica uno es que pidan la práctica dos.

---

## Cómo usarla

### En tu computadora

Es un solo archivo HTML sin proceso de compilación. Abre `index.html` en cualquier navegador. Ya.

### En GitHub Pages

1. Pon `index.html` en la raíz de un repositorio público
2. **Settings → Pages →** Source: *Deploy from a branch*, rama `main`, carpeta `/ (root)`
3. Espera uno o dos minutos — tu sitio aparece en `https://kidsbackyardcoach-cyber.github.io/`

### En el celular

Abre la dirección en Safari o Chrome → **Compartir → Agregar a inicio**. Queda con su propio icono y abre en pantalla completa sin barras del navegador. Para la mayoría de las familias, esto ya es la app — sin tienda, sin instalación, sin cuenta.

---

## Notas técnicas

- **Un solo archivo, cero dependencias.** Sin framework, sin build, sin bundler, sin package.json. Unos 160 KB de HTML/CSS/JS.
- **Las tipografías** se cargan desde Google Fonts (Barlow, Barlow Condensed, Noto Sans SC). La primera carga necesita conexión; después queda en caché. Cámbialas por tipografías del sistema si necesitas que funcione totalmente sin conexión.
- **El almacenamiento** usa `localStorage`, con una cadena de respaldo que también funciona dentro de los artifacts de Claude y degrada a memoria si el almacenamiento está bloqueado. El progreso es por dispositivo y por navegador — borrar los datos del sitio lo reinicia.
- **Todas las ilustraciones y diagramas son SVG en línea**, dibujados para este proyecto. Sin fotos de producto, sin marcas, sin imágenes licenciadas — es deliberado, para que la app pueda publicarse o venderse sin problemas de derechos de imagen.
- **La internacionalización** es una búsqueda en un objeto (`T[lang]`), con las traducciones de cada elemento anidadas en los objetos de contenido (`drill.es.how`). Sin librería de i18n. Agregar un cuarto idioma es agregar una clave a cada objeto.
- **Accesibilidad:** botones semánticos con `aria-pressed`, foco de teclado visible y `prefers-reduced-motion` respetado.

### Estructura dentro del archivo

```
<style>          tokens de diseño, colores por deporte, reglas tipográficas por idioma
IC               16 iconos de equipo (SVG)
T                textos de interfaz, 3 idiomas
FIG              6 diagramas de campo y jugadas (generadores SVG)
BASICS           básicos de cada deporte, 3 idiomas
MOVE / D         43 ejercicios, 3 idiomas
SEASON           12 semanas x 4 deportes, 3 idiomas
SPORTS / KIT     listas de equipo y precios
RULES / FIXES    guía para entrenar, 3 idiomas
                 funciones de renderizado y estado
```

---

## Cómo contribuir

**Las traducciones** son la contribución más útil. Cada elemento traducible es un objeto con clave de idioma — agrega tu código de idioma junto a `en` / `zh` / `es` en `T`, `D`, `SEASON`, `SPORTS`, `BASICS`, `RULES` y `FIXES`, y luego agrega un botón en `#langsw`.

Notas para quien traduzca:

- Mantén las **frases para decir** cortas y gritables. Están hechas para gritarse a través de un patio, no para leerse.
- La versión en **chino** cambia a Noto Sans SC y desactiva las mayúsculas automáticas — el estilo en mayúsculas no aplica a los caracteres chinos. Si agregas otro sistema de escritura no latino, agrega la regla CSS equivalente.
- El **español** aquí es latinoamericano neutro, con vocabulario que tiende a mexicano (*cubeta*, *tenis*, *gis*). Las variantes regionales son bienvenidas como códigos separados.

**Los ejercicios nuevos** necesitan los seis campos (`n`, `setup`, `how`, `cue`, `e`, `h`) en todos los idiomas soportados, más un `tag` que exista en `T[lang].tags`.

---

## Avisos importantes

**Esto no es consejo médico, de seguridad ni de entrenamiento profesional.** Es un conjunto de actividades apropiadas para la edad, recopiladas para juego informal en el patio. Usa tu criterio sobre tu hijo o hija, supervisa directamente y consulta a tu pediatra ante cualquier duda sobre actividad física.

**Sobre seguridad en particular:**

- El flag football a esta edad es **sin contacto**. Sin cascos, sin hombreras, sin tacleadas. Si alguien te está vendiendo equipo de protección para un niño de cuatro años, te está vendiendo el juego equivocado.
- **"Suelta el bate"** es la regla más importante de toda la sección de t-ball. Los niños batean y corren todavía con el bate en la mano. Enséñala desde el primer día, todas las veces.
- Los precios son **estimados aproximados de EE. UU. para presupuestar**, no precios en vivo, y se van a desactualizar. Revisa los precios actuales antes de comprar.
- Las recomendaciones de tamaño (balón talla 3, bate de 61–66 cm, vallas de 15 cm) siguen la guía estándar para esta edad. Confírmalas con el reglamento de tu liga si van a inscribirse en una.

---

## Contacto

Preguntas, reportes de errores, ofertas de traducción, o una foto de tu hijo o hija usando esto de verdad — me daría gusto saberlo.

**kidsbackyardcoach@gmail.com**

Si estás reportando un problema, ayuda mucho que incluyas tu teléfono o navegador, el idioma que tenías seleccionado, y en qué deporte y semana ibas.

---

## Derechos de autor y uso

© 2026 Backyard Coach. Todos los derechos reservados.

Este proyecto se publica para que los papás y mamás puedan usarlo, no como software de código abierto. El código se ve aquí porque es un solo archivo HTML servido por GitHub Pages — que sea visible no es una licencia.

**Puedes:** usar la app libremente con tu familia, equipo o grupo; compartir el enlace; e imprimir sesiones para tu propio uso.

**Consúltame antes de:** redistribuirla o alojar tu propia copia, publicar versiones modificadas, integrarla en otro producto, o usarla comercialmente.

Las contribuciones y traducciones son bienvenidas — ver arriba. Al enviar una, aceptas que pueda incluirse en este proyecto. Si quieres construir algo sobre esto, escríbeme; la respuesta suele ser que sí.

*Este es un resumen en lenguaje sencillo, no asesoría legal.*

---

## Planes a futuro

Ideas, más o menos por orden de utilidad:

- [ ] Funcionamiento sin conexión: incrustar tipografías, agregar un service worker
- [ ] Chino tradicional (繁體中文) para Taiwán y Hong Kong
- [ ] Tenis, atletismo básico y un módulo bajo techo para días de lluvia
- [ ] Una versión para 3 años (sesiones más cortas, ejercicios más simples) y otra para 5–6
- [ ] Vista de impresión — una hoja por sesión para pegar en el refrigerador
- [ ] Exportar e importar el progreso, para que sobreviva a un teléfono nuevo
