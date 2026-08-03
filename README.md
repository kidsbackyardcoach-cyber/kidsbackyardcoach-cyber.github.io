# Backyard Coach

**English** · [中文](README.zh.md) · [Español](README.es.md)

**12-week practice plans for parents coaching soccer, t-ball, and flag football to 3–5 year olds — even if you've never played the sport yourself.**

Available in English, 中文 (Simplified Chinese), and Español.

[**→ Open the app**](https://YOUR-USERNAME.github.io/backyard-coach/)

---

## What this is

Most youth sports resources assume you already know the sport and already know how to run a session. This one assumes neither. It answers the two questions a parent actually has on a Saturday morning:

1. **What do I buy?** — checklists by priority, with rough prices and an explicit "don't buy this yet" list
2. **What do we actually do for the next 25 minutes?** — a full season of sessions, with a timer

Everything is built around one constraint: **a four-year-old's attention span is about two to five minutes per activity.** Every design decision follows from that.

---

## Features

| | |
|---|---|
| **Sport primers** | Never played? Each sport gets a plain-language explanation with diagrams — the field, how a game works, how scoring works, the rules that matter, and eight terms you'll hear. Plus an honest picture of what the game actually looks like at age 4. |
| **12-week seasons** | Two 25-minute sessions per week, in four phases from first touch to a real small-sided game. Each week has a focus and one concrete milestone to look for. |
| **43 drills** | Every drill has setup, how to play, the exact phrase to say, and how to make it easier or harder on the spot. |
| **Practice timer** | Full-screen run mode with a clock readable at arm's length in sunlight. |
| **Gear lists** | Three priority tiers, drawn illustrations, running budget total, and a list of what *not* to buy. |
| **Movement kit** | Optional ladder / hurdle / cone games that swap into any week's warm-up. |
| **Coaching guide** | Eight rules, developmental expectations, and troubleshooting for the wanderer, the meltdown, and the kid who dominates. |
| **Progress tracking** | Mark sessions done; progress saves in your browser. |

---

## The coaching principles behind it

These are load-bearing. If you change the content, keep these:

- **25 minutes, total.** A short practice that stays fun beats an hour that falls apart.
- **One ball per child.** Two kids sharing a ball means one kid touching a ball.
- **No lines, no laps, no lectures.** A child standing in a line is a child not practicing.
- **Games, not drills.** Same skill, different wrapper — only one of them works at this age.
- **Nobody ever sits out.** Elimination games produce a crying child and a ruined practice. Every game here is designed so getting caught means rejoining immediately.
- **End while they still want more.** The goal of practice one is that they ask for practice two.

---

## Running it

### Locally

It's a single HTML file with no build step. Open `index.html` in any browser. That's it.

### On GitHub Pages

1. Put `index.html` at the root of a public repo
2. **Settings → Pages →** Source: *Deploy from a branch*, branch `main`, folder `/ (root)`
3. Wait 1–2 minutes — your site appears at `https://<username>.github.io/<repo>/`

### On a phone

Open the URL in Safari or Chrome → **Share → Add to Home Screen**. It gets its own icon and opens full-screen without browser chrome. For most families this is the app — no store, no install, no account.

---

## Technical notes

- **Single file, zero dependencies.** No framework, no build, no bundler, no package.json. ~160 KB of HTML/CSS/JS.
- **Fonts** load from Google Fonts (Barlow, Barlow Condensed, Noto Sans SC). First load needs a connection; after that it's cached. Swap to system fonts if you need full offline.
- **Storage** uses `localStorage`, with a fallback chain so it also runs inside Claude artifacts and degrades to memory-only if storage is blocked. Progress is per-device and per-browser — clearing site data resets it.
- **All illustrations and diagrams are inline SVG**, drawn for this project. No product photos, no brand marks, no licensed imagery — deliberate, so the app can be published or sold without an image-rights problem.
- **Internationalization** is a plain object lookup (`T[lang]`), with per-item translations nested in the content objects (`drill.zh.how`). No i18n library. Adding a fourth language means adding one key to each object.
- **Accessibility:** semantic buttons with `aria-pressed`, visible keyboard focus rings, and `prefers-reduced-motion` respected.

### Structure inside the file

```
<style>          design tokens, per-sport accent colors, per-language type rules
IC               16 gear icons (SVG)
T                UI strings, 3 languages
FIG              6 field/play diagrams (SVG generators)
BASICS           sport primers, 3 languages
MOVE / D         43 drills, 3 languages
SEASON           12 weeks x 3 sports, 3 languages
SPORTS / KIT     gear lists and prices
RULES / FIXES    coaching guide, 3 languages
                 render + state functions
```

---

## Contributing

**Translations** are the most useful contribution. Each translatable item is an object keyed by language code — add your language code alongside `en` / `zh` / `es` in `T`, `D`, `SEASON`, `SPORTS`, `BASICS`, `RULES`, and `FIXES`, then add a button to `#langsw`.

Notes for translators:

- Keep drill **cues** short and shoutable. They're meant to be yelled across a yard, not read.
- The **Chinese** build switches to Noto Sans SC and disables uppercase transforms — uppercase styling doesn't apply to Chinese characters. If you add a non-Latin script, add the equivalent CSS override.
- **Spanish** here is neutral Latin American, leaning Mexican in vocabulary (*cubeta*, *tenis*, *gis*). Regional variants welcome as separate codes.

**New drills** need all six fields (`n`, `setup`, `how`, `cue`, `e`, `h`) in every supported language, plus a `tag` that exists in `T[lang].tags`.

---

## Important notes

**This is not medical, safety, or professional coaching advice.** It's a set of age-appropriate activities compiled for informal backyard play. Use your own judgment about your child, supervise directly, and check with your pediatrician about any physical activity concerns.

**On safety specifically:**

- Flag football at this age is **non-contact**. No helmets, no pads, no tackling. If you're being sold protective gear for a four-year-old, you're being sold the wrong game.
- **"Drop the bat"** is the single most important rule in the t-ball section. Children swing and then run while still holding it. Teach it from day one, every time.
- Prices are **rough US estimates for budgeting**, not live prices, and will go stale. Check current listings.
- Equipment size recommendations (size 3 ball, 24–26" bat, 6" hurdles) reflect standard guidance for this age group. Confirm against your league's rules if joining one.

---

## Contact

Questions, bug reports, translation offers, or a photo of your kid actually using this — I'd like to hear about it.

**kidsbackyardcoach@gmail.com**

If you're reporting a problem, it helps to include your phone or browser, the language you had selected, and which sport and week you were on.

---

## License

MIT — see [`LICENSE`](LICENSE).

Use it, fork it, translate it, run it at your local park. If it helps your kid have a good Saturday, that's the whole point.

---

## Roadmap

Ideas, in rough order of usefulness:

- [ ] Offline-capable: embed fonts, add a service worker
- [ ] Traditional Chinese (繁體中文) for Taiwan and Hong Kong
- [ ] Basketball and tennis seasons
- [ ] A 3-year-old track (shorter sessions, simpler drills) and a 5–6 track
- [ ] Print view — one page per session for the fridge
- [ ] Export/import progress, so it survives a new phone

# 后院教练 Backyard Coach

[English](README.md) · **中文** · [Español](README.es.md)

**给家长用的 12 周训练计划 —— 足球、棒球启蒙（T-ball）、腰旗橄榄球，适合 3–5 岁孩子。就算你自己完全没玩过这些运动，也能带。**

提供英文、简体中文、西班牙语三种语言。

[**→ 打开应用**](https://YOUR-USERNAME.github.io/backyard-coach/)

---

## 这是什么

大多数少儿体育资料都默认两件事：你懂这项运动，你也知道怎么组织一次训练。这个应用两样都不假设。它只回答家长在周六早上真正会问的两个问题：

1. **我该买什么？** —— 按优先级排的清单，附大致价格，还有一份明确的「现在别买」列表
2. **接下来这 25 分钟我们到底做什么？** —— 一整季的训练安排，配计时器

所有设计都围绕一个前提：**四岁孩子对每项活动的注意力大约只有二到五分钟。** 后面所有的取舍都是从这一条推出来的。

---

## 功能

| | |
|---|---|
| **运动入门** | 从没玩过？每项运动都有大白话讲解和示意图 —— 场地长什么样、一场比赛怎么进行、怎么得分、家长需要知道的规则、会听到的八个术语。还有一段实话：四岁的比赛实际长什么样。 |
| **12 周赛季** | 每周两次、每次 25 分钟，分四个阶段，从第一次碰球一直到真正的小型比赛。每周有一个重点和一个具体的观察目标。 |
| **43 个练习** | 每个练习都写清楚：怎么摆场地、怎么玩、该说的原话、以及现场怎么调难或调易。 |
| **训练计时器** | 全屏计时模式，字大到在阳光下伸直手臂也看得清。 |
| **装备清单** | 三个优先级档次、手绘插图、预算实时合计，还有一份「不要买」清单。 |
| **体能小工具** | 可选的敏捷梯／跨栏／标志桶游戏，可以替换任意一周的热身环节。 |
| **教练手册** | 八条原则、这个年纪的发育预期，以及各种突发状况怎么办 —— 跑掉的、崩溃的、一个人包场的。 |
| **进度记录** | 完成一次就打勾，进度保存在浏览器里。 |

---

## 背后的教学原则

这几条是承重墙。如果你要改内容，请保留它们：

- **总共 25 分钟。** 一次全程好玩的短训练，胜过一小时的兵荒马乱。
- **每人一个球。** 两个孩子共用一个球，等于只有一个孩子在碰球。
- **不排队、不跑圈、不训话。** 只要有孩子在排队，训练就已经停了。
- **要游戏，不要练习。** 同样的技能，换个包装 —— 这个年纪只有一种管用。
- **永远不让人出局。** 淘汰制游戏的结果就是一个哭的孩子和一场毁掉的训练。这里每个游戏都改成了：被抓到就立刻重新加入。
- **在他还想玩的时候收。** 第一次训练的唯一目标，就是让孩子主动要求第二次。

---

## 怎么运行

### 本地

就是一个 HTML 文件，不需要任何构建步骤。用浏览器打开 `index.html` 就行。

### 部署到 GitHub Pages

1. 把 `index.html` 放在一个公开仓库的根目录
2. **Settings → Pages →** Source 选 *Deploy from a branch*，分支 `main`，目录 `/ (root)`
3. 等一两分钟 —— 网站会出现在 `https://<用户名>.github.io/<仓库名>/`

### 在手机上

用 Safari 或 Chrome 打开网址 →**分享 → 添加到主屏幕**。它会有自己的图标，打开是全屏的，看不到浏览器界面。对大多数家庭来说，这就已经是「App」了 —— 不用商店、不用安装、不用注册账号。

---

## 技术说明

- **单文件，零依赖。** 没有框架、没有构建、没有打包工具、没有 package.json。约 160 KB 的 HTML/CSS/JS。
- **字体**从 Google Fonts 加载（Barlow、Barlow Condensed、Noto Sans SC）。第一次加载需要联网，之后会缓存。如果需要完全离线，可以换成系统字体。
- **存储**使用 `localStorage`，并带有降级链：也能在 Claude artifacts 环境里运行，如果存储被禁用则退化为仅内存保存。进度是按设备、按浏览器分别保存的 —— 清除网站数据会重置。
- **所有插图和示意图都是内联 SVG**，为这个项目手绘。没有产品照片、没有品牌标识、没有授权图片 —— 这是刻意的，这样应用可以发布甚至商用而不涉及图片版权问题。
- **多语言**用的是普通对象查表（`T[lang]`），每一条内容的翻译嵌在内容对象里（`drill.zh.how`）。没有用任何 i18n 库。加第四种语言，只需要给每个对象加一个键。
- **无障碍：** 使用语义化 button 配 `aria-pressed`、可见的键盘焦点框，并支持 `prefers-reduced-motion`。

### 文件内部结构

```
<style>          设计变量、各运动主题色、各语言的排版规则
IC               16 个装备图标（SVG）
T                界面文案，三种语言
FIG              6 张场地／战术示意图（SVG 生成函数）
BASICS           运动入门内容，三种语言
MOVE / D         43 个练习，三种语言
SEASON           12 周 × 3 项运动，三种语言
SPORTS / KIT     装备清单和价格
RULES / FIXES    教练手册，三种语言
                 渲染与状态函数
```

---

## 参与贡献

**翻译**是最有价值的贡献。每一条可翻译的内容都是按语言代码索引的对象 —— 在 `T`、`D`、`SEASON`、`SPORTS`、`BASICS`、`RULES`、`FIXES` 里，把你的语言代码加在 `en` / `zh` / `es` 旁边，然后在 `#langsw` 里加一个按钮。

给翻译者的几点提示：

- 练习里的**「就这样说」**要短、要喊得出来。这些话是要在院子里对着孩子喊的，不是给人读的。
- **中文**版本会切换到 Noto Sans SC 并关闭大写转换 —— 大写样式对汉字没有意义。如果你要加其他非拉丁文字，请同样加上对应的 CSS 覆盖。
- 这里的**西班牙语**是中性的拉美西班牙语，用词偏墨西哥（*cubeta*、*tenis*、*gis*）。欢迎以独立语言代码提交地区变体。

**新增练习**必须在每一种已支持的语言里都填全六个字段（`n`、`setup`、`how`、`cue`、`e`、`h`），并且 `tag` 要在 `T[lang].tags` 里存在。

---

## 重要提示

**这不是医疗、安全或专业教练建议。** 这只是一套为非正式的后院活动整理的、适合该年龄段的游戏。请自行判断是否适合你的孩子，全程在旁看护，如对运动有任何健康方面的疑虑，请咨询儿科医生。

**尤其是安全方面：**

- 这个年纪的腰旗橄榄球是**完全无身体对抗**的。不戴头盔、不穿护具、不擒抱。如果有人向你推销四岁孩子的护具，那说明他在卖的是一种不该玩的玩法。
- **「把棒子丢掉」**是棒球部分最重要的一条规则。孩子挥完棒常常会拿着棒子就跑。从第一天起就教，每一次都要教。
- 价格是**美国市场的大致区间，仅供预算参考**，不是实时价格，而且会过时。购买前请自行查看当前价格。
- 装备尺寸建议（3 号球、61–66 厘米球棒、15 厘米跨栏）参照的是该年龄段的通行标准。如果要参加正式联赛，请再核对该联赛的规定。

---

## 联系方式

有问题、发现 bug、想帮忙翻译，或者想发一张孩子真的在用这个的照片 —— 都欢迎联系我。

**kidsbackyardcoach@gmail.com**

如果是反馈问题，麻烦附上你的手机或浏览器型号、当时选的语言，以及在哪项运动的第几周。

---

## 许可协议

MIT —— 见 [`LICENSE`](LICENSE)。

随便用、随便改、随便翻译、随便拿去公园里带孩子玩。如果它能让你的孩子过一个开心的周六，那它的目的就达到了。

---

## 后续计划

按有用程度大致排序：

- [ ] 离线可用：内嵌字体，加 service worker
- [ ] 繁体中文（台湾、香港）
- [ ] 篮球和网球赛季
- [ ] 三岁版本（更短的训练、更简单的练习）和 5–6 岁版本
- [ ] 打印视图 —— 每次训练一页，可以贴冰箱上
- [ ] 进度导出／导入，换手机也不会丢

# Backyard Coach — Entrenador de Patio

[English](README.md) · [中文](README.zh.md) · **Español**

**Planes de práctica de 12 semanas para papás y mamás que entrenan fútbol, t-ball y flag football a niños de 3 a 5 años — aunque nunca hayas jugado el deporte.**

Disponible en inglés, 中文 (chino simplificado) y español.

[**→ Abrir la app**](https://YOUR-USERNAME.github.io/backyard-coach/)

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
| **Temporadas de 12 semanas** | Dos sesiones de 25 minutos por semana, en cuatro fases, desde el primer toque hasta un partido reducido real. Cada semana tiene un enfoque y una meta concreta que observar. |
| **43 ejercicios** | Cada uno trae montaje, cómo se juega, la frase exacta que decir y cómo hacerlo más fácil o más difícil sobre la marcha. |
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
3. Espera uno o dos minutos — tu sitio aparece en `https://<usuario>.github.io/<repo>/`

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
SEASON           12 semanas x 3 deportes, 3 idiomas
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

## Licencia

MIT — ver [`LICENSE`](LICENSE).

Úsala, bifúrcala, tradúcela, llévala al parque de tu colonia. Si le ayuda a tu hijo o hija a pasar un buen sábado, para eso es.

---

## Planes a futuro

Ideas, más o menos por orden de utilidad:

- [ ] Funcionamiento sin conexión: incrustar tipografías, agregar un service worker
- [ ] Chino tradicional (繁體中文) para Taiwán y Hong Kong
- [ ] Temporadas de básquetbol y tenis
- [ ] Una versión para 3 años (sesiones más cortas, ejercicios más simples) y otra para 5–6
- [ ] Vista de impresión — una hoja por sesión para pegar en el refrigerador
- [ ] Exportar e importar el progreso, para que sobreviva a un teléfono nuevo
