# Funções

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Aplicar uma função](#aplicar-uma-função)
2. [Parâmetro ou argumento](#parâmetro-ou-argumento)
3. [Retorno](#retorno)
4. [Yield](#yield)

## Aplicar uma função

> [!NOTE]
> Função é um pequeno bloco que reune um pequeno algoritmo, geralmente uma funcionalidade de um sistema, que é chamado no seu algoritmo principal. É utilizado para separar e organizar ideias do seu programa, e também para poder ser reutilizado sem precisar repetir várias linhas de código várias vezes. É declarada através do comando `def`.

Para declarar uma função e chamá-la no seu algoritmo principal:
~~~python
# declarando uma função
def boas_vindas():
    print("Olá, seja bem vindo!")

# chamando a função no seu programa
boas_vindas()
~~~

> [!IMPORTANT]
> Em Python, a função deve ser declarada obrigatoriamente antes do seu algoritmo principal.

## Parâmetro ou argumento

> [!NOTE]
> Um **parâmetro**, por vezes chamado também de **argumento**, é um valor que é repassado para a função para que o mesmo possa utilizá-lo dentro do bloco.

Para receber um parâmetro informado pelo usuário
~~~python
def boas_vindas(nome):
    print(f"Olá {nome}, seja bem vindo!")

# algoritmo principal
nome = input("Informe seu nome: ").strip().title()
boas_vindas(nome)
~~~

## Retorno

Uma função pode retornar um valor para ser utilizado no algoritmo principal.

Para retornar um valor:
~~~python
def boas_vindas(nome):
    return f"Olá {nome}, seja bem vindo!"

# algoritmo principal
nome = input("Informe seu nome: ").strip().title()
print(boas_vindas(nome))
~~~

> [!TIP]
> Uma função pode receber mais de um parâmetro, mas só pode ter um único retorno.

Para informar vários parâmetros em uma função:
~~~python
def primeiro_grau(a, b):
    return -b/a

# algoritmo principal
a = 2
b = -15

print(f"O resultado da equação do 1º grau é {primeiro_grau(a, b)}.")
~~~

## Yield

> [!NOTE]
> Foi falado anteriormente que uma função só pode ter um único retorno. Bom, isso é verdade, mas existe uma exceção: o `yield`. Ele faz a mesma coisa que o `return`, mas com uma diferença: ao invés de interromper definitivamente a função, ele pausa a função no mesmo ponto onde ela parou, e quando ela é chamada de novo, ela continua de onde parou.
> Pode ser bastante útil quando se deseja retornar mais de um valor na função, como uma lista, por exemplo.

Para fazer uma função retornar mais de um valor:
~~~python
def gerar_pares(n):
    """Gera os números pares de 0 até n-1."""
    for i in range(n):
        if i % 2 == 0:
            yield i

# algoritmo principal
for par in gerar_pares(10):
    print(par)
~~~