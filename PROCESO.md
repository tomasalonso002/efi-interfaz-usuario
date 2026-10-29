# Proceso de Desarrollo: De la Teoría a la Práctica
**Proyecto:** Patitas Conectadas (Refugio de Animales)  
**Referencia:** Contenidos de las Clases y `especioficaciones.md`

En este documento explicamos de forma simple y directa cómo fuimos aplicando lo aprendido en cada clase para construir el sistema web (HTML y CSS). No nos quedamos solo con la teoría, sino que mostramos exactamente en qué pantallas y componentes se usó cada concepto, con 3 o 4 ejemplos claros por clase.

---

## Clase 1: Usabilidad y Accesibilidad (A11y / WCAG)

### ¿Qué nos pedía la teoría?
Hacer una web que cualquier persona pueda usar sin trabas, que sea fácil de entender, rápida de completar y accesible para personas que navegan con teclado o lectores de pantalla (reglas WCAG: contraste de colores de al menos 4.5:1, etiquetas alt en imágenes, foco visible y validaciones al instante para no frustrar al usuario).

### ¿Cómo lo implementamos en el proyecto?
* **Ejemplo 1 (Contraste de color):** En `css/variables.css`, elegimos un texto casi negro (`#191c1f`) sobre fondo blanco (`#ffffff`) que da un ratio de 15.8:1, y los botones principales terracota (`#df7054`) tienen letras blancas con ratio de 4.7:1, superando el mínimo de 4.5:1 exigido por la norma.
* **Ejemplo 2 (Navegación por teclado y foco visible):** En `css/reset.css`, definimos que al presionar la tecla `Tab`, cualquier botón, input o enlace muestre un borde grueso y bien visible (`:focus-visible { outline: 3px solid var(--color-primary); }`). Se puede probar en `autenticacion/iniciar_sesion.html` navegando solo con el teclado sin tocar el mouse.
* **Ejemplo 3 (Imágenes con descripción):** En `autenticacion/inicio.html` y `usuario/animales.html`, ninguna imagen tiene textos genéricos como "foto". Todas describen lo que se ve para los lectores de pantalla: `alt="Milo, perro mestizo tamaño mediano de 2 años"`.
* **Ejemplo 4 (Validación en tiempo real sin frustración):** En `autenticacion/iniciar_sesion.html` y `autenticacion/registrarme.html`, los campos de correo y contraseña avisan inmediatamente si hay un error con un texto explicativo claro abajo del input (sin tener que apretar "Enviar" para recién enterarse de que algo estaba mal).

---

## Clase 2: Affordance, Modelos Mentales y Mapeo Natural

### ¿Qué nos pedía la teoría?
Que las cosas parezcan lo que son. Un botón tiene que parecer un botón (con relieve, sombra o bordes que inviten a hacer clic), no depender de textos como "Haga clic aquí", usar íconos que la gente ya conoce por su vida cotidiana y ubicar los controles pegados a lo que modifican (mapeo natural).

### ¿Cómo lo implementamos en el proyecto?
* **Ejemplo 1 (Affordance en botones):** En `css/components.css`, la clase `.btn` tiene forma de píldora redondeada, sombra suave y un efecto físico: cuando pasas el mouse flota un poquito hacia arriba (`translateY(-1px)`) y cuando hacés clic se hunde levemente (`translateY(1px)`). Esto se nota en el botón *"Adoptar Mascotas"* de `usuario/inicio.html`.
* **Ejemplo 2 (Modelos mentales en íconos):** En lugar de inventar símbolos raros, usamos convenciones que todos ya entienden: el candado (🔒) para contraseñas en `autenticacion/iniciar_sesion.html`, la patita (🐾) para los animales, el tacho de basura (🗑️) para borrar y el corazón (❤️) para favoritos.
* **Ejemplo 3 (Mapeo natural del corazón de favoritos):** En `usuario/animales.html`, el botón de favoritos no está suelto en una esquina de la pantalla: está flotando sobre la esquina inferior de la propia foto del animal que querés guardar.
* **Ejemplo 4 (Control de contraseña integrado):** En `autenticacion/iniciar_sesion.html`, el botón del ojito (👁️) para mostrar u ocultar la clave está ubicado exactamente dentro del input en el lateral derecho, donde la gente espera encontrarlo naturalmente.

---

## Clase 3: Leyes de Gestalt, Jerarquía Visual y Patrones de Lectura

### ¿Qué nos pedía la teoría?
Organizar la pantalla para que el cerebro del usuario no se canse. Aplicar la ley de proximidad (lo que va junto, espaciarlo más cerca), semejanza (lo que hace lo mismo tiene que verse igual), continuidad (mostrar cosas cortadas para que se entienda que hay más scroll) y ordenar la vista según cómo lee la gente (patrón en Z para landings y patrón en F para paneles).

### ¿Cómo lo implementamos en el proyecto?
* **Ejemplo 1 (Ley de Proximidad):** En los formularios de `autenticacion/registrarme.html` y `admin/nuevo_animal.html`, la etiqueta (`<label>`) está pegadita a su input con solo 8px (`--space-2`), mientras que la separación con el siguiente campo es el doble (16px, `--space-4`). Así el ojo agrupa automáticamente qué etiqueta pertenece a qué campo.
* **Ejemplo 2 (Ley de Semejanza):** Todos los botones primarios del sistema comparten la misma clase global `.btn-primary` y el mismo color terracota. Si el usuario ve ese color en `usuario/inicio.html` o en `admin/crear_tarea.html`, ya sabe de inmediato que es la acción principal de la pantalla.
* **Ejemplo 3 (Ley de Continuidad / Scroll):** En `usuario/animales.html`, los chips de categorías (`✨ Todos`, `🐶 Perros`, `🐱 Gatos`) tienen un desbordamiento horizontal suave que insinúa que se puede deslizar con el dedo.
* **Ejemplo 4 (Patrón de lectura en Z):** En `autenticacion/inicio.html`, diseñamos la página para que la vista haga el recorrido natural: arriba a la izquierda el logo del refugio, arriba a la derecha el botón de ingreso, al centro las fotos destacadas y abajo la llamada a la acción principal bien grande: *"Registrarme"*.

---

## Clase 4: Sistema de Diseño Visual (Colores, Tipografía y Estados UI)

### ¿Qué nos pedía la teoría?
Armar un sistema visual coherente con una paleta de colores con significado (semántica), una escala tipográfica clara (H1 > H2 > H3 > Body > Caption) y obligatoriamente programar los **5 estados visuales** de los componentes: reposo (Default), pasar el mouse (Hover), hacer clic (Active), foco de teclado (Focus) y deshabilitado (Disabled).

### ¿Cómo lo implementamos en el proyecto?
* **Ejemplo 1 (Paleta con significado semántico):** En `css/variables.css`, definimos colores con funciones claras:
  - Terracota cálido (`--color-primary`) para la identidad del refugio.
  - Verde esmeralda (`--color-green` / `--color-success`) para *"Disponible"*, login y tareas completadas.
  - Rojo (`--color-danger`) para acciones destructivas como el modal de eliminar animal en `admin/detalle_animal.html`.
  - Amarillo (`--color-warning`) para tareas pendientes y solicitudes en revisión.
* **Ejemplo 2 (Escala tipográfica estricta):** Cumplimos al pie de la letra los tamaños pedidos: H1 de 32px para los títulos principales, H2 de 24px con un puntito terracota característico para secciones, texto normal de 16px para lectura cómoda y letra chica (caption) de 12px para fechas y aclaraciones.
* **Ejemplo 3 (Los 5 estados de los botones):** En `css/components.css`, cada botón tiene sus 5 estados desarrollados. Por ejemplo, en `design-system.html` podés ver y probar el botón primario en reposo, al pasarle el cursor, al presionarlo, al seleccionarlo con tabulador y en gris deshabilitado con cursor bloqueado (`cursor: not-allowed`).
* **Ejemplo 4 (Diseño responsivo real):** Hicimos que el contenedor `.app-shell` se adapte con gracia. En un teléfono celular se usa a una sola mano en una columna, y al abrir la pantalla en una tablet o computadora de escritorio (como en `usuario/animales.html` o `admin/panel_administracion.html`), las tarjetas se acomodan solas en 2, 3 o 4 columnas aprovechando todo el ancho.

---

## Clase 5: Diseño Centrado en el Usuario (DCU) y Arquetipos

### ¿Qué nos pedía la teoría?
Diseñar pensando en quién usa el sistema, sus objetivos reales, sus necesidades y sus puntos de dolor. No hacer una sola interfaz genérica, sino crear interfaces pensadas a medida para cada perfil o arquetipo de persona.

### ¿Cómo lo implementamos en el proyecto?
* **Ejemplo 1 (Arquetipo Adoptante / Usuario):** La persona que busca adoptar no quiere ver paneles complejos de administración, quiere ver fotos grandes, conocer el carácter del animal y postularse fácil. En `usuario/detalle_animal.html` pusimos un carrusel de fotos grandes de Toby, sus datos de edad/tamaño, si necesita patio y un botón bien claro de *"Solicitar Adopción"*.
* **Ejemplo 2 (Arquetipo Voluntario / Cuidadores):** El voluntario llega al refugio a trabajar y necesita saber rápido qué tiene que hacer hoy sin perder tiempo. Por eso en `voluntario/inicio.html` tiene un acceso directo a *"Tareas"*, y en `voluntario/tareas.html` ve primero las tareas incompletas y prioritarias (*"Baño de Mango"*, canil 3, 30 min) con instrucciones claras de veterinaria.
* **Ejemplo 3 (Arquetipo Administrador):** El administrador necesita supervisar todo el refugio de un vistazo. En `admin/panel_administracion.html` creamos un tablero con 4 números grandes: cuántos animales hay (15/20), cuántos listos para adoptar (12), cuántas solicitudes esperan respuesta (1) y cuántos voluntarios están de turno hoy (6).
* **Ejemplo 4 (Salvaguarda para evitar errores graves):** Para proteger al usuario de clics por error, en `admin/detalle_animal.html` no se borra un animal de una; se abre un modal de confirmación con advertencia de que la acción es irreversible (`admin/confirmacion_borrar_animal.png`), y tras confirmarlo muestra la alerta de borrado exitoso (`admin/alert_animal_se_borro.png`).

---

## Clase 6: Arquitectura de Información (AI) y Card Sorting

### ¿Qué nos pedía la teoría?
Estructurar los contenidos de manera lógica: organizar la información, usar un vocabulario claro y humano (labeling), ofrecer sistemas de navegación simples (menús, sidebars, botones de volver) y mecanismos para filtrar o buscar.

### ¿Cómo lo implementamos en el proyecto?
* **Ejemplo 1 (Vocabulario humano y claro):** En todas las pantallas eliminamos cualquier término técnico interno del sistema o de base de datos. En vez de poner `SELECT * FROM PETS WHERE STATUS = 1`, la interfaz dice *"Nuestros animales en adopción"*, y en vez de `ID_VOL_44`, dice *"Franco (Sector A)"*.
* **Ejemplo 2 (Menú lateral Drawer unificado):** Tanto en usuario, voluntario como en admin, creamos un menú deslizable accesible (`.drawer-menu`) que muestra en qué sección estás parado, a dónde podés ir con un toque y un botón bien visible para *"Cerrar Sesión"*.
* **Ejemplo 3 (Navegación con retorno seguro):** En pantallas hijas de detalle (como `usuario/detalle_animal.html`, `voluntario/detalle_tarea_incompleta.html` o `admin/nuevo_voluntario.html`), agregamos siempre un botón de volver (`‹`) en la barra superior para que el usuario nunca se sienta atrapado y pueda regresar fácilmente a la pantalla anterior.
* **Ejemplo 4 (Organización y filtros lógicos):** En `usuario/animales.html`, clasificamos el contenido en las categorías más buscadas por los adoptantes (*Todos*, *Perros*, *Gatos*), permitiendo filtrar los animales al instante sin tener que recargar la página.
