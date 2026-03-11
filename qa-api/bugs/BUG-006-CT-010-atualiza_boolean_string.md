## 🆔 ID

BUG-006-CT-010-atualiza_boolean_string

---

## 📌 Título

API retorna 500 internal server error

---

## 📂 Módulo

Tutorials API — Endpoint de atualização

---

## 🔗 Endpoint

PUT `/api/tutorials/{id}`

Exemplo testado:

```
PUT /api/tutorials/5
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
2. Selecionar método **PUT**
3. Inserir endpoint:

```
http://localhost:6868/api/tutorials/5
```

4. modifica campo: published de "true" para "sim"
5. Clicar em **Send**

---

## 📊 Resultado Atual

* Status Code: **500 server internal error**
* Response Body:

```json
{
    "message": "error updating tutorial with id=5"
}
```

---

## ✅ Resultado Esperado

A API deve retornar erro informando que o tipo de published deve ser booleano.

Exemplo esperado:

**Status Code:** 400 Bad request

**Body:**

```json
{
  "message": "Invalid format published. The published parameter must be a boolean value."
}
```

---

## 📉 Impacto

* Gera comportamento ambíguo para consumidores da API
* Quebra contrato REST ao retornar tipo de erro incorreto
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
./evidencias/postman/CT-010-BUG-006-atualiza_boolean_string.png
```

---


## 📌 Status

Aberto

---

## 👤 Reportado por

QA — Projeto de Portfólio