# FIAP - Pós Tech Data Analytics | Tech Challenge (Fase 1)

Repositório destinado ao desenvolvimento do **Tech Challenge da Pós Tech em Data Analytics (FIAP/POSTECH)**, utilizando o dataset público da **Olist (Brazilian E-Commerce Public Dataset)**.

O objetivo do projeto é transformar dados transacionais em uma base analítica consolidada, permitindo a criação de **KPIs e análises executivas** voltadas para investidores e acionistas do setor de e-commerce, com foco em crescimento, logística e satisfação do cliente.

---

## Dataset Utilizado
Fonte: Kaggle – Brazilian E-Commerce Public Dataset by Olist  
Período analisado: 2016 a 2018

Tabelas utilizadas:
- `customers`
- `orders`
- `order_items`
- `payments`
- `reviews`
- `products`
- `sellers`
- `geolocation`
- `category_translation`

---

## Etapas do Projeto.

### 1. Download e carregamento dos dados.
O dataset foi obtido via `kagglehub` e carregado em DataFrames utilizando `pandas`.

DataFrames carregados:
- `customers`
- `orders`
- `order_items`
- `payments`
- `reviews`
- `products`
- `sellers`
- `geolocation`
- `category_translation`

---

### 2. Tratamento de datas.
As colunas de data foram convertidas para o tipo `datetime`, permitindo análises por período.

Colunas tratadas:

**orders**
- `order_purchase_timestamp`
- `order_approved_at`
- `order_delivered_carrier_date`
- `order_delivered_customer_date`
- `order_estimated_delivery_date`

**order_items**
- `shipping_limit_date`

**reviews**
- `review_creation_date`
- `review_answer_timestamp`

---

### 3. Métricas Criadas.

#### Métricas de tempo e logística
Foram criadas métricas relacionadas ao SLA de entrega e eficiência logística:

- `purchase_year_month`: ano-mês da compra (base para análises mensais)
- `purchase_year`: ano da compra
- `purchase_month`: mês da compra
- `delivery_days`: dias entre compra e entrega ao cliente
- `approval_days`: dias entre compra e aprovação do pedido
- `carrier_days`: dias entre aprovação e envio para transportadora
- `estimated_delivery_days`: prazo prometido ao cliente (dias)
- `delay_days`: diferença entre entrega real e entrega estimada
- `is_late`: indicador de atraso (1 = atrasou, 0 = não atrasou)

---

#### Métricas financeiras
- `item_total`: valor total do item incluindo frete (`price + freight_value`)

---

#### Sumarização de pagamentos
Como um pedido pode possuir múltiplos registros de pagamento, foi criada uma tabela consolidada por `order_id` contendo:

- `payment_value_total`: valor total pago no pedido
- `installments_mean`: média de parcelas do pedido
- `payment_type_main`: principal forma de pagamento registrada

---

#### Métricas de satisfação
Foram criados indicadores de avaliação do cliente:

- `review_is_good`: flag de avaliação boa (nota >= 4)
- `review_is_bad`: flag de avaliação ruim (nota <= 2)
- `review_response_days`: tempo de resposta em dias (entre criação e resposta da avaliação)

---

### 4. Criação de KPIs e gráficos executivos (Power BI)
A partir da base consolidada, foram desenvolvidos KPIs e gráficos com foco executivo, incluindo:

- **Pedidos e receita por mês** (crescimento do negócio)
- **Ticket médio** (faturamento médio por pedido)
- **Taxa de atraso (%)** (eficiência logística e SLA)
- **Atraso por região (UF)** (identificação de gargalos regionais)
- **Impacto do atraso nas avaliações** (relação entre atraso e satisfação do cliente)
- **Meios de pagamento mais utilizados** (comportamento do consumidor)

---

### 5. Base consolidada e exportação dos dados
Após os tratamentos, criação de métricas e consolidação das tabelas, foi gerada uma base final chamada **`fact_orders`**, estruturada no nível de granularidade de **1 linha por pedido**, permitindo análises consistentes e evitando duplicidades.

Essa base foi exportada em formato CSV e utilizada como fonte principal no Power BI para construção das visualizações e KPIs.

---

### 6. Preparação dos outputs para relatório e apresentação
Após a criação dos dashboards e KPIs, os gráficos foram exportados do Power BI em formato de imagem para inclusão nos entregáveis finais:

- `Relatório executivo`
- `Apresentação em slides (PPT)`

Esses outputs foram organizados de forma a suportar o storytelling do projeto, permitindo apresentação em linguagem executiva para stakeholders e investidores.

---

## Entregáveis do Projeto
Os entregáveis solicitados no Tech Challenge incluem:
- `Repositório GitHub com códigos e documentação`
- `Relatório executivo estruturado`
- `Apresentação executiva (slides)`
- `Vídeo executivo (até 5 minutos)`

---

## Como executar o projeto: 
Instale as dependências necessárias:
`pip install pandas kagglehub`
Abra o notebook no VSCode ou no Jupyter Notebook:
`tech-challenge-fase-um.ipynb`
Execute todas as células do notebook na ordem, garantindo que todas as etapas do pipeline sejam concluídas corretamente.
Ao final da execução, será gerado o arquivo consolidado:
`fact_orders_2.csv`

Esse arquivo é utilizado como base principal para importação no Power BI, permitindo a criação dos dashboards e KPIs executivos do projeto.
