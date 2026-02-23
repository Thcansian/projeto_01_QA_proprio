## 🆔 ID

BUG-005-CT-022-busca_tipo_invalidoID

---

## 📌 Título

API retorna 200 OK com body vazio tentar buscar tutorial com id de tipo invalido

---

## 📂 Módulo

Tutorials API — Endpoint de busca

---

## 🔗 Endpoint

GET `/api/tutorials/{id}`

Exemplo testado:

```
GET /api/tutorials/abc
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
2. Selecionar método **GET**
3. Inserir endpoint:

```
http://localhost:6868/api/tutorials/abc
```

4. Clicar em **Send**

---

## 📊 Resultado Atual

* Status Code: **200 OK**
* Response Body vazio:

```json

```

---

## ✅ Resultado Esperado

A API deve retornar erro informando que o id deve ser um id valido e de tipo valido.

Exemplo esperado:

**Status Code:** 400 Bad request

**Body:**

```json
{
  "message": "Invalid ID format. The 'id' parameter must be a numeric value."
}
```

---

## 📉 Impacto

* Gera comportamento ambíguo para consumidores da API
* Quebra contrato REST ao retornar sucesso para requisição inválida
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
./evidencias/postman/CT-022-BUG-005-busca_id_formato_invalido.png
```

---


## 📌 Status

Aberto

---

## 👤 Reportado por

QA — Projeto de Portfólio