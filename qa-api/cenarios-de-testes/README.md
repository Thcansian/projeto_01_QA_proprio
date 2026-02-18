# Cenários de Teste — API Tutoriais (Bezkoder)

## Sobre

Documento responsável por descrever os **cenários de teste** levantados para validação da API de Tutoriais.

Os cenários servem como base para criação dos **casos de teste detalhados**.

---

## Contexto da API

API REST responsável pelo gerenciamento de tutoriais.

### Campos do recurso

* **title** → obrigatório | string
* **description** → opcional | string
* **published** → opcional | boolean

---

## Endpoints mapeados

| Método | Endpoint                 | Ação              |
| ------ | ------------------------ | ----------------- |
| POST   | /api/tutorials           | Criar tutorial    |
| GET    | /api/tutorials           | Listar todos      |
| GET    | /api/tutorials/published | Listar publicados |
| GET    | /api/tutorials/{id}      | Buscar por ID     |
| PUT    | /api/tutorials/{id}      | Atualizar         |
| DELETE | /api/tutorials/{id}      | Deletar           |
| DELETE | /api/tutorials           | Deletar todos     |

---

## Observações levantadas

* API não possui autenticação
* Qualquer usuário pode executar operações
* É possível criar tutoriais com mesmo título e descrição

---

# Cenários de Teste

---

## 1. Criação de tutoriais (POST)

### Cenários positivos

* Criar tutorial com todos os campos válidos
* Criar tutorial apenas com campo obrigatório
* Criar tutorial com published = true
* Criar tutorial com published = false

### Cenários negativos

* Criar tutorial sem title
* Criar tutorial com title vazio
* Criar tutorial com tipo inválido em title
* Criar tutorial com published inválido (string, número)

### Regras observadas

* API permite títulos duplicados

---

## 2. Listagem de tutoriais (GET)

### Cenários positivos

* Listar todos os tutoriais cadastrados
* Listar com múltiplos registros

### Cenários negativos

* Listar sem possuir registros
* Validar estrutura do retorno

---

## 3. Listagem de publicados

### Cenários positivos

* Listar apenas tutoriais com published = true

### Cenários negativos

* Listar publicados sem possuir registros
* Validar se retorna vazio corretamente

---

## 4. Busca por ID

### Cenários positivos

* Buscar tutorial com ID válido

### Cenários negativos

* Buscar tutorial com ID inexistente
* Buscar tutorial com ID inválido (string, null)

---

## 5. Atualização de tutorial (PUT)

### Cenários positivos

* Atualizar com ID válido e dados válidos

### Cenários negativos

* Atualizar com ID inválido
* Atualizar com ID inexistente
* Atualizar com dados inválidos
* Atualizar sem body

### Observações levantadas

* Atualização com ID inválido retorna erro
* Atualização com dados inválidos validada

---

## 6. Deleção por ID

### Cenários positivos

* Deletar tutorial com ID válido

### Cenários negativos

* Deletar tutorial com ID inexistente
* Deletar tutorial com ID inválido

---

## 7. Deleção geral

### Cenários positivos

* Deletar todos os tutoriais

### Cenários negativos

* Executar deleção sem registros existentes

---

## Considerações finais

Os cenários foram levantados com base:

* Na análise da documentação da API
* Nos testes exploratórios realizados
* Nas regras de negócio observadas

Servem como base para criação e expansão dos casos de teste detalhados.
