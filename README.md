# 🐍 Guia Rápido de Python

<p align="center">
    <img src="img/python.png" alt="Python logo" width="100px">
    <br>
    <br>
    <img alt="Static Badge" src="https://img.shields.io/badge/3.11.0+-FFD43B?style=plastic&logo=python&logoColor=fff&label=Python&labelColor=306998">
    <img alt="Static Badge" src="https://img.shields.io/badge/10+-fff?style=plastic&logo=windows&logoColor=646464&label=Windows&labelColor=0078D6">
    <img alt="Static Badge" src="https://img.shields.io/badge/3.1.3-000?style=plastic&logo=flask&logoColor=fff&label=Flask&labelColor=44abbf">
    <img alt="Static Badge" src="https://img.shields.io/badge/6.1-333?style=plastic&logo=django&logoColor=fff&label=Django&labelColor=092E20">
    <img alt="Static Badge" src="https://img.shields.io/badge/3.53.0-003b57?style=plastic&logo=sqlite&logoColor=fff&label=SQLite&labelColor=%230f80cc">
    <img alt="Static Badge" src="https://img.shields.io/badge/8.0.0+-F29111?style=plastic&logo=mysql&logoColor=fff&label=MySQL&labelColor=00758F">
</p>

>[!IMPORTANT]
> Esse tutorial é destinado para máquinas com o Sistema Operacional **Windows 10** ou superior e **Python 3.11** ou superior.

## 📖 Sumário

1. [Lógica de Programação](https://github.com/dev-alexmachado/guia_rapido_python/blob/main/parte01/logica_de_programacao.md)
2. [Coleções](https://github.com/dev-alexmachado/guia_rapido_python/blob/main/parte02/colecoes.md)
3. [Funções](https://github.com/dev-alexmachado/guia_rapido_python/blob/main/parte03/funcoes.md)
4. [Import](https://github.com/dev-alexmachado/guia_rapido_python/blob/main/parte04/import.md)
5. [Orientação a Objetos em Python](https://github.com/dev-alexmachado/guia_rapido_python/blob/main/parte05/orientacao_a_objetos.md)
6. [Flask](https://github.com/dev-alexmachado/guia_rapido_python/blob/main/parte06/flask.md)
7. [Django](https://github.com/dev-alexmachado/guia_rapido_python/blob/main/parte07/django.md)
8. [Deploy](https://github.com/dev-alexmachado/guia_rapido_python/blob/main/parte08/deploy.md)

## 🛣️ Caminho Python

~~~mermaid
graph TD
    Python(Python)
    IA(IA)

    subgraph Programação
        direction TD
        Games(Games)
        Apps(Apps)
        Hacking(Hacking)
        Robótica(Robótica)
        BioInfo(Bio Informática)
        Automação(Automação)
        IoT(Internet das Coisas)
        BioHack(Bio Hacking)

        subgraph Dispositivos
            subgraph Placas
                Arduino(Arduino)
                RP(Raspberry Pi)
                SP32(SP32)
            end

            subgraph Usuários
                Desktop(Desktop)
                Mobile(Mobile)
                Web(Web)
            end
        end

        Usuários --> Apps
        Usuários --> Games
        Dispositivos --> Hacking
        Dispositivos --> IoT
        IoT <--> Hacking
        Apps <--> Hacking
        Placas --> Robótica
        Robótica --> Automação
        IoT --> Automação
        BioInfo --> BioHack
        IoT --> BioHack
        Hacking --> BioHack
    end

    subgraph ND [Notebooks e Dashboards]
        direction TD
        AD(Análise de Dados)
        WS(Web Scrapping)
        CD(Ciência de Dados)
        PowerBI(PowerBI)

        AD --> PowerBI
        AD --> WS
        WS --> CD
        AD --> CD
        PowerBI --> CD
    end

    Python --> Programação
    Python --> IA
    IA --> Programação
    IA --> ND
    Python --> ND
    Web --> ND
~~~