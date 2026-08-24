# Lógica de Programação

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Algoritmo](#algoritmo)
2. [Preparando o VSCode para o Python](#preparando-o-vscode-para-o-python)<br>
    2.1 [Extensões obrigatórias](#extensões-obrigatórias)<br>
    2.2 [Extensões recomendadas](#extensões-recomendadas)<br>
3. [Ambiente Virtual](#ambiente-virtual)
4. [Arquivos Python](#arquivos-python)
5. [Saída de dados](#saída-de-dados)
6. [Executar programa Python](#executar-programa-python)
7. [Comentários](#comentários)
8. [Variáveis](#variáveis)<br>
    8.1 [Tipos de variáveis](#tipos-de-variáveis)<br>
    8.2 [Convertendo tipos](#convertendo-tipos)<br>
    8.3 [Concatenação de valores](#concatenação-de-valores)<br>
9. [Entrada de dados](#entrada-de-dados)
10. [Estruturas de decisão](#estruturas-de-decisão)<br>
    10.1 [if...else](#ifelse)<br>
    10.2 [elif](#elif)<br>
    10.3 [Operadores booleanos](#operadores-booleanos<br>)
    10.4 [match...case](#matchcase)<br>
    10.5 [Tratamento de exceção](#tratamento-de-exceção)<br>
11. [Laços de repetição](#laços-de-repetição)<br>
    11.1 [while](#while)<br>
    11.2 [while True](#while-true)<br>
    11.3 [for](#for)
12. [Gravação de arquivo](#gravação-de-arquivo)

## Algoritmo

> [!NOTE]
> **Algoritmo** é o nome que se dá a solução de um problema, qualquer um que ele seja. É constituído de uma série de instruções passo-a-passo, que visam alcançar um determinado objetivo. Como exemplos, podemos pegar qualquer tutorial disponível na Internet, como este mesmo. Uma receita de bolo também pode ser considerado um algoritmo.

## Preparando o VSCode para o Python

> [!TIP]
> É interessante que antes de começar a configurar o VSCode para o desenvolvimento, crie um Perfil específico para trabalhar com a linguagem Python:
> 1. Vá no menu **Arquivo -> Preferências -> Perfil -> Perfis**.
> 2. Clique no botão **Novo Perfil**.
> 3. Escolha um nome, mude o ícone, e depois clique em **Criar**.
> 4. Somente após isso que você deve instalar as extensões que desejar.

### Extensões obrigatórias

- Python (pacote com extensões essenciais)
- Database Client
- Data Wrangler
- Data Preview
- Jupyter

### Extensões recomendadas

- Comment Anchors
- Error Lens
- VSCode icons

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

Veja abaixo um exemplo do clássico programa ***Hello World***. O fluxograma de um ***Hello World*** é esse:
~~~mermaid
graph TD
    A([Iníicio]) --> B@{ shape: curv-trap, label: "Olá, Mundo!" }
    B --> C([Fim])
~~~

O programa ***hello World*** feito em Python é esse:
~~~python
print("Olá, Mundo!")
~~~

> [!NOTE]
> Um texto escrito entre aspas (simples ou duplas) é chamado de ***string***.

> [!CAUTION]
> O comando `print()` realiza automaticamente uma quebra de linha. Ou seja, caso você coloque um `print()` após outro `print()`, eles serão exibidos em linhas diferentes.

## Executar programa Python

Para executar um programa Python:
1. Use a tecla de atalho `Ctrl+F5`.
2. Ou clique no botão **Run** no alto à direita da janela do VSCode.
3. Ou então abra o terminal e digite:
~~~
py nome-do-arquivo.py
~~~

## Comentários

Uma linha de comentário é uma linha de código que é desconsiderada pelo interpretador durante a execução do seu programa. Os comentários servem como uma anotação do que o desenvolvedor fez em determinado trecho de código, para que o mesmo possa se lembrar do que fez no futuro.

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

Uma variável é um elemento do programa que reserva um espaço na memória do computador para guardar um valor que você ainda não sabe qual é, daí o nome.

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

Fluxograma:
~~~mermaid
flowchart TD
    A([Início]) --> B[/Entrada String:<br>nome = "Alex Machado"/]
    B --> C@{ shape: curv-trap, label: "nome" }
    C --> D([Fim])
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

Concatenar significa juntar dois ou mais valores diferentes. Você pode (e deve) concatenar variáveis com strings normais.

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

A entrada de dados é a forma que o usuário tem de inserir os dados durante a execução do programa, e não diretamente no código-fonte.

Para exigir que o usuário insira dados durante a execução do programa, faça uso do comando `input()`. Exemplo:
~~~python
# entrada de dados
nome = input("Informe seu nome: ")

# saída de dados
print(f"Olá, o nome do usuário é {nome}.")
~~~

O fluxograma do programa acima é esse:
~~~mermaid
graph TD
    A([Início]) --> B@{ shape: manual-input, label: "String nome"}
    B --> C@{ shape: curv-trap, label: "'Olá, o nome do usuário é ' & nome & '.'" }
    C --> D([Fim])
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

Servem para ensinar ao computador a tomar decisões com base em condicionais.

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

O fluxograma do programa acima é:
~~~mermaid
graph TD
    A([Início]) --> B@{ shape: manual-input, label: "int idade"}
    B --> C{Se idade >= 18}
    C -- Sim --> D@{ shape: curv-trap, label: "Usuário é maior de idade." }
    C -- Não --> E@{ shape: curv-trap, label: "Usuário é menor de idade." }
    D --> F([Fim])
    E --> F([Fim])
~~~

> [!IMPORTANT]
> Vê esse recuo para a direita em algumas linhas de código É a indentação. Serve para organizar seu código-fonte, determinar onde começa e onde termina  um bloco de programação e facilitar a manutenção do programa.<br>
> Para indentar seu código-fonte, basta dar um **Enter** após o sinal de dois-pontos (`:`).<br>
> Caso não indente automaticamente, você pode indentar a linha com um **Tab** ou com **4 barras de espaço**.

> [!NOTE]
> Nem sempre o `else` é obrigatório dentro da estrutura `if`.

> [!CAUTION]
> Diferente de outras linguagens de programação, em Python, a indentação é **OBRIGATÓRIA**. Ou seja, o seu código-fonte pode não rodar, caso a indentação do seu código estiver errada, ou mal feita.

> [!TIP]
> Caso o bloco de um *if...else* seja pequeno e tenha apenas uma única linha de comando para cada bloco, você pode trocar pelo **Operador Ternário**.<br>
> O Operador Ternário é uma forma simplificada de se fazer o mesmo *if...else*. Veja no exemplo abaixo como fazer o mesmo programa da maioridade com o operador Ternário:
> ~~~python
> idade = int(input("Informe sua idade: "))
> print(f"O usuário é {'maior' if idade >= 18 else 'menor'} de idade.")
> ~~~

### elif

Às vezes, você precisa que o computador tenha mais do que verdadeiro ou falso para decidir. É aí onde entra o ***elif***: ele adiciona alternativas adicionais ao *if...else* tradicional. Veja:

Para adicionar uma terceira alternativa além do `if` e do `else`, acrescente o `elif` após o bloco do `if` e antes do bloco `else`:
~~~python
nota = float(input("Informe a nota do aluno: ").replace(",", "."))

if nota >= 7:
    print("Aluno está aprovado.")
elif nota >= 5:
    print("Aluno está de recuperação.")
else:
    print("Aluno está reprovado.")
~~~

O fluxograma do programa acima será:
~~~mermaid
graph TD
    A([Início]) --> B@{ shape: manual-input, label: "float nota"}
    B --> C{Se nota >= 7}
    C -- Sim --> D@{ shape: curv-trap, label: "Aluno está aprovado." }
    C -- Não --> E{Se nota >= 5}
    E -- Sim --> F@{ shape: curv-trap, label: "Aluno está de recuperação." }
    E -- Não --> G@{ shape: curv-trap, label: "Aluno está reprovado." }
    D --> H([Fim])
    F --> H([Fim])
    G --> H([Fim])
~~~

### Operadores booleanos

> [!TIP]
> Às vezes, é interessante (e necessário) incluir duas condicionais em uma estrutura do tipo *if...else*. Se for o caso, você precisa decidir se as duas condicionais precisam ser verdadeiras ou se somente uma delas pode ser considerada verdadeira. Veja:
> - Quando duas condicionais precisam ser verdadeiras:
> ~~~python
> nota = float(input("Informe a nota do aluno: ").replace(",", "."))
>
> if nota >= 0 and nota <= 10:
>     print("Nota recebida com sucesso.")
> else:
>     print("Nota informada inválida.")
> ~~~
> Fluxograma:
> ~~~mermaid
> graph TD
>   A([Início]) --> B@{ shape: manual-input, label: "float nota"}
>   B --> C{Se nota >= 0<br> e nota >= 10}
>   C -- Sim --> D@{ shape: curv-trap, label: "Nota recebida com sucesso." }
>   C -- Não --> E@{ shape: curv-trap, label: "Nota informada inválida." }
>   D --> F([Fim])
>   E --> F([Fim])
> ~~~
> - Quando apenas uma das condicionais precisa ser verdadeira:
> ~~~python
> idade = int(input("Informe a idade: "))
> peso = int(input("Informe o peso em kg: "))
>
> if idade >= 12 or peso >= 70:
>     print("Usuário não tem os requisitos para entrar.")
> else:
>     print("Usuário tem a entrada autorizada.")
> ~~~
> Fluxograma:
> ~~~mermaid
> graph TD
>   A([Início]) --> B@{ shape: manual-input, label: "int idade"}
>   B --> C@{ shape: manual-input, label: "float peso"}
>   C --> D{Se idade >= 12<br> ou peso >= 70}
>   D -- Sim --> E@{ shape: curv-trap, label: "Usuário não tem os requisitos para entrar." }
>   D -- Não --> F@{ shape: curv-trap, label: "Usuário tem a entrada autorizada." }
>   E --> G([Fim])
>   F --> G([Fim])
> ~~~

### match...case

Em alguns casos, o *if...else* pode ser substituido por uma solução melhor e mais elegante: o ***match...case***. Ele é usado para analisar valores exatos, e quando a estrutura pede mais de duas saídas possíveis.

Exemplo:
~~~python
n1 = int(input("Informe um número: "))
n2 = int(input("Informe outro número: "))
operacao = input("Informe o tipo de operação que deseja fazer: ")

match operacao:
    case "soma":
        print(n1+n2)
    case "subtração":
        print(n1-n2)
    case "multiplicação":
        print(n1*n2)
    case "divisão":
        print(n1/n2)
    case _:
        print("Operação inexistente.")
~~~

O fluxograma do programa acima é esse:
~~~mermaid
graph TD
    A([Início]) --> B@{ shape: manual-input, label: "int n1" }
    B --> C@{ shape: manual-input, label: "int n2" }
    C --> D@{ shape: manual-input, label: "String operacao" }
    D --> E{escolha operacao}
    E -- caso soma --> F[n1+n2]
    E -- caso subtração --> G[n1-n2]
    E -- caso multiplicação --> H[n1*n2]
    E -- caso divisão --> I[n1/n2]
    E -- caso default --> J@{ shape: curv-trap, label: "Operação inválida."}
    F --> K@{ shape: curv-trap, label: "Resultado" }
    G --> K@{ shape: curv-trap, label: "Resultado" }
    H --> K@{ shape: curv-trap, label: "Resultado" }
    I --> K@{ shape: curv-trap, label: "Resultado" }
    K --> L([Fim])
    J --> L([Fim])
~~~

### Tratamento de exceção

O tratamento de exceção é uma estrutura onde o computador analisa um bloco, e caso ele dê algum tipo de erro, interrompe esse bloco e executa outro bloco. Serve para evvitar que o programa *crashe* em caso de algum erro. É um bloco utilizado para fazer *debug* do seu código. Sua estrutura é formada pelo ***try...except***.

> [!NOTE]
> ***Debug*** é o nome dado para correções de erros do seu código-fonte.

Exemplo:
~~~python
try:
    # tenta executar esse trecho primeiro
    numero_inteiro = int(input("Informe um número inteiro: "))
    print(f"Número informado é {numero_inteiro}.")
except:
    # executa esse trecho caso o anterior dê erro
    print("O valor informado não é válido.")
~~~

Fluxograma:
~~~mermaid
flowchart TD
    A([Início]) --> B{try}
    B -- Sucesso --> C@{ shape: manual-input, label: "int numero_inteiro" }
    C --> D@{ shape: curv-trap, label: "'Número informado é ' & numero_informado & '.'" }
    B -- Exceção --> E@{ shape: curv-trap, label: "O valor informado não é válido." }
    D --> F([Fim])
    E --> F([Fim])
~~~

> [!TIP]
> Você pode pedir para exibir o erro em questão, a fim de facilitar o *debug* do seu código, acrescentando o `Exception` no `except`. Veja:
> ~~~python
> try:
>     # tenta executar esse trecho primeiro
>     numero_inteiro = int(input("Informe um número inteiro: "))
>     print(f"Número informado é {numero_inteiro}.")
> except Exception as e:
>     # executa esse trecho caso o anterior dê erro
>     print(f"O valor informado não é válido.{e}.")
> ~~~

## Laços de repetição

Um laço de repetição, também chamado de ***loop***, é uma estrutura que repete várias vezes o mesmo algoritmo, sem a necessidade de reescrever várias vezes o mesmo comando.

### while

O laço de repetição mais básico é o `while`. Ele executa um algoritmo enquanto uma determinada condição for verdadeira. Veja um exemplo:
~~~python
n = int(input("Informe um número inteiro: "))

# subtrai o valor por 1, exibe na tela e repete enquanto for maior que 0
while n > 0:
    n -= 1
    print(n)
~~~

Fluxograma:
~~~mermaid
graph TD
    A([Início]) --> B@{ shape: manual-input, label: "int n" }
    B --> C{n > 0?}
    C -- Sim --> D[n = n - 1]
    D --> E@{ shape: curv-trap, label: "n" }
    E --> C
    C -- Não --> F([Fim])
~~~

> [!CAUTION]
> No algoritmo acima, o comando `n -= 1` existe para que o número vá decrescendo até que a condição se torne falsa. Sem isso, o *loop* irá se repetir eternamente, sem diminuir o valor de `n`, até que o programa consuma 100% da memória RAM do computador e trave totalmente, impossibilitando seu uso, e ocasionando defeitos tanto de software quanto de hardware no PC. Portanto, use o `while` com muito cuidado.

### while True

O `while True` é utilizado quando você deseja executar um *loop infinito* até que o usuário informe quando deseja parar a repetição. Exemplo:
~~~python
# laço de repetição
while True:
    nome = input("Informe seu nome: ").strip().title()
    email = input("Informe seu e-mail: ").strip().lower()
    cpf = input("Informe seu CPF").strip()

    print(f"Nome: {nome}.")
    print(f"E-mail: {email}.")
    print(f"CPF: {cpf}.")

    continuar = input("Inserir dados de outro usuário? [y] para sim ou Enter para encerrar").strip().lower()

    match continuar:
        case "y":
            continue
        case _:
            break
~~~

Fluxograma do programa acima:
~~~mermaid
flowchart TD
    A([Início]) --> B@{ shape: manual-input, label: "String nome" }
    B --> C@{ shape: manual-input, label: "String email" }
    C --> D@{ shape: manual-input, label: "String cpf" }
    D --> E@{ shape: curv-trap, label: "'Nome: ' & nome & '.<br>E-mail: ' & email & '.<br>CPF: ' & cpf & '.'" }
    E --> F@{ shape: manual-input, label: "String continuar" }
    F --> G{continuar?}
    G -- y --> B
    G -- default --> H([Fim])
~~~

### for

O laço `for` é um tipo de laço que obrigatoriamente executa um número **finito** de vezes, nunca entrando em *loop infinito*. Isso acontece pois o laço já possui seu próprio contador, sem necessidade de inserirmos um. Exemplo:
~~~python
for n in range(5):
    print(n)
~~~

Fluxograma:
~~~mermaid
graph TD
    A([Início]) --> B[n = 0]
    B --> C{n < 5?}
    C -- Sim --> D[/print: n/]
    D --> E[n = n + 1]
    E --> C
    C -- Não --> F([Fim])

~~~

> [!NOTE]
> Esse programa irá exibir a numeração de 0 a 4, pois o computador sempre começa a contagem do zero (0), a não ser que você indique a partir de qual número ele deva começar a contagem. Exemplo:
> ~~~python
> for n in range(5, 11):
>     print(n)
> ~~~
> Nesse caso, o programa começa a contagem de 5 e termina em 10.
> Também posso mudar a ordem da contagem, como por exemplo fazer uma contagem regressiva de 10 até 1. Veja:
> ~~~python
> for n in range(10, 0, -1):
>     print(n)
> ~~~

## Gravação de arquivo

> [!TIP]
> Você já deve ter reparado que os dados repassados para as variáveis não persistem, ou seja, são apagados assim que o programa se encerra. Isso aconece porque os dados são armazenados na memória RAM, que é temporária. Para guardar os dados de forma definitiva, eles precisam ser armazenados em um arquivo. Dessa forma, os dados persistem mesmo após o encerramento do programa.

Para gravar dados em um arquivo de texto:
~~~python
texto = "Este é um texto que será gravado em um arquivo."
with open("arquivo.txt", "w", encoding="utf-8") as f:
    f.write(texto)
~~~

Fluxograma:
~~~mermaid
flowchart TD
    A([Início]) --> B@{ shape: manual-input, label: "String texto" }
    B --> C@{ shape: bow-rect, label: "arquivo.txt" }
    C --> D@{ shape: lin-cyl, label: "Disk storage" }
    D --> E([Fim])
~~~

Para ler um arquivo de texto já existente:
~~~python
with open("arquivo.txt", "r", encoding="utf-8") as f:
    dados = f.read()
print(dados)
~~~

Fluxograma:
~~~mermaid
flowchart TD
    A([Início]) --> B@{ shape: lin-cyl, label: "Disk storage" }
    B --> C@{ shape: bow-rect, label: "arquivo.txt" }
    C --> D[dados = arquivo.txt]
    D --> E@{ shape: curv-trap, label: "dados"}
    E --> F([Fim])
~~~

> [!CAUTION]
> Se desejar gravar dados em um arquivo já existente, ele irá sobrescrever o arquivo original.

---

- [Voltar ao início](#sumário)
- [Voltar ao índice do Guia Rápido de Python](https://github.com/dev-alexmachado/guia_rapido_python)