# Python Basics

- Hoje vamos aprender uma nova linguagem de programação chamada Python. Uma linguagem mais recente que a C, ela possui recursos adicionais, bem como simplicidade, levando à sua popularidade.
- O código-fonte em Python parece muito mais simples do que C. Na verdade, para imprimir “olá, mundo”, tudo o que precisamos escrever é:

```py
print("hello, world")
```

- Observe que, ao contrário de C, não precisamos especificar uma nova linha na `print` função ou usar um ponto-e-vírgula para encerrar nossa linha.
- Para escrever e executar este programa, usaremos o IDE CS50, salvaremos um novo arquivo `hello.py` apenas na linha acima e executaremos o comando `python hello.py`.
- Podemos obter strings de um usuário:
 
```py
answer = get_string("What's your name? ")
print("hello, " + answer)
```

- Também precisamos importar a versão Python da biblioteca CS50,, `cs50` apenas para a função `get_string`, então nosso código ficará assim:

```py
from cs50 import get_string

answer = get_string("What's your name? ")
print("hello, " + answer)
```
- Criamos uma variável chamada `answer` sem especificar o tipo e podemos combinar ou concatenar duas strings com o `+` operador antes de passá-lo para `print`.
- Podemos usar a sintaxe para **cadeias de formato**, `f"..."` para ligar variáveis. Por exemplo, poderíamos ter escrito `print(f"hello, {answer}")` para `answer` inserir o valor de em nossa string circundando-o com chaves.
- Podemos criar variáveis com apenas `counter = 0`. Ao atribuir o valor de `0`, estamos definindo implicitamente o tipo como um inteiro, portanto, não precisamos especificar o tipo. Para incrementar uma variável, podemos usar `counter = counter + 1` ou counter `+= 1`.
- As condições são semelhantes a:
- 
```py
if x < y:
    print("x is less than y")
elif x > y:
    print("x is greater than y")
else:
    print("x is equal to y")
```


- Ao contrário de C, onde as chaves são usadas para indicar blocos de código, o recuo exato de cada linha é o que determina o nível de aninhamento em Python.
- E em vez de `else if`, apenas dizemos `elif`.
- As expressões booleanas também são ligeiramente diferentes:

```py
while True:
    print("hello, world")
```

- Ambos `True` e `False` são maiúsculos em Python.
- Podemos escrever um loop com uma variável:

```py
i = 0
while i < 3:
    print("hello, world")
    i += 1
```

- Também podemos usar um `for` loop, onde podemos fazer algo para cada valor em uma lista:

```py
for i in [0, 1, 2]:
    print("cough")
```

- Listas em Python, `[0, 1, 2]` são como matrizes em C.
- Este `for` loop definirá a variável `i` para o primeiro elemento, `0` run e, em seguida, para o segundo elemento, `1` run e assim por diante.
- E podemos usar uma função especial,, `range` para obter alguns valores, como em `for i in range(3):`. `range(3)` nos dará uma lista até, mas não incluindo 3, com os valores `0`, `1`e `2`, que podemos usar. `range()` também aceita outras opções, portanto, podemos ter listas que começam com valores diferentes e têm incrementos diferentes entre os valores. Observando a [`documentação`](https://docs.python.org/3/library/stdtypes.html?highlight=range#range), por exemplo, podemos usar `range(0, 101, 2)` para obter um intervalo de `0` a `100` (já que o segundo valor é exclusivo), incrementando por `2` uma vez.
- Para imprimir itambém, podemos apenas escrever `print(i)`.
- Como geralmente há várias maneiras de escrever o mesmo código em Python, as formas mais comumente usadas e aceitas são chamadas de **Pythonic** .
- Em Python, existem muitos tipos de dados integrados:
- `bool`, `True` ou `False`
- `float`, numeros reais
- `int`, inteiros
- `str`, cordas
- Enquanto C é uma **linguagem fortemente tipada** , onde precisamos especificar tipos, Python é **fracamente tipada**, onde o tipo está implícito nos valores.
- Outros tipos em Python incluem:
- `range`, sequência de números
- `list`, sequência de valores mutáveis ou valores que podemos alterar
- E as listas, mesmo que sejam como arrays em C, podem aumentar e diminuir automaticamente em Python
`- tuple`, coleção de valores ordenados como coordenadas xey ou longitude e latitude
- `dict`, dicionários, coleção de pares chave / valor, como uma tabela hash
- `set`, coleção de valores únicos ou valores sem duplicatas
- A biblioteca CS50 para Python inclui:
- `get_float`
- `get_int`
- `get_string`
- E podemos importar funções uma de cada vez ou todas juntas:

```py
from cs50 import get_float
from cs50 import get_int
from cs50 import get_string
````

```py
import cs50
```

```py
from cs50 import get_float, get_int, get_string
```

## Exemplos

- Como o Python inclui muitos recursos, bem como bibliotecas de código escrito por outros, podemos resolver problemas em um nível mais alto de abstração, em vez de implementar todos os detalhes nós mesmos.
- Podemos desfocar uma imagem com:

```py
from PIL import Image, ImageFilter

before = Image.open("bridge.bmp")
after = before.filter(ImageFilter.BoxBlur(1))
after.save("out.bmp")
```

- No Python, incluímos outras bibliotecas com `import`, e aqui vamos `import` os nomes `Image` e `ImageFilter` da `PIL` biblioteca. (Outras pessoas escreveram esta biblioteca, entre outras, e disponibilizaram para todos nós baixarmos e usarmos.)
- `Imag`e` é uma estrutura que não apenas possui dados, mas funções que podemos acessar com a `.` sintaxe, como com `Image.open`.
- Abrimos uma imagem chamada `bridge.bmp`, chamamos uma função de filtro de desfoque e salvamos em um arquivo chamado `out.bmp`.
- E podemos executar isso python `blur.py` depois de salvar em um arquivo chamado `blur.py`.
- Podemos implementar um dicionário com:

```py
words = set()

def load(dictionary):
  file = open(dictionary, "r")
  for line in file:
      words.add(line.rstrip())
  file.close()
  return True

def check(word):
    if word.lower() in words:
        return True
    else:
        return False

def size():
    return len(words)

def unload():
    return True
```

- Primeiro, criamos um novo conjunto chamado `words`.
- Observe que não precisamos de uma `main` função. Nosso programa Python será executado de cima para baixo. Aqui, queremos definir uma função, então usamos `def load()`. `load` terá um parâmetro,, `dictionary` e seu valor de retorno está implícito. Abrimos o arquivo com `open` e iteramos sobre as linhas do arquivo com apenas `for line in file:`. Em seguida, removemos a nova linha no final de `line` e a adicionamos ao nosso conjunto `words`. Observe que `line` é uma string, mas tem uma `.rstrip` função que podemos chamar.
- Então, `check` podemos apenas pedir `if word.lower() in words`. Pois `size`, podemos usar `len` para contar o número de elementos em nosso conjunto e, finalmente, pois `unload`, não precisamos fazer nada, já que o Python gerencia a memória para nós.
- Acontece que, embora implementar um programa em Python seja mais simples para nós, o tempo de execução de nosso programa em Python é mais lento do que nosso programa em C, pois a linguagem tem que trabalhar mais para nós com soluções de uso geral, como para memória gestão.
- Além disso, Python também é o nome de um programa chamado **interpretador** , que lê nosso código-fonte e o traduz para um código que nossa CPU pode entender, linha por linha.
Por exemplo, se nosso pseudocódigo da semana 0 estava em espanhol e não entendíamos espanhol, teríamos que traduzi-lo lentamente, linha por linha, para o inglês antes de podermos pesquisar um nome em uma lista telefônica:

```py
1   Recoge guía telefónica
2   Abre a la mitad de guía telefónica
3   Ve la página
4   Si la persona está en la página
5       Llama a la persona
6   Si no, si la persona está antes de mitad de guía telefónica
7       Abre a la mitad de la mitad izquierda de la guía telefónica
8       Regresa a la línea 3
9   Si no, si la persona está después de mitad de guía telefónica
10      Abre a la mitad de la mitad derecha de la guía telefónica
11      Regresa a la línea 3
12  De lo contrario
13      Abandona
```
- Portanto, dependendo de nossos objetivos, também teremos que considerar a troca de tempo humano ao escrever um programa que é mais eficiente, versus o tempo de execução do programa.