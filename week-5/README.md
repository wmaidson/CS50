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

## Listas Ligadas

- Com uma **lista vinculada** , podemos armazenar uma lista de valores que pode ser facilmente aumentada, armazenando valores em diferentes partes da memória:


<h1 align="center">
   <img alt="linked_list" src=".github/linked_list.png" height="300px" />
</h1>

- Nós temos os valores `1`, `2` e `3`, cada um, em algum endereço na memória como `0x123`, `0x456`, e `0x789`.
- Isso é diferente de uma matriz, pois nossos valores não estão mais próximos um do outro na memória. Podemos usar quaisquer locais da memória que estejam livres.
- Para rastrear todos esses valores, precisamos vincular nossa lista, alocando, para cada elemento, memória suficiente para o valor que queremos armazenar e o endereço do próximo elemento:

<h1 align="center">
   <img alt="linked_list_with_addresses" src=".github/linked_list_with_addresses.png" height="300px" />
</h1>

- Próximo ao nosso valor de `1`, por exemplo, também armazenamos um ponteiro,, `0x456` para o próximo valor. Chamaremos isso de **nó** , um componente de nossa estrutura de dados que armazena um valor e um ponteiro. Em C, implementaremos nossos nós com uma estrutura.
- Para nosso último nó com valor `3`, temos o ponteiro nulo, já que não há próximo elemento. Quando precisamos inserir outro nó, podemos apenas alterar aquele único ponteiro nulo para apontar para nosso novo valor.
- Temos a desvantagem de precisar alocar o dobro de memória para cada elemento, a fim de gastar menos tempo adicionando valores. E não podemos mais usar a pesquisa binária, uma vez que nossos nós podem estar em qualquer lugar da memória. Só podemos acessá-los seguindo os ponteiros, um de cada vez.
- No código, podemos criar nosso próprio struct chamado `node` e precisamos armazenar nosso valor, um `int` chamado `number`, e um ponteiro para o próximo `node`, chamado `next`:

```c
typedef struct node
{
    int number;
    struct node *next;
}
node;
```

- Começamos essa estrutura com `typedef struct node` para que possamos nos referir a uma `node` dentro de nossa estrutura.
- Podemos construir uma lista vinculada no código começando com nossa estrutura. Primeiro, vamos querer lembrar uma lista vazia, para que possamos usar o ponteiro nulo: `node *list = NULL;`.
- Para adicionar um elemento, primeiro precisamos alocar um pouco de memória para um nó e definir seus valores:

```c
// We use sizeof(node) to get the right amount of memory to allocate, and
// malloc returns a pointer that we save as n
node *n = malloc(sizeof(node));

// We want to make sure malloc succeeded in getting memory for us
if (n != NULL)
{
    // This is equivalent to (*n).number, where we first go to the node pointed
    // to by n, and then set the number property. In C, we can also use this
    // arrow notation
    n->number = 1;
    // Then we need to make sure the pointer to the next node in our list
    // isn't a garbage value, but the new node won't point to anything (for now)
    n->next = NULL;
}
```

- Agora nossa lista precisa apontar para este nó `list = n;`

<h1 align="center">
   <img alt="list_with_one_node" src=".github/list_with_one_node.png" height="150px" />
</h1>

- Para adicionar à lista, criaremos um novo nó da mesma maneira, alocando mais memória:

```c
n = malloc(sizeof(node));
if (n != NULL)
{
    n->number = 2;
    n->next = NULL;
}
```

- Mas agora precisamos atualizar o ponteiro em nosso primeiro nó para apontar para nosso novo `n`:

```c
list->next = n;
```

- Para adicionar um terceiro nó, faremos o mesmo seguindo o nextponteiro em nossa lista primeiro e, em seguida, definindo o nextponteiro lá para apontar para o novo nó:

```c
n = malloc(sizeof(node));
if (n != NULL)
{
    n->number = 3;
    n->next = NULL;
}
list->next->next = n;
```

- Graficamente, nossos nós na memória se parecem com isto:

<h1 align="center">
   <img alt="list_with_three_nodes" src=".github/list_with_three_nodes.png" height="150px" />
</h1>

- `n` é uma variável temporária, apontando para nosso novo nó com valor 3.
- Queremos que o ponteiro em nosso nó com valor 2 aponte para o novo nó também, então começamos list(que aponta para o nó com valor 1), seguimos o nextponteiro para chegar ao nosso nó com valor 2 e atualizamos o nextponteiro para apontar n.
- Como resultado, a pesquisa em uma lista encadeada também terá um tempo de execução de O ( n ), uma vez que precisamos olhar todos os elementos em ordem seguindo cada ponteiro, mesmo se a lista estiver ordenada. A inserção em uma lista encadeada pode ter um tempo de execução de O (1), se inserirmos novos nós no início da lista.