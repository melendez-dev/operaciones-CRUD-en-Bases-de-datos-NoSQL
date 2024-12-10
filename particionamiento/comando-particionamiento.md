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