## Compilando

- Da última vez, aprendemos a escrever nosso primeiro programa em C, imprimindo “olá, mundo” na tela.
- Nós o compilamos `make hello` primeiro, transformando nosso código-fonte em código de máquina antes de podermos executar o programa compilado com `./hello`.
- `make` na verdade, é apenas um programa que chama `clang`, um compilador, com opções. Poderíamos compilar nosso arquivo de código-fonte `hello.c`, nós mesmos, executando o comando `clang hello.c`. Parece que nada aconteceu, o que significa que não houve erros. E se executarmos ls, agora vemos um `a.out` arquivo em nosso diretório. O nome do arquivo ainda é o padrão, para que possamos realmente executar um mais comando específico: `clang -o hello hello.c`.
-  Adicionamos outro **argumento de linha de comando** ou uma entrada para um programa na linha de comando como palavras extras após o nome do programa. `clang` é o nome do programa, e `-o`, `helloe hello.c` são argumentos adicionais. Estamos dizendo `clang` para usar `hello    como nome de arquivo de saída e hello.ccomo código-fonte. Agora, podemos ver `hello` sendo criado como saída.
- Se quisermos usar a biblioteca do CS50, via `#include <cs50.h>`, para a `get_string` função, também temos que adicionar um sinalizador `clang -o hello hello.c -lcs50`:

```c
#include <cs50.h>
#include <stdio.h>


int main(void)
{
    string name = get_string("What's your name? ");
    printf("hello, %s\n", name);
}
```

- O `-l` sinalizador vincula o `cs50` arquivo, que já está instalado no IDE CS50, e inclui o código de máquina para `get_string`(entre outras funções) que nosso programa pode consultar e usar também
- Com `make`, esses argumentos são gerados para nós, uma vez que a equipe já configurou `make` no IDE CS50 também.
- Compilar o código-fonte em código de máquina é, na verdade, feito de etapas menores:
-- pré-processando
-- compilando
-- montagem
-- ligando
- O **pré - processamento** geralmente envolve linhas que começam com a `#`, like `#include`. Por exemplo, `#include <cs50.h>` dirá `clang` para procurar esse arquivo de cabeçalho, uma vez que contém o conteúdo que queremos incluir em nosso programa. Em seguida, `clang` essencialmente substituirá o conteúdo desses arquivos de cabeçalho em nosso programa.
- Por exemplo …

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    string name = get_string("What's your name? ");
    printf("hello, %s\n", name);
}
```

... será pré-processado em:

```c
...
string get_string(string prompt);
int printf(string format, ...);
...

int main(void)
{
    string name = get_string("Name: ");
    printf("hello, %s\n", name);
}
```

- Isso inclui os protótipos de todas as funções dessas bibliotecas que incluímos, para que possamos usá-las em nosso código.
- **A compilação** pega nosso código-fonte, em C, e o converte em outro tipo de código-fonte chamado **código assembly** , que se parece com isto:

```c
...
main:                         # @main
    .cfi_startproc
# BB#0:
    pushq    %rbp
.Ltmp0:
    .cfi_def_cfa_offset 16
.Ltmp1:
    .cfi_offset %rbp, -16
    movq    %rsp, %rbp
.Ltmp2:
    .cfi_def_cfa_register %rbp
    subq    $16, %rsp
    xorl    %eax, %eax
    movl    %eax, %edi
    movabsq    $.L.str, %rsi
    movb    $0, %al
    callq    get_string
    movabsq    $.L.str.1, %rdi
    movq    %rax, -8(%rbp)
    movq    -8(%rbp), %rsi
    movb    $0, %al
    callq    printf
    ...
```

- Essas instruções são de nível inferior e estão mais próximas das instruções binárias que o processador de um computador pode entender diretamente. Eles geralmente operam nos próprios bytes, em oposição a abstrações como nomes de variáveis.
- A próxima etapa é pegar o código do assembly e traduzi-lo em instruções em binário, **montando** -o. As instruções em binário são chamadas de **código de máquina** , que a CPU de um computador pode executar diretamente.
- A última etapa é a **vinculação** , onde versões previamente compiladas de bibliotecas que incluímos anteriormente, como `cs50.c`, são realmente combinadas com o binário de nosso programa. Então vamos acabar com um arquivo binário, `a.out` ou `hell`o, que é o código de máquina combinada para `hello.c`, `cs50.c`, e `stdio.c`. (No IDE CS50, o código de máquina pré-compilado para `cs50.c`e `stdio.c` já foi instalado e `clang` foi configurado para localizá-los e usá-los.)
Essas quatro etapas foram abstraídas, ou simplificadas, por `make`, então tudo que temos que implementar é o código para nossos programas.