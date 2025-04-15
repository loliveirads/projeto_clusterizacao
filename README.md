# Segmentação de clientes por meio de algoritmos de clusterização

## 📌 Introdução

A personalização da experiência do cliente se tornou um dos pilares estratégicos mais importantes para empresas que buscam crescer de forma inteligente. Com base nessa premissa, este projeto tem como foco a **segmentação de clientes por meio de algoritmos de clusterização**, permitindo a identificação de grupos com comportamentos e características semelhantes.

Utilizando dados de uma base de clientes de e-commerce, realizei uma análise completa que envolve desde a **limpeza e engenharia de atributos**, até a **modelagem com K-Means** e a **visualização de perfis estratégicos no Power BI**. A segmentação possibilita ações como campanhas direcionadas, programas de fidelidade, reativação de clientes inativos e aumento do Lifetime Value (LTV) dos consumidores mais rentáveis.

Este repositório contempla o código, a documentação e os arquivos necessários para replicar o pipeline completo de análise e visualização dos resultados de forma prática, reprodutível e escalável.



## 🚀 Tecnologias Utilizadas

O projeto foi desenvolvido com ferramentas amplamente utilizadas no ecossistema de Ciência de Dados, com foco em reprodutibilidade, visualização e análise exploratória.

### 🐍 Linguagem

- **Python 3.11** — Linguagem principal para análise de dados, modelagem estatística e preparação dos dados.

### 📦 Gerenciamento de Ambiente

- **Poetry** — Gerenciador de dependências e ambientes virtuais, garantindo reprodutibilidade e isolamento do ambiente.

### 🔢 Bibliotecas Python

- `pandas` — Manipulação e transformação de dados tabulares.
- `numpy` — Operações matemáticas vetoriais.
- `matplotlib` e `seaborn` — Criação de gráficos estáticos e visualizações exploratórias.
- `scikit-learn` — Algoritmos de machine learning, especialmente K-Means.
- `plotly` — Gráficos interativos (opcional).
- `pickle` — Serialização e salvamento do modelo treinado.
- `ipykernel` — Integração do ambiente virtual com Jupyter.

### 📒 Desenvolvimento e Execução

- **Jupyter Notebook** — Utilizado para desenvolver e documentar todo o pipeline de análise e modelagem.

### 📊 Visualização e Apresentação

- **Power BI Desktop** — Ferramenta utilizada para criar o dashboard final, permitindo visualizações interativas por cluster, canal e perfil.

### 🧪 Complementares

- `openpyxl` — Leitura de arquivos Excel (caso necessário).
- `pyproject.toml` — Arquivo de configuração do projeto gerenciado pelo Poetry.

> Todas as dependências estão especificadas no `pyproject.toml` e podem ser instaladas automaticamente com `poetry install`.



## 🚀 Como Executar

```bash
# 1. Clone o repositório
git clone https://github.com/loliveirads/projeto_clusterizacao.git


2. Acesse a pasta do projeto:

```bash
cd projeto_clusterizacao
```

3. Ative o ambiente virtual:

```bash
poetry init
poetry shell
```

4. Instale as dependências com Poetry:

```bash
poetry install
```

5. Instale o kernel Jupyter para o ambiente Poetry:

```bash
poetry run python -m ipykernel install --user --name=segmentacao-clientes
```

6. Inicie o Jupyter Notebook:

```bash
poetry run jupyter notebook
```

7. No Jupyter, selecione o kernel `segmentacao-clientes` e abra o notebook principal:

```text
ClusterizaÇão.ipynb
```

## 📁 Etapas do Projeto

O desenvolvimento deste projeto seguiu uma estrutura organizada e iterativa, contemplando desde a aquisição dos dados até a entrega de visualizações estratégicas com foco em negócio. Abaixo, estão detalhadas as principais fases executadas:

### 1. 📥 Importação e Entendimento dos Dados

- Leitura do dataset `marketing_campaign.csv` contendo informações de 2.240 clientes.
- Análise da estrutura, tipos de variáveis e verificação de valores nulos.
- Separação das colunas em quatro grupos: `People`, `Products`, `Promotion` e `Place` para facilitar a organização e o entendimento das variáveis.

### 2. 🧼 Limpeza e Preparação dos Dados

- Conversão da coluna `Dt_Customer` para formato de data e criação de `CustomerTenure` (tempo como cliente).
- Substituição de categorias textuais por numéricas (ex: `Education`, `Marital_Status`).
- Criação da coluna `Children` como soma de `Kidhome` e `Teenhome`.
- Exclusão de registros inconsistentes e clientes inativos (sem compras).

### 3. 🛠 Engenharia de Atributos

- Criação das colunas `TotalMnt` (soma dos gastos), `TotalPurchases` (soma das compras), e `EngajamentoPromocional`.
- Cálculo do percentual de gastos por categoria (`MntWines_Pct`, etc.) e de compras por canal (`NumWebPurchases_Pct`, etc.) com base no total.
- Normalização dos dados com Min-Max Scaling.
- Alocação de pesos diferenciados às variáveis com maior impacto no modelo, como `TotalMnt`, `TotalPurchases`, `Income` e `CustomerTenure`.

### 4. 🤖 Modelagem com K-Means

- Aplicação do método do cotovelo (Elbow Method) para definição do número ideal de clusters.
- Treinamento do algoritmo K-Means com 4 grupos.
- Atribuição do cluster resultante a cada cliente.
- Armazenamento do modelo final com `pickle`.

### 5. 📊 Análise dos Clusters

- Análise estatística e visual de cada cluster: média por canal, categoria de produto, renda, tempo como cliente e engajamento.
- Interpretação dos perfis comportamentais e sua relação com as variáveis de entrada.
- Criação de gráficos comparativos (barras, boxplots, heatmaps) por cluster.

### 6. 📈 Visualização com Power BI

- Transformação do dataset em formato longo (long format) para facilitar visualizações dinâmicas.
- Criação de dashboard com gráficos de:
  - Distribuição de clientes por cluster
  - Gasto por categoria de produto
  - Compras por canal
  - Perfil demográfico dos clusters
- Inclusão de segmentações interativas por cluster e canal.

Cada etapa foi cuidadosamente documentada e organizada para permitir fácil reprodutibilidade e escalabilidade futura para outros tipos de segmentações.



## 📊 Insights Obtidos

Durante a análise exploratória e a aplicação do algoritmo de clusterização (K-Means), foram identificados **4 perfis distintos de clientes** com base em suas características demográficas e comportamentos de consumo. Abaixo estão os principais insights extraídos:

### 🔍 Perfis de Clientes

- **Cluster 0 – Caçador de Ofertas**  
  Clientes com menor poder aquisitivo, mas alta propensão a aproveitar promoções. Grande parte das compras ocorre durante ofertas. Estratégias promocionais podem gerar bom engajamento com esse grupo.

- **Cluster 1 – Comprador Equilibrado**  
  Perfil médio em renda e consumo. Realiza compras por múltiplos canais com frequência moderada. Ideal para campanhas de fidelização e conteúdos personalizados.

- **Cluster 2 – Cliente Premium**  
  Alto poder aquisitivo, ticket médio elevado e forte engajamento com categorias como vinhos e carnes. Deve ser priorizado em estratégias de retenção, programas VIP e ofertas exclusivas.

- **Cluster 3 – Engajado de Baixo Retorno**  
  Frequentemente visita os canais e responde bem a promoções, mas gera baixo retorno financeiro. Estratégia ideal: conversão em clientes ativos através de bundles ou campanhas específicas.

### 📈 Padrões Identificados

- **TotalMnt como fator crítico**: A variável que mais contribuiu para a segmentação foi o gasto total em produtos.  
- **Engajamento por canal**: O canal mais utilizado varia conforme o cluster — clientes premium preferem loja física, enquanto caçadores de ofertas são mais ativos online.  
- **Gasto por categoria**: Vinhos e carnes se destacam como os produtos mais consumidos pelos clientes com maior valor.  
- **Filhos como variável de segmentação**: A soma de `Kidhome` e `Teenhome` (coluna `Children`) revelou impacto no comportamento de compra, especialmente em clusters que priorizam produtos de consumo rápido.  
- **Variável Complain**: Extremamente desbalanceada (apenas 0,9% reclamaram), foi retirada do modelo e analisada separadamente.

### 💡 Decisões Estratégicas Potenciais

- Criar campanhas personalizadas por cluster (ex: descontos agressivos para caçadores de oferta, conteúdo premium para clientes VIP).  
- Direcionar o mix de produtos conforme a concentração de consumo em cada grupo.  
- Priorizar esforços de retenção nos clusters com maior Lifetime Value (ex: Cluster 2).  
- Tratar clusters com baixo retorno como públicos de reativação com foco em conversão.

Esses insights servem como base para a criação de ações comerciais mais eficientes e a implementação de estratégias de marketing orientadas por dados.

## ✅ Conclusão e Aplicações Futuras

O projeto demonstrou como a combinação de análise exploratória, engenharia de atributos e algoritmos de clusterização pode gerar insights valiosos sobre o comportamento dos clientes. A segmentação resultante permitiu identificar grupos distintos com diferentes níveis de engajamento, perfil de consumo e potencial de valor para o negócio.

Essa abordagem orientada por dados permite que empresas:

- Direcionem campanhas de marketing com maior precisão;
- Foquem esforços de retenção nos clientes com maior Lifetime Value;
- Reativem clientes inativos com ações específicas por perfil;
- Otimizem o mix de produtos e canais de comunicação com base em padrões reais.

### 🧭 Próximos Passos

- Aplicar modelos preditivos sobre propensão de compra por cluster;
- Implementar scoring de engajamento e churn;
- Automatizar a geração de clusters com pipelines em produção (ex: Airflow);
- Integrar a segmentação com plataformas de CRM ou campanhas digitais.

Este projeto serve como base sólida para iniciativas de inteligência comercial, CRM analítico e personalização de ofertas com apoio da Ciência de Dados.
