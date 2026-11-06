# Decisiones de diseño

## 1. Color

### Elección

He creado una paleta azul basada en el tono OKLCH 262°, asignado al Caso 07, Residencial Los Almendros.

Para el tema claro se utiliza un azul oscuro como color de acento. Para el tema oscuro se utiliza un azul más claro. De esta forma se mantiene un contraste suficiente en ambos temas.

### Motivo

La escala incluye colores desde acento-50 hasta acento-950. Esto permite utilizar la misma familia de color en botones, enlaces, fondos suaves, estados seleccionados y anillos de foco.

### Alternativas descartadas

He descartado utilizar un único azul para todos los elementos porque no tendría contraste suficiente en los dos temas. También he descartado escribir colores directamente en los componentes, ya que dificultaría cambiar el aspecto del proyecto.

## 2. Tipografía

### Elección

He utilizado la pila de fuentes del sistema `system-ui`, con una base de 16 px en móvil y 18 px en escritorio.

La escala utiliza una razón de 1,2 en móvil y 1,25 en escritorio. Los tamaños se publican en `rem` mediante valores fluidos con `clamp()`.

### Motivo

Las fuentes del sistema no requieren descargas, mejoran el rendimiento y se adaptan al sistema operativo del usuario. La escala fluida permite que los textos crezcan según el ancho de la pantalla sin perder accesibilidad.

### Alternativas descartadas

He descartado utilizar una fuente externa porque aumentaría el tiempo de carga y sería necesario documentar su licencia. También he descartado tamaños fijos en píxeles porque dificultan el cambio de tamaño del texto.

## 3. Espaciado y formas

### Elección

He utilizado una escala de espaciado basada en múltiplos de 4 px, desde 4 px hasta 64 px. Los valores se transforman a `rem` durante la compilación.

Los controles utilizan un radio de 8 px y las tarjetas un radio de 12 px.

### Motivo

Una escala limitada mantiene la separación uniforme entre los elementos. Los radios diferencian visualmente los controles de las tarjetas sin utilizar valores sueltos.

### Alternativas descartadas

He descartado escribir márgenes y rellenos manualmente en cada componente porque produciría inconsistencias y dificultaría el mantenimiento.

## 4. Componentes

### Botón

El botón utiliza el color de acento, texto con contraste y un tamaño táctil mínimo de 44 px. Incluye estados normal, hover, foco y desactivado.

### Tarjeta de turno

La tarjeta de turno está construida con un `label` que contiene un campo de tipo `radio`. Incluye los estados disponible, seleccionado, ocupado y foco.

El estado seleccionado cambia el fondo y el borde. El estado ocupado utiliza también un borde discontinuo y el texto “Ocupado”, por lo que no depende solamente del color.

### Contador de invitados

El contador utiliza un `fieldset` con cuatro radios para seleccionar entre 0 y 3 invitados. La opción marcada utiliza un borde más grueso, un fondo tenue y texto en negrita.

### Aviso de pago

El aviso presenta el importe, el teléfono de Bizum y el concepto. Utiliza un borde de acento, un fondo tenue y una fuente monoespaciada para el concepto.

## 5. Herramienta de diseño

### Elección

He elegido la ruta B, diseño directamente en código con Visual Studio Code.

### Comparación

- **Figma:** facilita el diseño visual, los componentes y la colaboración, pero después hay que trasladar las decisiones al código.
- **Penpot:** es una alternativa de código abierto y permite colaboración, pero también requiere trasladar el diseño al proyecto.
- **Diseño en código:** permite comprobar directamente el contraste, el tema, el foco y el comportamiento real de los componentes.

### Decisión

He elegido diseñar en código porque `guia.html` permite probar los componentes en el navegador y comprobar los cambios inmediatamente. La fuente de verdad sigue siendo `_tokens.scss`.

## 6. Tecnología de estilos

### Elección

He utilizado Sass modular con `@use` y `@forward`, junto con Custom Properties de CSS.

### Comparación

- **Sass:** permite utilizar mapas, funciones, mixins, bucles y archivos parciales.
- **CSS nativo:** podría utilizar Custom Properties, pero la generación y comprobación de escalas sería más manual.
- **Framework CSS:** aceleraría algunos estilos, pero dificultaría aplicar el sistema de tokens y las reglas específicas del proyecto.

### Decisión

Sass se utiliza para operaciones realizadas durante la compilación, como mapas, funciones, contrastes y conversión a `rem`.

Las Custom Properties se utilizan para colores, tipografía, espacios y formas porque deben estar disponibles en el navegador y cambiar con el tema.

## 7. Cascada y nomenclatura

Los estilos están organizados mediante `@layer`, por lo que la capa de componentes se aplica después de la capa base.

Las clases siguen la metodología BEM, por ejemplo:

- `.turno`
- `.turno__hora`
- `.turno__estado`
- `.invitados__opcion`
- `.aviso__concepto`

La especificidad máxima se mantiene en `(0,2,0)` y no se utiliza `!important`.

## 8. Datos del proyecto

Todos los datos de Residencial Los Almendros son ficticios y se utilizan únicamente para este proyecto académico de Diseño de Interfaces Web.