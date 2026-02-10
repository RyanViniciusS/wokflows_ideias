![Workflow – Ideia inicial](https://github.com/RyanViniciusS/wokflows_ideias/blob/main/WhatsApp%20Image%202026-02-10%20at%2019.23.45.jpeg?raw=true)


```sql
Project workflow_app {
  database_type: "PostgreSQL"
}

Table workflow {
  id string [pk]
  name string
  createdAt timestamp [default: `now()`]
  updatedAt timestamp [default: `now()`]

  userId string
  accountId string [null]

  Note: "Workflow definitions"
}

Table node {
  id string [pk]
  workflowId string
  name string
  type NodeType
  position json
  data json [default: "{}"]
  createdAt timestamp [default: `now()`]
  updatedAt timestamp [default: `now()`]

  Note: "Workflow nodes"
}

Table connection {
  id string [pk]
  workflowId string

  fromNodeId string
  toNodeId string

  fromOutput string [default: "main"]
  toInput string [default: "main"]

  createdAt timestamp [default: `now()`]
  updatedAt timestamp [default: `now()`]

  Indexes {
    (fromNodeId, toNodeId, fromOutput, toInput) [unique]
  }

  Note: "Connections between nodes"
}

/* =========================
   RELATIONSHIPS
========================= */


Ref: node.workflowId > workflow.id [delete: cascade]

Ref: connection.workflowId > workflow.id [delete: cascade]

Ref: connection.fromNodeId > node.id [delete: cascade]

Ref: connection.toNodeId > node.id [delete: cascade]


Ref: "node"."id" < "node"."workflowId"
```
