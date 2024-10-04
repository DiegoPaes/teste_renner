# Teste Renner

## Detalhamento do problema de negócio

Dado um conjunto de caixas contendo com um conjunto de itens (produtos), cada um com
uma quantidade de peças, desejamos organizá-las em ondas de produção de forma que cada
item apareça no menor número de ondas possível. Cada onda pode conter caixas até o total de
2000 peças. Este problema é descrito na formulação abaixo:

$$
\begin{align*}
(1) &\quad \text{Minimizar: } \frac{\sum_{k \in K, j \in J} z_{kj}}{|K|} \\
\text{Sujeito a:} \\
(2) &\quad \sum_{j \in J} x_{ij} = 1, \quad \forall i \in I \\
(3) &\quad x_{ij} \leq y_j, \quad \forall i \in I, j \in J \\
(4) &\quad z_{kj} \geq x_{ij}, \quad \forall k \in K_i, j \in J \\
(5) &\quad \sum_{i \in I} x_{ij} \cdot p_i \leq c \cdot y_j, \quad \forall j \in J \\
(6) &\quad \mathbf{x} \in \{0,1\}, \mathbf{y} \in \{0,1\}, \mathbf{z} \in \{0,1\}
\end{align*}
$$

## Conjunto de dados

O arquivo excel as seguintes informações:


*   Caixa ID: id de identificação da caixa
*   Item: id de identificação do item
*   Peça: Quantidade peças

## Formulação do problema

Esse problema se parece muito com um problema de empacotamento da programação inteira (otimização combinatória), sendo o tipo de problema binário, ou está na onda ou não está, por esse motivo as variaveis x, y e z pertencem ao intervalo {0,1}, com base nesse problema temos as seguinte variáveis:

* O conjunto de caixas *I*
* O conjunto de itens *K*
* Número máximo de ondas *J*
* Para cada caisa *i* ∈ *I*
  * A lista de itens *K<sub>i</sub>* presentes na caixa
  * A quantidade de peças *p<sub>i</sub>* na caixa

## Solução

Inicialmente, a ideia era utilizar o PuLP para resolver o problema por meio de programação inteira. No entanto, meu computador pessoal não possui memória suficiente para rodar o algoritmo de forma eficiente.

Diante dessa limitação, optei por uma solução heurística, utilizando uma abordagem com algoritmos gulosos. Embora algoritmos gulosos nem sempre encontrem a solução ótima, eles podem encontrar soluções subótimas de forma eficiente. A principal característica dessa técnica é tomar decisões locais que parecem ser as melhores no momento, sem voltar atrás, buscando a melhor escolha possível em cada passo.

Embora existam outras técnicas, como a programação dinâmica e algoritmos genéticos, escolhi a estratégia gulosa por ter aprendido recentemente e desejava colocá-la em prática.

Vocês podem encontrar a solução desse problema, junto com o código, na pasta **teste_renner**.