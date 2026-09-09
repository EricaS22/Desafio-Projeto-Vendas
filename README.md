# 📊 Dashboard de Vendas - Indicadores Comerciais

[![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](#)
[![DAX](https://img.shields.io/badge/DAX-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)](#)
[![Power Query](https://img.shields.io/badge/Power_Query-107C41?style=for-the-badge&logo=microsoft-excel&logoColor=white)](#)

## 📌 Visão Geral do Projeto
Este projeto consiste em um dashboard estratégico e tático de **Indicadores Comerciais** desenvolvido no Power BI. A solução foi estruturada para acompanhar a performance de vendas, faturamento, volume de produtos vendidos e ticket médio, permitindo que gestores analisem a evolução dos resultados por equipe de vendas, gerentes, linhas e grupos de produtos.

---

## 🎯 Objetivos do Negócio
* **Centralizar KPIs Comerciais:** Apresentar cartões em destaque com Faturamento Total, Quantidade de Vendas, Ticket Médio e Quantidade de Produtos Vendidos.
* **Análise Temporal de Performance:** Correlacionar a evolução do Faturamento (barras) com a Quantidade de Vendas (linha) ao longo dos anos de 2018, 2019 e 2020.
* **Mapeamento de Produtos e Categorias:** Avaliar o Ticket Médio por Grupo de Produtos (Doces, Cachaça, Energéticos, etc.) e o volume total de produtos vendidos por categoria (Farinhas, Fermentos, Óleos, etc.).
* **Acompanhamento por Equipe e Hierarquia:** Analisar o desempenho individual por Gerente, Vendedor e Equipes de Vendas (Atacadistas, Varejo, Web).
* **Rastreabilidade de Dados (Drill-Through):** Permitir a navegação detalhada a partir do campo *Grupo Produto* para uma página analítica dedicada.

---

## 🛠️ Tecnologias e Funcionalidades Aplicadas
* **Power Query (ETL):** Tratamento de dados, limpeza, relacionamentos de tabelas e construção da dimensão.
* **Modelagem de Dados & DAX:** Implementação do modelo dimensional *Star Schema* conectando tabelas fato e dimensões, além do cálculo de medidas de faturamento e volume.
* **Recursos Interativos do Power BI:**
  * **Página Principal (Dashboard):** Visão consolidada com cartões KPI, gráficos combinados (dois eixos), gráficos de barras horizontais, tabela de resumo hierárquico e segmentadores de dados.
  * **Drill-Through:** Navegação e filtro automático ativado a partir do campo `Grupo Produto` na página *Detalhar por Grupo*.
  * **Árvore de Decomposição:** Página dedicada à *Análise Hierárquica* para desdobrar o Faturamento por Gerente ➔ Equipe Vendas ➔ Grupo Produto ➔ Ano.
  * **Segmentadores de Dados:** Filtros por *Ano*, *Mês*, *Linha Produto*, *Grupo Produto*, *Vendedor* e *Equipe de Vendas*.
  * **Design & UX/UI (Capa / Home):** Layout personalizado na cor roxa corporativa com botão interativo "Clique aqui" para direcionamento ao painel principal.

---

## 📈 Indicadores e Visualizações

### 1. Cartões de Destaque (KPIs)
* **Faturamento Total** 
* **Quantidade de Vendas** 
* **Ticket Médio** 
* **Quantidade de Produtos Vendidos** 

### 2. Análises Gráficas
* **Faturamento x Qtd de Vendas:** Gráfico combinado de colunas (Faturamento) e linha (Qtd de Vendas) por Ano.
* **Ticket Médio por Grupo:** Ranking horizontal do valor médio por grupo de produtos.
* **Qtd Produtos Vendidos:** Ranking horizontal do volume físico distribuído por categoria.
* **Matriz de Performance Comercial:** Tabela detalhada agrupando Gerentes, Faturamento, Qtd Vendas, Ticket Médio e Qtd Produtos.
* **Análise Hierárquica de Causa-Raiz:** Árvore de Decomposição desdobrando Faturamento por Gerente ➔ Equipe ➔ Grupo Produto.

---

## 🗂️ Modelagem de Dados (Star Schema)

O modelo foi construído utilizando as seguintes tabelas:

* **`fVendas` (Fato):** Registros granulares das transações de vendas (`cdProduto`, `cdVendedor`, `DataEmissao`, `Nfe`, `QtdItens`, `Valor Total.1`, `ValorUnitario`).
* **`fMetas` (Fato):** Metas planejadas por vendedor e data (`cdVendedor`, `Data`, `Valor`).
* **`dProdutos` (Dimensão):** Cadastro de itens (`cdProduto`, `Grupo Produto`, `Linha Produto`, `Produto`).
* **`dVendedor` (Dimensão):** Estrutura comercial (`cdVendedor`, `Equipe Vendas`, `Gerente`, `Supervisor`, `Vendedor`).
* **`dCalendário` (Dimensão):** Dimensão temporal para inteligência de tempo (`Ano`, `Data`, `Dia`, `Mês`, `Nome do Dia`, `Nome do Mês`, `Semestre`).
* **`_Medidas`:** Tabela técnica dedicada para organização dos cálculos DAX.
  
---

📁 Estrutura da Solução no Power BI

🏠 Home                     -> Tela inicial de apresentação com botão de navegação.
📊 Dashboard                -> Painel principal com KPIs, gráficos combinados, tabelas e filtros.
🔎 Detalhar por Grupo       -> Relatório detalhado acionado via Drill-through por Grupo de Produto.
🌳 Análise Hierárquica      -> Visual de Árvore de Decomposição para exploração do Faturamento.

---

## ✨ Boas Práticas Aplicadas

* **Modelagem Star Schema:** Separação clara entre tabelas Fato (`fVendas`, `fMetas`) e tabelas Dimensão (`dCalendário`, `dProdutos`, `dVendedor`), otimizando o desempenho e evitando ambiguidade nos filtros.
* **Centralização de Medidas:** Organização de todas as regras de negócio e cálculos DAX na tabela exclusiva `_Medidas`.
* **Sinalização Visual e UX:** Uso de navegação intuitiva com menu lateral de filtros e botões de ação para navegação entre páginas (`Home`, `Dashboard`, `Detalhar por Grupo`, `Análise Hierárquica`).

---

## 🚀 Como Visualizar este Projeto

1. Faça o download ou clone este repositório:
   git clone [https://github.com/EricaS22/Dashboard-de-Vendas.git](https://github.com/EricaS22/Dashboard-de-Vendas.git)

2. Abra o arquivo `.pbix` no **Power BI Desktop**.
3. Interaja com os filtros temporais (Ano/Mês) ou utilize o recurso de **botão direito do mouse em um Ticket Médio por Grupo** para navegar via *Drill-Through*.
