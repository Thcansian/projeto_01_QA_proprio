# 🔌 Testes de API — Projeto QA

Esta pasta contém toda a estrutura de testes voltados para validação de endpoints da aplicação, incluindo planejamento, execução e registro de defeitos encontrados durante os testes.

---

## 📁 Estrutura de Navegação

### 📄 Cenários de Teste

Descrição em alto nível das funcionalidades testadas na API.

Contém a definição do **o que será testado**, sem detalhamento técnico de execução.

➡️ Acessar: `./cenarios-de-testes/`

---

### 🧪 Casos de Teste

Detalhamento completo de execução dos testes.

➡️ Acessar: `./casos-de-testes/`

---

### 🐞 Relatórios de Bugs

Registro de defeitos encontrados durante a execução dos testes de API.

➡️ Acessar: `./bugs/`

---

### 📦 Collections Postman

Collections exportadas contendo todos os requests utilizados nos testes.

Permite que qualquer pessoa importe e execute os testes rapidamente.

➡️ Acessar: `./collections/`

---

## 🎯 Objetivo dos Testes de API

Validar:

* Funcionalidade dos endpoints
* Regras de negócio
* Validação de campos
* Tratamento de erros
* Integridade dos dados
* Contrato de resposta

---

## 🛠️ Ferramentas Utilizadas

* Postman → Execução manual
* Newman → Execução via CLI (futuro)
* k6 → Performance (integrado ao projeto)

---

## 🔎 Escopo Coberto

* Métodos GET, POST, PUT, DELETE
* Testes positivos e negativos
* Validação de payload
* Testes de exceção
* Fluxo completo CRUD

---

Esta estrutura segue boas práticas de organização de testes de API utilizadas em ambientes profissionais de QA.
