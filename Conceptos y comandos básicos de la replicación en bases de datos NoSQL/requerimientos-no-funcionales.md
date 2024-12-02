# Documento de requerimiento no funcionales

1. ### Disponibilidad 24x7

   - Requerimientos: El sistema debe estar disponible para ser consultado y actualizado 24 horas al día, 7 días a la semana.
   - Justificación: Los organizadores y participantes necesitan acceso constante para gestionar el torneo, actualizar resultados en tiempo real y consultar información clave.
   - Estrategias:
       1. Configurar una arquitectura replicada en mongoDB para garantizar alta disponibilidad.
       2. Implementar réplicas distribuidas geográficamente para minimizar el impacto de fallos en nodos individuales.
       3. Implementar un balanceador de carga para distribuir las solicitudes entre las réplicas.

2. ### Redundancia

   - Requerimientos: Los datos deben estar disponibles incluso en caso de fallos de hardware o red.
   - Justificación: La pérdida de datos o la indisponibilidad del sistema afectaría la organización del torneo y la confianza en la plataforma.
   - Estrategias:
       1. Configurar un clúster de réplica con al menos un nodo primario y dos secundarios.
       2. Garantizar que las réplicas sean síncronas, asegurando que los datos se escriban en múltiples nodos antes de confirmar las operaciones al cliente.
       3. Programar respaldos regulares y pruebas periódicas de restauración para garantizar la integridad de los datos.

3. ### Rendimiento
   - Requerimientos: Las consultas deben ejecutarse en menos de 500 ms en un 90% de los casos.
   - Justificación: Los usuarios necesitan respuestas rápidas, especialmente durante la consulta de tablas de posiciones y estadísticas.
   - Estrategias:
       1. Crear índices en campos clave de las colecciones como _id, jugador_id, partido_id, y fecha.
       2. Usar índices compuestos para consultas frecuentes que involucren múltiples criterios.
       3. Implementar caché para resultados de consultas de estadísticas que no cambian frecuentemente.
