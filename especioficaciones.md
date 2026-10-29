## Clase 1. Usabilidad y Accesibilidad (A11y / WCAG)

La usabilidad define la funcionalidad del software en relación directa con el usuario, articulándose en dos dimensiones interdependientes:

**Dimensiones de la Usabilidad**
Dimensión Objetiva (Métricas cuantitativas):
       - Tasa de finalización de tareas (completitud).
       - Tiempo invertido por tarea (eficiencia).
       - Tasa de error por interacción.
Dimensión Subjetiva (Percepción cualitativa):
       - Nivel de frustración o fluidez percibida.
       - Satisfacción general al completar el flujo.
Fórmula Core: 
       - Usabilidad=Eficacia(Logro)+Eficiencia(Velocidad)+Satisfacción(ExperienciaPositiva)

**Principios WCAG (Web Content Accessibility Guidelines - W3C)**
La accesibilidad (A11y) es un estándar técnico obligatorio. La interfaz debe cumplir de forma estricta los 4 pilares WCAG:

┌─────────────────┬───────────────────────────────────────────┬──────────────────────────────────────────────────────────────┐
│                 │                                           │                                                              │
│ Pilar WCAG      │ Definición Técnica                        │ Requisito de Implementación                                  │
│                 │                                           │                                                              │
├─────────────────┼───────────────────────────────────────────┼──────────────────────────────────────────────────────────────┤
│                 │                                           │                                                              │
│ 1. Perceptible  │ La información debe poder ser captada     │ Contraste de color mínimo 4.5:1.                             │
│                 │ por la vista u oído.                      │ Atributos alt obligatorios en imágenes no decorativas.       │
│                 │                                           │                                                              │
├─────────────────┼───────────────────────────────────────────┼──────────────────────────────────────────────────────────────┤
│                 │                                           │                                                              │
│ 2. Operable     │ Navegabilidad completa sin                │ Navegación 100% por teclado (Tab, Enter, Space, Esc).        │
│                 │ dependencia de periféricos de puntero.    │ Anillos de foco (:focus) visibles y contrastados.            │
│                 │                                           │                                                              │
├─────────────────┼───────────────────────────────────────────┼──────────────────────────────────────────────────────────────┤
│                 │                                           │                                                              │
│ 3. Comprensible │ Lenguaje claro, consistente y             │ Evitar terminología técnica interna o identificadores        │
│                 │ predecible.                               │ del backend en la vista.                                     │
│                 │                                           │                                                              │
├─────────────────┼───────────────────────────────────────────┼──────────────────────────────────────────────────────────────┤
│                 │                                           │                                                              │
│ 4. Robusto      │ Compatibilidad con tecnologías            │ Código semántico (<main>, <nav>, <button>, <input>)          │
│                 │ asistivas.                                │ interpretable por lectores de pantalla (screen readers).     │
│                 │                                           │                                                              │
└─────────────────┴───────────────────────────────────────────┴──────────────────────────────────────────────────────────────┘

**Optimización Esfuerzo-Beneficio**
Para minimizar la carga cognitiva e interacción requerida del usuario:
       - Habilitar atributos de autocompletado en campos estructurados (autocomplete).
       - Implementar validaciones en tiempo real (inline validation) previas al envío de formularios.
        Proporcionar feedback inmediato ante cualquier interacción (cambio de estado visual, indicadores de carga).

-----------------------------------------------------------------------------------------------------------------------------------

## Clase 2. Affordance, Modelos Mentales y Mapeo Natural

**Affordance y Restricciones Visuales**
Los elementos interactivos deben comunicar explícitamente su función mediante su apariencia física digital:
       - Prohibido depender exclusivamente de etiquetas de texto explicativas como "Haga clic aquí".
       - Los elementos cliqueables deben incorporar pistas visuales: bordes definidos, relieve, sombras (box-shadow) y estados interactivos claros (:hover, :active).
**Modelos Mentales e Iconografía**
       - Los componentes deben alinearse con las convenciones culturales preexistentes del usuario.
       - Si se utilizan íconos abstractos o no estandarizados universalmente, es obligatorio acompañarlos de etiquetas de texto explicativas para evitar ambigüedades.
**Mapeo Natural**
La disposición de los controles debe imitar la lógica espacial y física del mundo real:
       - Proximidad física entre el control y el elemento que modifica (ej. botones de edición pegados directamente al componente correspondiente).
       - Relación directa de escala y movimiento: la variación en un control (ej. un slider) debe reflejarse de forma simultánea y proporcional en la representación visual del objeto.

-----------------------------------------------------------------------------------------------------------------------------------

## Clase 3. Leyes de Gestalt, Jerarquía Visual y Patrones de Lectura
**Leyes de Gestalt Aplicadas al Desarrollo**
[Proximidad]   -> Agrupamiento por Padding / Margin (elementos cercanos = mismo contexto).
[Semejanza]    -> Reutilización de clases CSS globales (ej. .btn-primary para misma acción).
[Continuidad]  -> Pistas visuales de desbordamiento (carruseles cortados para indicar scroll).

       - Ley de Proximidad: Ajuste estricto de margin y padding. Elementos relacionados (ej. etiqueta e input, o título, precio y botón de compra) deben tener un espaciado sensiblemente menor entre sí que respecto a otros grupos.
       - Ley de Semejanza: Consistencia estricta en componentes. Todos los elementos que cumplan una función análoga deben compartir la misma clase CSS, color y comportamiento.
       - Ley de Continuidad y Cierre: Disposición de elementos que guíe la vista. En listas o carruseles horizontales, los elementos del borde deben mostrarse ligeramente recortados para indicar la existencia de más contenido.
**Jerarquía Visual**
La atención visual se controla mediante tres variables críticas:
        1. Tamaño: Los elementos primarios deben escalar jerárquicamente (h1 > h2 > body > caption).
        2. Color y Contraste: Colores de alta saturación para llamadas a la acción (CTA) primarias; colores de baja saturación o grises para elementos secundarios o neutros.
        3. Espacio Negativo (Blanco): Uso intencional del aire visual para aislar módulos importantes y prevenir sobrecarga cognitiva.

**Patrones de Lectura**
        -Patrón en F: Aplicable a vistas densas en texto (documentación, paneles de información). Colocar términos clave y títulos resaltados a la izquierda.
        -Patrón en Z: Aplicable a Landing Pages y vistas principales.
                -Esquina Superior Izquierda: Identidad / Logo.
                -Esquina Superior Derecha: Acción secundaria / Acceso de usuario.
                -Centro: Elemento visual principal.
                -Inferior Centro/Izquierda: Llamada a la Acción Principal (CTA).

-----------------------------------------------------------------------------------------------------------------------------------

## Clase  4. Sistema de Diseño Visual: Color, Tipografía y Componentes UI

**Paleta Semántica de Colores**
Todos los colores aplicados deben responder a un rol técnico específico dentro de la aplicación:

┌──────────────────────┬──────────────────────────┬──────────────────────────────────────────────────────────────────────┐
│                      │                          │                                                                      │
│ Rol Semántico        │ Tono Sugerido            │ Función Técnica / Psicología                                         │
│                      │                          │                                                                      │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────────────────────────────────────┤
│                      │                          │                                                                      │
│ Primario             │ Azul / Celeste           │ Identidad de marca, confianza, acciones principales.                 │
│                      │                          │                                                                      │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────────────────────────────────────┤
│                      │                          │                                                                      │
│ Secundario           │ Gris / Variantes neutras │ Acciones secundarias, jerarquía de soporte ("Cancelar", "Ver más").  │
│                      │                          │                                                                      │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────────────────────────────────────┤
│                      │                          │                                                                      │
│ Success (Éxito)      │ Verde                    │ Confirmaciones, estados completados correctamente.                   │
│                      │                          │                                                                      │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────────────────────────────────────┤
│                      │                          │                                                                      │
│ Danger (Peligro)     │ Rojo                     │ Alertas críticas, errores del sistema, acciones destructivas.        │
│                      │                          │                                                                      │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────────────────────────────────────┤
│                      │                          │                                                                      │
│ Warning (Alerta)     │ Amarillo / Naranja       │ Precaución, estados intermedios, advertencias de sesión.             │
│                      │                          │                                                                      │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────────────────────────────────────┤
│                      │                          │                                                                      │
│ Info (Información)   │ Azul claro / Cian        │ Notificaciones secundarias, sugerencias contextuales.                │
│                      │                          │                                                                      │
└──────────────────────┴──────────────────────────┴──────────────────────────────────────────────────────────────────────┘

        -Regla de Contraste: Todos los pares de texto/fondo deben garantizar un contraste mínimo de 4.5:1 cumpliendo WCAG AA.

**Escala Tipográfica Sans-Serif**
Utilizar fuentes digitales sin serifas (Inter, Roboto, Helvetica) para optimizar la lectura en pantalla:

CSS
/* Escala de Tipografía Global */
--h1-size: 32px;      /* Título principal de pantalla */
--h2-size: 24px;      /* Títulos de secciones / Módulos */
--body-size: 16px;    /* Texto base / Formularios */
--caption-size: 12px; /* Letra chica, aclaraciones, fechas */

**Anatomía de Componentes y sus 5 Estados UI**
Cualquier componente interactivo (botones, inputs, selectores) debe tener definidos visualmente los siguientes 5 estados en CSS/Figma:
        1. Default (Reposo): Estado inicial neutro del componente.
        2. Hover (Sobrevuelo): Variación sutil de color o brillo que indica interactividad activa al posicionar el cursor.
        3. Active (Presionado): Cambio visual que simula la presión física (hundimiento/cambio de escala) en el instante del clic.
        4. Focus (Foco A11y): Borde o anillo de alto contraste que resalta la ubicación del elemento al navegar con teclado.
        5. Disabled (Deshabilitado): Reducción de opacidad/tono grisáceo con cursor deshabilitado (cursor: not-allowed), indicando la inactividad del elemento hasta cumplir ciertos requisitos.

-----------------------------------------------------------------------------------------------------------------------------------

## Clase  5. Diseño Centrado en el Usuario (DCU) y Arquetipos

**Bucle Iterativo del DCU**

El ciclo de desarrollo debe ejecutarse bajo 4 fases continuas:
[1. Entender Contexto] -> [2. Especificar Requisitos] -> [3. Producir Diseños] -> [4. Evaluar con Usuarios]
        ^                                                                                  |
        +---------------------------------- Iterar ----------------------------------------+

        1. Entender el Contexto de Uso: Investigar quién utiliza el sistema, bajo qué condiciones ambientales, de conectividad y en qué dispositivos.
        2. Especificar Requisitos: Traducir necesidades a requerimientos de UI (ej. tamaño de área táctil mínimo de 60px para trajes/guantes) y requerimientos de desarrollo (ej. almacenamiento local / caceo offline para inestabilidad de red).
        3. Producir Soluciones: Crear wireframes y prototipos funcionales sin saltar directamente al código final.
        4. Evaluar: Realizar pruebas de usabilidad con usuarios reales para identificar fallas antes del despliegue a producción.

**Definición de Personas (Arquetipos)**

Las fichas de usuario deben contemplar estrictamente:
        - Datos Reales: Basados en investigaciones, encuestas o analítica.
        - Contexto de Uso: Entorno físico, iluminación, calidad de red y tipo de dispositivo.
        - Puntos de Dolor (Frustraciones): Fricciones actuales a eliminar mediante la interfaz.
        - Objetivos y Motivaciones: La tarea exacta que el usuario necesita completar de manera eficiente.

-----------------------------------------------------------------------------------------------------------------------------------

## Clase  6. Arquitectura de Información (AI) y Card Sorting

**Los 4 Pilares de la Arquitectura de Información**

        1. Sistemas de Organización: Clasificación de datos por categorías, frecuencia de uso, secuencia de tareas u orden cronológico.
        2. Sistemas de Etiquetado (Labeling): Rotulado utilizando lenguaje claro y centrado en el usuario, eliminando nombres de variables, tablas de base de datos o lógica interna del backend.
        3. Sistemas de Navegación: Implementación de estructuras claras: menús principales, sidebars, pies de página y breadcrumbs (migas de pan) (Inicio > Categoria > Producto).
        4. Sistemas de Búsqueda: Barras de búsqueda con autocompletado y filtros para acelerar la localización de información.

**Metodologías de Card Sorting**

        - Abierto: Los usuarios agrupan tarjetas de contenido libremente y crean sus propias categorías. Utilizado en etapas iniciales para descubrir modelos mentales.
        - Cerrado: Los usuarios clasifican tarjetas dentro de categorías predefinidas. Utilizado para validar estructuras existentes.
        - Híbrido: Estructura con categorías predefinidas que permite al usuario añadir nuevas si considera que faltan.
