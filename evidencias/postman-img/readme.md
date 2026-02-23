# 🖼️ Evidências — Testes Postman

Esta pasta contém as evidências visuais geradas durante a execução dos testes de API utilizando o Postman.

As imagens registram os resultados obtidos em cada request executado, servindo como prova de validação dos casos de teste documentados no projeto.

---

## 📋 Organização dos Arquivos

Os arquivos seguem o padrão de nomenclatura:

```
CT-XXX-descricao.png
```

Onde:

* **CT** → Caso de Teste
* **XXX** → ID do caso
* **descricao** → Ação testada

---

## 📊 Mapeamento das Evidências

| Caso de Teste | Descrição             | Evidência                          |
| ------------- | --------------------- | ---------------------------------- |
| CT-001        | Criar tutorial válido | CT-001-cria-validos.png            |
| CT-002        | Busca dados validos   | CT-002-busca-validos.png          |
| CT-003        | Cria tutoriais s/obrigatorio      | CT-003-cria-sem-titulo.png                 |
| CT-004        | Buscar publicados | CT-004-busca-published.png |

---

## ⚠️ Observações

Arquivos contendo a marcação **(confere)** no nome indicam comportamentos que necessitaram validação adicional ou que apresentaram inconsistências durante os testes, podendo estar associados a bugs documentados na pasta correspondente.
Arquivos com "BUG" no nome, foram revisados e encontradas inconsistências em algum quesito e relatadas na aba bugsna pasta qa-api

---

## 🔗 Relacionamentos

* Casos de Teste → `../../qa-api/casos-de-testes/`
* Bugs Reportados → `../../qa-api/bugs/`

---

Estas evidências garantem rastreabilidade entre execução prática e documentação formal dos testes.
