## Examen 3 — Guía para preparar café en casa

### 1. Cambios realizados y hojas de estilo modificadas
Se agregó la página `guia.html` con el índice de anclas, los tres métodos de preparación (prensa francesa, filtro y moka) con ingredientes y pasos, el bloque `aside` de consejos del barista con cita, la tabla comparativa, el glosario y el formulario «Recibir la guía», además de agregar el enlace «Guía» en el menú de las cinco páginas. Se modificaron `css/tipografia.css`, `css/componentes.css` y `css/layout.css` (y se actualizó el menú en los HTML).

### 2. Tabla de medidas de `guia.html`

| Ancho de ventana | Columnas en grilla principal | Desplazamiento horizontal |
| :--- | :--- | :--- |
| **500 px** | 1 columna | No |
| **800 px** | 2 columnas (`metodo--tercero` con `span 2`) | No |
| **1200 px** | 3 columnas (`metodo` uno por columna) | No |

### 3. Tres selectores utilizados y por qué
- **Selector de atributo (`a[href^="#"]`):** Aplica estilos a los enlaces internos del índice que apuntan a anclas de la misma página.
- **Combinador hijo directo (`.metodo > .metodo__titulo`):** Aplica estilo exclusivamente al título principal directo de cada sección de método.
- **Pseudoclase `:not(.metodo--destacado)`:** Aplica borde superior secundario a los métodos que no tienen la clase modificadora `.metodo--destacado`.

### 4. Dificultad y resolución
La regla general `.main-container > section { grid-column: 1 / -1; }` podía competir con la distribución en columnas de los métodos en `guia.html`. Se resolvió definiendo `.guia-main > .metodo` con `span 1`, `.guia-main > .metodo--tercero` con `span 2` a `37.5rem` (600 px) y `span 1` a `56.25rem` (900 px), verificando luego en el navegador a 500 px, 800 px y 1200 px sin desplazamiento horizontal.



# Proyecto Final — Sitio Web Adaptable: Cafsé Macondo

- **Estudiante:** Carlos Yovanny Jaimes
- **Proyecto:** Sitio web multipágina para la cafetería de especialidad Café Macondo.
- **Tecnologías utilizadas:** HTML5 semántico y CSS3 (Grid Layout, Variables, Unidades Relativas). Sin frameworks ni JavaScript.

---

## 1. Mapa del Sitio
El sitio consta de cuatro páginas interconectadas mediante un menú de navegación unificado y centrado, tematizadas bajo la estética del realismo mágico colombiano:
- **`index.html` (Inicio):** Presenta el banner principal con la identidad visual de la marca, la propuesta de valor inspirada en la tradición cafetera, una sección de testimonios (con `blockquote`) y un enlace externo seguro hacia la Federación Nacional de Cafeteros.
- **`carta.html` (Carta):** Contiene un índice con anclas internas para navegar rápidamente entre secciones, tablas detalladas de precios con `thead`, `tbody`, `th` con `scope` y filas alternas con `:nth-child()`, además de listas de filtrados y acompañamientos (`dl`).
- **`sedes.html` (Sedes):** Muestra las tres ubicaciones de la cafetería utilizando elementos estructurados con `figure` y `figcaption` explicativos.
- **`reservas.html` (Reservas):** Incluye un formulario completo con `fieldset`, campos de selección (`select`), grupos de opción (`radio`), casillas de verificación (`checkbox`), área de texto y validaciones nativas. Además, cuenta con una sección inferior estructurada en tres tarjetas dinámicas que detallan los beneficios, el glosario de políticas y los pasos de confirmación.

---

## 2. Tabla de Medidas (Columnas y Desplazamiento Horizontal)

| Página | 500 px | 800 px | 1200 px |
| :--- | :--- | :--- | :--- |
| **`index.html`** | 1 columna, sin scroll | 2 columnas, sin scroll | 3 columnas, sin scroll |
| **`carta.html`** | 1 columna, sin scroll | 2 columnas, sin scroll | 3 columnas, sin scroll |
| **`sedes.html`** | 1 columna, sin scroll | 2 columnas, sin scroll | 3 columnas, sin scroll |
| **`reservas.html`** | 1 columna, sin scroll | 2 columnas, sin scroll | 3 columnas, sin scroll |

---

## 3. Justificación de Unidades (RF-06.5)
1. **`font-size: 100%` (en el elemento `html`):** Se utilizó esta unidad porcentual como base para garantizar la accesibilidad y respetar las preferencias de zoom del navegador del usuario.
2. **`rem` (en tamaños de letra y espaciados generales):** Elegido porque es una unidad relativa al tamaño raíz, lo que mantiene una escala tipográfica y de espaciado perfectamente proporcional y predecible en todo el sitio.
3. **`ch` (en el ancho de párrafos `max-width: 65ch`):** Se usó para limitar la longitud de las líneas de texto según la medida ideal de caracteres por línea, garantizando una lectura sumamente cómoda para la vista humana.
4. **`%` (en anchos como `width: 100%` y grillas flexibles):** Utilizado para asegurar que contenedores e imágenes se adapten de forma fluida al 100% del espacio disponible de su contenedor padre sin desbordarse.
5. **`vh` (en la altura mínima de secciones hero `min-height: 50vh`):** Seleccionado para tomar una proporción exacta de la altura visible de la ventana del dispositivo y dar presencia visual a los encabezados de portada.
6. **`px` / `rem` equivalente (en bordes finos):** Se reservó de forma estricta únicamente para líneas divisorias y bordes pequeños donde una unidad mayor perdería nitidez visual.

---

## 4. Decisiones de Diseño y Conceptualización
- **Identidad de Marca:** Se estructuró el proyecto bajo la marca **Café Macondo**, integrando una propuesta visual basada en el realismo mágico colombiano. Se incorporó un logotipo circular corporativo de gran formato con alineación vertical centrada frente a los títulos institucionales en tipografía Georgia de alta elegancia.
- **Enfoque Móvil Primero (Mobile First):** Se diseñó la estructura CSS base pensando en los teléfonos celulares (una sola columna vertical) y se fueron incorporando complejidades mediante consultas de medios (`@media (min-width: ...)`) de menor a mayor (`600px` y `900px`). Esto garantiza un rendimiento óptimo y un diseño sólido en pantallas pequeñas.
- **Puntos de ruptura elegidos:** Se establecieron en `37.5rem` (600px) para dar el salto a dos columnas en tabletas, y `56.25rem` (900px) para alcanzar las tres columnas en computadores de escritorio, optimizando el espacio visual de manera fluida y sin recurrir jamás a Flexbox ni frameworks externos.

---

## 5. Dificultades y Resolución
- **Dificultad 1:** Inicialmente, las tablas de precios de la carta causaban un leve desbordamiento horizontal en la prueba a 500px debido al ancho fijo de las celdas en pantallas muy reducidas.
  - *Resolución:* Se solucionó envolviendo la etiqueta `table` dentro de un contenedor dedicado (`.table-container`) con la propiedad CSS `overflow-x: auto`, permitiendo un desplazamiento interno fluido sin romper el diseño de la página.
- **Dificultad 2:** La distribución inicial de los bloques informativos inferiores en la página de reservas se apilaba verticalmente en una sola columna estrecha en pantallas grandes.
  - *Resolución:* Se reestructuró el componente utilizando la clase `.card` y un contenedor Grid adaptable con `repeat(auto-fit, minmax(18rem, 1fr))`, logrando que se desplieguen armónicamente en tres columnas horizontales en computadores de escritorio.

 