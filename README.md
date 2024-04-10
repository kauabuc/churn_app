# Minimizando o Churn em app de delivery com Excel, SQL e Power BI

### O projeto completo se encontra no meu [Medium](https://medium.com/@kakabuchweitz/minimizando-o-churn-em-app-de-delivery-com-excel-sql-e-power-bi-449ff93ab8e3)

### Overview do Projeto
---

O projeto apresenta uma análise feita em cima de uma base de um aplicativo de delivery que foi disponibilizada pela preditiva, com o objetivo de diminuir o churn encontrado no uso do aplicativo.

No projeto, foi feito seguindo as normas e orientações da metodologia CRISP-DM.

### DATA

Data: O conjunto de dados foi disponibilizado pela servidor da [Preditiva](https://www.preditiva.ai).

### Ferramentas

- Excel - Análise Dos Dados
- SQL - Coleta dos Dados
- PowerBI - Criação do relatório e acompanhamento dos indicadores

### Coleta Dos Dados

Foi utilizado o seguindo comando para obter os dados:

```
SELECT 
	dc."ClientId",
	dc."DataExtracao", 
	dc."Score_Credito", 
	dc."Estado", 
	dc."Gênero", 
	dc."Idade", 
	dc."Tempo_Cliente", 
	dc."Limite_Credito_Mercado", 
	dc."Qte_Categorias", 
	dc."Usa_Cartao_Credito", 
	dc."Programa_Fidelidade", 
	dc."Sum_Pedidos_Acumulados", 
	fc."DataUltimaTransacao" 
FROM 
	db_churn.dim_clientes dc 
JOIN 
	db_churn.fato_churn fc 
ON 
	dc."ClientId" = fc."ClientId" 
ORDER BY "ClientId"
```


### Preparação dos Dados

Consta com 14 variáveis, sendo 2 identificadores únicos, 2 datas, 6 variáveis quantitativas, 2 variáveis binárias e 2 qualitativas.

Além disso não foi necessário nenhum tratamento/preparação dos dados.

### Exploratory Data Analysis (Análise Exploratória dos Dados)

Ao longo da Análise, se baseou em perguntas chaves como critério de sucesso, sendo: 

- “Quais fatores de risco estão associados com o Churn de Clientes?”

- “Segmentar os clientes com a probabilidade de darem Churn nos próximos 4 meses em relação à data de extração de referência.”

- “Quais os possíveis planos de ação que a empresa pode fazer para diminuir esse problema?”

### Análise

Alguns dos insigths obtidos nessa etapa foram: 

1. 2013 clientes não transacionaram em nosso aplicativo nos últimos 30 dias, totalizando 20,13% de churn dos clientes.
2. Apenas 45 clientes não fizeram nenhuma transação nos últimos 4 meses.
3. Os dois scores mais frequente estão bem próximos sendo 550–649 (33,10%) e 650–749 (34,77%).
4. O Score crédito médio é de 650.
5. A maior concentração de clientes (31%) fica na faixa de 1000 a 2000.

### Resultados e Recomendações

Alguns dos resultados a serem comunicados:
1. Clientes sem fidelidade também apresentam uma chance maior de parar de usar nosso aplicativo.
2. O maior poder de separação entre as variáveis é a quantidade de categorias que apresenta um valor de 0,93 muito forte. É necessário entender os produtos que estão sendo consumidos por estes clientes.
3. Pessoas acima de 48 anos de idade também apresentam o dobro de chance de churn. Dado que provavelmente eles não tenham tanta intimidade com os aparelhos tecnológicos. Eles acabam fazendo o uso algumas vezes e depois param de usar.
4. Como foi demonstrado no estudo, as variáveis que foram compradas, Limite_Crédito e Score_crédito acabam não tendo um grande valor de significância na nossa variável alvo, em futuros estudos elas poderiam ser descartadas.








