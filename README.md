# Teste-Inicial - Analise-de-dados-


##Temos 1 base de dados com informações dos clientes, tanto clientes atuais quanto clientes que cancelaram o cartão

Passo 1 - IMPORTAR BASE DE DADOS
PASSO 2 - VISUALIZAR E TRATAR BASE DE DADOS
PASSO 3 - DAR UMA OLHADA NA BASE DE DADOS-ver colunas da base
PASSO 4- CONSTRUIR UMA ANALISE PARA IDENTIFICAR O MOTIVO DE CANCELAMENTO.

##IDENTIFICAR QUAL O MOTIVO OU OS PRINCIPAIS MOTIVOS DOS CLIENTES ESTAREM CANCELANDO O CARTÃO.
[]
#from google.colab import drive
#drive.mount('/content/drive')
Mounted at /content/drive
[ ]
from google.colab import files
uploaded = files.upload()

[ ]
import pandas as pd
tabela = pd.read_csv('BMB CSV.csv', encoding="latin1")
#tabela = tabela.drop("CLIENTNUM", axis=1)

display(tabela)

##Função dropna() - O método Pandas dropna() permite que o usuário analise e solte Linhas / Colunas com valores Nulos de diferentes maneiras. 
##Parâmetros: eixo: o eixo leva o valor int ou string para linhas / colunas. A entrada pode ser 0 ou 1 para Inteiro e 'índice' ou 'colunas' para String.
[ ]

tabela = tabela.dropna()

[ ]
# Função display exibe a tabela do banco de dados
display(tabela.info())
#Função display(tabela.describe- exibe a tabela do banco de dados com informações resumidas. A função round(1)- arredonda as casas decimais para 1 casa decimal, tornando a visualização mais facil.)
display(tabela.describe().round(1))


##Agora devemos tratar os valores vazios e exibir um resumo das colunas da base de dados.
## Devemos avaliar a divisão entre clientes e cancelados, separando a coluna categorias em clientes e cancelados, para saber qual % são clientes e qual % são cancelados. 
##Metodo de contagem de valores- numeros absolutos ou percentual
[ ]
qtde_categoria = tabela["Categoria"].value_counts()
display(qtde_categoria)

qtde_categoria_perc = tabela["Categoria"].value_counts(normalize=True)
display(qtde_categoria_perc)

##Há varias formas de descobrir o motivo do cancelamento - Podemos olhar a comparação entre clientes e cancelados em cada uma das colunas da base de dados, para ver se essa informação traz algum insight novo.
## Podemos utilizar a Biblioteca do Python chamada plotly - exibição de gráficos usando o Python (Deve-se importar a biblioteca primeiro.
[ ]
#Biblioteca do Python chamada plotly - exibição de gráficos usando o Python (Deve-se importar a biblioteca primeiro.
import plotly.express as px
grafico_idade = px.histogram(tabela, x="Idade", color="Categoria")
grafico_idade.show()

[ ]
grafico_dependentes = px.histogram(tabela, x="Dependentes", color="Categoria")
grafico_dependentes.show()

[ ]
grafico_limite = px.histogram(tabela, x="Limite", color="Limite Consumido")
grafico_limite.show()

[ ]
Grafico_teste = px.histogram(tabela, x="Limite", x[1]="Limite Consumido", color="Categorias")
grafico_teste.show()
