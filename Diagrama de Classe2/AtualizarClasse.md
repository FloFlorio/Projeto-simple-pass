```plantuml
@startuml
skinparam class {
    BackgroundColor #F4F4F4
    BorderColor #2E86C1
    ArrowColor #117A65
}

class Usuario {
    - id: String
    + visualizarStatusLinhas()
    + mostrarFeedback()
}

class AbaAtualizacao {
    - linhas: String
    - status: String
    + solicitarDadosAtualizados()
}

class Sistema {
    - dadosAtualizados: List_Linha
    + atualizarDados()
    + processaFeedback()
}

class Linha {
    - status: String
    - tempoEstimado: int
    + obterStatusLinhas()
}

class Aplicativo {
    + iniciar()
    + finalizar()
}

Usuario --> Aplicativo : interage
Aplicativo --> Sistema : verifica
AbaAtualizacao --> Sistema : obtém dados
AbaAtualizacao --> Linha : exibe

@enduml
