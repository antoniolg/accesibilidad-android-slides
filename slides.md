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

### 4.1 Diseño accesible

## Cada componente de UI tiene sus **guidelines** y **guías de accesibilidad**

---

### 4.1 Diseño: El problema del contraste

<div class="flex justify-center">
<img src="/CleanShot 2025-03-26 at 17.14.05@2x.png" />
</div>

---

### 4.1 Diseño: Tamaño adecuado

- Líneas inferiores a 120 caracteres
- Botones con un ancho máximo de 320dp
- Área táctil de los elementos clickables mínimo 48dp
- Uso de `sp` en lugar de `dp` para fuentes

---

### 4.1 Diseño: Área táctil (Touch Target)

- Área táctil de los elementos clickables mínimo 48dp

<div class="flex justify-center">
<img src="/Arc 2025-03-26 17.18.24.png" />
</div>

---

### 4.1 Diseño: Indicadores visuales

<div class="flex justify-center">
<img src="/Slides - Accesibilidad en Android.png" />
</div>

---

### 4.2 Semántica: **Descripciones útiles**

- En widgets de Compose obligatorios

```kotlin
Icon(
    imageVector = Icons.Filled.Favorite,
    contentDescription = stringResource(id = R.string.favorite),
)
```

---

### 4.2 Semántica: **Descripciones útiles**

- En widgets de Compose donde no es obligatorio

```kotlin
Text(
    text = "This is a text",
    modifier = Modifier
      .semantics { contentDescription = "This is a text" }
)
```

---

### 4.2 Semántica: **Elementos decorativos**

- Si el elemento es solo decorativo, debemos ocultarlo al lector:

```kotlin
Icon(
    imageVector = Icons.Filled.Favorite,
    contentDescription = null,
)

Text(
        text = "Hide from accessibility"
        modifier = Modifier.semantics { hideFromAccessibilty = true }
)
```

---

### 4.2 Semántica: **Agrupación de elementos**

- Problema: TalkBack lee cada texto por separado.
- Solución: `mergeDescendants`

```kotlin
Column(
    Modifier.semantics(mergeDescendants = true){}
) {
    Text("Item 1")
    Text ("Description for item 1.")
}
```

<div class="flex justify-center">
<img src="/CleanShot 2025-03-27 at 11.32.55.png" width="800" />
</div>

---

### 4.2 Semántica: **Navegación por Encabezados**

<div class="flex justify-center">
<img src="/talkback-encabezados.png" width="700" />
</div>

---

### 4.2 Semántica: **Encabezados**

- Permite al usuario saltar rápidamente entre secciones.
<br/>

```kotlin
Text(
    text = item.title,
    style = MaterialTheme.typography.titleMedium,
    modifier = Modifier.semantics { heading() }
)
```

---

### 4.3 Interacción accesible

- Gestión del foco
- Alternativas a gestos
- Manejo de cambios bruscos de contexto

---

### Gestión del foco

- ⚠️ **Importante**: modificar el foco manualmente es un antipatrón
  - Utilizarlo como último recurso

- Es importante que el **diseño sea accesible** para evitar usar "trucos"

---

### Gestión del foco: **Orden de lectura**

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

---

### Gestión del foco: **Orden de lectura**

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

---

### Gestión del foco: **Propiedades**

- Focus properties
  - **`previous`, `next`**: anterior y siguiente widget (navegación con tabulador)
  - **`up`, `down`, `left`, `right`**: dirección del foco (navegación con teclas de dirección)
  - **`start`, `end`**: izquierda y derecha para soporte RTL
  - **`canFocus`**: si el widget puede recibir foco
  - **`enter`, `exit`**: entrada y salida del widget. Recibe la dirección del foco

---

### Gestión del foco: **Grupos de Traversal**

- Modificar el orden de accesibilidad sin focusRequester
  - **`Modifier.semantics { isTraversalGroup = true }`**: agrupa widgets semánticamente.
  - **`Modifier.semantics { traversalIndex = 1f }`**: prioriza el orden de lectura (float).

---

### Alternativas a gestos

- Problema: Swipe o Drag & Drop son difíciles para usuarios con movilidad reducida.

<div class="flex justify-center">
<img src="/swipe-to-reveal.png" width="1200" />
</div>

---

### Alternativas a gestos: **Custom Actions**

- Solución: Añadir una acción semántica al menú de TalkBack.

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

---

### Cambios bruscos de contexto
#### **Anunciar cambios críticos**

- Problema: Aparece un error o mensaje y el lector no lo anuncia porque no tiene el foco.
- Solución: **Live Regions**.

---

### Cambios bruscos de contexto
#### **Live Regions**

- Compose

```kotlin
modifier = Modifier
    .semantics {
        // Assertive: Interrumpe la lectura actual (¡Urgente!)
        // Polite: Espera a terminar la frase actual.
        liveRegion = LiveRegionMode.Assertive
    }
```

---

### Cambios bruscos de contexto
#### **Informar de elementos emergentes**

- Usar widgets y composables estándares, derivados de:
  - **Popup**: para mensajes emergentes o menús
  - **Dialog**: para mensajes de confirmación
-  `Modifier.semantics { paneTitle = "Título de la ventana" }`

---

### Carruseles accesibles

<div class="flex justify-center">
<img src="/carruseles-accesibles.png" width="1000" />
</div>

---
layout: center
---

# 5. **Testing**

---

### 5.1 Testing manual

- TalkBack
- Switch Access
- Voice Access

---

### 5.2 Herramientas de análisis

- **Accessibility Scanner**

<div class="flex justify-center">
<img src="/accessibility-scanner.png" />
</div>

---

### 5.2 Herramientas de análisis

- **Android Studio**
  - Previews: Compose UI Check

<div class="flex justify-center">
<img src="/compose-ui-check.png" />
</div>

---

### 5.2 Herramientas de análisis

- **Google Play Pre-launch report**
  - Análisis automático de accesibilidad al subir la app

<div class="flex justify-center">
<img src="/pre-launch-report.png" width="1100" />
</div>

---

### 5.3 Testing automatizado

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

---

### 5.3 Testing automatizado: Comprobar accesibilidad

- Verificar roles semánticos en tests de UI:

```kotlin
composeTestRule
    .onNodeWithText("My Button")
    .assert(
        SemanticsMatcher("has correct role") {
            it.config.getOrNull(SemanticsProperties.Role) == Role.Button
        },
    )
```

---

### 5.4 Buenas prácticas

- **Testing con usuarios reales**
  - Realizar pruebas con personas con discapacidad
  - Obtener feedback directo
  - Validar la experiencia real

---

### 5.4 Buenas prácticas

- **Proceso continuo**
  - Integrar el testing de accesibilidad en el CI/CD
  - Realizar pruebas en cada release
  - Mantener un registro de problemas y mejoras

---
layout: center
---

# 6. **Conclusiones**

---

### Conclusiones

+ La accesibilidad es un **derecho**, no una opción
+ Diseñar con accesibilidad desde el principio
+ Usar componentes estándar siempre que sea posible
+ Testear la accesibilidad de forma continua
+ Escuchar a los usuarios y mejorar constantemente

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
