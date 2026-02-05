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

