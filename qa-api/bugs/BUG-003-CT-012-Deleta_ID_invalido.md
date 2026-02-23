## 🆔 ID

BUG-003-CT-012-deleta_ID_invalido

---

## 📌 Título

API retorna 200 OK com body ao tentar deletar tutorial com ID inexistente (100)

---

## 📂 Módulo

Tutorials API — Endpoint de delete por ID

---

## 🔗 Endpoint

DELETE `/api/tutorials/{id}`

Exemplo testado:

```
DELETE /api/tutorials/100
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
2. Selecionar método **DELETE**
3. Inserir endpoint:

```
http://localhost:6868/api/tutorials/100
```

4. Clicar em **Send**

---

## 📊 Resultado Atual

* Status Code: **200 OK**
* Response Body:

```json
{ "message": "cannot delete Tutorial with id=100. maybe tutorial was not found!"}
```

---

## ✅ Resultado Esperado

A API deve retornar erro informando que o ID não foi encontrado ou é inválido para ser deletado.

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
./evidencias/postman/CT-012-BUG-003-Deleta_ID_invalido-BUG.png
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