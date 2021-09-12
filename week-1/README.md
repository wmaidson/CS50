## C

- Hoje vamos aprender uma nova linguagem, C : uma linguagem de programação que tem todos os recursos do Scratch e muito mais, mas talvez um pouco menos amigável, pois é puramente em texto:

```c
#include <stdio.h>

int main(void)
{
    printf("hello, world");
}
```

- Embora a princípio, pegando emprestado uma frase do MIT, tentar absorver todos esses novos conceitos pode parecer como beber de uma mangueira de incêndio, tenha certeza de que, no final do semestre, estaremos capacitados e experientes em aprender e aplicar esses conceitos .
- Podemos comparar muitos dos recursos de programação em C aos blocos que já vimos e usamos no Scratch. Os detalhes da sintaxe são muito menos importantes do que as ideias, às quais já fomos apresentados.
- Em nosso exemplo, embora as palavras sejam novas, as ideias são exatamente as mesmas que os blocos "quando a bandeira verde for clicada" e "diga (olá, mundo)" no Scratch:

<h1 align="center">
   <img alt="when_green_flag" src=".github/when_green_flag.png" height="300px" />
</h1>

- Ao escrever o código, podemos considerar as seguintes qualidades:
-- **Correção** , ou se nosso código funciona corretamente, conforme pretendido.
-- **Design** , ou uma medida subjetiva de quão bem escrito nosso código é, com base em quão eficiente ele é e quão elegante ou logicamente legível é, sem repetição desnecessária.
-- **Estilo** , ou o quão esteticamente formatado nosso código é, em termos de indentação consistente e outro posicionamento de símbolos. As diferenças de estilo não afetam a exatidão ou o significado do nosso código, mas afetam o quão legível é visualmente.

## CS50 IDE

- Para começar a escrever nosso código rapidamente, usaremos uma ferramenta para o curso, [`CS50 IDE`](https://ide.cs50.io/) , um *ambiente de desenvolvimento integrado* que inclui programas e recursos para escrever código. CS50 IDE é construído sobre um IDE baseado em nuvem popular usado por programadores gerais, mas com recursos educacionais adicionais e personalização.
- Abriremos o IDE e, após o login, veremos uma tela como esta:

<h1 align="center">
   <img alt="cs50_ide" src=".github/cs50_ide.png" height="300px" />
</h1>

- O painel superior, em branco, conterá arquivos de texto nos quais podemos escrever nosso código.
- O painel inferior, uma janela de **terminal** , nos permitirá digitar vários comandos e executá-los, incluindo programas de nosso código acima.
- Nosso IDE é executado na nuvem e vem com um conjunto padrão de ferramentas, mas saiba que também existem muitos IDEs baseados em desktop, oferecendo mais personalização e controle para diferentes fins de programação, ao custo de maior tempo e esforço de configuração.
- No IDE, iremos para Arquivo> Novo arquivo e, em seguida, Arquivo> Salvar para salvar nosso arquivo como `hello.c`, indicando que nosso arquivo será um código escrito em C. Veremos que o nome de nossa guia realmente mudou para `hello.c`, e agora colaremos nosso código acima:

```c
#include <stdio.h>

int main(void)
{
    printf("hello, world");
}
```

- Para executar nosso programa, usaremos uma CLI, ou **interface de linha de comando** , um prompt no qual precisamos inserir comandos de texto. Isso contrasta com a interface gráfica do usuário , ou GUI, como o Scratch, onde temos imagens, ícones e botões além do texto.


## Compilando


- No terminal no painel inferior de nosso IDE, iremos **compilar** nosso código antes de podermos executá-lo. Os computadores só entendem binário, que também é usado para representar instruções como imprimir algo na tela. Nosso **código-fonte** foi escrito em caracteres que podemos ler, mas precisa ser compilado: convertido em **código de máquina** , padrões de zeros e uns que nosso computador possa entender diretamente.
- Um programa chamado **compilador** pegará o código-fonte como entrada e produzirá o código de máquina como saída. No IDE CS50, já temos acesso a um compilador, por meio de um comando chamado **make** . Em nosso terminal, digitaremos `make hello`, o que encontrará automaticamente nosso `hello.c`arquivo com nosso código-fonte e o compilará em um programa chamado hello. Haverá alguma saída, mas nenhuma mensagem de erro em amarelo ou vermelho, então nosso programa foi compilado com sucesso.
- Para executar nosso programa, digitaremos outro comando ./hello,, que procura na pasta atual ., por um programa chamado helloe o executa.
- O `$` no terminal é um indicador de onde está o prompt ou onde podemos digitar mais comandos.

## Funções e argumentos

- Usaremos as mesmas ideias que exploramos no Scratch.
- Funções são pequenas ações ou verbos que podemos usar em nosso programa para fazer algo, e as entradas para funções são chamadas de **argumentos** .
-- Por exemplo, o bloco “diga” no Scratch pode ter considerado algo como “olá, mundo” como um argumento. Em C, é chamada a função de imprimir algo na tela `printf`(com a `f` posição de texto “formatado”, que veremos em breve). E em C, passamos os argumentos entre parênteses, como em `printf("hello, world");`. As aspas duplas indicam que queremos imprimir as letras `hello, world` literalmente, e o ponto-e-vírgula no final indica o final de nossa linha de código.
- As funções também podem ter dois tipos de saídas:
-- **efeitos colaterais** , como algo impresso na tela,
-- e **valores de retorno** , um valor que é passado de volta ao nosso programa que podemos usar ou armazenar para mais tarde.
O bloco “perguntar” no Scratch, por exemplo, criou um bloco “responder”.
- Para obter a mesma funcionalidade do bloco “ask”, usaremos uma **biblioteca** ou um conjunto de código já escrito. A Biblioteca CS50 incluirá algumas funções básicas e simples que podemos usar imediatamente. Por exemplo, `get_string` pedirá ao usuário uma **string** , ou alguma sequência de texto, e a retornará ao nosso programa. `get_string` recebe alguma entrada como prompt para o usuário, como What's your name?, e teremos que salvá-la em uma variável com:

```c
string answer = get_string("What's your name? ");
```

- Em C, o single `=` indica atribuição , ou configuração do valor à direita para a variável à esquerda. E C chamará a `get_string` função para obter sua saída primeiro.
- E também precisamos indicar que nossa variável chamada `answer` tem um **tipo** de string, então nosso programa sabe interpretar os zeros e uns como texto.
- Finalmente, precisamos nos lembrar de adicionar um ponto-e-vírgula para encerrar nossa linha de código.
No Scratch, também usamos o bloco “responder” dentro de nossos blocos “juntar” e “dizer”. Em C, faremos isso:

```c
printf("hello, %s", answer);
```

- O `%s` é chamado de código de formato , o que significa apenas que queremos que a `printf` função substitua uma variável onde está o `%s` espaço reservado. E a variável que queremos usar é `answer`, que fornecemos `printf` como outro argumento, separado do primeiro por uma vírgula. ( `printf("hello, answer")` seria literalmente impresso `hello, answer` todas as vezes).
- De volta ao IDE CS50, adicionaremos o que descobrimos:


```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    string answer = get_string("What's your name? ");
    printf("hello, %s", answer);
}
```

- Precisamos dizer ao compilador para incluir a Biblioteca CS50, com `#include <cs50.h>`, para que possamos usar a `get_string` função.
- Também temos a oportunidade de usar um estilo melhor aqui, já que poderíamos nomear nossa `answer` variável com qualquer coisa, mas um nome mais descritivo nos ajudará a entender sua finalidade melhor do que um nome mais curto como `a`ou `x`.
- Depois de salvar o arquivo, precisaremos recompilar nosso programa com `make hello`, já que alteramos apenas o código-fonte, mas não o código de máquina compilado. Outras linguagens ou IDEs podem não exigir que recompilemos manualmente nosso código depois de alterá-lo, mas aqui temos a oportunidade de ter mais controle e compreensão do que está acontecendo nos bastidores.
- Agora, `./hello` executará nosso programa e solicitará nosso nome conforme pretendido. Podemos notar que o próximo prompt é impresso imediatamente após a saída de nosso programa, como em `hello, Brian~/ $`. Podemos adicionar uma nova linha após a saída de nosso programa, de modo que o próximo prompt esteja em sua própria linha, com `\n`:

```c
printf("hello, %s\n", answer);
```

- `\n` é um exemplo de sequência de escape ou algum texto que representa algum outro texto.
