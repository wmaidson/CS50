## Semana Anterior

- Aprendemos sobre ferramentas para resolver problemas, ou bugs, em nosso código. Em particular, descobrimos como usar um depurador, uma ferramenta que nos permite percorrer lentamente nosso código e examinar os valores na memória enquanto nosso programa está em execução.
- Outra ferramenta poderosa, embora menos técnica, é a depuração de pato de borracha, onde tentamos explicar o que estamos tentando fazer com um pato de borracha (ou algum outro objeto) e, no processo, percebemos o problema (e esperamos solução!) - Em nosso próprio.
Olhamos para a memória, visualizando bytes em uma grade e armazenando valores em cada caixa, ou byte, com variáveis ​​e matrizes.

## Procurando

- Acontece que, com matrizes, um computador não pode olhar para todos os elementos de uma vez. Em vez disso, um computador só pode olhar para eles um de cada vez, embora a ordem possa ser arbitrária. (Lembre-se de que, na semana 0, David só conseguia olhar uma página de cada vez na lista telefônica, quer folheasse em ordem ou de maneira mais sofisticada.)
- **Pesquisar** é como resolvemos o problema de encontrar um valor específico. Um caso simples pode ter uma entrada de alguma matriz de valores e a saída pode ser simplesmente um bool, esteja ou não um valor específico na matriz.
- Hoje veremos algoritmos de pesquisa. Para discuti-los, consideraremos o tempo de execução , ou quanto tempo um algoritmo leva para ser executado dado algum tamanho de entrada.

## Grande

- Na semana 0, vimos diferentes tipos de algoritmos e seus tempos de execução:

<h1 align="center">
<img alt="running_time" src=".github/running_time.png" height="300px" />
</h1>

- Lembre-se de que a linha vermelha está pesquisando linearmente, uma página por vez; a linha amarela está pesquisando duas páginas por vez; e a linha verde está pesquisando logaritmicamente, dividindo o problema pela metade a cada vez.
- E esses tempos de execução são para o pior caso, ou o caso em que o valor leva mais tempo para ser encontrado (na última página, ao contrário da primeira página).

- A maneira mais formal de descrever cada um desses tempos de execução é com ** grandes notação** , que podemos pensar como “na ordem de”. Por exemplo, se nosso algoritmo é uma pesquisa linear, levará aproximadamente (n) passos, leia como “grande "O"  do n ”Ou“ na ordem de n”. Na verdade, mesmo um algoritmo que olha para dois itens de uma vez e leva n/2 passos tem . Isso porque, como fica cada vez maior, apenas o fator dominante, ou termo maior, , assuntos. No gráfico acima, se afastássemos o zoom e mudássemos as unidades em nossos eixos, veríamos as linhas vermelha e amarela ficando muito próximas.
- Um tempo de execução logarítmico é , não importa qual seja a base, uma vez que esta é apenas uma aproximação do que fundamentalmente acontece com o tempo de execução se  é muito grande.
- Existem alguns tempos de execução comuns:
-- (pesquisando uma página por vez, em ordem) 
-- (dividindo a lista telefônica pela metade a cada vez)
- Um algoritmo que executa um número constante de etapas, independentemente do tamanho do problema.
- Os cientistas da computação também podem usar grandes , grande notação Omega, que é o limite inferior do número de etapas do nosso algoritmo. Grande é o limite superior do número de etapas ou o pior caso.
- E temos um conjunto semelhante de grandes tempos de execução mais comuns:
- (pesquisar em uma lista telefônica, pois podemos encontrar nosso nome na primeira página que verificarmos)

## Pesquisa linear, pesquisa binária

No palco, temos algumas portas de adereço, com números escondidos atrás delas. Como um computador só pode olhar para um elemento de cada vez em um array, só podemos abrir uma porta de cada vez.
Se quisermos procurar o número zero, por exemplo, teríamos que abrir uma porta por vez, e se não soubéssemos nada sobre os números atrás das portas, o algoritmo mais simples seria ir da esquerda para a direita.
Então, podemos escrever pseudocódigo para pesquisa linear com:

```c
For i from 0 to n–1
    If number behind i'th door
        Return true
Return false
```

- Identificamos cada uma das n portas de 0 para n–1 e verificamos cada uma delas em ordem.
“Return false” está fora do loop for, já que só queremos fazer isso depois de olharmos por trás de todas as portas.
O grande o tempo de execução para este algoritmo seria , e o limite inferior, grande Omega, seria 1 .
Se soubermos que os números atrás das portas estão classificados, podemos começar pelo meio e encontrar nosso valor com mais eficiência.
Para pesquisa binária, nosso algoritmo pode ser semelhante a:

```c
If no doors
    Return false
If number behind middle door
    Return true
Else if number < middle door
    Search left half
Else if number > middle door
    Search right half
```

- O limite superior da pesquisa binária é (log n) , e o limite inferior também omega 1, se o número que procuramos estiver no meio, por onde começamos.
Com 64 lâmpadas, notamos que a pesquisa linear leva muito mais tempo do que a pesquisa binária, que leva apenas alguns passos.
Desligamos as lâmpadas na frequência de um **hertz** , ou ciclo por segundo, e a velocidade de um processador pode ser medida em gigahertz, ou bilhões de operações por segundo.