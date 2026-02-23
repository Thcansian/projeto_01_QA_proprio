## 🆔 ID

BUG-004-CT-018-cria_tutorial_title_tipo_invalido

---

## 📌 Título

API retorna 200 OK com body ao tentar criar tutorial com tipo obrigatorio invalido

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

4. Inserir body: 

```JSON
{
  "title": 1234,
  "description": "Criando tutorial com titulo number",
  "published": true
}
```

5. Clicar em **Send**

---

## 📊 Resultado Atual

* Status Code: **200 OK**
* Response Body:

```json
{ 
    "id": 9,
    "title": 1234,
    "description": "Criando tutorial com titulo number",
    "published": true,
    "updatedAt": "2026-02-16T00:22:18.944Z",
    "createdAt": "2026-02-16T00:22:18.944Z"
}
```

---

## ✅ Resultado Esperado

A API deve retornar erro informando que o titulo que é campo obrigatorio não pode ser do tipo number.

Exemplo esperado:

**Status Code:** 400 Not Found

**Body:**

```json
{
  "message": "The 'title' field is required and must be a string, not a number."
}
```

---

## 📉 Impacto

* Permite persistência de dados inválidos no banco
* pode gerar inconsistência de dados no sistema
* Pode causar falhas em integrações externas
* Quebra regra de negócio e contrato da API
* Compromete validações automatizadas e frontend

---

## 🚨 Severidade

Alta

---

## ⏱️ Prioridade

Alta

---

## 🖼️ Evidência

Print da execução no Postman:

```
./evidencias/postman/CT-018-BUG-004-title_tipo_invalido.png
```

---


## 📌 Status

Aberto

---

## 👤 Reportado por

QA — Projeto de Portfólio