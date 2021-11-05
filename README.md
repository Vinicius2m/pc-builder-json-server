## Endpoints

Assim como a documentação do JSON-Server-Auth traz (https://www.npmjs.com/package/json-server-auth), existem 3 endpoints que podem ser utilizados para cadastro e 2 endpoints que podem ser usados para login.

Nesse trabalho também existem mais 5 endpoints, 1 para listar os usuários cadastrados, 2 para cadastrar pokémons e visualizar pokémons cadastrados, e mais 2 para cadastrar digimons e visualizar digimons cadastrados.

### Cadastro

POST /register <br/>
POST /signup <br/>
POST /users

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.
Exemplo de requisição:

{ <br/>
"email": "kenzo2021@bol.com", <br/>
"password": "123456", <br/>
"name": "Kenzo2021", <br/>
"age": 20 <br/>
}

### Login

POST /login <br/>
POST /signin

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users", passando como campos o email e a senha no corpo da requisição. <br/>
Exemplo de requisição:

{ <br/>
"email": "kenzo2021@bol.com", <br/>
"password": "123456" <br/>
}

### Users

GET /users

A requisição GET /users pode ser usada para listar todos os usuários cadastrados na API. Esse endpoint não precisa de nenhuma autorização especial.

### Pokémons

POST /pokemons <br/>
GET /pokemons

A requisição POST /pokemons pode ser usada para cadastrar pokémons novos. Qualquer usuário logado pode cadastrar um novo pokémon, bastando apenas que informe o Bearer Token no cabeçalho da requisição (Authorization: Bearer {token}), e passe no corpo da requisição os dados do novo pokémon a ser cadastrado (os novos dados podem ser escolhidos à vontade pelo usuário), como, por exemplo:

{ <br/>
"name": "Pikachu", <br/>
"type": "Electric" <br/>
}

Já a requisição GET /pokemons pode ser usada pra listar todos os pokémons já cadastrados. Esse endpoint não precisa de nenhuma autorização especial.

### Digimons

POST /digimons <br/>
GET /digimons

A requisição POST /digimons pode ser usada para cadastrar digimons novos. Apenas o usuário dono da requisição pode cadastrar um novo digimon, tendo que informar o Bearer Token no cabeçalho da requisição (Authorization: Bearer {token}), e passar no corpo da requisição os dados do novo pokémon a ser cadastrado (os novos dados podem ser escolhidos à vontade pelo usuário), junto com a userId do usuário criador, como, por exemplo:

{ <br/>
"userId": "1", <br/>
"name": "Greymon" <br/>
}

Já a requisição GET /digimons pode ser usada pra listar todos os pokémons já cadastrados. Esse endpoint não precisa de autorização alguma.
