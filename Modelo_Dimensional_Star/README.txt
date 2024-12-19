## Desafio Modelagem Dimensional em Star Schema - Professor.

**Introdução**

Este documento descreve a modelagem dimensional em esquema estrela desenvolvida para o projeto Power BI Analyst - DIO, utilizando o MySQL Workbench. O objetivo principal da modelagem é criar uma estrutura de dados que facilite a análise e a geração de relatórios com dados sobre Professores.

**Esquema Dimensional**

O modelo consiste em uma tabela fato central, **Fato_Professor**, conectada a diversas tabelas dimensão:

* **Dimensão_Professor:** Contém informações detalhadas sobre os professores, como nome, titulação e área de atuação.
* **Dimensão_Curso:** Contém informações sobre os cursos ministrados, incluindo nome, nível e área do conhecimento.
* **Dimensão_Departamento:** Contém informações sobre os departamentos aos quais os professores estão vinculados.
* **Dimensão_Data:** Contém informações sobre a data de oferta dos cursos, como ano, mês, trimestre e dia da semana.

**Relações entre as Tabelas**

* A tabela fato **Fato_Professor** está relacionada a todas as tabelas dimensão através de chaves estrangeiras.
* A chave primária de cada tabela dimensão (ProfessorID, CursoID, DepartamentoID, DataID) é a chave estrangeira na tabela fato, estabelecendo a relação entre as tabelas.

**Justificativa da Modelagem**

A escolha do esquema estrela foi baseada nos seguintes motivos:

* **Simplicidade:** O esquema estrela é fácil de entender e implementar, facilitando a compreensão e a manutenção do modelo.
* **Desempenho:** O esquema estrela é otimizado para consultas analíticas, permitindo que sejam realizadas rapidamente.
* **Flexibilidade:** O esquema estrela permite a adição de novas dimensões e medidas de forma relativamente simples.

**Ferramentas Utilizadas**

* **MySQL Workbench:** Ferramenta utilizada para a criação e modelagem do banco de dados.

**Próximos Passos**

* **Implementação:** Criação das tabelas e inserção dos dados no banco de dados.
* **ETL:** Desenvolvimento dos processos de extração, transformação e carga dos dados.
* **Criação de Cubos OLAP:** Desenvolvimento de cubos OLAP para análise multidimensional dos dados.
* **Criação de Dashboards:** Desenvolvimento de dashboards para visualização dos dados.

**Considerações Finais**

Este modelo dimensional fornece uma base sólida para a análise dos dados de [Seu Projeto]. A flexibilidade do esquema estrela permite que o modelo seja adaptado e expandido para atender às futuras necessidades de análise.

