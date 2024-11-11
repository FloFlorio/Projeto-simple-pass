```plantuml
@startuml

skinparam class {
    BackgroundColor #F4F4F4
    BorderColor #2E86C1
    ArrowColor #117A65
}

class Usuario {
    - id: String
    - pesquisa: String
}

class Mapa {
    - dadosMapa: String
    + mostrarMapa()
}

class Sistema {
    - dadosMapa: String
    + verificarAPI()
    + validaLocalizacao()
    + consultaCaminho()
}

class Caminho {
    - distancia: float
    - estacoes: List_Estacao
    - duracao: int
    + consultaCaminhoPorNome()
    + consultaCaminhoPorMapa()
}

class Estacao {
    - nome: String
    - local: String
    - descricao: String
}

class Aplicativo {
    + iniciar()
    + finalizar()
}

Usuario "1" --> "1" Aplicativo : "Interage com"
Aplicativo "1" --> "1" Sistema : "Verifica dados em"
Aplicativo "1" --> "1" Mapa : "Exibe informações de"
Mapa "1" --> "1" Sistema : "Obtém dados de"
Mapa "1" --> "*" Caminho : "Encontra rota em"
Caminho "1" --> "*" Estacao : "Inclui várias"

@enduml

