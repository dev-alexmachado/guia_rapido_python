# Coleções

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Lista](#lista)<br>
    1.1 [Armazenar itens na lista](#armazenar-itens-na-lista)<br>
    1.2 [Inserir itens na lista](#inserir-itens-na-lista)<br>
    1.3 [Ordenar uma lista](#ordenar-uma-lista)<br>
    1.4 [Pesquisar por um item da lista](#pesquisar-por-um-item-da-lista)<br>
    1.5 [Alterar um item da lista](#alterar-um-item-da-lista)<br>
    1.6 [Excluir item da lista](#excluir-item-da-lista)<br>
    1.7 [Separando item da lista em uma variável](#separando-item-da-lista-em-uma-variável)<br>
    1.8 [Join](#join)<br>
    1.9 [Split](#split)<br>
2. [Tuplas](#tuplas)
3. [Dicionário](#dicionário)<br>
    3.1 [Adicionar nova chave](#adicionar-nova-chave)<br>
    3.2 [Alterar os dados de uma chave](#alterar-os-dados-de-uma-chave)<br>
    3.3 [Remover uma chave](#remover-uma-chave)<br>
4. [Juntando coleções](#juntando-coleções)<br>
    4.1 [Listas aninhadas](#listas-aninhadas)<br>
    4.2 [Lista de dicionários](#lista-de-dicionários)<br>
5. [JSON](#json)

## Lista

Uma lista é uma variável que consegue armazenar vários valores diferentes dentro dela, não só um.

> [!NOTE]
> Para identificar uma lista, os dados sempre estarão dentro de colchetes (`[]`).

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

> [!TIP]
> É possível percorrer os caracteres de uma string como se fosse uma lista. Veja:
> ~~~python
> texto = "Texto qualquer"
>
> for l in texto:
>     print(l)
> ~~~

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

> [!WARNING]
> Alterar a ordem dos itens da lista também altera o valor de sua posição.

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

> [!TIP]
> A diferença entre um *array* e uma lista em Python é que um *array* aceita apenas um único tipo de dado para todos os seus itens, enquanto uma lista pode aceitar qualquer tipo de dado em qualquer um dos seus valores:
> ~~~python
> lista = ["Fulano", 18, 1.85]
>
> for item in lista
>     print(item)
> ~~~

### Separando item da lista em uma variável

É possível retirar um determinado item de uma lista, mas sem que esse valor seja perdido para sempre. Basta armazená-lo em uma variável.

Para separar um item de uma lista e armazenar em uma variável:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]
indice = 2

# separa item da lista e armazena em uma variável
nome_separado = nomes.pop(indice)

print(f"Nome separado: {nome_separado}")
for i, nome in enumerate(nomes):
    print(f"Posição {i}: {nome}")
~~~

### Join

O `join` permite juntar valores de uma lista em uma única variável.

Para juntar todos os itens da lista em uma única variável:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]

# insere um separador entre os itens da lista
separador = ", "

# junta todos os itens
nomes_string = separador.join(nomes)

print(nomes_string)
~~~

> [!TIP]
> Você também pode juntar apenas alguns itens da lista, não necessariamente todos. Veja a seguir:

Para juntar uma sequencia da lista:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]
separador = ", "

# neste exemplo, vamos juntar apenas os dois primeiros valores
nomes_string = separador.join(nomes[0:2])

print(nomes_string)
~~~

Para juntar itens de posições diferentes da lista:
~~~python
nomes = ["Fulano", "Cicrano", "Beltrano"]
separador = ", "

# neste exemplo, vamos juntar o primeiro e o terceiro item da lista
nomes_string = separador.join([nomes[0], nomes[3]])

print(nomes_string)
~~~

> [!IMPORTANT]
> O `join` só funciona com elementos string da lista.

### Split

O `split` faz o contrário do join, ou seja, separa os valores de uma variável string em uma lista.

Para juntar valores de uma string em uma lsita:
~~~python
nomes = "Fulano, Cicrano, Beltrano"

# cria a lista a partir da variável
nomes_lista = nomes.split(", ")

for nome in nomes_lista:
    print(nome)
~~~

## Tuplas

Uma tupla é um tipo de lista imutável, ou seja, diferente de uma lista tradicional, na tupla você não pode acrecentar, deletar, alterar ou ordenar, apenas exibir.

> [!NOTE]
> A tupla é identificada por parênteses (`()`).

> [!WARNING]
> Não confunda a tupla em Python com a tupla em banco de dados relacional. São conceitos completamente diferentes e um não tem nada a ver com outro.

Para armazenar e exibir itens de uma tupla:
~~~python
dias_da_semana = ("Domingo", "Segunda-Feira", "Terça-Feira", "Quarta-Feira", "Quinta-Feira", "Sexta-Feira", "Sábado")

for dia in dias_da_semana:
    print(dia)
~~~

> [!NOTE]
> Embora não seja possível ordenar a tupla, é possível transformá-la em uma lista ordenada com `sorted()`. Veja:
> ~~~python
> primeiro_trimestre = ("janeiro", "Fevereiro", "Março")
>
> # transofmra tupla em lista ordenada
> meses = sorted(primeiro_trimestre)
>
> for mes in meses:
>     print(mes)
> ~~~

## Dicionário

Um dicionário em Python é um tipo de lista identificada por valores conhecidos como **chaves**. Cada chave representa um dado. É como se fosse um "dicionário" do mundo real: uma palavra é substantivo de alguma coisa.

> [!NOTE]
> Diferentemente das listas e das tuplas, um dicionário é identificado por chaves (`{}`).

Para armazenar dados em um dicionário e exibí-los na tela:
~~~python
# dicionário
usuario = {
    'nome': "Alex Machado",
    'idade': 41,
    'profissão': "desenvolvedor"
}

# exibe os dados na tela
# forma 1
print(usuario)

# forma 2
print(f"Nome: {usuario['nome']}")
print(f"Idade: {usuario['idade']}")
print(f"Profissão: {usuario['profissão']}")

# forma 3
print(f"Nome: {usuario.get('nome')}")
print(f"Idade: {usuario.get('idade')}")
print(f"Profissão: {usuario.get('profissão')}")

# forma 4
for chave in usuario:
    print(f"{chave.capitalize()}: {usuario.get(chave)}")
~~~

> [!IMPORTANT]
> A diferença entre `dicionario[chave]` e `dicionario.get(chave)` é que no primeiro caso pode ser usado para outras operações além de exibir, como inserir ou alterar os dados da chave, mas caso tente exibir uma chave inexistente, o programa *crasha*. Já no segundo só é possível exibir o dado da chave, mas em compensação ele retorna `None` caso você tente informar o valor de uma chave inexistente, e não *crasha* o programa.

> [!TIP]
> A boa prática pede para que as chaves dos dicionários sejam escritas entre aspas simples (`''`), e seus valores em aspas duplas (`""`).

### Adicionar nova chave

É possível adicionar uma nova chave a um dicionário já existente.

Para adicionar uma nova chave:
~~~python
usuario = {
    'nome': "Alex Machado",
    'idade': 41,
    'profissão': "desenvolvedor"
}

# nova chave
usuario['cidade'] = "Brasília"

# exibe o dicionário já com o novo valor
for chave in usuario:
    print(f"{chave.capitalize()}: {usuario.get(chave)}")
~~~

### Alterar os dados de uma chave

Para alterar os dados de uma chave:
~~~python
usuario = {
    'nome': "Alex Machado",
    'idade': 41,
    'profissão': "desenvolvedor"
}

# alterando os dados de uma chave
usuario['profissão'] = 'gerente de projetos'

for chave in usuario:
    print(f"{chave.capitalize()}: {usuario.get(chave)}")
~~~

### Remover uma chave

Para remover uma chave do dicionário:
~~~python
usuario = {
    'nome': "Alex Machado",
    'idade': 41,
    'profissão': "desenvolvedor"
}

# removendo a chave
# forma 1
usuario.pop('profissão', None)

# forma 2
del usuario['idade']

for chave in usuario:
    print(f"{chave.capitalize()}: {usuario.get(chave)}")
~~~

## Juntando coleções

> [!NOTE]
> É possível juntar várias coleções em um único objeto, como formar uma lista aninhada ou uma lista de dicionários.

### Listas aninhadas

Listas aninhadas é basicamente uma lista que contém dentro dela outras listas.

Para armazenar e listar uma lista aninhada:
~~~python
usuarios = [
    ["Fulano", 18],
    ["Cicrano", 21],
    ["Beltrano", 35]
]

# exibe os dados na tela
for usuario in usuarios:
    nome, idade = usuario

    print(f"Nome: {nome}")
    print(f"Idade: {idade}")
~~~

### Lista de dicionários

É uma lista em que cada item é na verdade um dicionário.

~~~python
# lista de dicionários
usuarios = [
    {
        'nome': "Fulano",
        'idade': 18
    },
    {
        'nome': "Cicrano",
        'idade': 21
    },
    {
        'nome': "Beltrano",
        'idade': 35
    }
]

# exibe os dados da lista na tela
for usuario in usuarios:
    for chave in usuario:
        print(f"{chave.capitalize()}: {usuario.get(chave)}")
~~~

## JSON

> [!NOTE]
> **JSON** é a sigla para **JavaScript Object Notation**, ou em português, **Objeto de Notação JavaScript**. Atualmente é um dos formatos mais populares do mundo da programação, concorrendo diretamente com o XML.
> O formato JSON é muito parecido com o dicionário, e portanto este formato, mesmo sendo de outra linguagem de programação, trabalha muito bem com a linguagem Python.

O formato JSON se aprenseta da seguinte forma:
~~~json
[
    {
        'nome': "Fulano",
        'idade': 18
    },
    {
        'nome': "Cicrano",
        'idade': 21
    }
]
~~~

> [!IMPORTANT]
> Para trabalhar com arquivos JSON em Python, é necessário importar a biblioteca `json` para o seu algoritmo.

Para ler um arquivo JSON:
~~~python
# importa a biblioteca json
import json

# abre e desserializa o arquivo json
with open("arquivo.json", "r", encoding="utf-8") as f:
    dados = json.load(f)

# exibe os dados do arquivo json
for dicionario in dados:
    for chave, valor in dicionario.items():
        print(f"{chave.capitalize()}: {valor}")
~~~

Para gravar dados em um novo arquivo JSON:
~~~python
import json

usuarios = [
    {
        'nome': "Fulano",
        'idade': 18
    }
]

# gravar os dados em json
with open("novo_arquivo.json", "w", encoding="utf-8") as f:
    json.dump(usuarios, f)
~~~

Para inserir novos dados em um arquivo JSON já existente:
~~~python
import json

# abre e desserializa o arquivo json {#abre-e-desserializa-o-arquivo-json  data-source-line="526"}
with open("arquivo.json", "r", encoding="utf-8") as f:
    dados = json.load(f)

# novos dados a serem inseridos
usuario = {
    'nome': "Fulano",
    'idade': 18
}

# insere os novos dados junto com os dados anteriores
dados.append(usuario)

# grava os novos dados no mesmo arquivo json
with open("arquivo.json", "w", encoding="utf-8") as f:
    json.dump(dados, f)
~~~

---

- [Voltar ao início](#sumário)
- [Voltar ao índice do Guia Rápido de Python](https://github.com/dev-alexmachado/guia_rapido_python)