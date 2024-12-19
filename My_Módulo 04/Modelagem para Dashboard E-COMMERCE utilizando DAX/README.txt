# Modelagem e Transformação de dados com DAX

Este projeto demonstra a implementação de um modelo dimensional para análise de dados de vendas, utilizando Power Query para transformações e DAX para cálculos avançados no Power BI.

## Estrutura do Projeto

### Tabelas e Transformações

#### 1. Fonte Principal (Financials_origem)
- Base central dos dados utilizando referência para criação das demais tabelas
- Garante consistência e integridade na atualização dos dados
- Identificador único SK_ID mantido em todas as tabelas derivadas

#### 2. Tabela Fato (Fvendas)
- Criada a partir da referência da Financials_origem
- Transformações realizadas:
  - Adição de SK_ID como identificador único (índice iniciando em 0)
  - Criação de ID_produto baseado na coluna de produtos
  - Mantém métricas principais de vendas e relacionamentos

#### 3. Dimensões

##### Ddetalhes
- Deriva da Financials_origem por referência
- Mantém SK_ID para relacionamento com Fvendas
- Contém detalhes complementares das transações

##### Ddesconto
- Referência da tabela Fvendas
- Foco em informações de descontos aplicados
- Relacionamento via ID_produto

##### Dprodutos_detalhes
- Referência da tabela Fvendas
- Agregações por produto incluindo:
  - Média de unidades vendidas
  - Médias de valor de vendas
  - Mediana de valor de vendas
  - Valores máximo e mínimo de venda
- Mantém consistência através do ID_produto

##### Dcalendario
- Criada via função DAX
- Geração automática baseada no intervalo de datas de Fvendas
- Inclui dimensões temporais como:
  - Ano, Mês, Trimestre, Semestre
  - Formatações específicas para análise temporal
  - Suporte a análises de tendências

Função DAX
Dcalendario = 
VAR MinDate = MIN(Fvendas[Date])
VAR MaxDate = MAX(Fvendas[Date])
RETURN
ADDCOLUMNS(
    CALENDAR(MinDate, MaxDate),
    "Ano", YEAR([Date]),
    "Mês Número", MONTH([Date]),
    "Mês Nome", FORMAT([Date], "mmmm"),
    "Trimestre", "T" & FORMAT([Date], "Q"),
    "Semestre", "S" & IF(MONTH([Date])<=6,1,2),
    "Dia da Semana Número", WEEKDAY([Date],2),
    "Dia da Semana", FORMAT([Date], "dddd"),
    "Ano-Mês", FORMAT([Date], "yyyy-mm"),
    "Data Formato BR", FORMAT([Date], "dd/mm/yyyy")
)

## Modelo Dimensional

### Relacionamentos
- Estrutura Star Schema (Modelo Estrela)
- Fvendas como tabela fato central
- Relacionamentos unidirecionais (1:N) com dimensões
- Evita relacionamentos muitos-para-muitos
- Otimizado para performance e simplicidade de consultas

### Boas Práticas Implementadas
1. Uso de referências ao invés de cópias diretas
2. Manutenção de identificadores únicos
3. Padronização de nomenclatura
4. Relacionamentos otimizados
5. Transformações documentadas

## Uso e Manutenção

### Atualizações
- Dados atualizados a partir da fonte Financials_origem
- Transformações aplicadas automaticamente
- Integridade mantida através dos relacionamentos

### Considerações Importantes
- Manter consistência do ID_produto em novas entradas
- Verificar integridade dos relacionamentos após atualizações
- Monitorar performance das transformações

Este modelo fornece uma base sólida para análises de vendas, permitindo visualizações e insights através de um modelo dimensional bem estruturado e manutenível.