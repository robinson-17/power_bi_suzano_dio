**README**

**Projeto: Dashboard Corporativo**

Este repositório contém os scripts SQL para criação de um banco de dados MySQL no Azure e o preenchimento com dados para um dashboard corporativo no MS Power BI.

**Estrutura do Banco de Dados:**

1. **Tabelas:**
    * **employee:** 
        * Armazena informações sobre funcionários, incluindo Fname, Minit, Lname, Ssn, Bdate, Address, Sex, Salary, Super_ssn e Dno.
        * `Ssn` é a chave primária.
        * `Super_ssn` é uma chave estrangeira referenciando o `Ssn` do supervisor do funcionário.
        * `Dno` é uma chave estrangeira referenciando o `Dnumber` do departamento.
    * **department:**
        * Armazena informações sobre departamentos, incluindo Dname, Dnumber, Mgr_ssn, Mgr_start_date e Start_date.
        * `Dnumber` é a chave primária.
        * `Dname` é único.
        * `Mgr_ssn` é uma chave estrangeira referenciando o `Ssn` do gerente do departamento.
    * **dept_locations:**
        * Armazena informações sobre locais de departamentos, incluindo Dnumber e Dlocation.
        * `Dnumber` e `Dlocation` juntos formam a chave primária.
        * `Dnumber` é uma chave estrangeira referenciando o `Dnumber` do departamento.
    * **project:**
        * Armazena informações sobre projetos, incluindo Pname, Pnumber, Plocation e Dnum.
        * `Pnumber` é a chave primária.
        * `Pname` é único.
        * `Dnum` é uma chave estrangeira referenciando o `Dnumber` do departamento.
    * **works_on:**
        * Armazena informações sobre funcionários trabalhando em projetos, incluindo Essn, Pno e Hours.
        * `Essn` e `Pno` juntos formam a chave primária.
        * `Essn` é uma chave estrangeira referenciando o `Ssn` do funcionário.
        * `Pno` é uma chave estrangeira referenciando o `Pnumber` do projeto.
        * **week:** (Adicionada posteriormente) Armazena a semana de trabalho do funcionário no projeto.
    * **dependent:**
        * Armazena informações sobre dependentes de funcionários, incluindo Essn, Dependent_name, Sex, Bdate e Relationship.
        * `Essn` e `Dependent_name` juntos formam a chave primária.
        * `Essn` é uma chave estrangeira referenciando o `Ssn` do funcionário.

2. **Inserção de Dados:**
    * Dados de exemplo são inseridos em cada tabela usando instruções `INSERT`.

**Criação do Banco de Dados e Inserção de Dados:**

1. **Conectar ao MySQL:**
    * Utilize uma ferramenta como o MySQL Workbench para se conectar ao seu banco de dados MySQL no Azure.

2. **Criar Banco de Dados:**
    * Execute o comando `show databases;` para listar os bancos de dados existentes.
    * Se o banco de dados "company" não existir, crie-o usando `CREATE DATABASE company;` e selecione-o usando `USE company;`.

3. **Criar Tabelas:**
    * Execute as instruções `CREATE TABLE` para criar as tabelas com suas respectivas colunas, tipos de dados e restrições (chaves primárias, chaves estrangeiras, restrições únicas).

4. **Inserir Dados:**
    * Execute as instruções `INSERT` para preencher cada tabela com dados de exemplo.

5. **Atualizar Tabela works_on:**
    * Adicione uma nova coluna chamada "week" à tabela `works_on`: `ALTER TABLE works_on ADD COLUMN week INT;`
    * Atualize a coluna "week" com valores aleatórios entre 47 e 52: `UPDATE works_on SET week = FLOOR(47 + (RAND() * 6));`

**Observação:**

* Este README fornece uma visão geral básica da estrutura do banco de dados e do processo de inserção de dados.
* Você pode personalizar ainda mais o banco de dados e os dados para atender aos requisitos específicos do seu dashboard corporativo.
* Este projeto utiliza MySQL no Azure.

Espero que este README seja útil!
