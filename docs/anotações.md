# ANOTAÇÕES SOBRE APRENDIZADOS EM QA 

## coisas observadas 
- consigo criar tutoriais com o mesmo titulo e mesma descrição.

# API Bezkoder fakeAPI

## Criação de tutorials 
- cria lista de tutoriais com 
    - titulo (title)[obrigatorio e estring] 
    - descrição (description) [não obrigatorio em string]
    - published (publicado) [ não obrigatorio em booleano]

## CRUD da API: 
- POST | /api/tutorials |	Criar tutorial
- GET |	/api/tutorials |	Listar todos
- GET |	/api/tutorials/published |	Listar publicados
- GET |	/api/tutorials/{id} |	Buscar por ID
- PUT |	/api/tutorials/{id} |	Atualizar
- DELETE |	/api/tutorials/{id} |	Deletar
- DELETE |	/api/tutorials |	Deletar todos

### Observações: 
- não possui cadastro ou login, qualquer usuario pode fazer qualquer uma das coisas dentro da API


- atualizar com id valido e dados válidos OK
- atualizar co id invalido dados válidos OK 
- atualizar com id valido mas dados inválidos para atualizar OK

- deletar id inválido OK
- deletar id valido OK 

- deletar todos ok OK 