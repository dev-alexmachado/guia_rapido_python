# Coleções

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Lista](#lista)<br>
    1.1 [Armazenar itens na lista](#armazenar-itens-na-lista)<br>
    1.2 [Inserir itens na lista](#inserir-itens-na-lista)<br>
    1.3 [Ordenar uma lista](#ordenar-uma-lista)<br>
    1.4 [Pesquisar por um item da lista](#pesquisar-por-um-item-da-lista)<br>
    1.5 [Alterar um item da lista](#alterar-um-item-da-lista)<br>
    1.6 [Excluir item da lista](#excluir-item-da-lista)

## Lista

Uma lista é uma variável que consegue armazenar vários valores diferentes dentro dela, não só um.

> [!NOTE]
> Para identificar uma lista, os dados sempre estarão dentro de colchetes `[]`.

### Armazenar itens na lista

Para armazenar e exibir uma lista de nomes:
~~~python
# armazena uma lista de nomes
nomes = ["Fulano", "Cicrano", "Beltrano"]

# imprime a lista de nomes
# forma 1
print(nomes)

# forma 2
print(nomes[0])
print(nomes[1])
print(nomes[2])

# forma 3
for nome in nomes:
    print(nome)

# forma 4
for i in range(len(nomes)):
    print(f"Nome na posição {i}: {nomes[i]}")

# forma 5
for i, nome in enumerate(nomes, start=1):
    print(f"{i}º nome da lista: {nome})
~~~

> [!TIP]
> Considere quando possível a forma 5 de exibir os itens de uma lista. É a forma considerada mais elegante. Quando quiser apenas uma impressão simples na tela, considere a forma 3.

Para armazenar e exibir uma lista numérica:
~~~python
numeros = [1, 2, 3, 4, 5]

for n in numeros:
    print(n)
~~~

### Inserir itens na lista

Para inserir itens em uma lista já existente:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]

# insere novo nome na lista
novo_nome = "Alex"
nomes.append(novo_nome)

# exibe a lista já com o novo item inserido
for nome in nomes:
    print(nome)
~~~

Para inserir itens em uma posição específica de uma lista:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]
novo_nome = "Alex"
posicao = 1

# insere novo nome na posição informada
nomes.insert(posicao, novo_nome)

# novo nome será exibido após "Fulano" e antes de "Cicrano"
for i, nome in enumerate(nomes):
    print(f"Nome na posição {i}: {nome}")
~~~

Para inserir vários itens em uma lista vazia:
~~~python
# lista vazia
nomes = []

while True:
    novo_nome = input("Informe novo nome ou deixe em branco para finalizar: ").strip().title()
    nomes.append(novo_nome)
    continue if novo_nome else break

# exibe a lista completa
for i, nome in enumerate(nomes, start=1):
    print(f"{i}º nome inserido: {nome})
~~~

### Ordenar uma lista

Para ordenar uma lista de strings em ordem alfabética:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]

# ordenando a lista
nomes.sort()

# exibindo a lista ordenada
for nome in nomes:
    print(nomes)
~~~

Para ordenar uma lista de strings em ordem inversa:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]
nomes.sort(reverse=True)
for nome in nomes:
    print(nomes)
~~~

### Pesquisar por um item da lista

Para verificar se um valor existe em uma lista:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]
nome = input("Informe o nome a pesquisar: ").strip().title()

# busca pelo nome desejado e informa o resultado
print(nome if nome in nomes else f"{nome} não encontrado.")
~~~

Para mostrar em qual posição o item está na lista:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]
nome = input("Informe o nome a pesquisar: ").strip().title()

if nome in nomes:
    # retorna o índice do nome pesquisado
    indice = nomes.index(nome)
    print(f"Índice do nome pesquisado é {indice}.")
else:
    print(f"{nome} não encontrado.")
~~~

> [!WARNING]
> Essas formas só retornam a primeira ocorrência da lista. Se o item pesquisado tier valores repetidos dentro da lista, a segunda ocorrência em diante ficará de fora da pesquisa.

Para retornar quantas vezes o item pesquisado existe dentro da lista:
~~~python
nomes = ["Fulano", "Cicrano", "Fulano", "Cicrano", "Beltrano", "Fulano"]
nome = input("Informe o nome a pesquisar: ").strip().title()

# conta a quantidade de ocorrências na lista, se tiver
quantidade = nomes.count(nome)

# exibe o resultado
print(f"{nome} foi encontrado {quantidade} vezes na lista.")
~~~

### Alterar um item da lista

Para mudar o valor de uma posição específica:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]
nomes[0] = input("Informe o novo nome: ").strip().title()

# lista exibe a lista com o novo valor
for nome in nomes:
    print(nome)
~~~

### Excluir item da lista

Para deletar uma posição específica:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]
posicao = 1

# exclui item da lista na posição desejada
del(nomes[posicao])

# exibe lista com o valor deletado
for nome in nomes:
    print(nome)
~~~

Para deletar um valor específico:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]
nome = "Fulano"

# exclui o nome
nomes.remove(nome)

# exibe a lista sem o Fulano
for nome in nomes:
    print(nome)
~~~