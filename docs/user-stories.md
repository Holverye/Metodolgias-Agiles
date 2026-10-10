# Historias de usuario

Cada historia mantiene el mismo identificador, épica, feature y estimación del Product Backlog. Los criterios propuestos deben revisarse con el equipo antes de programar.

## US-01: Consultar cartelera

**Épica:** EP-01 · **Feature:** FE-01 · **Prioridad:** Alta · **Estimación:** 3 puntos · **Estado:** To Do

Como **visitante**, quiero **consultar las películas en cartelera**, para **elegir qué película ver**.

**Dependencias:** Ninguna.

### Criterios de aceptación

- CA-01: Dado un catálogo con películas, cuando abro la cartelera, entonces veo título, duración y clasificación de cada película.
- CA-02: Dado un catálogo vacío, cuando abro la cartelera, entonces aparece el mensaje "No hay películas disponibles".
- CA-03: Dada una pantalla de 360 px y otra de 1366 px, cuando consulto la cartelera, entonces las tarjetas se leen sin desplazamiento horizontal.

## US-02: Consultar detalle

**Épica:** EP-01 · **Feature:** FE-02 · **Prioridad:** Alta · **Estimación:** 2 puntos · **Estado:** To Do

Como **visitante**, quiero **ver el detalle de una película**, para **conocer su duración y clasificación antes de elegir**.

**Dependencias:** US-01.

### Criterios de aceptación

- CA-01: Dada una película visible, cuando selecciono su título, entonces se muestra su título, duración y clasificación.
- CA-02: Dado el detalle abierto, cuando regreso a la cartelera, entonces puedo seleccionar otra película.
- CA-03: Dado un identificador inexistente, cuando intento abrir el detalle, entonces se informa que la película no está disponible.

## US-03: Consultar funciones

**Épica:** EP-01 · **Feature:** FE-02 · **Prioridad:** Alta · **Estimación:** 3 puntos · **Estado:** To Do

Como **cliente**, quiero **consultar las funciones de una película**, para **elegir fecha, hora y tipo de sala**.

**Dependencias:** US-02.

### Criterios de aceptación

- CA-01: Dada una película con funciones, cuando las consulto, entonces veo fecha, hora, sala, tipo 2D o 3D y precio en COP.
- CA-02: Dada una película sin funciones, cuando las consulto, entonces veo "No hay funciones disponibles".
- CA-03: Dadas funciones pasadas y futuras, cuando consulto las disponibles, entonces solo puedo seleccionar las futuras respecto a la fecha y hora del dispositivo.

## US-04: Buscar película

**Épica:** EP-01 · **Feature:** FE-01 · **Prioridad:** Media · **Estimación:** 2 puntos · **Estado:** To Do

Como **visitante**, quiero **buscar una película por su título**, para **encontrarla rápidamente**.

**Dependencias:** US-01.

### Criterios de aceptación

- CA-01: Dada la cartelera, cuando escribo parte de un título, entonces se muestran las coincidencias sin distinguir mayúsculas y minúsculas.
- CA-02: Dada una búsqueda sin resultados, cuando se aplica, entonces se muestra "No se encontraron películas".
- CA-03: Dado un filtro activo, cuando borro el texto, entonces vuelve a mostrarse toda la cartelera.

## US-05: Seleccionar asientos

**Épica:** EP-02 · **Feature:** FE-03 · **Prioridad:** Alta · **Estimación:** 5 puntos · **Estado:** To Do

Como **cliente**, quiero **seleccionar asientos disponibles de una función**, para **ubicar mi lugar en la simulación**.

**Dependencias:** US-03.

### Criterios de aceptación

- CA-01: Dada una función seleccionada, cuando abro el mapa, entonces distingo asientos disponibles, ocupados y seleccionados.
- CA-02: Dado un asiento ocupado en los datos de ejemplo, cuando lo pulso, entonces no se agrega a la selección.
- CA-03: Dado un asiento disponible, cuando lo selecciono y lo vuelvo a pulsar, entonces se agrega y luego se retira.
- CA-04: Dado que cambio de función, cuando se carga el nuevo mapa, entonces se limpia la selección anterior.

## US-06: Consultar combos

**Épica:** EP-03 · **Feature:** FE-05 · **Prioridad:** Media · **Estimación:** 2 puntos · **Estado:** To Do

Como **visitante**, quiero **ver los combos de comida**, para **comparar las opciones y sus precios**.

**Dependencias:** Ninguna.

### Criterios de aceptación

- CA-01: Dado un catálogo de combos, cuando lo consulto, entonces veo nombre y precio en COP de cada uno.
- CA-02: Dado un catálogo vacío, cuando lo consulto, entonces aparece "No hay combos disponibles".
- CA-03: Dado un precio cero o negativo en los datos, cuando se carga el catálogo, entonces ese combo se señala como no disponible para agregar.

## US-07: Agregar combos

**Épica:** EP-03 · **Feature:** FE-06 · **Prioridad:** Media · **Estimación:** 3 puntos · **Estado:** To Do

Como **cliente**, quiero **agregar o quitar combos de mi compra simulada**, para **personalizar mi pedido**.

**Dependencias:** US-05, US-06.

### Criterios de aceptación

- CA-01: Dado un combo disponible, cuando indico una cantidad entera entre 1 y 10, entonces se agrega al pedido y se actualiza su subtotal.
- CA-02: Dada una cantidad negativa, decimal o mayor de 10, cuando intento agregarla, entonces aparece un mensaje y no se modifica el pedido.
- CA-03: Dado un combo agregado, cuando lo elimino, entonces se retira y su subtotal deja de sumarse.
- CA-04: Dado un pedido sin combos, cuando continúo, entonces puedo comprar únicamente boletería de demostración.

## US-08: Consultar total

**Épica:** EP-02 · **Feature:** FE-04 · **Prioridad:** Alta · **Estimación:** 3 puntos · **Estado:** To Do

Como **cliente**, quiero **ver el resumen y total de mi selección**, para **revisar lo que estoy eligiendo**.

**Dependencias:** US-05, US-07.

### Criterios de aceptación

- CA-01: Dada una selección, cuando abro el resumen, entonces veo película, función, sala, asientos y combos con sus cantidades.
- CA-02: Dados 2 asientos de $15.000 y 1 combo de $12.000, cuando calculo el total, entonces el resultado es $42.000 COP.
- CA-03: Dado que retiro un asiento o combo, cuando consulto el resumen, entonces el total se recalcula.
- CA-04: Dada una selección sin asientos, cuando intento confirmar, entonces se bloquea la confirmación y se pide escoger al menos uno.

## US-09: Generar comprobante

**Épica:** EP-02 · **Feature:** FE-04 · **Prioridad:** Alta · **Estimación:** 3 puntos · **Estado:** To Do

Como **cliente**, quiero **generar un comprobante de demostración**, para **conservar el detalle de la selección**.

**Dependencias:** US-08.

### Criterios de aceptación

- CA-01: Dado un pedido válido, cuando confirmo, entonces el comprobante muestra identificador local, película, función, sala, asientos, combos y total.
- CA-02: Dado el comprobante, cuando lo leo, entonces aparece "SIMULACIÓN ACADÉMICA: no válido para ingreso ni pago".
- CA-03: Dada una confirmación realizada, cuando pulso nuevamente confirmar, entonces no se genera otro comprobante para el mismo pedido.

## US-10: Simular puntos

**Épica:** EP-04 · **Feature:** FE-07 · **Prioridad:** Baja · **Estimación:** 3 puntos · **Estado:** To Do

Como **cliente**, quiero **ver puntos de demostración por mi compra**, para **comprender el beneficio de fidelización**.

**Dependencias:** US-09.

### Criterios de aceptación

- CA-01: Dado un cliente con cédula y nombre de ejemplo, cuando confirmo 2 tickets, entonces su saldo local aumenta 20 puntos conforme a la regla propuesta de 10 por ticket.
- CA-02: Dado un pedido con combos, cuando confirmo, entonces los combos no suman puntos.
- CA-03: Dado un comprobante ya registrado, cuando vuelvo a abrirlo, entonces no se vuelven a acumular puntos.

## US-11: Editar películas de ejemplo

**Épica:** EP-05 · **Feature:** FE-08 · **Prioridad:** Baja · **Estimación:** 5 puntos · **Estado:** To Do

Como **encargado del prototipo**, quiero **editar el catálogo local de películas**, para **mantener actualizada la demostración**.

**Dependencias:** US-01.

### Criterios de aceptación

- CA-01: Dado el editor local, cuando guardo un título, duración entera positiva y clasificación no vacíos, entonces la película aparece en la cartelera.
- CA-02: Dado un formulario incompleto, cuando intento guardar, entonces se informan los campos inválidos y no se agrega la película.
- CA-03: Dada una película vinculada a funciones, cuando intento eliminarla, entonces se bloquea la eliminación hasta retirar esas funciones.

## US-12: Editar funciones de ejemplo

**Épica:** EP-05 · **Feature:** FE-08 · **Prioridad:** Baja · **Estimación:** 5 puntos · **Estado:** To Do

Como **encargado del prototipo**, quiero **asociar películas a salas y horarios**, para **organizar la programación de demostración**.

**Dependencias:** US-03, US-11.

### Criterios de aceptación

- CA-01: Dada una película y sala existentes, cuando registro una fecha y hora futuras y un precio positivo, entonces se agrega la función con identificador único local.
- CA-02: Dada una sala con una función existente, cuando registro otra que se solapa con la duración de la película más 15 minutos de limpieza, entonces se rechaza.
- CA-03: Dada una sala 3D, cuando consulto la nueva función, entonces se identifica como 3D.

## Reglas propuestas y límites

Los límites de 10 combos por tipo, 10 puntos por ticket y 15 minutos de limpieza son propuestas del taller, no reglas del documento original. Todo el flujo opera con datos de ejemplo; las historias de edición local no constituyen un módulo seguro de administración para producción. No se agrega registro de cuentas porque no es necesario para el MVP.
