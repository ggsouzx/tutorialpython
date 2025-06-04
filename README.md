# Tutorial do Python, Release 3.13.3

**Autor:** Guilherme de Souza  
**Data:** 27 de abril de 2025  
**Fundação de Software Python**  
**E-mail:** [guilhermedesouza.dev@gmail.com](mailto:guilhermedesouza.dev@gmail.com)

## ÍNDICE

1.  **Despertando Seu Interesse**
2.  **Usando o Interpretador Python**  
    2.1 Invocando o Interpretador  
    2.1.1 Passagem de Argumentos  
    2.2.1 Codificação do Código-Fonte
3.  **Uma Introdução Informal ao Python**  
    3.1.1 Números  
    3.1.2 Texto  
    3.1.3 Listas  
    3.2 Primeiros Passos em Programação

## CAPÍTULO UM: DESPERTANDO SEU INTERESSE

Se você trabalha muito com computadores, eventualmente desejará automatizar algumas tarefas. Por exemplo, pode querer realizar uma busca e substituição em vários arquivos de texto, renomear e organizar arquivos de fotos de maneira complexa, ou criar um banco de dados personalizado, uma aplicação de interface gráfica (GUI) ou um jogo simples.

Se você é um desenvolvedor de software profissional, pode precisar trabalhar com bibliotecas em C, C++ ou Java, mas o ciclo de escrita/compilação/teste/recompilação pode ser muito lento. Talvez você esteja desenvolvendo uma suíte de testes para uma biblioteca e ache a tarefa de escrever o código de teste tediosa, ou talvez tenha escrito um programa que poderia se beneficiar de uma linguagem de extensão, mas não deseja criar uma nova linguagem do zero. Python é a linguagem ideal para você.

Você poderia escrever um script de shell Unix ou um arquivo em lote do Windows para algumas dessas tarefas, mas scripts de shell são mais adequados para mover arquivos e manipular dados de texto, não sendo ideais para aplicações GUI ou jogos. Você poderia escrever um programa em C, C++ ou Java, mas isso pode exigir muito tempo de desenvolvimento, mesmo para um rascunho inicial. Python é mais simples de usar, está disponível para Windows, macOS e sistemas operacionais Unix, e ajuda a realizar o trabalho mais rapidamente.

Python é fácil de usar, mas é uma linguagem de programação robusta, oferecendo mais estrutura e suporte para programas grandes do que scripts de shell ou arquivos em lote. Comparado ao C, Python fornece mais verificação de erros e, sendo uma linguagem de alto nível, possui tipos de dados avançados, como arrays flexíveis e dicionários. Devido a seus tipos de dados mais gerais, Python é aplicável a um domínio de problemas muito maior do que Awk ou até mesmo Perl, mas muitas tarefas são tão fáceis em Python quanto nessas linguagens.

Python permite dividir seu programa em módulos que podem ser reutilizados em outros programas Python. Ele vem com uma grande coleção de módulos padrão que você pode usar como base para seus programas ou como exemplos para começar a aprender a programar em Python. Alguns desses módulos oferecem funcionalidades como entrada/saída de arquivos, chamadas de sistema, sockets e até interfaces para ferramentas de interface gráfica, como Tk.

Python é uma linguagem interpretada, o que economiza tempo considerável durante o desenvolvimento, pois não é necessário compilar e linkar. O interpretador pode ser usado interativamente, permitindo experimentar recursos da linguagem, escrever programas descartáveis ou testar funções durante o desenvolvimento _bottom-up_ (de baixo para cima). Ele também é uma calculadora de mesa prática.

Python permite escrever programas de forma compacta e legível. Programas escritos em Python são geralmente muito mais curtos do que seus equivalentes em C, C++ ou Java, por várias razões:

-   Tipos de dados de alto nível permitem expressar operações complexas em uma única instrução;
-   O agrupamento de instruções é feito por indentação, em vez de chaves de início e fim;
-   Não é necessário declarar variáveis ou argumentos.

Python é extensível: se você sabe programar em C, é fácil adicionar uma nova função ou módulo ao interpretador, seja para realizar operações críticas na máxima velocidade, seja para conectar programas Python a bibliotecas que podem estar disponíveis apenas em forma binária (como uma biblioteca gráfica específica de um fornecedor). Quando você estiver realmente envolvido, pode integrar o interpretador Python em uma aplicação escrita em C e usá-lo como uma linguagem de extensão ou comando para essa aplicação.

A propósito, a linguagem leva o nome do programa da BBC _Monty Python's Flying Circus_ e não tem relação com répteis. Fazer referências a esquetes de Monty Python na documentação não é apenas permitido, mas incentivado!

Agora que você está entusiasmado com o Python, vai querer examiná-lo em mais detalhes. Como a melhor maneira de aprender uma linguagem é usá-la, este tutorial convida você a experimentar o interpretador Python enquanto lê.

No próximo capítulo, explicamos a mecânica de uso do interpretador. Essa informação é um tanto básica, mas essencial para testar os exemplos apresentados mais adiante.

O restante do tutorial apresenta várias funcionalidades da linguagem e do sistema Python por meio de exemplos, começando com expressões simples, declarações e tipos de dados, passando por funções e módulos, e finalmente abordando conceitos avançados, como exceções e classes definidas pelo usuário.

## CAPÍTULO DOIS: USANDO O INTERPRETADOR PYTHON

### 2.1 Invocando o Interpretador

O interpretador Python geralmente é instalado em `/usr/local/bin/python3.13` nas máquinas onde está disponível; adicionar `/usr/local/bin` ao caminho de busca do shell Unix permite iniciá-lo digitando o comando:

```bash
python3.13

```

no shell. Como a escolha do diretório onde o interpretador está instalado é uma opção de instalação, outros locais são possíveis; verifique com seu guru local de Python ou administrador do sistema. (Por exemplo, `/usr/local/python` é uma alternativa popular.)

Em máquinas Windows onde o Python foi instalado a partir da Microsoft Store, o comando `python3.13` estará disponível. Se você tiver o lançador `py.exe` instalado, pode usar o comando `py`. Consulte a documentação sobre variáveis de ambiente para outras formas de iniciar o Python.

Digitar um caractere de fim de arquivo (Control-D no Unix, Control-Z no Windows) no prompt primário faz o interpretador sair com um status de saída zero. Se isso não funcionar, você pode sair do interpretador digitando o comando: `quit()`.

Os recursos de edição de linha do interpretador incluem edição interativa, substituição de histórico e preenchimento de código em sistemas que suportam a biblioteca GNU Readline. Uma maneira rápida de verificar se a edição de linha está disponível é digitar Control-P no primeiro prompt do Python. Se ele emitir um bipe, a edição de linha está ativa; consulte o Apêndice sobre Edição de Entrada Interativa e Substituição de Histórico para uma introdução às teclas. Se nada acontecer, ou se `^P` for exibido, a edição de linha não está disponível; você só poderá usar a tecla de retrocesso para remover caracteres da linha atual.

O interpretador opera de forma semelhante ao shell Unix: quando chamado com a entrada padrão conectada a um dispositivo tty, ele lê e executa comandos interativamente; quando chamado com um nome de arquivo como argumento ou com um arquivo como entrada padrão, ele lê e executa um script desse arquivo.

Uma segunda forma de iniciar o interpretador é com `python -c comando [arg]...`, que executa as instruções no _comando_, análogo à opção `-c` do shell. Como as instruções Python frequentemente contêm espaços ou outros caracteres especiais para o shell, é recomendável colocar o _comando_ entre aspas.

Alguns módulos Python também são úteis como scripts. Eles podem ser invocados usando `python -m módulo [arg]...`, que executa o arquivo-fonte do módulo como se seu nome completo tivesse sido especificado na linha de comando.

Quando um arquivo de script é usado, às vezes é útil executar o script e entrar no modo interativo depois. Isso pode ser feito passando `-i` antes do script.

Todas as opções de linha de comando estão descritas na documentação sobre uso geral.

**Nota:** No Unix, o interpretador Python 3.x não é instalado por padrão com o executável chamado `python`, para evitar conflitos com um executável Python 2.x instalado simultaneamente.

### 2.1.1 Passagem de Argumentos

Quando conhecidos pelo interpretador, o nome do script e os argumentos adicionais são transformados em uma lista de strings e atribuídos à variável `argv` no módulo `sys`. Você pode acessar essa lista executando `import sys`. O comprimento da lista é pelo menos um; quando nenhum script ou argumento é fornecido, `sys.argv[0]` é uma string vazia. Quando o nome do script é fornecido como `-` (significando entrada padrão), `sys.argv[0]` é definido como `-`. Quando `-c comando` é usado, `sys.argv[0]` é definido como `-c`. Quando `-m módulo` é usado, `sys.argv[0]` é definido como o nome completo do módulo localizado. As opções após `-c comando` ou `-m módulo` não são consumidas pelo processamento de opções do interpretador Python, mas deixadas em `sys.argv` para o comando ou módulo manipular.

### 2.1.2 Modo Interativo

Quando os comandos são lidos de um dispositivo tty, o interpretador está no modo interativo. Nesse modo, ele solicita o próximo comando com o prompt primário, geralmente três sinais de maior (`>>>`); para linhas de continuação, ele usa o prompt secundário, por padrão três pontos (`...`). O interpretador imprime uma mensagem de boas-vindas com seu número de versão e um aviso de copyright antes de exibir o primeiro prompt:

```bash
$ python3.13
Python 3.13 (default, 4 de abril de 2023, 09:25:04)
[GCC 10.2.0] no Linux
Digite "help", "copyright", "credits" ou "license" para mais informações.
>>>

```

Linhas de continuação são necessárias ao inserir uma construção de várias linhas. Como exemplo, veja esta instrução `if`:

```python
>>> the_world_is_flat = True
>>> if the_world_is_flat:
...     print("Cuidado para não cair!")
Cuidado para não cair!

```

Para mais informações sobre o modo interativo, consulte a documentação sobre Modo Interativo.

### 2.2.1 Codificação do Código-Fonte

Por padrão, os arquivos-fonte Python são tratados como codificados em UTF-8. Nessa codificação, caracteres da maioria dos idiomas do mundo podem ser usados simultaneamente em literais de string, identificadores e comentários — embora a biblioteca padrão use apenas caracteres ASCII para identificadores, uma convenção que qualquer código portável deve seguir. Para exibir todos esses caracteres corretamente, seu editor deve reconhecer que o arquivo é UTF-8 e usar uma fonte que suporte todos os caracteres no arquivo.

Para declarar uma codificação diferente do padrão, uma linha de comentário especial deve ser adicionada como a primeira linha do arquivo. A sintaxe é a seguinte:

```python
# -*- coding: encoding -*-

```

onde _encoding_ é um dos codecs válidos suportados pelo Python.

Por exemplo, para declarar que a codificação Windows-1252 deve ser usada, a primeira linha do arquivo-fonte deve ser:

```python
# -*- coding: cp1252 -*-

```

Uma exceção à regra da primeira linha é quando o código-fonte começa com uma linha _shebang_ Unix. Nesse caso, a declaração de codificação deve ser adicionada como a segunda linha do arquivo. Por exemplo:

```python
#!/usr/bin/env python3
# -*- coding: cp1252 -*-

```

## CAPÍTULO TRÊS: UMA INTRODUÇÃO INFORMAL AO PYTHON

Nos exemplos a seguir, entrada e saída são distinguidas pela presença ou ausência de prompts (`>>>` e `...`): para repetir o exemplo, você deve digitar tudo após o prompt quando ele aparecer; linhas que não começam com um prompt são saídas do interpretador. Note que um prompt secundário em uma linha por si só em um exemplo significa que você deve digitar uma linha em branco; isso é usado para encerrar um comando de várias linhas.

Muitos dos exemplos neste manual, mesmo aqueles inseridos no prompt interativo, incluem comentários. Comentários em Python começam com o caractere de cerquilha (`#`) e se estendem até o final da linha física. Um comentário pode aparecer no início de uma linha ou após um espaço em branco ou código, mas não dentro de um literal de string. Um caractere de cerquilha dentro de um literal de string é apenas um caractere de cerquilha. Como os comentários servem para esclarecer o código e não são interpretados pelo Python, eles podem ser omitidos ao digitar os exemplos.

Alguns exemplos:

```python
# este é o primeiro comentário
spam = 1  # e este é o segundo comentário
          # ... e agora um terceiro!
text = "# Isto não é um comentário porque está entre aspas."

```

### 3.1 Usando Python como Calculadora

Vamos experimentar alguns comandos simples do Python. Inicie o interpretador e aguarde o prompt primário, `>>>`. (Não deve demorar muito.)

#### 3.1.1 Números

O interpretador funciona como uma calculadora simples: você pode digitar uma expressão e ele exibirá o valor. A sintaxe das expressões é direta: os operadores `+`, `-`, `*` e `/` podem ser usados para realizar aritmética; parênteses (`()`) podem ser usados para agrupamento. Por exemplo:

```python
>>> 2 + 2
4
>>> 50 - 5 * 6
20
>>> (50 - 5 * 6) / 4
5.0
>>> 8 / 5  # divisão sempre retorna um número de ponto flutuante
1.6

```

Os números inteiros (por exemplo, 2, 4, 20) são do tipo `int`, enquanto aqueles com uma parte fracionária (por exemplo, 5.0, 1.6) são do tipo `float`. Veremos mais sobre tipos numéricos mais adiante no tutorial.

A divisão (`/`) sempre retorna um `float`. Para realizar uma divisão inteira e obter um resultado inteiro, você pode usar o operador `//`; para calcular o resto, pode usar `%`:

```python
>>> 17 / 3  # divisão clássica retorna um float
5.666666666666667
>>> 17 // 3  # divisão inteira descarta a parte fracionária
5
>>> 17 % 3  # o operador % retorna o resto da divisão
2
>>> 5 * 3 + 2  # quociente inteiro * divisor + resto
17

```

Com Python, é possível usar o operador `**` para calcular potências:

```python
>>> 5 ** 2  # 5 ao quadrado
25
>>> 2 ** 7  # 2 elevado à sétima potência
128

```

O sinal de igual (`=`) é usado para atribuir um valor a uma variável. Após a atribuição, nenhum resultado é exibido antes do próximo prompt interativo:

```python
>>> width = 20
>>> height = 5 * 9
>>> width * height
900

```

Se uma variável não estiver "definida" (atribuída um valor), tentar usá-la resultará em um erro:

```python
>>> n  # tentar acessar uma variável não definida
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'n' is not defined

```

Há suporte completo para ponto flutuante; operadores com operandos de tipos mistos convertem o operando inteiro para ponto flutuante:

```python
>>> 4 * 3.75 - 1
14.0

```

No modo interativo, a última expressão impressa é atribuída à variável `_`. Isso facilita a continuação de cálculos quando se usa o Python como uma calculadora de mesa, por exemplo:

```python
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _
113.0625
>>> round(_, 2)
113.06

```

Essa variável deve ser tratada como somente leitura pelo usuário. Não atribua explicitamente um valor a ela — isso criaria uma variável local independente com o mesmo nome, mascarando o comportamento mágico da variável embutida.

Além de `int` e `float`, o Python suporta outros tipos de números, como `Decimal` e `Fraction`. O Python também tem suporte embutido para números complexos, usando o sufixo `j` ou `J` para indicar a parte imaginária (por exemplo, `3+5j`).

**Nota:** Como `**` tem precedência maior que `-`, `-3**2` será interpretado como `-(3**2)` e resultará em `-9`. Para evitar isso e obter `9`, use `(-3)**2`.

#### 3.1.2 Texto

O Python pode manipular texto (representado pelo tipo `str`, as chamadas "strings") assim como números. Isso inclui caracteres como `"!"`, palavras como `"rabbit"`, nomes como `"Paris"`, frases como `"Got your back."`, etc. `"Yay! :)"`. Elas podem ser delimitadas por aspas simples (`'...'`) ou aspas duplas (`"..."`), com o mesmo resultado:

```python
>>> 'spam eggs'  # aspas simples
'spam eggs'
>>> "Paris rabbit got your back :)! Yay!"  # aspas duplas
'Paris rabbit got your back :)! Yay!'
>>> '1975'  # dígitos e numerais entre aspas também são strings
'1975'

```

Para incluir uma aspa em uma string, é necessário "escapar" ela, precedendo-a com `\`. Alternativamente, pode-se usar o outro tipo de aspas:

```python
>>> 'doesn\'t'  # use \' para escapar a aspa simples...
"doesn't"
>>> "doesn't"  # ...ou use aspas duplas
"doesn't"
>>> '"Yes," they said.'
'"Yes," they said.'
>>> "\"Yes,\" they said."
'"Yes," they said.'
>>> '"Isn\'t," they said.'
'"Isn\'t," they said.'

```

No shell do Python, a definição de uma string e sua saída podem parecer diferentes. A função `print()` produz uma saída mais legível, omitindo as aspas que delimitam a string e imprimindo caracteres especiais e escapados:

```python
>>> s = 'Primeira linha.\nSegunda linha.'  # \n significa nova linha
>>> s  # sem print(), caracteres especiais são incluídos na string
'Primeira linha.\nSegunda linha.'
>>> print(s)  # com print(), caracteres especiais são interpretados, então \n produz uma nova linha
Primeira linha.
Segunda linha.

```

Se você não quiser que caracteres precedidos por `\` sejam interpretados como caracteres especiais, pode usar strings brutas adicionando um `r` antes da primeira aspa:

```python
>>> print('C:\some\name')  # aqui \n significa nova linha!
C:\some
ame
>>> print(r'C:\some\name')  # note o r antes da aspa
C:\some\name

```

Strings literais podem se estender por várias linhas. Uma maneira é usar aspas triplas: `"""..."""` ou `'''...'''`. O fim de linha é incluído automaticamente na string, mas é possível evitar isso adicionando uma `\` no final da linha. Por exemplo:

```python
>>> print("""\
... Uso: algo
...         -h                        Exibe esta mensagem de ajuda
...         -f <arquivo>              Especifica um arquivo
... """)
Uso: algo
        -h                        Exibe esta mensagem de ajuda
        -f <arquivo>              Especifica um arquivo

```

Strings podem ser concatenadas (juntadas) com o operador `+` e repetidas com `*`:

```python
>>> # 3 vezes 'un', seguido de 'ium'
>>> 3 * 'un' + 'ium'
'unununium'

```

Duas ou mais strings literais (ou seja, aquelas entre aspas) colocadas lado a lado são automaticamente concatenadas:

```python
>>> 'Py' 'thon'
'Python'

```

Esse recurso é particularmente útil quando você deseja quebrar strings longas:

```python
>>> text = ('Coloque várias strings dentro de parênteses '
...         'para que sejam concatenadas.')
>>> text
'Coloque várias strings dentro de parênteses para que sejam concatenadas.'

```

Isso só funciona com duas strings literais, não com variáveis ou expressões:

```python
>>> prefix = 'Py'
>>> prefix 'thon'  # não pode concatenar uma variável e uma string literal
  File "<stdin>", line 1
    prefix 'thon'
                ^
SyntaxError: invalid syntax
>>> ('un' * 3) 'ium'
  File "<stdin>", line 1
    ('un' * 3) 'ium'
                    ^
SyntaxError: invalid syntax

```

Se você deseja concatenar variáveis ou uma variável com uma literal, use `+`:

```python
>>> prefix = 'Py'
>>> prefix + 'thon'
'Python'

```

Strings podem ser indexadas (acessadas por subscrito), com o primeiro caractere tendo índice 0. Não há tipo separado para caracteres; um caractere é simplesmente uma string de tamanho 1:

```python
>>> word = 'Python'
>>> word[0]  # caractere na posição 0
'P'
>>> word[5]  # caractere na posição 5
'n'

```

Índices também podem ser negativos, começando a contagem a partir do final da string:

```python
>>> word[-1]  # último caractere
'n'
>>> word[-2]  # penúltimo caractere
'o'
>>> word[-6]  # primeiro caractere
'P'

```

Além da indexação, também é suportado o fatiamento (_slicing_). Enquanto a indexação é usada para obter caracteres individuais, o fatiamento permite obter substrings:

```python
>>> word[0:2]  # caracteres da posição 0 (incluída) até 2 (excluída)
'Py'
>>> word[2:5]  # caracteres da posição 2 (incluída) até 5 (excluída)
'tho'

```

Os índices de fatiamento têm valores padrão úteis; um primeiro índice omitido assume o valor zero, um segundo índice omitido assume o tamanho da string sendo fatiada:

```python
>>> word[:2]   # caracteres do início até a posição 2 (excluída)
'Py'
>>> word[4:]   # caracteres da posição 4 (incluída) até o final
'on'
>>> word[-2:]  # caracteres do penúltimo (incluído) até o final
'on'

```

Note que o início está sempre incluído, e o fim está sempre excluído. Isso garante que `s[:i] + s[i:]` seja sempre igual a `s`:

```python
>>> word[:2] + word[2:]
'Python'
>>> word[:4] + word[4:]
'Python'

```

Uma maneira de lembrar como os fatiamentos funcionam é pensar nos índices como apontando _entre_ os caracteres, com a borda esquerda do primeiro caractere numerada como 0. Para uma string de comprimento _n_, há _n+1_ pontos, numerados de 0 a _n_. Por exemplo:

```
 +---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1

```

A primeira linha de números dá as posições dos índices 0...6 na string; a segunda linha dá os índices negativos correspondentes. O fatiamento de _i_ a _j_ consiste em todos os caracteres entre as bordas rotuladas como _i_ e _j_, respectivamente.

Para índices não negativos, o comprimento de um fatiamento é a diferença entre os índices, se ambos estiverem dentro dos limites. Por exemplo, `word[1:3]` tem comprimento 2.

Tentar usar um índice fora dos limites resultará em um erro:

```python
>>> word[42]  # a string tem apenas 6 caracteres
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range

```

No entanto, índices fora dos limites em fatiamentos são tratados de maneira elegante: um índice maior que o comprimento da string é substituído pelo comprimento da string; um índice inicial maior que o índice final retorna uma string vazia:

```python
>>> word[4:42]
'on'
>>> word[42:]
''

```

Strings do Python são imutáveis; elas não podem ser alteradas no lugar. Portanto, atribuir a uma posição indexada de uma string resulta em um erro:

```python
>>> word[0] = 'J'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
>>> word[2:] = 'py'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment

```

Se você precisa de uma string diferente, deve criar uma nova:

```python
>>> 'J' + word[1:]
'Jython'
>>> word[:2] + 'py'
'Pypy'

```

A função embutida `len()` retorna o comprimento de uma string:

```python
>>> s = 'supercalifragilisticexpialidocious'
>>> len(s)
34

```

Consulte também:

-   **Objetos semelhantes a sequências**: Strings são exemplos de tipos de sequência, e suportam os métodos comuns que esses tipos oferecem. Veremos mais sobre isso na seção sobre sequências.
-   **Métodos de string**: Strings suportam um grande número de métodos para transformações e buscas básicas.
-   **Strings formatadas**: Informações sobre formatação de strings com `str.format()` estão descritas na documentação correspondente.
-   **Literais de string formatada**: Strings formatadas permitem incluir o valor de expressões Python dentro de uma string prefixando-a com `f` ou `F` e escrevendo expressões como `{expressão}`.

Um exemplo que usa vários desses recursos de strings:

```python
>>> f'Nome: {word!r}, Comprimento: {len(word)}'
"Nome: 'Python', Comprimento: 6"

```

#### 3.1.3 Listas

O Python possui vários tipos compostos, usados para agrupar valores. O mais versátil é a _lista_, que pode ser escrita como uma sequência de valores (itens) separados por vírgulas, entre colchetes. Os itens de uma lista não precisam ser do mesmo tipo.

Criar uma lista é tão simples quanto colocar valores separados por vírgulas entre colchetes `[]`:

```python
>>> squares = [1, 4, 9, 16, 25]
>>> squares
[1, 4, 9, 16, 25]

```

Assim como strings (e todos os outros tipos de sequência embutidos), listas podem ser indexadas e fatiadas:

```python
>>> squares[0]  # indexação retorna o item
1
>>> squares[-1]
25
>>> squares[-3:]  # fatiamento retorna uma nova lista
[9, 16, 25]

```

Todos os fatiamentos retornam uma nova lista contendo os elementos solicitados. Isso significa que o seguinte fatiamento retorna uma cópia rasa (_shallow copy_) da lista:

```python
>>> squares[:]
[1, 4, 9, 16, 25]

```

Listas também suportam operações como concatenação:

```python
>>> squares + [36, 49, 64, 81, 100]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

```

Diferentemente das strings, que são imutáveis, listas são um tipo mutável, ou seja, é possível alterar seu conteúdo:

```python
>>> cubes = [1, 8, 27, 65, 125]  # algo está errado aqui
>>> 4 ** 3  # o cubo de 4 é 64, não 65!
64
>>> cubes[3] = 64  # substitui o valor errado
>>> cubes
[1, 8, 27, 64, 125]

```

Você também pode adicionar novos itens ao final de uma lista usando o método `append()` (veremos mais sobre métodos de lista mais adiante):

```python
>>> cubes.append(216)  # adiciona o cubo de 6
>>> cubes.append(7 ** 3)  # e o cubo de 7
>>> cubes
[1, 8, 27, 64, 125, 216, 343]

```

A atribuição a fatiamentos também é possível, e isso pode até mudar o tamanho da lista ou limpá-la completamente:

```python
>>> letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> letters
['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> # substitui alguns valores
>>> letters[2:5] = ['C', 'D', 'E']
>>> letters
['a', 'b', 'C', 'D', 'E', 'f', 'g']
>>> # agora remove eles
>>> letters[2:5] = []
>>> letters
['a', 'b', 'f', 'g']
>>> # limpa a lista substituindo todos os elementos por uma lista vazia
>>> letters[:] = []
>>> letters
[]

```

A função embutida `len()` também se aplica a listas:

```python
>>> letters = ['a', 'b', 'c', 'd']
>>> len(letters)
4

```

É possível aninhar listas (criar listas contendo outras listas), por exemplo:

```python
>>> a = ['a', 'b', 'c']
>>> n = [1, 2, 3]
>>> x = [a, n]
>>> x
[['a', 'b', 'c'], [1, 2, 3]]
>>> x[0]
['a', 'b', 'c']
>>> x[0][1]
'b'

```

#### 3.2 Primeiros Passos em Programação

Claro, podemos usar o Python para tarefas mais complicadas do que somar dois e dois. Por exemplo, podemos escrever uma subseqüência inicial da série de Fibonacci assim:

```python
>>> # Série de Fibonacci:
>>> # a soma de dois elementos define o próximo
>>> a, b = 0, 1
>>> while a < 10:
...     print(a)
...     a, b = b, a + b
0
1
1
2
3
5
8

```

Este exemplo introduz várias características novas:

-   A primeira linha contém uma atribuição múltipla: as variáveis `a` e `b` recebem simultaneamente os valores 0 e 1. Na última linha, isso é usado novamente, demonstrando que as expressões do lado direito são todas avaliadas primeiro antes que qualquer atribuição ocorra. As expressões do lado direito são avaliadas da esquerda para a direita.
    
-   O laço `while` executa enquanto a condição (aqui: `a < 10`) permanecer verdadeira. Em Python, como em C, qualquer valor inteiro diferente de zero é verdadeiro; zero é falso. A condição também pode ser uma string ou um valor de lista, na verdade qualquer sequência; qualquer coisa com comprimento diferente de zero é verdadeira, sequências vazias são falsas. O teste usado no exemplo é uma comparação simples. Os operadores de comparação padrão são escritos como em C: `<` (menor que), `>` (maior que), `==` (igual a), `<=` (menor ou igual a), `>=` (maior ou igual a) e `!=` (diferente de).
    
-   O _corpo_ do laço é indentado: a indentação é a maneira do Python de agrupar instruções. No prompt interativo, você deve digitar uma tabulação ou espaço(s) para cada linha indentada. Na prática, você escreverá programas Python em um editor de texto; todos os editores decentes têm suporte para indentação automática. Quando uma instrução composta é inserida interativamente, ela deve ser seguida por uma linha em branco para indicar sua conclusão (já que o analisador não pode adivinhar quando você terminou de digitar a última linha). Note que cada linha dentro de um bloco básico deve ter o mesmo nível de indentação.
    
-   A função `print()` escreve o valor dos argumentos que recebe. Ela difere de simplesmente escrever a expressão que você deseja exibir (como fizemos anteriormente nos exemplos de calculadora) na maneira como lida com múltiplos argumentos, valores de ponto flutuante e strings. Strings são impressas sem aspas, e um espaço é inserido entre os itens, para que você possa formatar as coisas de maneira agradável:
    

```python
>>> i = 256 * 256
>>> print('O valor de i é', i)
O valor de i é 65536

```

O argumento nomeado `end` pode be usado para evitar a quebra de linha após a saída, ou para terminar a saída com uma string diferente:

```python
>>> a, b = 0, 1
>>> while a < 1000:
...     print(a, end=', ')
...     a, b = b, a + b
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987,

```

**Nota:** Como `**` tem precedência maior que `-`, `-3**2` será interpretado como `-(3**2)` e resultará em `-9`. Para evitar isso e obter `9`, você pode usar `(-3)**2`.
