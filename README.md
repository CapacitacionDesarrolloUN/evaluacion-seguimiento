# Seguimiento de la evaluación de desempeño

Tablero para ver cómo va la campaña de evaluación de desempeño de la Universidad del Norte: qué porcentaje de cuestionarios está respondido, qué jefes faltan, quién falta dentro de cada equipo y cuál es el promedio de las respuestas.

Es una sola página (`index.html`, sin servidor ni dependencias). **No guarda ni publica datos de evaluación**: los datos se leen en tu navegador, se calculan ahí y desaparecen al cerrar la pestaña. Este repositorio no contiene ninguna respuesta ni lista de personas.

## Qué muestra

- Porcentaje de cuestionarios respondidos (respondidos de total), cuántos faltan, cuántos llegaron hoy y en los últimos 7 días, y los días que faltan para el cierre.
- Un mapa de cuestionarios: un cuadro por cuestionario, agrupados en un bloque por jefe. Los respondidos se ven en amarillo roble y los pendientes, apagados. Al tocar un bloque se abre ese jefe en la lista.
- Promedio general, promedio por pregunta y por bloque (Gestión, Servicio, Seguridad y salud en el trabajo), y respuestas por día.
- Jefes agrupados en Sin iniciar, En curso y Completos. La lista arranca en Todos y se busca por líder o por técnico o auxiliar, según lo que se elija antes de escribir.
- Al abrir un jefe: quién falta por evaluar y quién ya fue evaluado (con fecha y promedio), y al lado del nombre el porcentaje de evaluaciones respondidas.
- Al tocar a alguien ya evaluado: su respuesta completa, con todas las preguntas, su gráfica y un botón para descargarla en PDF. El PDF se arma en el navegador.
- Mejores y peores calificaciones: personas ordenadas por promedio, de mejor a peor por defecto; el ícono de filtro cambia el orden.
- Respuestas en gráfica: línea con la calificación en el eje vertical y la pregunta en el horizontal, para el promedio de todos o para una persona.
- Qué pregunta es cuál: el texto completo de G1 a SST3.
- Botones para copiar los nombres de los jefes que faltan o descargarlos en CSV, para armar los recordatorios.
- "Revisión de datos": respuestas que no coinciden con ninguna relación jefe–subordinado (no cuentan en el avance ni en el promedio) y nombres repetidos.

## Cómo cargar los datos

**Opción 1: favorito "Cargar al tablero" (recomendada).**
1. Abre el tablero y arrastra el botón *Cargar al tablero* (pantalla de inicio o *Actualizar datos*) a la barra de favoritos. Solo hay que hacerlo una vez.
2. Abre cualquiera de las listas Relaciones o Respuestas en SharePoint ("Mis listas" de capacitacion@uninorte.edu.co) y pulsa el favorito.
3. El favorito lee las dos listas con tu sesión (solo lectura) y se las entrega al tablero. Los datos no pasan por ningún servidor. El tablero solo acepta datos que vengan de `uninorte-my.sharepoint.com` o `uninorte.sharepoint.com`.

**Opción 2: archivos.** En cada lista usa Exportar → Exportar a CSV y sube ambos archivos a la vez (*Elegir archivos* o arrastrándolos). Acepta `.csv` con coma o punto y coma, y `.xlsx`/`.xls` (para Excel descarga el lector SheetJS desde cdnjs la primera vez).

Sin datos, el tablero ofrece *Ver datos de ejemplo*, con información inventada.

## Cómo se calcula

- Un cuestionario cuenta como respondido cuando existe una fila en Respuestas con el mismo jefe y subordinado que en Relaciones. Los nombres se comparan sin tildes, sin importar mayúsculas ni espacios dobles.
- Si hay varias respuestas para el mismo par, cuenta la más reciente.
- El promedio es el de la columna Promedio de cada respuesta (media simple de las 12 preguntas).
- La escala se asume de 1 a 5. Si en los datos aparece un valor mayor, la escala se ajusta sola. Si la app califica de otra forma, cámbialo en `CONFIG.escalaMax`.

## Configuración

Todo está en el bloque `CONFIG` al inicio del script de `index.html`: fecha de cierre, zona horaria, escala, orígenes de SharePoint permitidos, nombres de las listas, bloques y preguntas, nombre corto (`textos`) y texto completo (`completas`) de cada pregunta, y niveles de respuesta (`niveles`).

## Diseño

Colores de la marca Uninorte (rojo hondo, rojo, amarillo roble y negro) y tipografía Nunito, que se pide a Google Fonts (esa petición solo descarga la letra; no lleva datos de la evaluación). Si no carga, se usan Poppins e Inter, incrustadas en `index.html` (licencia SIL OFL 1.1). Hay tema claro y oscuro, y animaciones que se apagan si el sistema pide reducir el movimiento.

## Publicación

GitHub Pages, desde la rama `main` y la carpeta raíz. El archivo `.nojekyll` evita que Pages procese la carpeta. Cualquier cambio en `index.html` se publica solo al hacer push.

## Privacidad

El repositorio es público porque no tiene datos. La evaluación es confidencial: no cargues datos reales en copias del tablero que alojes en otro sitio ni subas exportaciones (CSV) al repositorio.
