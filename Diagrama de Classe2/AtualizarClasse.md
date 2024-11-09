```plantuml
@startuml

class Usuario {
    - id: String
    + visualizarStatusLinhas()
    + mostrarFeedback()
}

class AbaAtualizacao {
    - linhas: String
    - Status: String
    + atualizarDados()
}

class Sistema {
    - dadosAtualizados List<Linha>
    + solicitarDadosAtualizados()
    + processaFeedback()
}

class Linha {
    - status: String
    - tempoEstimado: int
    + obterStatusLinhas()
}

class Aplicativo {
    
}

Usuario --> Aplicativo : "interage"
Aplicativo --> Sistema : "verifica"
AbaAtualizacao --> Sistema : "obtém dados"
AbaAtualizacao --> Linha : "exibe"

@enduml
