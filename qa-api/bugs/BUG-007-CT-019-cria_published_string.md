## 🆔 ID

BUG-007-CT-019-cria_published_string

---

## 📌 Título

API retorna 500 internal server error

---

## 📂 Módulo

Tutorials API — Endpoint de criação

---

## 🔗 Endpoint

POST `/api/tutorials`

Exemplo testado:

```
POST /api/tutorials
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
http://localhost:6868/api/tutorials
```

4. campo: published de "true" para "sim"
5. Clicar em **Send**

---

## 📊 Resultado Atual

* Status Code: **500 server internal error**
* Response Body:

```json
{
    "message": "incorrect integer value:  'sim' for column 'published' at row 1"
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
./evidencias/postman/CT-019-BUG-007-cria_published_string.png
```

---


## 📌 Status

Aberto

---

## 👤 Reportado por

QA — Projeto de Portfólio