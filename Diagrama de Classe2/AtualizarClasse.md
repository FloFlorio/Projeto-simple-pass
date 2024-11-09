```plantuml
@startuml

class Usuario {
    - id: String
}

class AbaAtualizacao {
    - linhas: String
    - Status: String
}

class Sistema {
    - dadosAtualizados List<Linha>
}

class Linha {
    - status: String
    - tempoEstimado: int
}

class Aplicativo {
    
}

Usuario --> Aplicativo : "interage"
Aplicativo --> Sistema : "verifica"
AbaAtualizacao --> Sistema : "obtém dados"
AbaAtualizacao --> Linha : "exibe"

@enduml
