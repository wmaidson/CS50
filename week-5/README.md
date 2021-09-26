## Redimensionando matrizes

- Da última vez, aprendemos sobre ponteiros malloce outras ferramentas úteis para trabalhar com memória.
- Na semana 2, aprendemos sobre matrizes, onde poderíamos armazenar o mesmo tipo de valor em uma lista, consecutivamente na memória. Quando precisamos inserir um elemento, precisamos aumentar o tamanho do array também. Mas, a memória depois dele em nosso computador já pode ser usada para alguns outros dados, como uma string:

<h1 align="center">
<img alt="array_of_length_3" src=".github/array_of_length_3.png" height="300px" />
</h1>

- Uma solução pode ser alocar mais memória onde houver espaço suficiente e mover nosso array para lá. Mas precisaremos copiar nosso array lá, o que se torna uma operação com tempo de execução de O ( n ), já que precisamos copiar cada um dos n elementos originais primeiro:

<h1 align="center">
<img alt="array_of_length_4" src=".github/array_of_length_4.png" height="300px" />
</h1>

- O limite inferior da inserção de um elemento em um array seria O (1), pois já podemos ter espaço para ele no array.


## Estruturas de dados

- **As estruturas de dados** são formas mais complexas de organizar os dados na memória, permitindo-nos armazenar informações em diferentes layouts.
- Para construir uma estrutura de dados, precisaremos de algumas ferramentas:
- `struct` para criar tipos de dados personalizados
- `.` para acessar propriedades em uma estrutura
- `*` para ir para um endereço na memória apontado por um ponteiro
- `->` para acessar propriedades em uma estrutura apontada por um ponteiro