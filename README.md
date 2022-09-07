* 设置分片集

```sh.addShard("shard1/mongodb-shading-psmdb-papertiger-2.mongodb-shading-psmdb-papertiger.mongodb.svc.cluster.local:27017,mongodb-shading-psmdb-papertiger-0.mongodb-shading-psmdb-papertiger.mongodb.svc.cluster.local:27017,mongodb-shading-psmdb-papertiger-1.mongodb-shading-psmdb-papertiger.mongodb.svc.cluster.local:27017");```

---

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

---

* connect sharding

`kubectl run -i --rm --tty pe --image=percona/percona-server-mongodb:5.0 --restart=Never -- mongo "mongodb://userAdmin:userAdmin123456@mongodb-shading-psmdb-mongos.<namespace name>.svc.cluster.local/admin?ssl=false"`

---

* connect replia

`kubectl run -i --rm --tty pe --image=percona/percona-server-mongodb:5.0 --restart=Never -- mongo "mongodb://userAdmin:userAdminPassword@my-cluster-name-rs0.<namespace name>.svc.cluster.local/admin?replicaSet=rs0&ssl=false"
`
