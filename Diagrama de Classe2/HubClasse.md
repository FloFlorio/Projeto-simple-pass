```plantuml
@startuml

class Usuario {
    - id: String
    - abas: String
}

class Abas {
    - ajuda: String
    - consultaRecarga: String
    - atualizarLinhas: String
    - mostrarMapa: String
}

class Sistema {
}

class Aplicativo {
}

Usuario --> Aplicativo : "interage"
Aplicativo --> Sistema : "verifica"
Aplicativo --> Abas : "exibe"

@enduml

