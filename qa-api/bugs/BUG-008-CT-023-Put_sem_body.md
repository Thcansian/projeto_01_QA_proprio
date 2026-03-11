## 🆔 ID

BUG-008-CT-023-atualiza_sem_body

---

## 📌 Título

API retorna 200 OK em atualização sem body

---

## 📂 Módulo

Tutorials API — Endpoint de atualização

---

## 🔗 Endpoint

PUT `/api/tutorials/{id}`

Exemplo testado:

```
PUT /api/tutorials/10
```

---

## ⚙️ Ambiente

* Ambiente: Local (Docker)
* Ferramenta: Postman
* Data do teste: 17/02/2026
* Versão da API: v1

---

## 📋 Pré-condições

* API em execução
* Banco de dados ativo


---

## 🔁 Passos para Reproduzir

1. Abrir Postman
2. Selecionar método **POST**
3. Inserir endpoint:

```
http://localhost:6868/api/tutorials/10
```

4. Clicar em **Send**

---

## 📊 Resultado Atual

* Status Code: **200 OK**
* Response Body:

```json
{
  "message": "Cannot update tutorial with id=10. Maybe tutorial was not found or req.body is empty!"
}
```

---

## ✅ Resultado Esperado

A API deve retornar erro informando que o body esta vazio.

Exemplo esperado:

**Status Code:** 400 Bad request

**Body:**

```json
{
  "message": "Cannot update tutorial with id=10. Maybe tutorial was not found or req.body is empty!"
}
```

---

## 📉 Impacto

* Gera comportamento ambíguo para consumidores da API
* Quebra contrato REST ao retornar Ok quando se tem um erro
* Pode dificultar debugging e rastreabilidade de erro
* Pode impactar validações automatizadas que esperam erro 400
* Reduz previsibilidade da API para integrações externas

---

## 🚨 Severidade

Média

---

## ⏱️ Prioridade

Média

---

## 🖼️ Evidência

Print da execução no Postman:

```
./evidencias/postman/CT-023-BUG-008-Put_sem_body.png
```

---


## 📌 Status

Aberto

---

## 👤 Reportado por

QA — Projeto de Portfólio