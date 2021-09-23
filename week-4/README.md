## Hexadecimal

- Na semana 2, falamos sobre memória e como cada byte tem um endereço, ou identificador, para que possamos nos referir a onde nossos dados estão realmente armazenados.
- Acontece que, por convenção, os endereços de memória usam o sistema de contagem **hexadecimal** , ou base-16, onde existem 16 dígitos: 0-9, e AF como equivalentes a 10-15.
- Vamos considerar um número hexadecimal de dois dígitos:

```
16^1 16^0
   0    A
```

- Aqui, o A na casa das unidades (uma vez que 16 ^ 0 = 1) tem um valor decimal de 10. Podemos continuar contando até `0F`, que é equivalente a 15 em decimal.
Depois `0F`, precisamos carregar o um, pois iríamos de 09 para 10 em decimal:

```
16^1 16^0
   1    0
```

- Aqui, o 1tem um valor de 16 ^ 1 * 1 = 16, então `10` em hexadecimal é 16 em decimal.
- Com dois dígitos, podemos ter um valor máximo de `FF`, ou 16 ^ 1 * 15 + 16 ^ 0 * 15 = 240 + 15 = 255, que é o mesmo valor máximo com 8 bits de binário. Portanto, dois dígitos em hexadecimal podem representar convenientemente o valor de um byte em binário. (Cada dígito em hexadecimal, com 16 valores, mapeia para quatro bits em binário.)
- Por escrito, indicamos que um valor está em hexadecimal prefixando-o com `0x`, como em `0x10`, onde o valor é igual a 16 em decimal, em oposição a 10.
- O sistema de cores RGB convencionalmente usa hexadecimal para descrever a quantidade de cada cor. Por exemplo, `000000`em hexadecimal representa 0 para cada um de vermelho, verde e azul, para uma cor combinada de preto. E `FF0000`seria 255, ou a maior quantidade possível de vermelho. `FFFFFF` indicaria o valor mais alto de cada cor, combinando para ser o branco mais brilhante. Com valores diferentes para cada cor, podemos representar milhões de cores diferentes.
Para a memória do nosso computador, também usaremos hexadecimal para cada endereço ou localização.

## Endereços

- Podemos criar um valor ne imprimi-lo:

```c
#include <stdio.h>

int main(void)
{
    int n = 50;
    printf("%i\n", n);
}
```

- Na memória do nosso computador, existem agora 4 bytes em algum lugar que têm o valor binário de 50, rotulados n:

<h1 align="center">
   <img alt="n" src=".github/n.png" height="300px" />
</h1>

- Acontece que, com os bilhões de bytes na memória, os bytes da variável `n` começam em algum local, que pode ser semelhante a `0x12345678`.
- Em C, podemos realmente ver o endereço com o `&`operador, o que significa “obter o endereço desta variável”:

```c
#include <stdio.h>

int main(void)
{
    int n = 50;
    printf("%p\n", &n);
}
```

- `%p` é o código de formato de um endereço.
- No IDE CS50, vemos um endereço como `0x7ffd80792f7c`. O valor do endereço em si não é útil, pois é apenas algum local na memória onde a variável está armazenada; em vez disso, a ideia importante é que podemos usar esse endereço mais tarde.
- O `*` operador, ou o operador de **desreferência**, nos permite "ir para" o local para o qual um ponteiro está apontando.
- Por exemplo, podemos imprimir `*&n`, em que “ir para” o endereço `n`, e que irá imprimir o valor de `n`, `50`, já que é o valor no endereço `n`:

```c
#include <stdio.h>

int main(void)
{
    int n = 50;
    printf("%i\n", *&n);
}
```

## Ponteiros


- Uma variável que armazena um endereço é chamada de **ponteiro** , que podemos pensar como um valor que “aponta” para um local na memória. Em C, os ponteiros podem se referir a tipos específicos de valores.
Podemos usar o `*` operador (de uma forma infelizmente confusa) para declarar uma variável que queremos ser um ponteiro:

```c
#include <stdio.h>

int main(void)
{
   int n = 50;
   int *p = &n;
   printf("%p\n", p);
}
```
- Aqui, usamos `int *p` para declarar uma variável,, pque tem o tipo de `*`, um ponteiro, para um valor do tipo int, um inteiro. Então, podemos imprimir seu valor (um endereço, algo parecido `0x12345678`), ou imprimir o valor em sua localização com `printf("%i\n", *p);`.
- Na memória do nosso computador, as variáveis serão assim:

<h1 align="center">
   <img alt="p" src=".github/p.png" height="300px" />
</h1>

- Uma vez que pé uma variável em si, está em algum lugar na memória, e o valor armazenado lá é o endereço de `n`.
- Os sistemas de computador modernos são “64 bits”, o que significa que eles usam 64 bits para endereçar a memória, então um ponteiro terá na realidade 8 bytes, duas vezes o tamanho de um inteiro de 4 bytes.
Podemos abstrair o valor real dos endereços, uma vez que eles serão diferentes conforme declaramos variáveis ​​em nossos programas e não muito úteis, e simplesmente pensar pcomo "apontando para" algum valor:

<h1 align="center">
   <img alt="pointing" src=".github/pointing.png" height="300px" />
</h1>
- No mundo real, podemos ter uma caixa de correio identificada como “p”, entre muitas caixas de correio com endereços. Dentro de nossa caixa de correio, podemos colocar um valor como `0x123`, que é o endereço de alguma outra caixa de correio n, com o endereço `0x123`.