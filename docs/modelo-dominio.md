# Modelo de dominio: base del proyecto

Adaptación del contenido de `Cine Cesde Documentacion (1).pdf`. Esta tabla conserva las entidades del análisis original; no significa que sus clases ya estén programadas en JavaScript.

| Entidad | Atributos originales | Comportamiento | Tipo |
| --- | --- | --- | --- |
| Cliente | cedula: String; nombre: String; puntosCesde: int | acumularPuntos() | Concreta |
| Empleado | idEmpleado: String; nombre: String; salarioBase: double | calcularSueldo(): double | Abstracta |
| Taquillero | boletasVendidas: int | calcularSueldo(): double | Hija de Empleado |
| Confitero | combosVendidos: int | calcularSueldo(): double | Hija de Empleado |
| Ticket | asiento: String; precio: double | imprimirTicket() | Concreta |
| Sala | numeroSala: int; capacidadAsientos: int | obtenerTipoPantalla(): String | Abstracta |
| Sala2D | tieneSonidoDolby: bool | obtenerTipoPantalla(): "2D" | Hija de Sala |
| Sala3D | versionGafas: String | obtenerTipoPantalla(): "3D" | Hija de Sala |
| Pelicula | titulo: String; duracionMinutos: int; clasificacion: String | getTitulo(): String | Concreta |
| ComboComida | nombreCombo: String; precio: double | setPrecio(precio) | Concreta |

## Abstracción

Se conservan los datos necesarios para la lógica del cine. Cliente se identifica y acumula puntos; Ticket representa el asiento y precio; Pelicula aporta título, duración y clasificación; ComboComida aporta nombre y precio. Empleado y Sala reúnen datos comunes y sus subclases especializan comportamientos. Teléfono, dirección y otros datos no requeridos se excluyen del modelo base.

## Relaciones

- Herencia: Empleado es padre de Taquillero y Confitero. Sala es padre de Sala2D y Sala3D.
- Asociación: Cliente compra Ticket; Ticket referencia Pelicula, Sala y, opcionalmente, ComboComida.
- Sala existe aunque se elimine un ticket; por ello Ticket-Sala se mantiene como asociación. El documento original plantea esta aclaración, aunque su último párrafo está cortado.

## Ajustes propuestos para la página

Se agrega conceptualmente **Funcion** con identificador, película, sala, fecha, hora, precio y asientos ocupados. La disponibilidad se debe consultar por función, no solo por sala. Para varios asientos se generan líneas o tickets por asiento dentro de un resumen de compra.

HTML y CSS mostrarán los datos; JavaScript administrará objetos y listas locales. No es obligatorio reproducir todas las clases del ejercicio de POO para crear la interfaz.

Empleado, Taquillero y Confitero se conservan como documentación de origen, pero su cálculo salarial no integra el MVP. Las comisiones y la tasa de acumulación de puntos no estaban definidas: cualquier regla nueva se identifica como propuesta.
