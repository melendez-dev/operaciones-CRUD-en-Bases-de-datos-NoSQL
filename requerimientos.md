# Documento de Requerimientos: Sistema de Gestión de Torneo de Baloncesto

## 1. Introducción
Este documento describe los requerimientos para un sistema de gestión de un torneo de baloncesto utilizando una base de datos NoSQL MongoDB.

## 2. Reglas del Torneo

### 2.1 Equipos y Jugadores
- Cada equipo debe tener un mínimo de 5 jugadores y un máximo de 12.
- Cada equipo debe tener al menos un entrenador.

### 2.2 Árbitros
- Cada partido debe ser supervisado por al menos 2 árbitros.

### 2.3 Partidos
- Los partidos se juegan en 4 cuartos de 10 minutos cada uno.
- En caso de empate, se jugarán tiempos extras de 5 minutos hasta que haya un ganador.

### 2.4 Puntuación
- Cada canasta vale 2 puntos, excepto los tiros libres (1 punto) y los tiros de 3 puntos.
- Victoria: 2 puntos en la tabla de posiciones
- Derrota: 1 punto en la tabla de posiciones

## 3. Informes Requeridos
- Tabla de posiciones actualizada
- Estadísticas de jugadores (puntos, rebotes, asistencias por partido)
- Calendario de partidos
- Resultados de partidos
- Rendimiento de árbitros

## 4. Colecciones de la Base de Datos
1. Equipos
2. Jugadores
3. Entrenadores
4. Árbitros
5. Partidos
6. Estadísticas
