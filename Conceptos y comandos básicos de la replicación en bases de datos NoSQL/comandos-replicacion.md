# Consultas para configurar la replicación en MongoDB

Configuración de un Clúster de réplica 

1. Inicialización el cluster de réplica 

```
mongod --replSet "rsTorneo" --port 27017 --dbpath /data/db1 --bind_ip localhost
```
- Este comando inicia un nodo primario como parte del conjunto de réplicas llamado rsTorneo


2. Iniciar la Réplica en el Shell de MongoDB

```
rs.initiate({
  _id: "rsTorneo",
  members: [
    { _id: 0, host: "localhost:27017" },
    { _id: 1, host: "localhost:27018" },
    { _id: 2, host: "localhost:27019" }
  ]
})
```

- Aquí se configura el clúster con tres nodos: un primario (localhost:27017) y dos secundarios (localhost:27018 y localhost:27019).

3. Configurar Réplicas Secundarias En diferentes terminales, se inician los nodos secundarios:

```
mongod --replSet "rsTorneo" --port 27018 --dbpath /data/db2 --bind_ip localhost
mongod --replSet "rsTorneo" --port 27019 --dbpath /data/db3 --bind_ip localhost
```

4. Verificar el Estado del Clúster
   
```
rs.status()
```

## Consulta de prueba

```
db.partidos.find({ estado: "finalizado" }).explain("executionStats")
```

```
db.partidos.aggregate([
  {
    $match: { estado: "finalizado" } // Filtrar solo partidos terminados
  },
  {
    $project: {
      ganador: {
        $cond: [
          { $gt: ["$equipo_local.puntos", "$equipo_visitante.puntos"] },
          "$equipo_local.id",
          "$equipo_visitante.id"
        ]
      }
    }
  },
  {
    $group: {
      _id: "$ganador",
      victorias: { $sum: 1 }
    }
  },
  {
    $sort: { victorias: -1 }
  },
  {
    $limit: 1
  }
])

```

```
db.jugadores.aggregate([
  {
    $lookup: {
      from: "equipos",
      localField: "equipo_id",
      foreignField: "_id",
      as: "equipo_info"
    }
  },
  {
    $group: {
      _id: "$equipo_id",
      equipo: { $first: { $arrayElemAt: ["$equipo_info.nombre", 0] } },
      jugadores: { $push: { nombre: "$nombre", apellido: "$apellido" } }
    }
  }
])

```

```
db.equipos.aggregate([
  {
    $lookup: {
      from: "entrenadores",
      localField: "entrenador_id",
      foreignField: "_id",
      as: "entrenador_info"
    }
  },
  {
    $project: {
      equipo: "$nombre",
      entrenador: { $arrayElemAt: ["$entrenador_info.nombre", 0] },
      apellido: { $arrayElemAt: ["$entrenador_info.apellido", 0] }
    }
  }
])
```

```
db.arbitros.aggregate([
  {
    $project: {
      nombre: 1,
      apellido: 1,
      partidos_arbitrados: { $size: "$partidos_arbitrados" }
    }
  },
  {
    $match: { partidos_arbitrados: { $gt: 5 } }
  }
])

```



