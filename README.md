* 设置分片集

`sh.addShard("shard1/mongodb-shading-psmdb-papertiger-2.mongodb-shading-psmdb-papertiger.mongodb.svc.cluster.local:27017,mongodb-shading-psmdb-papertiger-0.mongodb-shading-psmdb-papertiger.mongodb.svc.cluster.local:27017,mongodb-shading-psmdb-papertiger-1.mongodb-shading-psmdb-papertiger.mongodb.svc.cluster.local:27017");`


* 增加超级用户

`use admin`

`db.createUser({
     user: "root",
     pwd: "root123",
     roles: [
      { db: "admin", role: "root" }
    ],
 mechanisms: [
       "SCRAM-SHA-1"
    ]
})
`
