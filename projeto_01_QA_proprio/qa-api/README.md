# Casos de Teste possiveis API 

## CT-001
- ID: CT - cria tutorial - 001

- titulo: cria tutotial com dados válidos

- descrição: testar a criação de um tutorial válido dentro da API.

- endpoint: /api/tutorials

- metodo: POST

- Pré-condições: 
    - Sistema disponivel (no caso subido através do docker) 

- Passos: 
    1. Abrir postman 
    2. Selecionar o metodo POST 
    3. inserir a URL corretamente junto ao endpoint
    4. adicionar body: 
        {
        "title": "Teste QA",
        "description": "Criando tutorial",
        "published": true
        }
    5. configurar header [COntent-Type + application/json]
    6. clicar em send

- resultado esperado: 
    - Status 200 OK 
    - Body parecido com: 
        {
        "id": 1,
        "title": "FilmeTeste3",
        "description": "Segundo filme Teste 3 que crio no Postman",
        "published": true,
        "createdAt": "2026-02-05T02:11:32.000Z",
        "updatedAt": "2026-02-05T02:11:32.000Z"
        }
    
---

## CT-002
- ID: CT - Busca lista de tutorial - 002

- titulo: busca lista de tutotial com dados válidos

- descrição: testar a busca completa de um tutoriais dentro da API.

- endpoint: /api/tutorials

- metodo: GET

- Pré-condições: 
    - Sistema disponivel (no caso subido através do docker) 

- Passos: 
    1. Abrir postman 
    2. Selecionar o metodo GET
    3. inserir a URL corretamente junto ao endpoint
    4. clicar em send

- resultado esperado: 
    - Status 200 OK 
    - Body parecido com: 
        {
        "id": 1,
        "title": "FilmeTeste3",
        "description": "Segundo filme Teste 3 que crio no Postman",
        "published": true,
        "createdAt": "2026-02-05T02:11:32.000Z",
        "updatedAt": "2026-02-05T02:11:32.000Z"
    },
    {
        "id": 2,
        "title": "FilmeTeste3",
        "description": "Segundo filme Teste 3 que crio no Postman",
        "published": true,
        "createdAt": "2026-02-05T21:59:36.000Z",
        "updatedAt": "2026-02-05T21:59:36.000Z"
    },
    {
        "id": 3,
        "title": "teste002",
        "description": "teste do postman fake api",
        "published": true,
        "createdAt": "2026-02-05T22:01:46.000Z",
        "updatedAt": "2026-02-05T22:01:46.000Z"
    }

--- 

## CT-003
- ID: CT - cria tutorial inválido - 003

- titulo: cria tutotial com dados inválidos

- descrição: testar a criação de um tutorial inválido dentro da API.

- endpoint: /api/tutorials/

- metodo: POST

- Pré-condições: 
    - Sistema disponivel (no caso subido através do docker) 

- Passos: 
    1. Abrir postman 
    2. Selecionar o metodo POST 
    3. inserir a URL corretamente junto ao endpoint
    4. adicionar body (sem titulo): 
        {
        
        "description": "Criando tutorial",
        "published": true
        }
    5. configurar header [COntent-Type + application/json]
    6. clicar em send

- resultado esperado: 
    - Status 400 bad request
    - Body parecido com: 
       {
    "message": "Content can not be empty!"
    }

---

## CT-004
- ID: CT - busca tutorial válido publicados - 004

- titulo: busca tutotial com dados válidos PUBLICADOS

- descrição: testar a busca de um tutorial válido e publicado dentro da API.

- endpoint: /api/tutorials/published

- metodo: GET

- Pré-condições: 
    - Sistema disponivel (no caso subido através do docker) 
    - possuir tutoriais publicados para que tenha conteudo

- Passos: 
    1. Abrir postman 
    2. Selecionar o metodo GET
    3. inserir a URL corretamente junto ao endpoint
    4. clicar em send

- resultado esperado: 
    - Status: 200 OK
    - Body parecido com (todos onde o campo published estejam true): 
       {
        "id": 1,
        "title": "FilmeTeste3",
        "description": "Segundo filme Teste 3 que crio no Postman",
        "published": true,
        "createdAt": "2026-02-05T02:11:32.000Z",
        "updatedAt": "2026-02-05T02:11:32.000Z"
    },
    {
        "id": 2,
        "title": "FilmeTeste3",
        "description": "Segundo filme Teste 3 que crio no Postman",
        "published": true,
        "createdAt": "2026-02-05T21:59:36.000Z",
        "updatedAt": "2026-02-05T21:59:36.000Z"
    },

---

## CT-005
- ID: CT - busca tutorial publicado sem possuir publicados - 005

- titulo: busca tutotial publicado sem possuir nada publicado

- descrição: testar a busca de um tutorial publicado sem possuir nenhum tutorial ja publicado dentro da API.

- endpoint: /api/tutorials/published

- metodo: GET

- Pré-condições: 
    - Sistema disponivel (no caso subido através do docker) 

- Passos: 
    1. Abrir postman 
    2. Selecionar o metodo GET
    3. inserir a URL corretamente junto ao endpoint
    4. clicar em send

- resultado esperado: 
    - Status 200 OK
    - Body vazio ou mensagem de nenhum tutorial publicado

---

## CT-006
- ID: CT - busca tutorial pelo id válido - 006

- titulo: busca tutotial pelo id válido

- descrição: testar a busca de um tutorial através de um ID válido dentro da API.

- endpoint: /api/tutorials/{id}

- metodo: GET

- Pré-condições: 
    - Sistema disponivel (no caso subido através do docker) 
    - exixtir um tutorial válido com ID

- Passos: 
    1. Abrir postman 
    2. Selecionar o metodo GET
    3. inserir a URL corretamente junto ao endpoint + ID 
    4. clicar em send

- resultado esperado: 
    - Status 200 OK
    - Body com dados do tutorial buscado 

---

## CT-007
- ID: CT - busca tutorial pelo id inválido - 007

- titulo: busca tutotial pelo id inválido

- descrição: testar a busca de um tutorial através de um ID inválido, um Id que não existe dentro da API.

- endpoint: /api/tutorials/{id-inválido}

- metodo: GET

- Pré-condições: 
    - Sistema disponivel (no caso subido através do docker) 

- Passos: 
    1. Abrir postman 
    2. Selecionar o metodo GET
    3. inserir a URL corretamente junto ao endpoint + ID inválido
    4. clicar em send

- resultado esperado: 
    - Status 400 bad request
    - Body com erro mostrando ID inválido 

---

