-- =========================
-- Table: workflow
-- =========================
| ID     | Name                | User ID | Account ID | CreatedAt        | UpdatedAt        |
| ------ | ------------------ | ------- | ---------- | ---------------- | ---------------- |
| wf_001 | Workflow de Teste 1 | user_01 | acc_01     | 2026-02-10 10:00 | 2026-02-10 10:00 |

-- =========================
-- Table: node
-- =========================
| ID       | Workflow ID | Name                       | Type   | Position          | Data                                                                                                                                 | CreatedAt        | UpdatedAt        |
| -------- | ----------- | -------------------------- | ------ | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ---------------- | ---------------- |
| node_001 | wf_001      | Receber Pergunta Usuário   | input  | {"x":100,"y":100} | { "body": "{{user.question}}", "method": "POST", "endpoint": "[http://localhost:3000/ask](http://localhost:3000/ask)" }              | 2026-02-10 10:01 | 2026-02-10 10:01 |
| node_002 | wf_001      | Buscar Previsão do Tempo   | action | {"x":300,"y":100} | { "api": "[http://api.weather.com](http://api.weather.com)", "params": {"city": "{{user.city}}"}, "method": "GET" }                  | 2026-02-10 10:02 | 2026-02-10 10:02 |
| node_003 | wf_001      | Formatar Resposta          | action | {"x":500,"y":100} | { "template": "Olá {{user.name}}, a previsão do tempo em {{user.city}} é {{weather.temp}}°C" }                                       | 2026-02-10 10:03 | 2026-02-10 10:03 |
| node_004 | wf_001      | Enviar Resposta ao Cliente | action | {"x":700,"y":100} | { "method": "POST", "endpoint": "[http://localhost:3000/respond](http://localhost:3000/respond)", "body": "{{formatted.response}}" } | 2026-02-10 10:04 | 2026-02-10 10:04 |
-- =========================
-- Table: connection
-- =========================
| ID       | Workflow ID | From Node ID | To Node ID | From Output | To Input | CreatedAt        | UpdatedAt        |
| -------- | ----------- | ------------ | ---------- | ----------- | -------- | ---------------- | ---------------- |
| conn_001 | wf_001      | node_001     | node_002   | main        | main     | 2026-02-10 10:01 | 2026-02-10 10:01 |
| conn_002 | wf_001      | node_002     | node_003   | main        | main     | 2026-02-10 10:02 | 2026-02-10 10:02 |
| conn_003 | wf_001      | node_003     | node_004   | main        | main     | 2026-02-10 10:03 | 2026-02-10 10:03 |
