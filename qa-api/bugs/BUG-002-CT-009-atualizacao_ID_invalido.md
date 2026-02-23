## 🆔 ID

BUG-002-CT-009-atualizacao_ID_invalido

---

## 📌 Título

API retorna 200 OK com body ao tentar atualizar tutorial com ID inexistente (500)

---

## 📂 Módulo

Tutorials API — Endpoint de atualização por ID

---

## 🔗 Endpoint

PUT `/api/tutorials/{id}`

Exemplo testado:

```
PUT /api/tutorials/500
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
2. Selecionar método **PUT**
3. Inserir endpoint:

```
http://localhost:6868/api/tutorials/500
```
4. Inserir body: 

``` JSON

{
        "title": "CT-009",
        "description": "atualizando tutorial inexistente dados OK",
        "published": true
 }

```
5. Clicar em **Send**

---

## 📊 Resultado Atual

* Status Code: **200 OK**
* Response Body:

```json
{ "message": "cannot update Tutorial with id=500. maybe tutorial was not found or req.body is empty!"}
```

---

## ✅ Resultado Esperado

A API deve retornar erro informando que o ID não foi encontrado ou é inválido para atualização.

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
./evidencias/postman/CT-009-BUG-001-Atualiza_ID_invalido-BUG.png
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
