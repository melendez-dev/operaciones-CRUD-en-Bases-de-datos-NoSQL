# Documento de requerimiento no funcionales para la fragmentación o particionamiento

1. ### Escalabilidad

   - Crecimiento horizontal: El sistema permite agregar de manera simple nodos para manejar el aumento de datos.

   - Distribución equitativa: Los datos se distribuirán de forma equitativa entre los diferentes fragmentos.

2. ### Rendimiento
    
    - Baja latencia: Las consultas deben ejecutarse de forma rápida a pesar de tener los datos en diferentes fragmentos.
    
    - Rendimiento consistente: El tiempo de respuesta no debe verse afectado a pesar del crecimiento de las particiones.

3. ### Disponibilidad
    - Tolerancia a fallos: El sistema debe seguir en funcionamiento a pesar de que falle algún nodo.
    
    - Replicación: Cada nodo debe estar respaldado por backup por si se presenta alguna novedad. 
