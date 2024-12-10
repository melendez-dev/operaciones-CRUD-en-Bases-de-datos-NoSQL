## Comandos para la fragmentación

```
shard 1

md c:\shard_data\shard1\data1
md c:\shard_data\shard1\data2
md c:\shard_data\shard1\data3
```

```
shard 2

md c:\shard_data\shard2\data1
md c:\shard_data\shard2\data2
md c:\shard_data\shard2\data3
```

```
shard 3

md c:\shard_data\shard3\data1
md c:\shard_data\shard3\data2
md c:\shard_data\shard3\data3
```

```
shard 1

start mongo.exe --shardsvr --port 26017 --dbpath "c:\shard_data\shard1\data1" --repSet shard1_repset

start mongo.exe --shardsvr --port 26117 --dbpath "c:\shard_data\shard1\data2" --repSet shard1_repset

start mongo.exe --shardsvr --port 26217 --dbpath "c:\shard_data\shard1\data3" --repSet shard1_repset
```

```
shard 2

start mongo.exe --shardsvr --port 28017 --dbpath "c:\shard_data\shard2\data1" --repSet shard2_repset

start mongo.exe --shardsvr --port 28117 --dbpath "c:\shard_data\shard2\data2" --repSet shard2_repset

start mongo.exe --shardsvr --port 28217 --dbpath "c:\shard_data\shard2\data3" --repSet shard2_repset
```

```
shard 3

start mongo.exe --shardsvr --port 29017 --dbpath "c:\shard_data\shard3\data1" --repSet shard3_repset

start mongo.exe --shardsvr --port 29117 --dbpath "c:\shard_data\shard3\data2" --repSet shard3_repset

start mongo.exe --shardsvr --port 29217 --dbpath "c:\shard_data\shard3\data3" --repSet shard3_repset
```

```
mongo.exe hostname:26017

MongoDB Enterprise > rs.initiate(
    {
        _id: "shard1_repset",
        members: [
            _id: 0, host: "hostname:26017",
            _id: 1, host: "hostname:26117",
            _id: 2, host: "hostname:26217"
        ]
    }
)
```

```
mongo.exe hostname:28017

MongoDB Enterprise > rs.initiate(
    {
        _id: "shard2_repset",
        members: [
            _id: 0, host: "hostname:28017",
            _id: 1, host: "hostname:28117",
            _id: 2, host: "hostname:28217"
        ]
    }
)
```

```
mongo.exe hostname:29017

MongoDB Enterprise > rs.initiate(
    {
        _id: "shard3_repset",
        members: [
            _id: 0, host: "hostname:29017",
            _id: 1, host: "hostname:29117",
            _id: 2, host: "hostname:29217"
        ]
    }
)
```
