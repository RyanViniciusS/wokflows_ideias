![Workflow – Ideia inicial](https://github.com/RyanViniciusS/wokflows_ideias/blob/main/WhatsApp%20Image%202026-02-10%20at%2019.23.45.jpeg?raw=true)

-- =========================
-- Table: workflow
-- =========================
| ID     | Name                | User ID | Account ID | CreatedAt        | UpdatedAt        |
| ------ | ------------------ | ------- | ---------- | ---------------- | ---------------- |
| wf_001 | Workflow de Teste 1 | user_01 | acc_01     | 2026-02-10 10:00 | 2026-02-10 10:00 |

-- =========================
-- Table: node
-- =========================
| ID       | Workflow ID | Name               | Type       | Position          | Data | CreatedAt        | UpdatedAt        |
| -------- | ----------- | ----------------- | ---------- | ---------------- | ---- | ---------------- | ---------------- |
| node_001 | wf_001      | Start              | input      | {"x":100,"y":100} | {"body": "{{ryan.teste", "method": "POST", "endpoint": "http://localhost:3000"}   | 2026-02-10 10:01 | 2026-02-10 10:01 |
| node_002 | wf_001      | Validar Dados      | validation | {"x":300,"y":100} | {}   | 2026-02-10 10:02 | 2026-02-10 10:02 |
| node_003 | wf_001      | Enviar Email       | action     | {"x":500,"y":100} | {}   | 2026-02-10 10:03 | 2026-02-10 10:03 |
| node_004 | wf_001      | Finalizar Processo | action     | {"x":700,"y":100} | {}   | 2026-02-10 10:04 | 2026-02-10 10:04 |

-- =========================
-- Table: connection
-- =========================
| ID       | Workflow ID | From Node ID | To Node ID | From Output | To Input | CreatedAt        | UpdatedAt        |
| -------- | ----------- | ------------ | ---------- | ----------- | -------- | ---------------- | ---------------- |
| conn_001 | wf_001      | node_001     | node_002   | main        | main     | 2026-02-10 10:01 | 2026-02-10 10:01 |
| conn_002 | wf_001      | node_002     | node_003   | main        | main     | 2026-02-10 10:02 | 2026-02-10 10:02 |
| conn_003 | wf_001      | node_003     | node_004   | main        | main     | 2026-02-10 10:03 | 2026-02-10 10:03 |

