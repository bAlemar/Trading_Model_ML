# Trading Model using Decision Tree
## Explicação das funções:
### base_dados: 
Criar as variáveis target e tirar as colunas que não iremos utilizar.
### Add_var: 
Caso queiramos adicionar uma variável que não consegue ser calculada pelo Fechamento,alta,etc. Para adicionarmos essa variável, teremos que te-la numa pd.series, o qual tenha como índice a data. Após isso será aplicado um merge no index. OBS: DADOS PODEM SER PERDIDOS.
### Train_Test: 
Por se tratar de um série temporal devemos fazer divisão correta dos dados respeitando a variável tempo. Você pode determinar o tamanho da base de treinamento retornando valores entre 0-1.
### Modelo: 
Treinamento do modelo, é válido por outros parâmetros e ir comparando, como fizemos com o tamanho da base em Train_Test.

### Analise_resultado: 
Acurácia tanto do treinamento quanto do teste. Aqui podemos ver se nosso modelo está overfittado ou não. Além disso, podemos ver a precision e recall do modelo, por meio da matrix de confusão. Eu tenho estudo de Matrix de Confusion aqui no Github mesmo, só procurar, acho que foi primeiro upado.

### Retorno_modelo: 
Iremos fazer um merge com df original a fim de pegar o retorno de mercado para os y_test. Agora, com retorno iremos aplicar np.where e pegar o retorno dos dias que nosso y_pred previu como alta. Nesse modelo apenas entramos comprado.

### ativo_retorno: 
Basicamente ver retorno de um ativo dada a data de inicio do test. ( X_test.index[0]).  
OBS: Parando para pensar nem precisavamos dessa função para comparar retorno do mesmo ativo, podíamos ter feito na função acima(utilizando y_test).Mas fica como função para comparar outros ativos 😉

### Comparacao_ativo: 
Plota gráfico a fim de verificar retornos dos modelo e ativo ao longo do tempo.

### Analise_feature: 
Analisarmos as melhores features e seus coeficientes, lembrando que essa função é para model de Decision Trees, caso tenta outro modelo pode dar erro.

### Heat_map: 
Plota uma matriz de correlação, dada um certo data_frame.



## Seleção das Variáveis
Sinceramente, apenas peguei  os indicadores de Momento da TA-lib(e fui testando os melhores set-ups, sem pretensão alguma. Essa parte ainda será atualizada ao longo da semana.
Um bom estudo, seria pegar todos os indicadores rodar numa arvore de decisão ou numa Random Forest e fazer um feature selection. 
https://mrjbq7.github.io/ta-lib/func_groups/momentum_indicators.html)
## Seleção do Modelo
OBS: Explicação de árvore decisão fica para uma próxima,intuito do código não é esse.
Árvore de decisão é um ótimo modelo de máquina supervisionada que provém ótimos resultados e uma fácil interpretação. Nesse sentido, a árvore traça todos os resultados possíveis de um decisão(nesse caso mercado sobe ou desce) e traça um caminho até chegar uma conclusão, nesse caminho é aplicado valores específicos a cada problema. Dessa maneira, a abordagem identifica caminhos de decisão relevantes, o que pode ser interpretado ao apresentar uma ideia ao gestor de um fundo talvez(?).
Fonte: https://smallbusiness.chron.com/advantages-decision-trees-75226.html
