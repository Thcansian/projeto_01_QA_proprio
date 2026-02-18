# 🐞 BUG REPORT — API

---

# 🐞 BUG REPORT

---

## 🆔 ID

BUG-XXX

---

## 📌 Título

<!-- Descreva o problema de forma curta e objetiva -->

Ex: API retorna 200 OK para ID inexistente

---

## 📂 Módulo / Funcionalidade

<!-- Área do sistema onde ocorreu -->

Ex: Tutorials API / Login / Cadastro / UI Home

---

## 🔗 Endpoint / Tela / URL

<!-- Se aplicável -->

Ex: GET /api/tutorials/{id}
Ex: http://localhost:3000/login

---

## ⚙️ Ambiente

* Ambiente: (Local / Homologação / Produção)
* Ferramenta: (Postman / Browser / k6 / Playwright)
* Versão do Sistema:
* Data do Teste:

---

## 📋 Pré-condições

<!-- O que precisa existir antes do teste -->

Ex:

* Usuário cadastrado
* API ativa
* Banco populado

---

## 🔁 Passos para Reproduzir

1.
2.
3.
4.

---

## 📊 Resultado Atual

<!-- O que aconteceu de fato -->

* Status Code:
* Mensagem:
* Body:
* Comportamento observado:

---

## ✅ Resultado Esperado

<!-- O que deveria acontecer -->

* Status Code esperado:
* Mensagem esperada:
* Comportamen


---

## 🆔 ID

BUG-001

---

## 📌 Título

API retorna 200 OK sem body ao buscar tutorial com ID inexistente

---

## 📂 Módulo

Tutorials API — Endpoint de busca por ID

---

## 🔗 Endpoint

GET `/api/tutorials/{id}`

Exemplo testado:

```
GET /api/tutorials/9999
```

---

## ⚙️ Ambiente

* Ambiente: Local (Docker)
* Ferramenta: Postman
* Data do teste: 16/02/2026
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
http://localhost:6868/api/tutorials/9999
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
./evidencias/postman/bug-001-id-invalido.png
```

---

## 🧠 Análise Técnica (Opcional)

Possível causa:

* Controller não trata retorno nulo do banco
* Falta validação de existência antes do response

Exemplo provável no código:

```js
if (!data) {
  res.send(data); // deveria retornar 404
}
```

---

## 📌 Status

Aberto

---

## 👤 Reportado por

QA — Projeto de Portfólio
