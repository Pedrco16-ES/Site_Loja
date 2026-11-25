# Loja (API e Front-end)
Sistema acadêmico de loja: cadastro de produtos com foto, painel de vendas com carrinho e fechamento de venda.

## Stack
| Parte | Tecnologias | Porta |
|---|---|---|
| API (`Api/`) | Node.js, Express, Sequelize, MariaDB | 5000 |
| Front-end (`FrontEnd/`) | React | 3000 |

## Subindo o projeto
**Banco:** no MariaDB, execute `CREATE DATABASE loja;`. As tabelas são geradas sozinhas ao iniciar a API. Login e senha do banco ficam em `Api/db/conn.js`.

**API:**
```bash
cd Api && npm install && npm start
```

**Front-end** (em outro terminal):
```bash
cd FrontEnd && npm install && npm start
```

## Referência da API
**Produtos**

- `POST /produto/create`: cadastra (form-data com `nome`, `preco` e `imagem`)
- `GET /produto/getAll`: retorna todos
- `GET /produto/getById/:id`: retorna um
- `PUT /produto/update/:id`: edita (form-data; `imagem` é opcional)
- `DELETE /produto/delete/:id`: apaga

Imagens: somente `.jpeg`, `.jpg` ou `.png`, até 2MB. Preço negativo é recusado.

**Carrinho**
- `POST /carrinho/create`: abre um carrinho novo
- `GET /carrinho/getById/:id`: traz os itens e o total
- `POST /carrinho/:id/adicionarItem`: inclui produto (JSON com `produtoId` e `quantidade`)
- `PUT /carrinho/:id/atualizarItem/:itemId`: muda a quantidade (JSON com `quantidade`)
- `DELETE /carrinho/:id/removerItem/:itemId`: tira um item
- `DELETE /carrinho/:id/limpar`: zera o carrinho

**Vendas**
- `POST /venda/finalizar`: fecha a venda (JSON com `carrinhoId` e `formaPagamento`)
- `GET /venda/getAll`: lista as vendas
- `GET /venda/getById/:id`: mostra uma venda

Pagamentos aceitos: Pix, cartão de crédito, cartão de débito e dinheiro.
