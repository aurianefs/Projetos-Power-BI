# Dashboard de Logística e Desempenho de Entregas

Este dashboard foi criado para monitorar e analisar o desempenho das entregas, fornecendo insights sobre o total de entregas, entregas no prazo, desempenho por canal de entrega, performance de vendedores, status das entregas, entregas mensais, desempenho por equipe e distribuição geográfica das entregas.

## Fontes de Dados

*   Banco de dados ou arquivo(s) Excel contendo informações sobre as entregas, incluindo:
    -   Data da entrega
    -   Data prevista de entrega
    -   Canal de entrega (ex: Correios, transportadora, entrega própria)
    -   Vendedor responsável
    -   Status da entrega (ex: Entregue, Pendente, Atrasado, Cancelado)
    -   Equipe responsável pela entrega
    -   Cidade de destino
    -  Avaliação (rating) da entrega pelo cliente

## Visualizações

*   Total de Entregas:
    -   Cartão (KPI) mostrando o número total de entregas no período analisado.
*   **Total de Entregas no Prazo:**
    -   Cartão (KPI) mostrando o número de entregas realizadas dentro do prazo.
    -   Percentual de entregas no prazo em relação ao total.
*   **Total de Entregas no Prazo por Canal de Entrega:**
    -   Gráfico de linhas mostrando o número de entregas no prazo para cada canal.
*   **Vendedor, Total de Entregas e Rating:**
    -   Tabela mostrando cada vendedor, o total de entregas realizadas por ele e a média do rating das entregas.
    -   Gráfico de dispersão relacionando o total de entregas com o rating dos vendedores.
*   **Percentual de Entrega por Status de Entrega:**
    -   Gráfico de barras mostrando a proporção de entregas para cada status (ex: Entregue, Atrasado, etc.).
*   **Total de Entrega por Mês:**
    -   Gráfico de linhas mostrando o número de entregas por mês ao longo do tempo.
*   **Percentual de Entrega por Equipe:**
    -   Gráfico de barras mostrando a proporção de entregas realizadas por cada equipe.
*   **Total de Entrega por Cidade:**
    -   Gráfico de barras mostrando o número de entregas para cada cidade.

[Captura de tela do Dashboard] - ![Análise de dados de logística](https://github.com/user-attachments/assets/71861693-3322-4dea-9cfa-651405c8cba3)

## Processo de ETL

1.  **Extração:** Os dados foram extraídos das fontes de dados usando o Power Query no Power BI Desktop.
2.  **Transformação:**
    -   Limpeza dos dados: tratamento de valores ausentes, remoção de duplicatas, etc.
    -   Criação de colunas calculadas:
        -   `Entrega no Prazo = IF(TabelaDeEntregas[Data da Entrega] <= TabelaDeEntregas[Data Prevista de Entrega], "Sim", "Não")`
    -   Modelagem dos dados: criação de relações entre as tabelas, se necessário.
    *   Criação de medidas DAX (exemplos):
        -   `Total de Entregas = COUNTROWS(TabelaDeEntregas)`
        -   `Total de Entregas no Prazo = CALCULATE([Total de Entregas], TabelaDeEntregas[Entrega no Prazo] = "Sim")`
        -   `Taxa de Entregas no Prazo = DIVIDE([Total de Entregas no Prazo], [Total de Entregas])`
        -   Medidas para calcular totais e percentuais por canal, vendedor, status, mês, equipe e cidade, usando funções como `CALCULATE`, `SUM`, `AVERAGE`, `COUNTROWS` e funções de data/hora.
3.  **Carga:** O modelo de dados foi carregado no Power BI Service para publicação e compartilhamento.

## Arquivo .pbix

O arquivo `https://github.com/aurianefs/Projetos-Power-BI/blob/main/An%C3%A1lise%20de%20dados%20-%20Log%C3%ADstica.pbix` contém o projeto completo do Power BI.

## Como visualizar

Para visualizar o dashboard interativamente, é necessário ter o Power BI Desktop instalado e abrir o arquivo `.pbix`. Para visualizar o dashboard online, acesse o link publicado no Power BI Service https://app.powerbi.com/groups/me/reports/f8551fad-ce8a-4f46-ba13-6bf57c6d47e0?ctid=e5a2d57f-82e3-43da-af1c-1a2cc1b42330&pbi_source=linkShare.

## Contato

Auriane F Sousa - aurianef8@gmail.com
