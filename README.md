# URL base da API

https://pc-builder-json-api.herokuapp.com/

## Endpoints

Assim como a documentação do JSON-Server-Auth traz (https://www.npmjs.com/package/json-server-auth), existem 3 endpoints que podem ser utilizados para cadastro e 2 endpoints que podem ser usados para login.

Nesse trabalho também existem mais 5 endpoints, 1 para listar os usuários cadastrados, 2 para cadastrar produtos e visualizar produtos cadastrados, e mais 2 para cadastrar produtos no carrinho e visualizar produtos cadastrados no carrinho.

### Cadastro

POST /register <br/>
POST /signup <br/>
POST /users

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.
Exemplo de requisição:

```json
{
  "email": "kenzo2021@bol.com",
  "password": "123456",
  "name": "Kenzo2021",
  "age": 20
}
```

### Login

POST /login <br/>
POST /signin

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users", passando como campos o email e a senha no corpo da requisição. <br/>
Exemplo de requisição:

```json
{
  "email": "kenzo2021@bol.com",
  "password": "123456"
}
```

### Users

GET /users

A requisição GET /users pode ser usada para listar todos os usuários cadastrados na API. Esse endpoint não precisa de nenhuma autorização especial.

### Products

GET /products <br/>

A requisição GET /products pode ser usada pra listar todos os produtos já cadastrados. Esse endpoint não precisa de autorização alguma para ser acessado.

### Cart

POST /cart <br/>
GET /cart <br/>
PATCH /cart <br/>
DEL /cart

A requisição POST /cart pode ser usada para cadastrar novos produtos no carrinho. Qualquer usuário logado pode cadastrar uma novo produto no carrinho, bastando apenas que informe o Bearer Token no cabeçalho da requisição (Authorization: Bearer {token}), e passe no corpo da requisição os dados do novo produto a ser cadastrado no carrinho (os novos dados podem ser escolhidos à vontade pelo usuário), como, por exemplo:

```json
{
  "model": "AMD Ryzen 5 3600",
  "cores": "6",
  "threads": "12",
  "socket": "AM4",
  "baseClock": "3.6",
  "coolerBox": true,
  "graphics": false,
  "price": 1678.31
}
```

Já a requisição GET /cart pode ser usada pra listar todos os produtos já cadastrados no carrinho. Qualquer usuário logado pode listar os produtos cadastrados no carrinho, bastando apenas que informe o Bearer Token no cabeçalho da requisição (Authorization: Bearer {token}).

Por sua vez, a requisição PATCH /cart/:idDoProduto: pode ser usada para editar um dado do produto. Qualquer usuário logado pode editar um dado de um produto no carrinho, bastando apenas que informe o Bearer Token no cabeçalho da requisição (Authorization: Bearer {token}), e passe no corpo da requisição os novos dados do produto a serem editados, como, por exemplo:

```json
{
  "price": 1599.25
}
```

Por último, a requisição DEL /cart/:idDoProduto: pode ser usada para deletar um produto cadastrado no carrinho. Qualquer usuário logado pode deletar um produto do carrinho, bastando apenas que informe o Bearer Token no cabeçalho da requisição (Authorization: Bearer {token}), e passe o id do produto na url da requisição.
