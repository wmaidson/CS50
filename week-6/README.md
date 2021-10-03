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

## Entrada, condições

- Podemos obter a entrada do usuário com a inputfunção:


```py
answer = input("What's your name? ")
print(f"hello, {answer}")
```

- Podemos pedir ao usuário dois inteiros e adicioná-los:

```py
from cs50 import get_int

# Prompt user for x
x = get_int("x: ")

# Prompt user for y
y = get_int("y: ")

# Perform addition
print(x + y)
```

- Os comentários começam com em `#` vez de `//`.
- Se chamarmos input nós mesmos, obtemos strings para nossos valores:

```py
# Prompt user for x
x = input("x: ")

# Prompt user for y
y = input("y: ")

# Perform addition
print(x + y)
```

- Portanto, precisamos **lançar** , ou converter, cada valor inputem um intantes de armazená-lo:

```py
# Prompt user for x
x = int(input("x: "))

# Prompt user for y
y = int(input("y: "))

# Perform addition
print(x + y)
```

- Mas se o usuário não digitou um número, precisaremos fazer ainda mais verificações de erro ou nosso programa travará. Portanto, geralmente queremos usar uma biblioteca comumente usada para resolver problemas como este.
- Vamos dividir os valores:

```py
# Prompt user for x
x = int(input("x: "))

# Prompt user for y
y = int(input("y: "))

# Perform division
print(x / y)
```

- Observe que obtemos valores decimais de ponto flutuante de volta, mesmo se dividirmos dois inteiros.
- E podemos demonstrar as condições:

```py
from cs50 import get_int

x = get_int("x: ")
y = get_int("y: ")

if x < y:
    print("x is less than y")
elif x > y:
    print("x is greater than y")
else:
    print("x is equal to y")
```

- Podemos importar bibliotecas inteiras e usar funções dentro delas como se fossem uma estrutura:

```py
import cs50

x = cs50.get_int("x: ")
y = cs50.get_int("y: ")
```

- Se nosso programa precisasse importar duas bibliotecas diferentes, cada uma com uma `get_int` função, por exemplo, precisaríamos usar este método para funções de **namespace** , mantendo seus nomes em espaços diferentes para evitar que colidam.
- Para comparar strings, podemos dizer:

```py
from cs50 import get_string

s = get_string("Do you agree? ")

if s == "Y" or s == "y":
    print("Agreed.")
elif s == "N" or s == "n":
    print("Not agreed.")
```


- Python não tem chars, então verificamos Ye outras letras como strings. Também podemos comparar strings diretamente com `==`. Finalmente, em nossas expressões booleanas usamos ore em andvez de símbolos.
- Também podemos dizer `if s.lower() in ["y", "yes"]:` para verificar se nossa string está em uma lista, depois de convertê-la em minúsculas primeiro.
 
## Miau

- Também podemos melhorar as versões de `meow`:

```py
print("meow")
print("meow")
print("meow")
```

- Não precisamos declarar uma `main` função, então apenas escrevemos a mesma linha de código três vezes.
Podemos definir uma função que podemos reutilizar:

```py
for i in range(3):
    meow()

def meow():
    print("meow")
```

- Mas isso faz com que um erro quando tentamos executá-lo: `NameError: name 'meow' is not defined`. Acontece que precisamos definir nossa função antes de usá-la, então podemos mover nossa definição de meowpara o topo ou definir uma função principal primeiro:

```py
def main():
    for i in range(3):
        meow()

def meow():
    print("meow")

main()
```

- Agora, quando realmente chamarmos nossa `main`função, `meow` ela já terá sido definida.
- Nossas funções também podem receber entradas:


```py
def main():
    meow(3)

def meow(n):
    for i in range(n):
        print("meow")

main()
```

- Nossa `meow` função recebe um parâmetro `n`, e o passa para `range`.

## get_positive_int

- Podemos definir uma função para obter um número inteiro positivo:

```py
from cs50 import get_int

def main():
    i = get_positive_int()
    print(i)

def get_positive_int():
    while True:
        n = get_int("Positive Integer: ")
        if n > 0:
            break
    return n

main()
```

- Como não há loop do-while em Python como há em C, temos um `while`loop que continuará infinitamente e usará `break` para encerrar o loop assim que possível `n > 0`. Finalmente, nossa função irá `return n`, em nosso nível de indentação original, fora do whileloop.
- Observe que as variáveis em Python têm como **escopo funções** por padrão, o que significa que npodem ser inicializadas em um loop, mas ainda podem ser acessadas posteriormente na função.

## Mario

- Podemos imprimir uma linha de pontos de interrogação na tela:

```py
for i in range(4):
    print("?", end="")
print()
```

- Quando imprimimos cada bloco, não queremos a nova linha automática, então podemos passar um **argumento nomeado**, também conhecido como argumento de palavra-chave, para a `print` função, que especifica o valor para um parâmetro específico. Até agora, vimos apenas **argumentos posicionais**, onde os parâmetros são definidos com base em sua posição na chamada de função.
- Aqui, dizemos `end=""` para especificar que nada deve ser impresso no final de nossa string. `end` também é um **argumento opcional** , que não precisamos passar, com um valor padrão de `\n`, que é o motivo pelo qual `print` geralmente adiciona uma nova linha para nós.
- Finalmente, depois de imprimir nossa linha com o loop, podemos chamar `print` sem outros argumentos para obter uma nova linha.
- Nós também pode “multiplicar” uma string e imprimir essa diretamente com: `print("?" * 4)`.
- Podemos implementar loops aninhados:

```py
for i in range(3):
    for j in range(3):
        print("#", end="")
    print()
```

## Transbordamento, imprecisão

- Em Python, tentar causar um estouro de número inteiro não funcionará:

```py
i = 1
while True:
    print(i)
    i *= 2
```
- Vemos números cada vez maiores sendo impressos, já que o Python usa automaticamente cada vez mais memória para armazenar números para nós, ao contrário de C, em que os inteiros são fixados em um determinado número de bytes.
- A imprecisão de ponto flutuante também ainda existe, mas pode ser evitada por bibliotecas que podem representar números decimais com quantos bits forem necessários.

# Listas, strings

- Podemos fazer uma lista:
 
```py
scores = [72, 73, 33]

print("Average: " + str(sum(scores) / len(scores)))
```

- Podemos usar `sum`, uma função incorporada em Python, para somar os valores em nossa lista e dividi-lo pelo número de pontuações, usando a `len` função para obter o comprimento da lista. Em seguida, convertemos o float em uma string antes de podermos concatená-lo e imprimi-lo.
Podemos até adicionar a expressão inteira em uma string formatada para o mesmo efeito:

```py
print(f"Average: {sum(scores) / len(scores)}")
```

- Podemos adicionar itens a uma lista com:

```py
from cs50 import get_int

scores = []
for i in range(3):
    scores.append(get_int("Score: "))
...
```

- Podemos iterar sobre cada caractere em uma string:

```py
from cs50 import get_string

s = get_string("Before:  ")
print("After: ", end="")
for c in s:
    print(c.upper(), end="")
print()
```

- Python irá iterar cada caractere na string para nós com apenas `for c in s`.
- Para tornar uma string maiúscula, também podemos simplesmente chamar `s.upper()`, sem ter que iterar sobre cada caractere nós mesmos.
 
## Argumentos de linha de comando, códigos de saída

- Podemos aceitar argumentos de linha de comando com:

```py
from sys import argv

if len(argv) == 2:
    print(f"hello, {argv[1]}")
else:
    print("hello, world")
```

- Importamos `argv` de `sys`, ou módulo de sistema, integrado em Python.
- Como `argv` é uma lista, podemos obter o segundo item com `argv[1]`, portanto, adicionar um argumento com o comando `python argv.py` David resultará em `hello`, Davidimpresso.
- Como em C, `argv[0]` seria o nome do nosso programa, como `argv.py`.
- Também podemos permitir que o Python itere sobre a lista para nós:

```py
from sys import argv

for arg in argv:
    print(arg)
```

- Também podemos retornar códigos de saída quando nosso programa for encerrado:

```py
import sys

if len(sys.argv) != 2:
    print("missing command-line argument")
    sys.exit(1)
print(f"hello, {sys.argv[1]}")
sys.exit(0)
````

- Importamos todo o `sys` módulo agora, já que estamos usando vários componentes dele. Agora podemos usar `sys.argv` e `sys.exit()` sair do nosso programa com um código específico.

## Algoritmos

- Podemos implementar a pesquisa linear apenas verificando cada elemento em uma lista:

```py
import sys

numbers = [4, 6, 8, 2, 7, 5, 0]

if 0 in numbers:
    print("Found")
    sys.exit(0)

print("Not found")
sys.exit(1)
```

- Com `if 0 in numbers:` , estamos pedindo ao Python para verificar a lista para nós.
Uma lista de strings também pode ser pesquisada com:

```py
names = ["Bill", "Charlie", "Fred", "George", "Ginny", "Percy", "Ron"]

if "Ron" in names:
    print("Found")
else:
    print("Not found")
```

- Se tivermos um dicionário, um conjunto de pares de valores-chave, também podemos verificar se há uma chave específica e examinar o valor armazenado para ela:

```py
from cs50 import get_string

people = {
    "Brian": "+1-617-495-1000",
    "David": "+1-949-468-2750"
}

name = get_string("Name: ")
if name in people:
    print(f"Number: {people[name]}")
```

- Primeiro declaramos um dicionário,, `people` onde as chaves são strings de cada nome que queremos armazenar, e o valor que queremos associar a cada chave é uma string de um número de telefone correspondente.
- Em seguida, usamos `if name in people` :para pesquisar as chaves do nosso dicionário para a `name`. Se a chave existe, então podemos obter o valor com a notação de colchetes,, `people[name]` muito parecido com a indexação em uma matriz com C, exceto que aqui usamos uma string em vez de um inteiro.
- Os dicionários, assim como os conjuntos, são normalmente implementados em Python com uma estrutura de dados como uma tabela hash, para que possamos ter uma pesquisa de tempo quase constante. Novamente, temos a desvantagem de ter menos controle sobre exatamente o que acontece nos bastidores, como poder escolher uma função hash, com a vantagem de ter que fazer menos trabalho nós mesmos.
- A troca de duas variáveis também pode ser feita simplesmente atribuindo os dois valores ao mesmo tempo:

```py
x = 1
y = 2

print(f"x is {x}, y is {y}")
x, y = y, x
print(f"x is {x}, y is {y}")
```

- Em Python, não temos acesso a ponteiros, o que nos protege de cometer erros com a memória.

## arquivos

- Vamos abrir um arquivo CSV:

```py
import csv

from cs50 import get_string

file = open("phonebook.csv", "a")

name = get_string("Name: ")
number = get_string("Number: ")

writer = csv.writer(file)
writer.writerow([name, number])

file.close()
```

- Acontece que Python também tem uma `csv` biblioteca que nos ajuda a trabalhar com arquivos CSV, portanto, depois de abrir o arquivo para anexar, podemos chamar `csv.writer` para criar um a `writer` partir do arquivo, o que fornece funcionalidade adicional, como `writer.writerow` escrever uma lista como uma linha.
- Podemos usar a `with` palavra - chave, que fechará o arquivo para nós quando terminarmos:

```py
...
with open("phonebook.csv", "a") as file:
    writer = csv.writer(file)
    writer.writerow((name, number))
```

- odemos abrir outro arquivo CSV, calculando o número de vezes que um valor aparece:

```py
import csv

houses = {
    "Gryffindor": 0,
    "Hufflepuff": 0,
    "Ravenclaw": 0,
    "Slytherin": 0
}

with open("Sorting Hat (Responses) - Form Responses 1.csv", "r") as file:
    reader = csv.reader(file)
    next(reader)
    for row in reader:
        house = row[1]
        houses[house] += 1

for house in houses:
    print(f"{house}: {houses[house]}")
```

- Usamos a `reader` função da `csv` biblioteca, pulamos a linha de cabeçalho com `next(reader)` e, em seguida, iteramos sobre cada uma das demais linhas.
- O segundo item em cada linha,, `row[1]` é a string de uma casa, portanto, podemos usá-la para acessar o valor armazenado `houses` para aquela chave e adicionar um a ela.
- Por fim, imprimiremos a contagem de cada casa.

## Mais bibliotecas

- Em nosso próprio Mac ou PC, podemos abrir um terminal após instalar o Python e usar outra biblioteca para converter texto em fala:

```py
import pyttsx3

engine = pyttsx3.init()
engine.say("hello, world")
engine.runAndWait()
````

- Lendo a documentação, podemos descobrir como inicializar a biblioteca e dizer uma string.
- Podemos até mesmo passar uma string de formato `engine.say(f"hello, {name}")` para dizer alguma entrada.
- Podemos usar outra biblioteca,, `face_recognition` para encontrar rostos nas imagens:

```py
# Find faces in picture
# https://github.com/ageitgey/face_recognition/blob/master/examples/find_faces_in_picture.py

from PIL import Image
import face_recognition

# Load the jpg file into a numpy array
image = face_recognition.load_image_file("office.jpg")

# Find all the faces in the image using the default HOG-based model.
# This method is fairly accurate, but not as accurate as the CNN model and not GPU accelerated.
# See also: find_faces_in_picture_cnn.py
face_locations = face_recognition.face_locations(image)

for face_location in face_locations:

    # Print the location of each face in this image
    top, right, bottom, left = face_location

    # You can access the actual face itself like this:
    face_image = image[top:bottom, left:right]
    pil_image = Image.fromarray(face_image)
    pil_image.show()
```

- Com [`reconheça.py`](https://cdn.cs50.net/2020/fall/lectures/6/src6/6/faces/recognize.py) , podemos escrever um programa que encontra uma correspondência para um rosto específico.
- Podemos criar um código QR, ou código de barras bidimensional, com outra biblioteca:

```py
import os
import qrcode

img = qrcode.make("https://youtu.be/oHg5SJYRHA0")
img.save("qr.png", "PNG")
os.system("open qr.png")
```
- Podemos reconhecer a entrada de áudio de um microfone:

```py
import speech_recognition

# Obtain audio from the microphone
recognizer = speech_recognition.Recognizer()
with speech_recognition.Microphone() as source:
    print("Say something:")
    audio = recognizer.listen(source)

# Recognize speech using Google Speech Recognition
print("You said:")
print(recognizer.recognize_google(audio))
```

- Estamos seguindo a documentação da biblioteca para ouvir nosso microfone e convertê-lo em texto.
- Podemos até adicionar lógica adicional para respostas básicas:

```py
...
words = recognizer.recognize_google(audio)

# Respond to speech
if "hello" in words:
    print("Hello to you too!")
elif "how are you" in words:
    print("I am well, thanks!")
elif "goodbye" in words:
    print("Goodbye to you too!")
else:
    print("Huh?")
```    

- Finalmente, usamos outro programa mais sofisticado para gerar deepfakes, ou vídeos que parecem realistas, mas gerados por computador, de várias personalidades.
- Tirando proveito de todas essas bibliotecas disponíveis gratuitamente online, podemos facilmente adicionar funcionalidades avançadas aos nossos próprios aplicativos.