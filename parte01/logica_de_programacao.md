# Lógica de Programação

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

>[!IMPORTANT]
> Esse tutorial é destinado para máquinas com o Sistema Operacional Windows 10 ou superior.

## Sumário

1. [Ambiente Virtual](#ambiente-virtual)
2. [Arquivos Python](#arquivos-python)
3. [Saída de dados](#saída-de-dados)
4. [Comentários](#comentários)
5. [Variáveis](#variáveis)<br>
    5.1 [Tipos de variáveis](#tipos-de-variáveis)<br>
    5.2 [Convertendo tipos](#convertendo-tipos)<br>
    5.3 [Concatenação de valores](#concatenação-de-valores)<br>
6. [Entrada de dados](#entrada-de-dados)
7. [Estruturas de decisão](#estruturas-de-decisão)

## Ambiente Virtual

> [!IMPORTANT]
> O ambiente virtual Python, também conhecido como **.venv**, é uma pasta criada dentro do projeto que guarda uma cópia isolada do interpretador Python, junto com as biliotecas que o projeto precisa.
>
> Ela é utilizada para:
> - isolar projetos diferentes;
> - evitar conflitos entre versões de bibliotecas;
> - manter o ambiente organizado;
> - facilitar a reprodução do projeto em outra máquina, caso seja necessário.
>
> A pasta **.venv** deve ser criada via **CLI**, ou seja, no terminal aberto na pasta do projeto.

Para criar um ambiente virtual Python, digite no terminal:
~~~
py -m venv .venv
~~~

> [!WARNING]
> Após criar o ambiente virtual **.venv**, é necessário ativá-lo, senão existe o risco das bibliotecas do projeto irem parar no Python global, deixando o Sistema Operacional mais pesado. **Nunca se esqueça disso!**

Para ativar o ambiente virtual, digite no terminal:
~~~
.venv\Scripts\activate
~~~

Esse procedimento irá criar e ativar a **venv**, e você poderá instalar as bibliotecas necessárias para seu projeto sem o riscco de conflitos entre eles.

Caso precise, você pode desativar a **venv** executando no terminal o comando:
~~~
deactivate
~~~

## Arquivos Python

> [!IMPORTANT]
> Os programas Python são executados em arquivos com a extensão `.py`. Exemplo: `main.py`; `app.py`.

## Saída de dados

> [!NOTE]
> A saída de dados de um programa Python é feita através do comando `print()`, e a informação a ser exibida deve estar entre aspas, que podem ser simples (`'`) ou duplas (`"`).

Veja abaixo um exemplo do clássico programa ***Hello World***:
~~~python
print("Olá, Mundo!")
~~~

> [!NOTE]
> Um texto escrito entre aspas (simples ou duplas) é chamado de ***string***.

> [!CAUTION]
> O comando `print()` realiza automaticamente uma quebra de linha. Ou seja, caso você coloque um `print()` após outro `print()`, eles serão exibidos em linhas diferentes.

## Comentários

> [!NOTE]
> Uma linha de comentário é uma linha de código que é desconsiderada pelo interpretador durante a execução do seu programa. Os comentários servem como uma anotação do que o desenvolvedor fez em determinado trecho de código, para que o mesmo possa se lembrar do que fez no futuro.

Para inserir um comentário de uma linha, use `# `:
~~~python
# esta é uma linha de comentário
~~~

Para inserir múltiplas linhas de comentário, você pode usar 3 aspas simples (`'''`) para começar e 3 para terminar:
~~~python
'''
Este é um comentário
de múltiplas linhas
'''
~~~

Ou você pode trocar as aspas simples por duplas (`"""`):
~~~python
"""
Este também
é um comentário
de múltiplas linhas
"""
~~~

> [!WARNING]
> Comentários são considerados uma boa prática de desenvolvimento, mas não abuse. Sempre comente seus códigos com parcimônia.

## Variáveis

> [!NOTE]
> Uma variável é um elemento do programa que reserva um espaço na memória do computador para guardar um valor que você ainda não sabe qual é, daí o nome.

Exemplo:
~~~python
nome = "Alex Machado"
idade = 41
altura = 1.72
programador = True
~~~

Para exibir o valor de uma variável, chame o nome da variável dentro de um `print()` sem usar as aspas. Exemplo:
~~~python
nome = "Alex Machado"
print(nome)
~~~

> [!NOTE]
> O padrão de nomenclatura de variáveis em Python é o ***snake_case***, em que se separa duas palavras ou mais por sinal de ***underscore*** (`_`). Exemplo: `nome_completo` é um nome de variável válido.

> [!IMPORTANT]
> Para nomear uma variável, você pode escolher o nome que desejar, desde que siga algumas regras:
> - Não pode ter espaço
> - Não pode ter acento
> - Não pode ter `ç`
> - Não pode ser uma palavra reservada pelo sistema. Exemplo: não posso chamar uma variável de `input`
> - Não pode ter duas variáveis com nomes iguais, a não ser que elas sejam variáveis locais ao invés de globais
> - Pode ter numerais no nome da variável, mas ela não pode começar com um numeral. Exemplo: `num1` pode, mas `1num` não pode

> [!WARNING]
> O Python é uma linguagem *sensitive case*, ou seja, ele diferencia letras minúsculas das maiúsculas. Exemplo: uma variável chamada `nome` é diferente de uma variável chamada `Nome`, que é diferente de uma variável chamada `NOME`.

### Tipos de variáveis

> [!NOTE]
> As variáveis Python podem ser de 4 tipos diferentes:
> - ***String***: valores do tipo texto
> - ***Integer*** ou ***Int***: valores numéricos do tipo inteiro
> - ***Float***: valores numéricos do tipo decimal
> - ***Boolean*** ou ***Bool***: valores *booleanos* ou lógicos, como verdadeiro ou falso

> [!IMPORTANT]
> O Python é uma linguagem de tipagem dinâmica, ou seja, a própria linguagem define o tipo de variável que você vai trabalhar.
> Saber o tipo de variável que está trabalhando pode definir a performance do seu programa, e também como ele vai trabalhar com os dados que está recebendo.

Para saber que tipo de dado uma variável está recebendo, você pode usar o comando `type()`. Veja no exemplo:
~~~python
valor = "Conteúdo da minha variável"
print(type(valor))
~~~

> [!WARNING]
> Nem sempre um número enviado para uma variável é um número de verdade. Às vezes, ele pode ser um texto disfarçado de um número, por exemplo. Sempre tenha certeza sobre o tipo de dado que uma variável está recebendo.

### Convertendo tipos

> [!NOTE]
> Caso uma variável não esteja trabalhando com o tipo de dado desejado, você pode converter o tipo de dado dele.

Para converter uma variável para inteiro:
~~~python
# variável do tipo string
valor = "10"

# converte para int
valor = int(valor)
~~~

Para converter uma variável para float:
~~~python
# variável do tipo string
valor = "7.5"

# converte para float
valor = float(valor)
~~~

> [!CAUTION]
> As variáveis do tipo *float* separam os valores decimais com ponto (`.`), e não com vírgula. Informar um número decimal separado por vírgula em uma variável do tipo *float* ocasionará um erro, e provocará um ***crash*** do programa, o que irá interrompê-lo. Para o computador, um número com vírgula (,) é um texto.

Para converter para string:
~~~python
# variável do tipo int
valor = 10

# converte para string
valor = str(valor)
~~~

Para converter para booleano:
~~~python
# variável do tipo string
valor = "True"

# converte para booleano
valor = bool(valor)
~~~

### Concatenação de valores

> [!IMPORTANT]
> Concatenar significa juntar dois ou mais valores diferentes. Você pode (e deve) concatenar variáveis com strings normais.

Há 4 formas de se concatenar valores.

Forma 1:
~~~python
# variáveis
nome = "Alex Machado"
idade = 41

# saída
print("Olá, meu nome é", nome, "e tenho", idade, "anos.")
~~~

> [!CAUTION]
> Nessa forma, o Python adiciona automaticamente um espaço entre as strings e as variáveis.

Forma 2:
~~~python
nome = "Alex Machado"
idade = 41

print("Olá, meu nome é " + nome + " e tenho " + str(idade) + " anos.")
~~~

> [!CAUTION]
> Nessa forma, o Python não adidiona automaticamente o espaço entre as string e as variáveis, o que permite um controle maior. Porém, ele só reconhece valores do tipo string. Caso queira adicionar um valor numérico, é necessário convertê-lo para ***string***, conforme o exemplo.

Forma 3:
~~~python
nome = "Alex Machado"
idade = 41

print("Olá, meu nome é {} e tenho {} anos.".format(nome, idade))
~~~

Forma 4:
~~~python
nome = "Alex Machado"
idade = 41

print(f"Olá, meu nome é {nome} e tenho {idade} anos.")
~~~

> [!TIP]
> A forma 4 é chamada de ***f-string***, e é considerada a forma mais elegante de concatenar valores. Semrpe que possível, prefira essa forma.

Para eliminar a quebra de linha entre dois `print()`, insira um `end=""` ao final do comando:
~~~python
print("Este é um texto.", end="")
~~~

## Entrada de dados

> [!NOTE]
> A entrada de dados é a forma que o usuário tem de inserir os dados durante a execução do programa, e não diretamente no código-fonte.

Para exigir que o usuário insira dados durante a execução do programa, faça uso do comando `input()`. Exemplo:
~~~python
# entrada de dados
nome = input("Informe seu nome: ")

# saída de dados
print(f"Olá, o nome do usuário é {nome}.")
~~~

Para eliminar possíveis espaços acidentais inseridos antes ou depois dos valores inseridos pelo usuário, use a função `.strip()`:
~~~python
nome = input("Informe seu nome: ").strip()
~~~

Para converter a primeira letra de cada palavra em maisúcula, use a função `.title()`:
~~~python
nome = input("Informe seu nome: ").title()
~~~

> [!TIP]
> Você pode combinar mais de uma função ao mesmo tempo, caso precise. Por exemplo, você pode eliminar os espaços antes e depois do nome, e ao mesmo tempo converter as inicais minúsculas em maiúsculas:
> ~~~python
> nome = input("Informe seu nome: ").strip().title()
> ~~~

Para converter apenas a inicial de um texto de minúscula para maiúscula, use a função `.capitalize()`:
~~~python
texto = input("Digite um texto: ").capitalize()
~~~

Para converter um texto de minúscculo para totalmente maisúculo, use a função `.upper()`:
~~~python
texto = input("Digite um texto: ").upper()
~~~

Para converter um texto totalmente em maiúsculo para minúsculo, use a função `.lower()`:
~~~python
texto = input("Digite um texto: ").lower()
~~~

Para substituir um valor inserido pelo usuário por outro, use a função `.replace("valor inserido", "novo valor")`:
~~~python
numero_decimal = input("Informe um número decimal: ").replace(",", ".")
~~~

> [!CAUTION]
> O comando `input()` SEMPRE irá receber do usuário um valor do tipo ***string***, mesmo que ele informe apenas um número. Caso queira receber do usuário um valor numérico, é necessário converter o valor. Exemplos:
> - Para receber do usuário um número inteiro:
> ~~~python
> numero_inteiro = int(input("Informe um número inteiro: "))
> ~~~
> - Para receber do usuário um número decimal:
> ~~~python
> numero_decimal = float(input("Informe um número decimal: "))
> ~~~

> [!TIP]
> O usuário provavelmente não sabe que o número decimal em programação é separado por ponto (`.`), e não por vírgula, o que invariavelmente o fará separar as casas decimais por vírgula(,), e invevitavelmente fará o programa *crashar* e parar a execução com um erro.<br>
> Para evitar isso, voc~e pode usar o `float()` em conjunto com o `replace()`. Veja no exemplo:
> ~~~python
> numero_decimal = float(input("Informe um número decimal: ").replace(",", "."))
> ~~~

## Estruturas de decisão

> [!NOTE]
> Servem para ensinar ao computador a tomar decisões com base em condicionais.

### if...else

Duas decisões podem ser tomadas pelo computador com base em uma condição: Verdadeiro ou Falso.

Exemplo: para fazer o computador decidir se o usuário é maior ou menor de idade:
~~~python
idade = int(input("Informe sua idade: "))

# estrutura de decisão
if idade >= 18:
    print("Usuário é maior de idade.")
else:
    print("Usuário é menor de idade.")
~~~

> [!IMPORTANT]
> Vê esse recuo para a direita em algumas linhas de código É a indentação. Serve para organizar seu código-fonte, determinar onde começa e onde termina  um bloco de programação e facilitar a manutenção do programa.<br>
> Para indentar seu código-fonte, basta dar um **Enter** após o sinal de dois-pontos (`:`).<br>
> Caso não indente, você pode indentar a linha com um **Tab** ou com **4 barras de espaço**.

> [!CAUTION]
> Diferente de outras linguagens de programação, em Python, a indentação é **OBRIGATÓRIA**. Ou seja, o seu código-fonte pode não rodar, caso a indentação do seu código estiver errada, ou mal feita.

> [!TIP]
> Caso o bloco de um *if...else* seja pequeno e tenha apenas uma única linha de comando para cada bloco, você pode trocar pelo **Operador Ternário**.<br>
> O Operador Terminário é uma forma simplificada de se fazer o mesmo *if...else*. Veja no exemplo abaixo como fazer o mesmo programa da maioridade com o operador terminário:
> ~~~python
> idade = int(input("Informe sua idade: "))
> print("O usuário é {'maior' if idade >= 18 else 'menor'} de idade.")
> ~~~