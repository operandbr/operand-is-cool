# Relacionamentos

Uma boa definição de relacionamentos (utilizando-se também da normalização) entre tabelas é o que nos resulta em um banco de dados ótimo para se trabalhar e "ler".

Exitem vários tipos de relacionamento, iremos falar sobre os mais comuns.

**Tipos básicos de relacionamento**

1. **1:1** - 1 para 1
2. **1:N** - 1 para muitos
3. **N:N** - muitos para muitos

Exemplo 1:1 :

Tabela: Clientes

| iClienteId    | iClienteNome       | sClienteEndereco  |
| ------------- |:------------------:| -----------------:|
| 1             | Cliente 1          | Rua xxxxx, 256    |
| 2             | Cliente 2          | Rua yyyy, 123     |
| 3             | Cliente 3          | Rua vvvvv, 777    |


Neste caso podemos facilmente criar uma tabela para relacionar endereços (1 por cliente) e clientes.

Tabela: Clientes

| iClienteId    | iClienteNome       | iEnderecoId  |
| ------------- |:------------------:| ------------:|
| 1             | Cliente 1          | 1            |
| 2             | Cliente 2          | 2            |
| 3             | Cliente 3          | 3            |

Tabela: Enderecos

| iEnderecoId    | sEndereco        |
| -------------- |:----------------:|
| 1              | Rua xxxxx, 256   |
| 2              | Rua yyyy, 123    |
| 3              | Rua vvvvv, 777   |

Exemplo 1:N :

Tabela: Fornecedores

| iFornecedorId  | sFornecedorNome  |  sFornecedorEndereco   |    sFornecedorTelefone    |
| -------------- |:----------------:|:----------------------:|:-------------------------:|
| 1              | Fornecedor 1     |  Rua xxx, 256          | 47 34330000               |
| 2              | Fornecedor 2     |  Rua yyy, 777          | 96758585                  |
| 3              | Fornecedor 3     |  Rua zzz, 123          | 11 23456789 / 48 98899898 |

Neste exemplo visto na normalização 1FN temos muitos telefones para 1 fornecedor, o fornecedor id 3 possui dois telefones.

Tabela: Fornecedores

| iFornecedorId  | sFornecedorNome  |  sFornecedorEndereco   |
| -------------- |:----------------:|:----------------------:|
| 1              | Fornecedor 1     |  Rua xxx, 256          |
| 2              | Fornecedor 2     |  Rua yyy, 777          |
| 3              | Fornecedor 3     |  Rua zzz, 123          |


Tabela: FornecedoresTelefones

| iFornecedorTelefoneId  | iFornecedorId  |  sFornecedorTelefone |
| ---------------------- |:--------------:|:--------------------:|
| 1                      | 1              |  47 34330000         |
| 2                      | 2              |  96758585            |
| 3                      | 3              |  11 23456789         |
| 4                      | 3              |  48 98899898         |

Exemplo N:N :

Para este caso, temos o modelo de Produtos e Tags, várias tags pertencem à vários produtos e vários produtos possuem várias tags.

Tabela: Produtos

| iProdutoId  | sProdutoNome     |
| ----------- |:----------------:|
| 1           | Câmera Digital   |
| 2           | Cartão SD (16GB) |
| 3           | Filtro UV        |
| 4           | Filtro Sépia     |


Tabela: Tags

| iTagId      | sTagNome  |
| ----------- |:-------------:|
| 1           | Fotografia    |
| 2           | Eletrônicos   |
| 3           | Filtros       |


Tabela: ProdutosTags

| iTagId      | iProdutoId    |
| ----------- |:-------------:|
| 1           | 1             |
| 1           | 2             |
| 1           | 3             |
| 1           | 4             |
| 2           | 1             |
| 2           | 2             |
| 3           | 3             |
| 3           | 4             |


Como podemos ver, a câmera digital possui as tags de Fotografia e Eletrônicos. Os filtros (3 e 4) pertence à tag Filtros. Já o Cartão SD está em Fotografia e Eletrônicos. Se vermos do ponto de vista das tags, temos na tag Fotografia dois produtos e na tag Filtro outros dois produtos. Espero ter esclarecido o funcionamento dos relacionamentos mais utilizados.

[Início](https://github.com/operandbr/operand-is-cool/blob/master/MySQL/README.md)
|
[Próximo >>](https://github.com/operandbr/operand-is-cool/blob/master/MySQL/Indices.md)
