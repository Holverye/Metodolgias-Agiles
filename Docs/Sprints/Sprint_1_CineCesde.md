# 🟦 SPRINT 1 — Consulta de cartelera

**Proyecto:** CineCesde  
**Duración sugerida:** 1 semana  
**Objetivo:** Crear la primera versión funcional de CineCesde que permita al usuario consultar las películas disponibles y conocer información básica de cada una.

---

## 🎯 Objetivo del Sprint

> **Como cliente del CineCesde, quiero consultar las películas disponibles y su información básica, para poder conocer la cartelera antes de comprar una entrada.**

Este Sprint se concentra inicialmente en la entidad **Pelicula**, con los atributos `titulo`, `duracionMinutos` y `clasificacion`, y el comportamiento `getTitulo()`.

---

# 📋 Historias de usuario

## HU-01 — Visualizar cartelera

**Como** cliente  
**Quiero** visualizar las películas disponibles  
**Para** conocer la cartelera del cine.

### Criterios de aceptación

**CA-01**
- Dado que el usuario ingresa a la sección de cartelera,
- cuando existen películas registradas,
- entonces el sistema debe mostrar las películas disponibles.

**CA-02**

Cada película debe mostrar como mínimo:
- Título
- Duración
- Clasificación

**CA-03**

Si no existen películas registradas, el sistema debe mostrar:

> "No hay películas disponibles actualmente."

---

## 🎬 HU-02 — Consultar información de una película

**Como** cliente  
**Quiero** consultar la información de una película  
**Para** conocer sus características antes de comprar un ticket.

### Criterios de aceptación

**CA-01**
- Dado que el usuario está viendo la cartelera,
- cuando selecciona una película,
- entonces el sistema debe mostrar su información.

**CA-02**

La información debe incluir:
- Título
- Duración
- Clasificación

**CA-03**

El sistema debe permitir regresar a la cartelera después de consultar la película.

---

## 🎟️ HU-03 — Consultar disponibilidad de funciones

**Como** cliente  
**Quiero** consultar las funciones disponibles de una película  
**Para** conocer cuándo puedo asistir al cine.

### Criterios de aceptación

**CA-01**
- Dado que existe una película,
- cuando el usuario consulta sus funciones,
- entonces el sistema debe mostrar las funciones disponibles.

**CA-02**

Cada función debe mostrar como mínimo:
- Película
- Sala
- Horario

**CA-03**

Si no existen funciones disponibles, debe aparecer:

> "No hay funciones disponibles para esta película."

---

## 🪑 HU-04 — Consultar información de las salas

**Como** cliente  
**Quiero** conocer el tipo de sala donde se proyecta una película  
**Para** saber qué tipo de experiencia ofrece la función.

### Criterios de aceptación

**CA-01**

El sistema debe mostrar el número de sala.

**CA-02**

El sistema debe mostrar la capacidad de la sala.

**CA-03**

El sistema debe indicar si la sala es:
- 2D
- 3D

**CA-04**

Para una sala 2D se podrá mostrar:

```text
Sala 2
Capacidad: 100
Tipo: 2D
Sonido Dolby: Sí
```

Para una sala 3D:

```text
Sala 3
Capacidad: 120
Tipo: 3D
Versión de gafas: X
```

---

# 📊 Product Backlog del Sprint 1

| ID | Historia | Prioridad | Criterios |
|---|---|---|---|
| HU-01 | Visualizar cartelera | Alta | 3 |
| HU-02 | Consultar película | Alta | 3 |
| HU-03 | Consultar funciones | Alta | 3 |
| HU-04 | Consultar salas | Media | 4 |

---

# 🏃 Tareas del Sprint

## Tarea 1 — Crear clase `Pelicula`

```java
private String titulo;
private int duracionMinutos;
private String clasificacion;

public String getTitulo()
```

## Tarea 2 — Crear clase `Sala`

```text
Sala
├── Sala2D
└── Sala3D
```

## Tarea 3 — Crear cartelera

```text
Cartelera
│
├── Avatar
├── Minecraft
├── Superman
└── Lilo & Stitch
```

## Tarea 4 — Crear interfaz de consulta

```text
╔══════════════════════════════════╗
║          CINE CESDE              ║
╠══════════════════════════════════╣
║            CARTELERA             ║
║                                  ║
║ 🎬 Película 1                    ║
║ Duración: 120 minutos            ║
║ Clasificación: +12               ║
║                                  ║
║ 🎬 Película 2                    ║
║ Duración: 105 minutos            ║
║ Clasificación: Todo público      ║
║                                  ║
╚══════════════════════════════════╝
```

---

# ✅ Definición de terminado — Definition of Done

- [ ] La clase `Pelicula` está creada.
- [ ] La clase `Sala` está creada.
- [ ] `Sala2D` hereda de `Sala`.
- [ ] `Sala3D` hereda de `Sala`.
- [ ] Existen películas de prueba.
- [ ] El usuario puede visualizar la cartelera.
- [ ] El usuario puede consultar información de una película.
- [ ] Se pueden consultar las funciones.
- [ ] Se puede identificar el tipo de sala.
- [ ] Los criterios de aceptación de las historias se cumplen.
- [ ] El código fue probado.
- [ ] Los cambios fueron guardados mediante Git.
- [ ] El proyecto está actualizado en GitHub.

---

# 📝 Resultado esperado del Sprint

```text
             CINE CESDE
                  │
                  ▼
             CARTELERA
                  │
       ┌──────────┼──────────┐
       ▼          ▼          ▼
    Película    Película    Película
       │          │          │
       ▼          ▼          ▼
    Detalle     Detalle     Detalle
       │
       ▼
    Funciones
       │
       ▼
      Sala
     /    \
   2D      3D
```

---

# 📌 Resumen para presentación

> **Sprint 1: Consulta de cartelera.**
>
> El objetivo es desarrollar una primera versión de CineCesde que permita a los clientes consultar las películas disponibles, su información básica, las funciones y el tipo de sala.
>
> El Sprint está compuesto por cuatro historias de usuario y sus respectivos criterios de aceptación.
