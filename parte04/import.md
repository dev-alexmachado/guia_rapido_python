# Import

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Importando bibliotecas](#importando-bibliotecas)
2. [Bibliotecas externas](#bibliotecas-externas)
3. [Módulo](#módulo)
4. [`if __name__ == "__main__"`](#if-name--main)
5. [Requirements](#requirements)

## Importando bibliotecas

> [!NOTE]
> São um conjunto de comandos separados que não estão entre os comandos padrões do Python, e por isso precisam ser acrescenados manualmente, através do comando `import`. Exemplo:
> ~~~python
> import nome_da_biblioteca
> ~~~
> Caso seja necessário importar apenas uma parte de uma biblioteca, é necessário saber o nome da biblioteca e o nome da função/classe/método que deseja importar, sem necessariamente importar toda a biblioteca só para usar um comando ou um recursos específico. Exemplo:
> ~~~python
> from nome_da_biblioteca import nome_do_recurso
> ~~~

> [!TIP]
> Se o nome da biblioteca for muito grande, pode ser interessate usar o recurso de ***alias*** do Python, da seguinte forma:
> ~~~python
> import nome_da_biblioteca as nb
> ~~~

## Bibliotecas externas

> [!IMPORTANT]
> Algumas bibliotecas não existem nativamente dentro do Python, exigindo a necessidade de instalação para a futura utilização.
> Essa instalação é feita por padrão utilizando o gerenciador de pacotes **pip**. O `pip` é utilizando no terminal dentro do diretório do projeto. Utilize esse comando:
> ~~~
> pip install nome_da_biblioteca
> ~~~

> [!TIP]
> É possível instalar duas ou mais bibliotecas com um único comando:
> ~~~
> pip install biblioteca_1 biblioteca_2
> ~~~

Para usar uma biblioteca instalada, o comando é o mesmo de qualquer biblioteca: `import biblioteca` ou `from biblioteca import recurso`.

> [!CAUTION]
> Para conseguir instalar e utilizar uma biblioteca externa com sucesso, verifique se o ambiente virtual `.venv` foi criado e está ativado. Caso contrário, a biblioteca pode dar problemas no seu computador e pode até mesmo não rodar no seu projeto.

Para verificar se uma biblioteca está instalada:
~~~
pip freeze
~~~

Para desinstalar uma biblioteca:
~~~
pip uninstall nome_da_biblioteca
~~~

> [!WARNING]
> Se você instalou uma biblioteca, mas ela parece não ser reconhecida pelo programa, você pode ter instalado no Python global. Execute os comandos abaixo para verificar:
> ~~~
> deactivate
> pip freeze
> ~~~
> Se após os comandos acima o nome da biblioteca não aparecer, possivelmente é só reiniciar o VSCode e o problema é resolvido. Se aprecer, é porque instalou no ambiente errado. Caso o ambiente não tenha sido criado, execute os comandos nessa ordem:
> ~~~
> pip uninstall nome_da_biblioteca
> cd diretorio-do-projeto
> py -m venv .venv
> .venv\Scripts\activate
> pip install nome_da_biblioteca
> ~~~
> Caso o ambiente virtual já tenha sido criado:
> ~~~
> pip uninstall nome_da_biblioteca
> cd diretorio-da-venv
> .venv\Scripts\activate
> pip install nome_da_biblioteca
> ~~~

## Módulo

O módulo é uma minibiblioteca criada por você mesmo, e que se encontra em outro arquivo `.py` dentro do mesmo diretório ou do mesmo projeto onde será utilizada. Exemplo: dentro da pasta de um projeto você terá os arquivos `main.py` e `modulo.py`.

Para importar o módulo:
~~~python
import nome_do_arquivo
~~~
Ou
~~~python
import nome_do_arquivo as alias
~~~

Para importar uma função do módulo:
~~~python
from nome_do_arquivo import funcao
~~~

> [!IMPORTANT]
> Ao importar o módulo usando `import modulo`, é preciso citá-lo ao chamar uma função que esteja dentro desse módulo da seguinte forma:
> ~~~python
> modulo.funcao()
> ~~~
> Ou usando alias:
> ~~~python
> alias.funcao()
> ~~~
> Se usar o `from modulo import funcao`, não há necessidade de informar o nome do módulo, basta chamar a função pelo nome:
> ~~~python
> funcao()
> ~~~

Exemplo. Suponha que você tenha uma função para calcular a área do triângulo em um arquivo chamado `modulo.py`:
~~~python
def area_triangulo(b, h):
    return (b*h)/2
~~~
Então no arquivo `main.py` o código será esse:
~~~python
import modulo

b = 3
h = 5

print(f"Área do trriângulo: {modulo.area_triangulo(b, h)}")
~~~
Ou
~~~python
import modulo as md

b = 3
h = 5

print(f"Área do trriângulo: {md.area_triangulo(b, h)}")
~~~

Ou ainda
~~~python
from modulo import area_triangulo

b = 3
h = 5

print(f"Área do trriângulo: {area_triangulo(b, h)}")
~~~

> [!TIP]
> Ao usar módulo, quando o programa é executado, é criado na raiz uma pasta chamada `__pycache__`. Não se preocupe com ela. É normal que ela apareça para garantir a transferência de dados entre dois arquivos `.py`.

## `if __name__ == "__main__"`

> [!WARNING]
> Para evitar que o seu algoritmo principal seja importado para outro código, é uma boa prática criar uma função chamada `main()`, e chamar essa função dentro da estrutura `if __name__ == "__main__":`. Veja um exemplo abaixo:
> ~~~python
> def main():
>     nome = input("Informe seu nome: ").strip().title()
>     idade = int(input("Informe sua idade: "))
>
>     print(f"Olá, meu nome é {nome} e tenho {idade}.")
>
> if __name__ == "__main__":
>     main()
> ~~~

## Requirements

> [!NOTE]
> O ***requirements*** é um arquivo de texto que contém uma lista com todas as bibliotecas e suas respectivas versões instaladas em um determinado projeto.
> Um *requirements* é criado acessando o diretório do projeto no terminal.

Para criar um novo *requirements*, acesse o terminal e execute o seguinte comando:
~~~
pip freeze > requirements.txt
~~~

Ele irá gerar um arquivo .txt chamado requirements, que pode ser *commitado* e usado para trabalhar com o projeto em questão em outra máquina.

Caso isso seja feito, a nova máquina não terá nem o ambiente virtual, muito menos as bibliotecas do qual o projeto é dependente. Por isso, é necessário a recriação do ambiente virtual, e em seguida, a instalação das bibliotecas do projeto.

É aí onde entra o requirements.txt: para não ter que instalar todas as bibliotecas manualmente, basta executar este arquivo no terminal para que todas as bibliotecas necessárias sejam instaladas:
~~~
pip install -r requirements.txt
~~~

> [!IMPORTANT]
> O arquivo requirements.txt é obrigatório para deploy em alguns serviços de hospedagem, como o Render e o Vercel.

### Desinstalando várias bibliotecas de uma só vez

O requirementes também pode ser usado para desinstalar as bibliotecas de uma única vez:
~~~
pip uninstall -r requirements.txt -y
~~~

Caso queira desinstalar todas as bibliotecas de um ambiente, mas não sabe quais existem, siga esses comandos:
~~~
pip freeze > requirements.txt
pip uninstall -r requirements.txt -y
~~~

---

- [Voltar ao início](#sumário)
- [Voltar ao índice do Guia Rápido de Python](https://github.com/dev-alexmachado/guia_rapido_python)