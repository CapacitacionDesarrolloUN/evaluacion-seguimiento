# Resultados de los sondeos SST y ELT 2027

Tablero de una sola página (`index.html`) con dos secciones: el sondeo de formación en SST 2027 y el de la Escuela de Liderazgo Transformador 2027. Se cambia entre ellas con el selector del encabezado (o Alt+1 / Alt+2).

Publicado en https://capacitaciondesarrolloun.github.io/evaluacion-seguimiento/sondeos/

## Cómo cargar los datos

1. Arrastra el botón *Cargar sondeos* a la barra de favoritos (solo la primera vez).
2. Abre cualquier lista de "Mis listas" de capacitacion@uninorte.edu.co y pulsa el favorito.
3. El favorito lee SST_Personas, SST_Respuestas, ELT_Personas y ELT_Respuestas con tu sesión (solo lectura) y se las pasa al tablero. Nada pasa por un servidor ni se guarda.

También acepta las listas exportadas a CSV (el nombre del archivo debe empezar por SST_ o ELT_).

## Cómo se calcula

- El avance compara los nombres de Respuestas con los de Personas, sin tildes ni mayúsculas.
- Como cada persona puede enviar el cuestionario varias veces, por defecto las gráficas usan su envío más reciente. El selector "Contar" permite usar todos.
- Prioridades (SST) y habilidades (ELT): 3 puntos al primer lugar, 2 al segundo y 1 al tercero.

## Edición

El archivo se genera a partir de piezas (núcleo común, módulo SST y módulo ELT). Para cambios pequeños se puede editar `index.html` directamente: los bloques `window.APPS.sst` y `window.APPS.elt` tienen las preguntas y gráficas de cada sondeo.
