# CineCesde

## Integrantes

-   Juan Camilo Ramirez Sanchez
-   Holver David Yepes Hernandez
-   Carlos Sebastián Rivera Pantoja
-   Alejandro Rivera Caro

**Repositorio:**
https://github.com/areviRPC/Cine_Cesde_Primer_Momento.git

------------------------------------------------------------------------

## 1. Identificación del problema

El cine presenta baja asistencia a sus funciones debido a que las
personas solo pueden acceder a la boletería de manera física y no hay un
canal disponible para ver el catálogo y la disponibilidad de salas,
cartelera, horario y opciones de comida dentro del cine.

Las personas que acceden al servicio deben hacer largas filas debido a
que solo existe un punto físico de venta, perdiéndose una importante
oportunidad de crecimiento y atracción de nuevos clientes.

## 2. Identificar las entidades que lo componen

Después de un detenido estudio de la lógica de negocio y la dinámica
entre las entidades hemos concluido crear las siguientes entidades con
su respectivo comportamiento.

### Cliente

-   **Atributos:** `cedula` (String), `nombre` (String), `puntosCesde`
    (int)
-   **Comportamientos:** `acumularPuntos()` --- suma puntos de fidelidad
    cada vez que el cliente compra un ticket.
-   **Tipo de clase:** Concreta (independiente, no hereda ni es
    heredada).

### Empleado

-   **Atributos:** `idEmpleado` (String), `nombre` (String),
    `salarioBase` (double)
-   **Comportamientos:** `calcularSueldo() : double` --- cada subclase
    lo implementa a su manera.
-   **Tipo de clase:** Abstracta (padre de Taquillero y Confitero).

### Taquillero

-   **Atributos:** `boletasVendidas` (int)
-   **Comportamientos:** `calcularSueldo() : double` --- sobrescribe el
    de Empleado, probablemente sumando comisión por boleta vendida.
-   **Tipo de clase:** Concreta, hija de Empleado.

### Confitero

-   **Atributos:** `combosVendidos` (int)
-   **Comportamientos:** `calcularSueldo() : double` --- sobrescribe el
    de Empleado, sumando comisión por combo vendido.
-   **Tipo de clase:** Concreta, hija de Empleado.

### Ticket

-   **Atributos:** `asiento` (String), `precio` (double)
-   **Comportamientos:** `imprimirTicket()` --- genera/muestra el
    comprobante de la compra.
-   **Tipo de clase:** Concreta, asociada a Cliente, Sala, Pelicula y
    ComboComida.

### Sala

-   **Atributos:** `numeroSala` (int), `capacidadAsientos` (int)
-   **Comportamientos:** `obtenerTipoPantalla() : String` --- cada
    subclase define qué tipo de pantalla es.
-   **Tipo de clase:** Abstracta (padre de Sala2D y Sala3D).

### Sala2D

-   **Atributos:** `tieneSonidoDolby` (bool)
-   **Comportamientos:** `obtenerTipoPantalla()` --- sobrescribe el de
    Sala, devuelve `"2D"`.
-   **Tipo de clase:** Concreta, hija de Sala.

### Sala3D

-   **Atributos:** `versionGafas` (String)
-   **Comportamientos:** `obtenerTipoPantalla()` --- sobrescribe el de
    Sala, devuelve `"3D"`.
-   **Tipo de clase:** Concreta, hija de Sala.

### Pelicula

-   **Atributos:** `titulo` (String), `duracionMinutos` (int),
    `clasificacion` (String)
-   **Comportamientos:** `getTitulo() : String`
-   **Tipo de clase:** Concreta (independiente).

### ComboComida

-   **Atributos:** `nombreCombo` (String), `precio` (double)
-   **Comportamientos:** `setPrecio(precio: double)`
-   **Tipo de clase:** Concreta (independiente).

## 3. Usando abstracción identificar atributos y comportamientos

### Concepto

La abstracción es el proceso de identificar las características
relevantes para el problema y descartar todo lo que sea ruido.

Un Cliente en la vida real tiene miles de atributos posibles (edad,
dirección, color de ojos, teléfono...), pero para el sistema de un cine
solo importa lo que el software necesita usar.

**Analogía:** es como dibujar un plano de una casa --- no dibujas cada
clavo ni cada hilo eléctrico, solo lo que necesitas para construir y
entender la estructura.

### Aplicando abstracción a cada entidad

-   **Cliente:** se abstrajo como alguien que se identifica (`cedula`),
    tiene nombre y acumula beneficios (`puntosCesde`). Se descartó
    teléfono, dirección, correo e historial de compras porque no son
    necesarios para la lógica de negocio actual (acumular puntos).
-   **Empleado:** se abstrajo lo común a cualquier trabajador del cine:
    identificación, nombre y salario base. Se descartó fecha de
    contratación, horario y dirección porque lo único que el sistema
    necesita calcular es el sueldo.
-   **Taquillero / Confitero:** aquí la abstracción es más fina: solo se
    agregó el atributo que diferencia su forma de ganar comisión
    (`boletasVendidas` vs `combosVendidos`). No se repite nombre ni
    salario porque ya lo heredan de Empleado.
-   **Ticket:** se abstrajo como el resultado mínimo de una compra:
    asiento y precio. No se guardó, por ejemplo, la hora exacta de
    impresión o el método de pago, porque no forman parte del alcance
    del ejercicio.
-   **Sala / Sala2D / Sala3D:** lo común (`numeroSala`,
    `capacidadAsientos`) queda en el padre; lo que varía según el tipo
    de proyección (sonido Dolby, versión de gafas) se abstrae solo en la
    subclase correspondiente.
-   **Pelicula:** se abstrajo con lo mínimo para identificarla y
    filtrarla: título, duración y clasificación. Se descartó director,
    actores y sinopsis porque no se usan en la lógica del sistema.
-   **ComboComida:** solo nombre y precio, porque el sistema únicamente
    necesita mostrarlo y cobrarlo, no describir sus ingredientes.

## 4. Identificar relaciones de herencia

Solo hay dos jerarquías de herencia real (triángulo hueco).

Las demás flechas (Cliente → Ticket, Ticket → Pelicula, Ticket →
ComboComida, Ticket → Sala) son asociaciones, no herencia.

### Jerarquía 1: Empleado

``` text
Empleado (clase padre / abstracta)
├── Taquillero → "un Taquillero ES UN Empleado"
└── Confitero → "un Confitero ES UN Empleado"
```

### Jerarquía 2: Sala

``` text
Sala (clase padre / abstracta)
├── Sala2D → "una Sala2D ES UNA Sala"
└── Sala3D → "una Sala3D ES UNA Sala"
```

## 5. Identificar relaciones de asociación

### Asociación simple

-   **Cliente → Ticket:** un cliente compra tickets, pero un Ticket
    puede analizarse sin depender de que el objeto Cliente siga en
    memoria. Relación de uso.
-   **Ticket → Pelicula:** el ticket referencia una película, pero la
    Película existe independientemente (sigue en cartelera aunque se
    borren tickets).
-   **Ticket → ComboComida:** igual: el combo existe en el menú del cine
    sin importar si hay tickets que lo referencien.

### Composición

La parte no vive sin el todo.

-   **Ticket → Sala:** aquí hay un matiz interesante: si el ticket
    depende completamente de que exista una sala asignada para tener
    sentido, se modela como composición.
-   Pero si la Sala es un recurso físico del cine que existe
    independientemente del ticket (lo normal), en realidad es
    asociación, no composición --- la Sala no "muere" si se borra el
    Ticket.
