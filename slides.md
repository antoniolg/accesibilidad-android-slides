---
theme: the-unnamed

themeConfig:
  default-font-size: 1em
---

# Accesibilidad en Android
## Guía completa para desarrolladores

<div class="absolute right-12 bottom-12 flex items-center gap-4">
  <div class="h-20 w-20 overflow-hidden rounded-full border border-emerald-400/80">
    <img src="/antonio-leiva.jpg" alt="Antonio Leiva" class="h-full w-full object-cover" />
  </div>
  <div class="flex flex-col text-left text-slate-100 leading-tight gap-1">
    <div class="font-semibold">Antonio Leiva</div>
    <div class="text-slate-300">GDE Android y Partner JetBrains</div>
    <div class="text-slate-400"><i>DevExpert SLU</i></div>
  </div>
</div>

---
layout: about-me

helloMsg: ¡Hola!
name: Antonio Leiva
nameTitle: Formador DevExpert
imageSrc: /antonio-leiva.jpg
position: left
job: Formador DevExpert
social1: 🐦 @devexpert_io
social2: 🎥 @devexpert-io
social3: 🌍 https://devexpert.io
---

---
layout: center
background: /section-accessibility-bg.png
---

# Accesibilidad en Android
## Cómo funciona

---

# **Android** no es web

<div class="flex justify-center">
<img src="/ajustes_accesibilidad.png" width="550" />
</div>

---

# TalkBack: Navegación sin vista

<div class="grid grid-cols-2 gap-8 items-center">
  <div class="flex justify-center">
    <img src="/talkback.png" width="500" />
  </div>
  <div class="text-left">
    <ul class="text-xl space-y-4">
      <li><b>Navegación Lineal</b>: Siguiente / Anterior.</li>
      <li><b>Exploración Táctil</b>: Tocar para saber qué hay.</li>
      <li><b>Feedback Auditivo</b>: El sistema "lee" la UI.</li>
    </ul>
  </div>
</div>

---

# Switch Access: Movilidad Reducida

<div class="grid grid-cols-2 gap-8 items-center">
  <div class="flex justify-center">
    <img src="/switch_access.png" width="500" />
  </div>
  <div class="text-left">
    <ul class="text-xl space-y-4">
      <li><b>Escaneo automático</b>: El sistema recorre los elementos.</li>
      <li><b>Pulsadores externos</b>: El usuario selecciona cuando el foco está sobre el elemento deseado.</li>
    </ul>
  </div>
</div>

---

# Voice Access: Manos Libres

<div class="grid grid-cols-2 gap-8 items-center">
  <div class="flex justify-center">
    <img src="/voice_access.png" width="500" />
  </div>
  <div class="text-left">
    <ul class="text-xl space-y-4">
      <li>Control total del dispositivo mediante voz.</li>
      <li>Etiquetas numéricas para elementos sin texto claro.</li>
      <li>Comandos semánticos ("Hacer scroll", "Ir atrás").</li>
    </ul>
  </div>
</div>

---

# Buenas prácticas

<div class="grid grid-cols-3 gap-8 mt-12">
  <div class="p-6 rounded-xl border border-slate-200/20 bg-slate-800/30 backdrop-blur-sm">
    <div class="text-4xl mb-4 text-emerald-400">🎨</div>
    <h3 class="text-xl font-bold mb-2 text-slate-100">Diseño Inclusivo</h3>
    <p class="text-sm opacity-90 leading-relaxed text-slate-300">
      Diseñar con la accesibilidad en mente desde el principio del proyecto, no como un añadido final.
    </p>
  </div>

  <div class="p-6 rounded-xl border border-slate-200/20 bg-slate-800/30 backdrop-blur-sm">
    <div class="text-4xl mb-4 text-blue-400">⚙️</div>
    <h3 class="text-xl font-bold mb-2 text-slate-100">Preferencias</h3>
    <p class="text-sm opacity-90 leading-relaxed text-slate-300">
      Detectar y responder activamente a las preferencias de accesibilidad configuradas por el usuario.
    </p>
  </div>

  <div class="p-6 rounded-xl border border-slate-200/20 bg-slate-800/30 backdrop-blur-sm">
    <div class="text-4xl mb-4 text-rose-400">🛡️</div>
    <h3 class="text-xl font-bold mb-2 text-slate-100">No Interferir</h3>
    <p class="text-sm opacity-90 leading-relaxed text-slate-300">
      Evitar interferir con los servicios de accesibilidad del sistema (como TalkBack o Switch Access).
    </p>
  </div>
</div>

---
layout: center
background: /section-compose-bg.png
---

# **Jetpack Compose**
## Accesibilidad en el sistema de interfaces

---

# Árbol de Accesibilidad y Semántica

<div class="grid grid-cols-2 gap-8 items-center">
  <div class="flex justify-center">
    <img src="/arbol-accesibilidad.png" width="500" />
  </div>
  <div class="text-left">
    <ul class="text-xl space-y-4">
      <li>Todos los Composables del SDK son accesibles por defecto.</li>
      <li>Proporcionan información sobre su contenido y estado a los servicios de accesibilidad.</li>
      <li>Utilizan un árbol de accesibilidad basado en la semántica de los componentes.</li>
    </ul>
  </div>
</div>

---

# Debugging: Layout Inspector

<div class="flex justify-center">
<img src="/CleanShot 2025-01-21 at 17.01.59.png" />
</div>

---

# APIs de accesibilidad: Semantics

- Permite añadir/modificar información semántica de un Composable.
- Se usa a través de `Modifier.semantics { ... }`

<br/>

```kotlin
Text(
        text = "Hello World",
        modifier = Modifier.semantics {
                contentDescription = "Texto de saludo"
        }
)
```

---

# APIs de accesibilidad: Roles

<div class="grid grid-cols-2 gap-12 items-start mt-8">
  <div class="text-left">
  <div>
```kotlin
Text(
        text = "Hello world",
        modifier = Modifier.semantics {
                role = Role.Button
                onClick {
                        /* Acción del botón */
                        true
                }
        }
)
```
</div>
  <div v-click>
```kotlin
Text(
    text = "Hello world",
    modifier = Modifier.clickable(role = Role.Button) { 
      /* Acción */ 
    }
)
```
</div>
  </div>

  <div class="grid grid-cols-2 gap-4 content-start">
    <div class="p-4 rounded-lg bg-slate-800/50 border border-slate-700 text-center font-mono text-sm text-emerald-300">Button</div>
    <div class="p-4 rounded-lg bg-slate-800/50 border border-slate-700 text-center font-mono text-sm text-emerald-300">Checkbox</div>
    <div class="p-4 rounded-lg bg-slate-800/50 border border-slate-700 text-center font-mono text-sm text-emerald-300">Switch</div>
    <div class="p-4 rounded-lg bg-slate-800/50 border border-slate-700 text-center font-mono text-sm text-emerald-300">RadioButton</div>
    <div class="p-4 rounded-lg bg-slate-800/50 border border-slate-700 text-center font-mono text-sm text-emerald-300">Tab</div>
    <div class="p-4 rounded-lg bg-slate-800/50 border border-slate-700 text-center font-mono text-sm text-emerald-300">Image</div>
    <div class="p-4 rounded-lg bg-slate-800/50 border border-slate-700 text-center font-mono text-sm text-emerald-300 col-span-2">DropdownList</div>
  </div>
</div>

---

# Accesibilidad obligatoria por contrato

<div class="flex flex-col items-center justify-center mt-10 gap-8">
  <div class="bg-amber-400/10 border border-amber-400/50 p-6 rounded-lg max-w-2xl text-center backdrop-blur-md">
    <h3 class="text-xl font-bold text-amber-300 mb-2 flex items-center justify-center gap-2">
      <span class="text-2xl">⚠️</span> Compilación fallida si falta
    </h3>
    <p class="text-slate-200">
      Compose fuerza la accesibilidad en el sistema de tipos. Si un componente necesita descripción, <b>es obligatorio</b>.
    </p>
  </div>

  <div class="w-full max-w-3xl transform hover:scale-105 transition-transform duration-300">
```kotlin
Image(
    imageVector = Icons.Default.Favorite,
    contentDescription = "Mark as Favorite" // <--- ¡Obligatorio!
)
```
  </div>
</div>

---
layout: center
background: /section-recipes-bg.png
---

# **Recetas** de Accesibilidad

---

# En este bloque...

<div class="grid grid-cols-3 gap-8 mt-20">
  <div class="flex flex-col items-center p-8 rounded-2xl bg-slate-800/50 border border-emerald-500/30 backdrop-blur-sm">
    <div class="text-6xl mb-6">🎨</div>
    <h2 class="text-2xl font-bold text-emerald-400 text-center">Diseño<br>accesible</h2>
  </div>

  <div class="flex flex-col items-center p-8 rounded-2xl bg-slate-800/50 border border-blue-500/30 backdrop-blur-sm">
    <div class="text-6xl mb-6">📝</div>
    <h2 class="text-2xl font-bold text-blue-400 text-center">Contenido<br>accesible</h2>
  </div>

  <div class="flex flex-col items-center p-8 rounded-2xl bg-slate-800/50 border border-purple-500/30 backdrop-blur-sm">
    <div class="text-6xl mb-6">👆</div>
    <h2 class="text-2xl font-bold text-purple-400 text-center">Interacción<br>accesible</h2>
  </div>
</div>

---
layout: center
background: /section-recipes-bg.png
---

<div class="flex flex-col items-center p-16 rounded-3xl bg-slate-800/60 border border-emerald-500/40 backdrop-blur-md shadow-2xl">
  <div class="text-8xl mb-8">🎨</div>
  <h1 class="text-5xl font-bold text-emerald-400 text-center !mb-0 leading-tight">Diseño<br>accesible</h1>
</div>

---

# 4.1 Diseño accesible

<div class="grid grid-cols-2 gap-12 items-center mt-10">
  <div class="text-left">
    <h2 class="!text-4xl leading-tight">Cada componente de UI tiene sus <b>guidelines</b> y <b>guías de accesibilidad</b></h2>
  </div>
  <div class="flex justify-center transform hover:scale-105 transition-transform duration-500">
    <img src="/material-guidelines.png" class="rounded-xl shadow-2xl border border-slate-700/50" />
  </div>
</div>

---

# 4.1 Diseño: El problema del contraste

<div class="flex justify-center">
<img src="/CleanShot 2025-03-26 at 17.14.05@2x.png" width="800" />
</div>

---

# 4.1 Diseño: Tamaño adecuado

<div class="grid grid-cols-2 gap-8 mt-10">
  <div class="flex items-center gap-4 p-4 rounded-lg bg-slate-800/50 border border-slate-700">
    <div class="text-4xl text-emerald-400">📏</div>
    <p class="text-lg text-slate-200">Líneas inferiores a 120 caracteres</p>
  </div>
  <div class="flex items-center gap-4 p-4 rounded-lg bg-slate-800/50 border border-slate-700">
    <div class="text-4xl text-blue-400">👆</div>
    <p class="text-lg text-slate-200">Botones con un ancho máximo de 320dp</p>
  </div>
  <div class="flex items-center gap-4 p-4 rounded-lg bg-slate-800/50 border border-slate-700">
    <div class="text-4xl text-rose-400">🎯</div>
    <p class="text-lg text-slate-200">Área táctil de los elementos clickables mínimo 48dp</p>
  </div>
  <div class="flex items-center gap-4 p-4 rounded-lg bg-slate-800/50 border border-slate-700">
    <div class="text-4xl text-purple-400">🔡</div>
    <p class="text-lg text-slate-200">Uso de <code class="text-emerald-300">sp</code> en lugar de <code class="text-emerald-300">dp</code> para fuentes</p>
  </div>
</div>

---

# 4.1 Diseño: Área táctil (Touch Target)

<div class="flex justify-center">
<img src="/Arc 2025-03-26 17.18.24.png" />
</div>

---

# 4.1 Diseño: Indicadores visuales

<div class="flex justify-center">
<img src="/Slides - Accesibilidad en Android.png" />
</div>

---
layout: center
background: /section-recipes-bg.png
---

<div class="flex flex-col items-center p-16 rounded-3xl bg-slate-800/60 border border-blue-500/40 backdrop-blur-md shadow-2xl">
  <div class="text-8xl mb-8">📝</div>
  <h1 class="text-5xl font-bold text-blue-400 text-center !mb-0 leading-tight">Contenido<br>accesible</h1>
</div>

---

# 4.2 Contenido: Descripciones útiles

<div class="flex flex-col gap-6 mt-6">
  <div class="grid grid-cols-[1fr_2fr] gap-6 items-center p-4 rounded-xl border border-blue-400/50 bg-blue-900/20 backdrop-blur-sm">
    <div>
      <h2 class="text-xl font-bold text-blue-300">En widgets de Compose obligatorios</h2>
    </div>
    <div class="bg-slate-900 rounded-lg p-3 font-mono text-xs text-slate-200 leading-tight">
```kotlin
Icon(
    imageVector = Icons.Filled.Favorite,
    // Obligatorio en componentes visuales como Icon e Image
    contentDescription = stringResource(id = R.string.favorite),
)
```
    </div>
  </div>

  <div class="grid grid-cols-[1fr_2fr] gap-6 items-center p-4 rounded-xl border border-emerald-400/50 bg-emerald-900/20 backdrop-blur-sm">
    <div>
      <h2 class="text-xl font-bold text-emerald-300">En widgets de Compose donde no es obligatorio</h2>
    </div>
    <div class="bg-slate-900 rounded-lg p-3 font-mono text-xs text-slate-200 leading-tight">
```kotlin
Text(
    text = "This is a text",
    modifier = Modifier
      .semantics { 
          // Añadimos descripción explícita si el texto no es suficiente
          contentDescription = "This is a text" 
      }
)
```
    </div>
  </div>
</div>

---

# 4.2 Contenido: Elementos decorativos

<div class="flex flex-col gap-6 mt-6">
  <div class="grid grid-cols-[1fr_2fr] gap-6 items-center p-4 rounded-xl border border-rose-400/50 bg-rose-900/20 backdrop-blur-sm">
    <div>
      <h2 class="text-xl font-bold text-rose-300">Ocultar Iconos</h2>
    </div>
    <div class="bg-slate-900 rounded-lg p-3 font-mono text-sm text-slate-200 leading-relaxed">
```kotlin
Icon(
    imageVector = Icons.Filled.Favorite,
    contentDescription = null,
)
```
    </div>
  </div>

  <div class="grid grid-cols-[1fr_2fr] gap-6 items-center p-4 rounded-xl border border-purple-400/50 bg-purple-900/20 backdrop-blur-sm">
    <div>
      <h2 class="text-xl font-bold text-purple-300">Ocultar Texto/Composables</h2>
    </div>
    <div class="bg-slate-900 rounded-lg p-3 font-mono text-sm text-slate-200 leading-relaxed">
```kotlin
Text(
        text = "Hide from accessibility",
        modifier = Modifier.semantics { hideFromAccessibilty = true }
)
```
    </div>
  </div>
</div>

---

# 4.2 Contenido: Agrupación de elementos

<div class="grid grid-cols-2 gap-12 items-start mt-10">
  <div class="text-left">
    <h2 class="text-3xl font-bold text-amber-300 mb-4">Problema</h2>
    <p class="text-xl text-slate-200 mb-6">TalkBack lee cada texto por separado, fragmentando la información de un mismo elemento.</p>
    <h2 class="text-3xl font-bold text-emerald-300 mb-4">Solución: <code class="text-emerald-300">mergeDescendants</code></h2>
    <p class="text-xl text-slate-200">Agrupa semánticamente los elementos para que se lean como una única unidad coherente.</p>
  </div>
  <div class="flex flex-col gap-8 justify-center items-center">
    <img src="/CleanShot 2025-03-27 at 11.32.55.png" width="500" class="rounded-xl shadow-2xl border border-slate-700/50" />
    <div class="bg-slate-900 rounded-lg p-4 font-mono text-sm text-slate-200 leading-relaxed w-full max-w-md">
```kotlin
Column(
    Modifier.semantics(mergeDescendants = true){}
) {
    Text("Item 1")
    Text ("Description for item 1.")
}
```
    </div>
  </div>
</div>

---

# 4.2 Contenido: Navegación por Encabezados

<div class="grid grid-cols-2 gap-12 items-center mt-10">
  <div class="flex justify-center">
    <img src="/talkback-encabezados.png" width="500" class="rounded-xl shadow-2xl border border-slate-700/50" />
  </div>
  <div class="text-left">
    <p class="text-xl text-slate-200 mb-6">Permite al usuario saltar rápidamente entre secciones, mejorando la navegación en contenido extenso.</p>
    <h2 class="text-3xl font-bold text-emerald-300 mb-4">Uso de <code class="text-emerald-300">Modifier.semantics { heading() }</code></h2>
    <div class="bg-slate-900 rounded-lg p-4 font-mono text-sm text-slate-200 leading-relaxed">
```kotlin
Text(
    text = item.title,
    style = MaterialTheme.typography.titleMedium,
    modifier = Modifier.semantics { heading() }
)
```
    </div>
  </div>
</div>

---
layout: center
background: /section-recipes-bg.png
---

<div class="flex flex-col items-center p-16 rounded-3xl bg-slate-800/60 border border-purple-500/40 backdrop-blur-md shadow-2xl">
  <div class="text-8xl mb-8">👆</div>
  <h1 class="text-5xl font-bold text-purple-400 text-center !mb-0 leading-tight">Interacción<br>accesible</h1>
</div>

---

# 4.3 Interacción accesible

<div class="grid grid-cols-3 gap-8 mt-20">
  <div class="flex flex-col items-center p-8 rounded-2xl bg-slate-800/50 border border-emerald-500/30 backdrop-blur-sm">
    <div class="text-6xl mb-6">🎯</div>
    <h2 class="text-2xl font-bold text-emerald-400 text-center">Gestión<br>del foco</h2>
  </div>

  <div class="flex flex-col items-center p-8 rounded-2xl bg-slate-800/50 border border-blue-500/30 backdrop-blur-sm">
    <div class="text-6xl mb-6">👋</div>
    <h2 class="text-2xl font-bold text-blue-400 text-center">Alternativas<br>a gestos</h2>
  </div>

  <div class="flex flex-col items-center p-8 rounded-2xl bg-slate-800/50 border border-rose-500/30 backdrop-blur-sm">
    <div class="text-6xl mb-6">🔔</div>
    <h2 class="text-2xl font-bold text-rose-400 text-center">Cambios bruscos<br>de contexto</h2>
  </div>
</div>

---

# Gestión del foco

<div class="flex flex-col items-center justify-center mt-10 gap-8">
  <div class="bg-amber-400/10 border border-amber-400/50 p-6 rounded-lg max-w-2xl text-center backdrop-blur-md">
    <h2 class="text-3xl font-bold text-amber-300 mb-2 flex items-center justify-center gap-2">
      <span class="text-4xl">⚠️</span> ¡Antipatrón! Modificar el foco manualmente
    </h2>
    <p class="text-xl text-slate-200">
      Utilizarlo solo como último recurso. Es crucial que el <b>diseño sea accesible</b> para evitar la necesidad de "trucos".
    </p>
  </div>
</div>

---

## Gestión del foco: Orden de lectura

<div class="flex flex-col gap-8 mt-10">
  <div class="bg-slate-900 rounded-lg p-4 font-mono text-sm text-slate-200 leading-relaxed">
```kotlin
val (first, second, third, fourth) = remember { FocusRequester.createRefs() }

Column {
  TextButton({}, Modifier.focusRequester(first)) { Text("First field") }
  // Queremos saltar del 1º al 3º visualmente
  TextButton({}, Modifier.focusRequester(third)) { Text("Third field") }
  TextButton({}, Modifier.focusRequester(second)) { Text("Second field") }
  TextButton({}, Modifier.focusRequester(fourth)) { Text("Fourth field") }
}
```
  </div>

  <div class="bg-slate-900 rounded-lg p-4 font-mono text-sm text-slate-200 leading-relaxed">
```kotlin
TextButton(
    {},
    Modifier
        .focusRequester(first)
        .focusProperties { next = second } // Forzamos el salto
) {
    Text("First field")
}
```
  </div>
</div>

---

## Gestión del foco: Propiedades

<div class="grid grid-cols-2 gap-6 mt-10">
  <div class="flex items-center gap-4 p-4 rounded-lg bg-slate-800/50 border border-slate-700">
    <div class="text-4xl text-emerald-400">↔️</div>
    <p class="text-lg text-slate-200"><code>previous</code>, <code>next</code>: Navegación lineal (tabulador)</p>
  </div>
  <div class="flex items-center gap-4 p-4 rounded-lg bg-slate-800/50 border border-slate-700">
    <div class="text-4xl text-blue-400">↕️</div>
    <p class="text-lg text-slate-200"><code>up</code>, <code>down</code>, <code>left</code>, <code>right</code>: Navegación direccional</p>
  </div>
  <div class="flex items-center gap-4 p-4 rounded-lg bg-slate-800/50 border border-slate-700">
    <div class="text-4xl text-rose-400">➡️</div>
    <p class="text-lg text-slate-200"><code>start</code>, <code>end</code>: Soporte RTL</p>
  </div>
  <div class="flex items-center gap-4 p-4 rounded-lg bg-slate-800/50 border border-slate-700">
    <div class="text-4xl text-purple-400">✅</div>
    <p class="text-lg text-slate-200"><code>canFocus</code>: Si el widget puede recibir foco</p>
  </div>
  <div class="flex items-center gap-4 p-4 rounded-lg bg-slate-800/50 border border-slate-700 col-span-2">
    <div class="text-4xl text-amber-400">🚪</div>
    <p class="text-lg text-slate-200"><code>enter</code>, <code>exit</code>: Entrada y salida del widget (recibe dirección)</p>
  </div>
</div>

---

## Gestión del foco: Grupos de Traversal

<div class="grid grid-cols-2 gap-8 mt-10">
  <div class="p-6 rounded-xl border border-blue-400/50 bg-blue-900/20 backdrop-blur-sm">
    <h3 class="text-2xl font-bold text-blue-300 mb-4"><code class="text-emerald-300">isTraversalGroup = true</code></h3>
    <p class="text-lg text-slate-200">Agrupa widgets semánticamente, permitiendo que el foco se mueva entre ellos como un único bloque antes de pasar a otros grupos.</p>
  </div>
  <div class="p-6 rounded-xl border border-emerald-400/50 bg-emerald-900/20 backdrop-blur-sm">
    <h3 class="text-2xl font-bold text-emerald-300 mb-4"><code class="text-emerald-300">traversalIndex = 1f</code></h3>
    <p class="text-lg text-slate-200">Prioriza el orden de lectura de los elementos dentro de un grupo o en la pantalla. Utiliza un valor flotante para mayor flexibilidad.</p>
  </div>
</div>

---

# Alternativas a gestos

<div class="grid grid-cols-2 gap-12 items-center mt-10">
  <div class="text-left">
    <h2 class="text-3xl font-bold text-amber-300 mb-4">Problema</h2>
    <p class="text-xl text-slate-200 mb-6">Gestos como Swipe o Drag & Drop son difíciles de realizar para usuarios con movilidad reducida o que utilizan tecnologías de asistencia.</p>
    <h2 class="text-3xl font-bold text-emerald-300 mb-4">Solución</h2>
    <p class="text-xl text-slate-200">Ofrecer alternativas interactivas que no dependan de gestos complejos.</p>
  </div>
  <div class="flex justify-center">
    <img src="/swipe-to-reveal.png" width="500" class="rounded-xl shadow-2xl border border-slate-700/50" />
  </div>
</div>

---

# Alternativas a gestos: Custom Actions

<div class="flex flex-col items-center mt-10 gap-8">
  <h2 class="text-3xl font-bold text-emerald-300 mb-4">Solución: Añadir acciones semánticas al menú de TalkBack</h2>
  <div class="w-full max-w-3xl bg-slate-900 rounded-lg p-6 font-mono text-sm text-slate-200 leading-relaxed shadow-lg border border-slate-700/50">
```kotlin

MyComposable(
  val deleteLabel = stringResource(R.string.delete)
  modifier = Modifier
      .semantics {
          customActions = listOf(
            // Añade "Eliminar" al menú de acciones
            CustomAccessibilityAction(deleteLabel) { delete(); true }
          )
      }
)
```
  </div>
</div>

---

# Cambios bruscos de contexto

<div class="grid grid-cols-2 gap-12 items-start">

<div>

<p class="text-2xl font-bold text-amber-300 mb-4">Problema: Anunciar cambios críticos</p>
<p class="text-xl text-slate-200 mb-6">Cuando aparece un error o mensaje, el lector de pantalla puede no anunciarlo si no tiene el foco.</p>

<p class="text-2xl font-bold text-emerald-300 mb-4">Solución: Live Regions</p>
<p class="text-xl text-slate-200 mb-4">Indican que un área se actualiza dinámicamente.</p>

```kotlin
modifier = Modifier
    .semantics {
        // Assertive: Interrumpe la lectura actual
        // Polite: Espera a terminar la frase actual
        liveRegion = LiveRegionMode.Assertive
    }
```

</div>

<div v-click>

<p class="text-2xl font-bold text-blue-300 mb-4">Informar de elementos emergentes</p>
<ul class="text-xl text-slate-200 mb-4">
    <li><b>Popup</b>: para mensajes emergentes o menús.</li>
    <li><b>Dialog</b>: para mensajes de confirmación.</li>
    <li>Añade <code class="text-emerald-300">paneTitle</code> en la semántica.</li>
</ul>

```kotlin
Modifier.semantics { 
    paneTitle = "Título de la ventana" 
}
```

</div>

</div>

---

# Carruseles accesibles

<div class="flex flex-col items-center">
  <img src="/carruseles-accesibles.png" width="700" />
</div>

---
layout: center
---

<div class="flex flex-col items-center p-16 rounded-3xl bg-slate-800/60 border border-yellow-500/40 backdrop-blur-md shadow-2xl">
  <div class="text-8xl mb-8">🧪</div>
  <h1 class="text-5xl font-bold text-yellow-400 text-center !mb-0 leading-tight">Testing</h1>
</div>

---

# 5.1 Testing manual

<div class="grid grid-cols-3 gap-8 mt-10">
  <div class="flex flex-col items-center p-6 rounded-xl border border-emerald-400/50 bg-emerald-900/20 backdrop-blur-sm">
    <div class="text-6xl mb-4">🗣️</div>
    <h3 class="text-xl font-bold text-emerald-300">TalkBack</h3>
  </div>
  <div class="flex flex-col items-center p-6 rounded-xl border border-blue-400/50 bg-blue-900/20 backdrop-blur-sm">
    <div class="text-6xl mb-4">♿</div>
    <h3 class="text-xl font-bold text-blue-300">Switch Access</h3>
  </div>
  <div class="flex flex-col items-center p-6 rounded-xl border border-rose-400/50 bg-rose-900/20 backdrop-blur-sm">
    <div class="text-6xl mb-4">🎤</div>
    <h3 class="text-xl font-bold text-rose-300">Voice Access</h3>
  </div>
</div>

---

# 5.2 Herramientas de análisis

<div class="grid grid-cols-3 gap-8">
  <div class="flex flex-col items-center p-6 rounded-xl border border-emerald-400/50 bg-emerald-900/20 backdrop-blur-sm">
    <p class="text-xl font-bold text-emerald-300 mb-4">Accessibility Scanner</p>
    <div class="flex justify-center mb-4">
      <img src="/accessibility-scanner.png" width="200" class="rounded-lg shadow-lg border border-slate-700/50" />
    </div>
    <p class="text-sm text-slate-200 text-center">Herramienta de Google para encontrar problemas de accesibilidad.</p>
  </div>

  <div class="flex flex-col items-center p-6 rounded-xl border border-blue-400/50 bg-blue-900/20 backdrop-blur-sm">
    <p class="text-xl font-bold text-blue-300 mb-4">Android Studio: Compose UI Check</p>
    <div class="flex justify-center mb-4">
      <img src="/compose-ui-check.png" width="200" class="rounded-lg shadow-lg border border-slate-700/50" />
    </div>
    <p class="text-sm text-slate-200 text-center">Análisis automático de accesibilidad en Previews de Compose.</p>
  </div>

  <div class="flex flex-col items-center p-6 rounded-xl border border-rose-400/50 bg-rose-900/20 backdrop-blur-sm">
    <p class="text-xl font-bold text-rose-300 mb-4">Google Play Pre-launch report</p>
    <div class="flex justify-center mb-4">
      <img src="/pre-launch-report.png" width="200" class="rounded-lg shadow-lg border border-slate-700/50" />
    </div>
    <p class="text-sm text-slate-200 text-center">Análisis automático al subir la app a Google Play.</p>
  </div>
</div>

---

# 5.3 Testing automatizado

<div class="grid grid-cols-2 gap-8 mt-10">
  <div class="p-6 rounded-xl border border-blue-400/50 bg-blue-900/20 backdrop-blur-sm">
    <h3 class="text-2xl font-bold text-blue-300 mb-4">Habilitar checks de accesibilidad</h3>
    <div class="bg-slate-900 rounded-lg p-4 font-mono text-sm text-slate-200 leading-relaxed">
```kotlin
@OptIn(ExperimentalTestApi::class)
@Test
fun myComposeTest(): Unit = runComposeUiTest {

    enableAccessibilityChecks() // ¡Mágico!

        setContentView {
                ...
        }
}
```
    </div>
    <p class="text-lg text-slate-200 mt-4">Activa las comprobaciones automáticas de accesibilidad en tus tests de UI.</p>
  </div>

  <div class="p-6 rounded-xl border border-emerald-400/50 bg-emerald-900/20 backdrop-blur-sm">
    <h3 class="text-2xl font-bold text-emerald-300 mb-4">Verificar roles semánticos</h3>
    <div class="bg-slate-900 rounded-lg p-4 font-mono text-sm text-slate-200 leading-relaxed">
```kotlin
composeTestRule
    .onNodeWithText("My Button")
    .assert(
        SemanticsMatcher("has correct role") {
            it.config.getOrNull(SemanticsProperties.Role) == Role.Button
        },
    )
```
    </div>
    <p class="text-lg text-slate-200 mt-4">Asegura que los componentes tienen los roles de accesibilidad correctos.</p>
  </div>
</div>

---

# 5.4 Buenas prácticas

<div class="grid grid-cols-2 gap-8 mt-10">
  <div class="p-6 rounded-xl border border-blue-400/50 bg-blue-900/20 backdrop-blur-sm">
    <h3 class="text-2xl font-bold text-blue-300 mb-4">Testing con usuarios reales</h3>
    <ul class="text-lg space-y-3 text-slate-200">
      <li>Realizar pruebas con personas con discapacidad.</li>
      <li>Obtener feedback directo.</li>
      <li>Validar la experiencia real.</li>
    </ul>
  </div>

  <div class="p-6 rounded-xl border border-emerald-400/50 bg-emerald-900/20 backdrop-blur-sm">
    <h3 class="text-2xl font-bold text-emerald-300 mb-4">Proceso continuo</h3>
    <ul class="text-lg space-y-3 text-slate-200">
      <li>Integrar el testing de accesibilidad en el CI/CD.</li>
      <li>Realizar pruebas en cada release.</li>
      <li>Mantener un registro de problemas y mejoras.</li>
    </ul>
  </div>
</div>

---
layout: center
---

<div class="flex flex-col items-center p-16 rounded-3xl bg-slate-800/60 border border-teal-500/40 backdrop-blur-md shadow-2xl">
  <div class="text-8xl mb-8">✨</div>
  <h1 class="text-5xl font-bold text-teal-400 text-center !mb-0 leading-tight">Conclusiones</h1>
</div>

---

# Conclusiones

<div class="mt-10 max-w-4xl mx-auto">
  <ul class="text-xl space-y-6 text-slate-200">
    <li class="flex items-start gap-3">
      <span class="text-emerald-400 text-3xl">✅</span>
      <span>La accesibilidad es un <b>derecho</b>, no una opción.</span>
    </li>
    <li class="flex items-start gap-3">
      <span class="text-blue-400 text-3xl">✨</span>
      <span>Diseñar con accesibilidad desde el principio.</span>
    </li>
    <li class="flex items-start gap-3">
      <span class="text-purple-400 text-3xl">🧩</span>
      <span>Usar componentes estándar siempre que sea posible.</span>
    </li>
    <li class="flex items-start gap-3">
      <span class="text-yellow-400 text-3xl">🧪</span>
      <span>Testear la accesibilidad de forma continua.</span>
    </li>
    <li class="flex items-start gap-3">
      <span class="text-rose-400 text-3xl">👂</span>
      <span>Escuchar a los usuarios y mejorar constantemente.</span>
    </li>
  </ul>
</div>

---
layout: about-me

helloMsg: ¡Gracias!
name: Antonio Leiva
nameTitle: Formador DevExpert
imageSrc: /antonio-leiva.jpg
position: left
job: Formador DevExpert
social1: 🐦 @devexpert_io
social2: 🎥 @devexpert-io
social3: 🌍 https://devexpert.io
---