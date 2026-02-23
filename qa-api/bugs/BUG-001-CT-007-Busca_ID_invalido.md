## 🆔 ID

BUG-001-CT-007-Busca_ID_invalido

---

## 📌 Título

API retorna 200 OK sem body ao buscar tutorial com ID inexistente (500)

---

## 📂 Módulo

Tutorials API — Endpoint de busca por ID

---

## 🔗 Endpoint

GET `/api/tutorials/{id}`

Exemplo testado:

```
GET /api/tutorials/500
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
* ID informado não existente na base

---

## 🔁 Passos para Reproduzir

1. Abrir Postman
2. Selecionar método **GET**
3. Inserir endpoint:

```
http://localhost:6868/api/tutorials/500
```

4. Clicar em **Send**

---

## 📊 Resultado Atual

* Status Code: **200 OK**
* Response Body:

```json
{}
```

ou vazio / null (sem dados e sem mensagem)

---

## ✅ Resultado Esperado

A API deve retornar erro informando que o recurso não foi encontrado.

Exemplo esperado:

**Status Code:** 404 Not Found

**Body:**

```json
{
  "message": "Tutorial not found"
}
```

---

## 📉 Impacto

* Dificulta validação no frontend
* Quebra validações automatizadas
* Gera ambiguidade na resposta
* Não segue boas práticas REST

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
./evidencias/postman/CT-007-BUG-001-Busca_ID_invalido-BUG.png
```

---

## 🧠 Análise Técnica (Opcional)

Possível causa:

* Controller não trata retorno nulo do banco
* Falta validação de existência antes do response

---

## 📌 Status

Aberto

---

## 👤 Reportado por

QA — Projeto de Portfólio
