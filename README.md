## Projeto de Sistema de Cadastros e Vendas (Java - Console)

Este projeto em Java implementa um sistema básico de gerenciamento de cadastros e registro de vendas, operando via console. O sistema permite cadastrar e listar informações de vendedores, clientes, fornecedores e produtos, além de registrar vendas e calcular o fechamento diário do caixa.

### Visão Geral da Estrutura

O sistema é modular, dividido em classes que representam as entidades de negócio e a lógica de persistência e interface.

| Arquivo | Classe | Descrição |
| :--- | :--- | :--- |
| **`Main.java`** | `Main` | Ponto de entrada do programa. Contém o menu de console e a lógica de interação do usuário para cadastro, listagem e registro de vendas. |
| **`Cadastros.java`** | `Cadastros` | Gerencia as listas (`ArrayList`) de todas as entidades: Vendedores, Clientes, Fornecedores, Produtos e Vendas. Contém métodos para cadastrar e listar cada tipo de entidade. |
| **`Vendedor.java`** | `Vendedor` | Representa um funcionário (vendedor) com dados pessoais, endereço, data de cadastro e informações de login/senha. |
| **`Cliente.java`** | `Cliente` | Representa um cliente com dados pessoais, endereço e data de cadastro. |
| **`Fornecedor.java`** | `Fornecedor` | Representa uma empresa fornecedora com `nomeFantasia`, `razaoSocial`, CNPJ e informações de contato/endereço. |
| **`Produto.java`** | `Produto` | Representa um produto com `nome`, `descricao`, `quantidade` em estoque, `preco` e o `fornecedor` associado. |
| **`Vendas.java`** | `Vendas` | Representa o registro de uma venda, associando um `cliente`, `produto`, quantidade e o `tipoPagamento`. |
| **`Administrador.java`** | `Administrador` | Uma classe simples que define o login e senha do administrador ("admin", "adminSenha"). |

### Funcionalidades do Sistema

O programa opera através de um menu principal interativo no console.

#### Menu Principal
1.  **Cadastrar:** Permite cadastrar Vendedor, Cliente, Fornecedor ou Produto.
2.  **Listar:** Permite listar Vendedores, Clientes, Fornecedores ou Produtos (Estoque).
3.  **Registrar Venda:** Permite registrar uma transação, debitando a quantidade do produto e processando o pagamento.
4.  **Listar Vendas:** Exibe todas as vendas registradas.
5.  **Fechamento do Dia:** Calcula o total das vendas pagas em Débito e Dinheiro.
9.  **Sair:** Encerra o programa.

#### Fluxo de Cadastro e Venda
* **Cadastro de Produtos:** Exige que o fornecedor já esteja cadastrado na lista de fornecedores, comparando pelo `nomeFantasia`.
* **Registro de Venda (Opção 3):**
    * Verifica se o Cliente e o Produto existem nas listas.
    * Se a venda for bem-sucedida, a `quantidade` do produto é diminuída em 1 (`decQntd()`).
    * **Pagamento em Crédito (Opção 1):** Oferece diferentes opções de parcelamento com ou sem juros, baseando-se no preço do produto (acima ou abaixo de R$1000).
    * **Pagamento em Débito/Dinheiro (Opção 2/3):** O valor do produto é somado à variável `fechamentoDoDia`.

#### Gestão de Cadastros (Opção 2)
* A listagem e edição de cadastros é controlada por um sistema simples de login.
* **Vendedor:** Pode listar todos os vendedores e editar o próprio cadastro.
* **Administrador (`admin`/`adminSenha`):** Pode listar vendedores/clientes/fornecedores/produtos, editar cadastros de clientes/fornecedores/produtos e tem a opção de **excluir** cadastros de Vendedor, Cliente ou Fornecedor.

### Implementação em Java

* As listas são gerenciadas pela classe `Cadastros` usando `ArrayList`.
* A interação com o usuário no `Main.java` utiliza a classe `Scanner` para receber a entrada do console.
* As classes de entidade (`Vendedor`, `Cliente`, etc.) utilizam *getters* e *setters* para acessar e modificar seus atributos.
