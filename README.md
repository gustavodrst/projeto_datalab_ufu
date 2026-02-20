## 🎯Objetivo
Este projeto visa avaliar o desempenho dos trainees do DataLab-UFU após a conclusão das trilhas obrigatórias do DataCamp, identificando lacunas de aprendizado e oportunidades de melhoria técnica.

## 📊Interpretação das estatísticas descritivas

Não temos diferenças significativas entre as estatísticas descritivas calculadas no Excel contra as calculadas no Python.

A maior nota foi 98 e a menor 45, uma amplitude de 53 pontos.

Como a mediana (74.5) é ligeiramente maior que a média (73.67), temos uma leve assimetria à esquerda indicando que há  algumas notas mais baixas (como o mínimo de 45) que estão puxando a média para baixo.
Além disso, há um desvio de aproximadamente 14 pontos que sugere uma turma heterogênea, ou seja, existem alunos que estão indo muito bem e os que estão com dificuldade.

De modo geral é uma turma com bom desempenho geral, já que a maioria (75%) tirou acima de 63 pontos.
![](https://github.com/gustavodrst/imagens/blob/main/gr%C3%A1ficos_desafio_trainee.png)

## 🧮Interpretação das Correlações 
### Correlações Positivas Fortes (Amarelo)
![](https://github.com/gustavodrst/imagens/blob/main/correla%C3%A7%C3%A3o_desafio_trainee.png)

Quando uma variável aumenta, a outra também aumenta quase na mesma proporção.

Horas de Estudo X Nota Final (Correlação = 1): estas variáveis apresentam uma correlação positiva perfeita. Indicando que, quanto mais tempo o aluno dedica ao estudo, maior é sua nota final.

Aulas Assistidas X Nota Final (Correlação = 0,99): estas variáveis apresentam uma correlação quase perfeita. Sugerindo que a presença e participação nas aulas estão diretamente ligadas a uma maior nota final.

## 📋Interpretação teste de Hipótese
A escolha de dividir os alunos exatamente em "Até 10h" e "Mais de 10h" foi feita para transformar uma variável contínua (horas_estudo) em uma variável categórica binária(até_10h e mais_10h), permitindo a comparação de médias entre dois grupos distintos.

Além disso, chegampos ao resultado de que rejeitamos a Hipótese Nula. Pois há evidências(p-valor<0.05) de que estudar mais de 10h aumenta a nota.

## 📈Interpreteção da Regressão
$\textbf{Mean Square Error (MSE) - Erro Quadrático Médio:}$ É a média dos quadrados dos erros. O erro é a diferença entre o valor real ($y$) e o valor previsto ($\hat{y}$) pelo modelo.

Sendo utilizado para medir o quão próximos os valores previstos estão dos reais. Por elevar o erro ao quadrado, o MSE penaliza severamente erros grandes, tornando-o ideal se você quer evitar grandes desvios a qualquer custo.

$$\text{Fórmula:}$$ $$MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$


$\textbf{Mean Absolute Error (MAE) - Erro Absoluto Médio:}$ É a média das diferenças absolutas entre os valores reais e previstos. 

Esta métrica fornece uma medida linear da magnitude do erro em uma escala que é fácil de interpretar (na mesma unidade dos dados originais). Ao contrário do MSE, ele não penaliza tanto os outliers, tratando todos os erros de forma proporcional.

$$\text{Fórmula:}$$ $$MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|$$

$\textbf{R2 Score (Coeficiente de Determinação):}$ É uma métrica estatística que representa a porcentagem da variância da variável dependente que é explicada pelo modelo, sendo utilizado para verificar a qualidade do ajuste. 
$$\text{Fórmula:}$$ $$R^2 = 1 - \frac{SS_{res}}{SS_{tot}}$$
Onde $SS_{res}$ é a soma dos quadrados dos resíduos e $SS_{tot}$ é a soma total dos quadrados

$\textbf{Como essas métricas avaliam o desempenho?}$ 

Tais métricas fornecem um diagnóstico do modelo

MSE/MAE baixos: Indicam que o modelo está errando pouco. Se o MSE estiver muito maior que o MAE, você sabe que tem alguns erros muito grandes (outliers) incomodando o modelo.

R2 Score alto: Indica que o modelo captura bem a tendência dos dados. Se o seu $R^2$ for baixo, a sua linha de regressão não está conseguindo "explicar" o que acontece com os dados.

$\textbf{Divisão de dados:}$

Ao usar a função train_test_split, dividimos o dataset em quatro partes:

x_train: As características que o modelo usará para aprender.

y_train: As respostas corretas que o modelo usa para ajustar seus parâmetros.

x_test: Dados novos que o modelo nunca viu, usados para fazer previsões após o treino.

y_test: As respostas reais do teste, usadas para comparar com as previsões e calcular o MSE, MAE e $R^2$.

E a função train_test_split realiza essa divisão para evitar o Overfitting (sobreajuste). Se testarmos o modelo com os mesmos dados que usamos para treiná-lo, ele pode simplesmente decorar os dados em vez de aprender a lógica por trás deles.

Dividir os dados nos permite simular o mundo real: treinando o modelo e verificamos se ele consegue prever com precisão.
