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
| CT-001        | Criar tutorial válido | CT-001-create-valid.png            |
| CT-002        | Criar sem título      | CT-002-create-invalid.png          |
| CT-003        | Listar tutoriais      | CT-003-get-all.png                 |
| CT-004        | Buscar ID inexistente | CT-004-get-id-invalido-confere.png |

---

## ⚠️ Observações

Arquivos contendo a marcação **(confere)** no nome indicam comportamentos que necessitaram validação adicional ou que apresentaram inconsistências durante os testes, podendo estar associados a bugs documentados na pasta correspondente.

---

## 🔗 Relacionamentos

* Casos de Teste → `../../qa-api/casos-de-testes/`
* Bugs Reportados → `../../qa-api/bugs/`

---

Estas evidências garantem rastreabilidade entre execução prática e documentação formal dos testes.
