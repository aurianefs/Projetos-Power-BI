# Dashboard de Análise de Vendas e Lucratividade

Este dashboard foi criado para analisar as vendas e a lucratividade da empresa, permitindo a visualização de métricas importantes como margem de lucro, valor médio por venda, lucro por categoria, custo de envio por mercado e valor de venda por modo de envio, com granularidade por dia, mês e ano.

## Fontes de Dados

*   Arquivo CSV com dados de vendas contendo informações como data da venda, valor da venda, custo do produto, categoria do produto, mercado, modo de envio e custo de envio.
*   (Opcional) Banco de dados SQL com informações de clientes (pode ser usado para enriquecer a análise com dados demográficos, por exemplo).

## Visualizações (Exemplos)

*   **Margem de Lucro:**
    *   Gráfico de linhas mostrando a evolução da margem de lucro ao longo do tempo (diário, mensal, anual).
    *   Cartões (KPIs) exibindo a margem de lucro atual, a margem de lucro média e a variação em relação ao período anterior.
*   **Média de Valor por Venda:**
    *   Gráfico de colunas mostrando a média de valor por venda por dia, mês ou ano.
    *   Gráfico de dispersão relacionando valor da venda com outras variáveis, como categoria ou mercado.
*   **Média de Lucro por Categoria:**
    *   Gráfico de barras mostrando a média de lucro para cada categoria de produto.
    *   Tabela mostrando o lucro total, a quantidade de vendas e a média de lucro por categoria.
*   **Média de Custo de Envio por Mercado:**
    *   Mapa mostrando os mercados e a média de custo de envio para cada um.
    *   Gráfico de barras comparando os custos de envio entre os diferentes mercados.
*   **Soma de Valor de Venda por Modo de Envio:**
    *   Gráfico de pizza ou gráfico de barras mostrando a proporção do valor total de vendas para cada modo de envio.
    *   Tabela mostrando o valor total de vendas e a quantidade de vendas por modo de envio.

[Captura de tela do Dashboard - [Dashboard lucro-vendas](https://github.com/user-attachments/assets/506eacbc-9438-4837-ad53-235e1af45c1a)


## Processo de ETL

1.  **Extração:** Os dados foram extraídos do arquivo CSV (e, se aplicável, do banco de dados SQL) usando o Power Query no Power BI Desktop.
2.  **Transformação:**
    *   Limpeza dos dados: tratamento de valores ausentes, remoção de duplicatas, correção de erros de digitação, etc.
    *   Criação de colunas calculadas:
        *   `Lucro = Valor da Venda - Custo do Produto`
        *   `Margem de Lucro = Lucro / Valor da Venda`
    *   Modelagem dos dados: criação de relações entre as tabelas, se necessário.
    *   Criação de medidas DAX:
        *   `Média de Valor por Venda = AVERAGE(TabelaDeVendas[Valor da Venda])`
        *   `Média de Lucro por Categoria = AVERAGEX(VALUES(TabelaDeProdutos[Categoria]), CALCULATE(AVERAGE(TabelaDeVendas[Lucro])))`
        *   `Média de Custo de Envio por Mercado = AVERAGEX(VALUES(TabelaDeVendas[Mercado]), CALCULATE(AVERAGE(TabelaDeVendas[Custo de Envio])))`
        *   `Soma de Valor de Venda por Modo de Envio = CALCULATE(SUM(TabelaDeVendas[Valor da Venda]), VALUES(TabelaDeVendas[Modo de Envio]))`
        *   Medidas para análise temporal (diária, mensal e anual) usando funções de data/hora do DAX (ex: `TOTALYTD`, `TOTALMTD`, `DAY`, `MONTH`, `YEAR`).
3.  **Carga:** O modelo de dados foi carregado no Power BI Service para publicação do dashboard e compartilhamento.

## Arquivo .pbix

O arquivo `analise_vendas_lucratividade.pbix` contém o projeto completo do Power BI.

## Como visualizar

Para visualizar o dashboard interativamente, é necessário ter o Power BI Desktop instalado e abrir o arquivo `.pbix`. Para visualizar o dashboard online, acesse o link publicado no Power BI Service (https://app.powerbi.com/groups/me/reports/1680b576-765e-4e09-95a4-0f3fb0b237b6?ctid=e5a2d57f-82e3-43da-af1c-1a2cc1b42330&pbi_source=linkShare).

## Contato

Auriane F Sousa - aurianef8@gmail.com
