
## 1. Introdução

Este projeto visa desenvolver um Sistema de Controle de Despesas completo, com foco na aplicação prática dos princípios da **Orientação a Objetos (POO)**, como Herança, Polimorfismo, Interfaces e Métodos Estáticos. O sistema permitirá ao usuário gerenciar despesas, realizar a conciliação de pagamentos e administrar usuários e tipos de despesa, armazenando todos os dados em arquivos de texto.

**Status da Entrega:** **0.0.1** (Estrutura e Planejamento Inicial)

**Autor:** [Seu Nome Completo]
**Professor:** prof.roldjunior@uninga.edu.br


## 2. Estratégia de Construção (Abstração POO)

A arquitetura do sistema é modular e baseada em classes bem definidas, garantindo o baixo acoplamento e a alta coesão, conforme os pilares da POO:

### 2.1. Módulos e Pacotes (Organização)

O código será organizado em pacotes lógicos para separar as responsabilidades:

* **`main`**: Contém a classe principal (`Main.java`) responsável pela inicialização do sistema e exibição do Menu Principal.
* **`entidades`**: Classes que representam os dados principais do sistema, como Despesas, Usuários e Tipos de Despesa.
* **`negocio`**: Classes de controle (Gerenciadores) que implementam as regras de negócio e interagem com a persistência.
* **`utilidades`**: Classes que fornecem funcionalidades auxiliares, como Criptografia, e podem conter métodos estáticos.

### 2.2. Aplicação dos Conceitos de POO

| Conceito | Aplicação no Sistema | Classes Envolvidas |
| :--- | :--- | :--- |
| **Classes/Herança** | A classe **`Despesa`** será **abstrata**, servindo como base. Subclasses concretas (ex: `DespesaTransporte`, `DespesaEventual`) herdarão suas propriedades, mas poderão ter implementações específicas (ex: cálculo de imposto). | `Despesa`, `DespesaTransporte` (exemplo), `DespesaEventual` (exemplo) |
| **Interfaces/Polimorfismo** | A interface **`Pagavel`** definirá o contrato de pagamento (`anotarPagamento()`). Classes como `Despesa` e potencialmente outras (se o escopo for expandido) a implementarão. O Polimorfismo será usado ao listar diferentes tipos de despesas. | `Pagavel` (Interface), `Despesa` |
| **Construtores** | Será implementada a **sobrecarga de construtores** em `Despesa` e suas subclasses, permitindo instanciar despesas com diferentes níveis de detalhe (ex: Despesa com ID ou sem ID). A **sobrescrita de construtores** será utilizada para inicializar subclasses. | `Despesa`, `DespesaEssencial` (exemplo) |
| **Estáticos** | A classe **`ContadorGlobal`** ou um atributo estático em `Despesa` manterá o controle de um ID global para garantir a unicidade. A classe `CriptografiaUtil` usará **métodos estáticos** para criptografar senhas. | `Despesa`, `CriptografiaUtil` |



## 3. Detalhamento da Abstração (Classes, Atributos e Métodos)

### 3.1. Entidades Principais

| Classe | Propósito | Atributos Chave | Métodos Chave |
| :--- | :--- | :--- | :--- |
| **`Usuario`** | Representa o login no sistema. | `login: String`, `senhaCriptografada: String` | `setSenha(String): void`, `validarLogin(String, String): boolean` |
| **`TipoDespesa`** | Categorias para filtragem e gestão (ex: Alimentação). | `id: int`, `nome: String` | `getNome(): String` |
| **`Despesa` (Abstrata)** | Classe base, implementa `Pagavel`. | `id: int`, `descricao: String`, `valor: double`, `dataVencimento: Date`, `statusPaga: boolean`, `tipo: TipoDespesa` | `anotarPagamento(double, Date): void` (implementação de `Pagavel`), `abstract calcularImposto(): double` |

### 3.2. Classes de Controle e Utilidades

| Classe | Propósito | Atributos Chave | Métodos Chave |
| :--- | :--- | :--- | :--- |
| **`GerenciadorUsuarios`** | Controla o CRUD e a persistência de `Usuario`. | `caminhoArquivo: String` | `cadastrar(Usuario): boolean`, `listar(): List<Usuario>`, `salvarNoArquivo(): void` |
| **`GerenciadorDespesas`** | Controla o CRUD e a conciliação das despesas. | `listaDespesas: List<Despesa>` | `entrarDespesa(): void`, `listarEmAberto(Date, Date): List<Despesa>`, `editarDespesa(): void` |
| **`CriptografiaUtil`** | Fornece o serviço estático de criptografia de senhas. | _(Nenhum, pois usará métodos estáticos)_ | `static criptografar(String): String` |


## 4. Estrutura de Entrega 0.0.1

### 4.1. Conteúdo do Commit

O primeiro commit (`0.0.1`) estabelece a base do projeto:

1.  **Repositório Inicial:** Criado e compartilhado.
2.  **Documentação:** Arquivo `README.md` completo e `CHANGELOG.md` em `/docs`.
3.  **Código Esqueleto:**
    * `Main.java` com o **Menu Principal** funcional.
    * Cada opção do menu, ao ser acessada, executa apenas um **`System.out.println()`** de confirmação.
    * Criação das classes base (`Despesa`, `Usuario`) na estrutura de pacotes.


## 5. Changelog

O histórico de entregas e versões está documentado em:

[docs/CHANGELOG.md](docs/CHANGELOG.md)



## 0.0.1 - 05/11/2025 [Data do Commit/Envio]

### Estrutura e Planejamento Inicial

* **Repositório Criado:** Inicialização do repositório Git no GitHub e compartilhamento com o professor.
* **Documentação:**
    * Criação do arquivo `README.md` detalhando a estratégia de construção e a abstração das classes conforme os princípios de POO.
    * Criação do próprio `CHANGELOG.md` para rastreamento de versões.
* **Estrutura de Pacotes:** Definição e criação dos pacotes iniciais (`entidades`, `utilidades`).
* **Classes Base:** Estrutura básica das classes `Despesa` (abstrata) e `Usuario` definida nos pacotes.
* **Funcionalidade Mínima (Menu):**
    * Implementação do `Main.java` com o **Menu Principal** interativo.
    * Todas as opções do menu foram configuradas para exibir um *`System.out.println()`* de confirmação ao serem acessadas, cumprindo o requisito de entrega mínima.
