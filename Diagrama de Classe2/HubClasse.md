```plantuml
@startuml

skinparam class {
    BackgroundColor #F4F4F4
    BorderColor #2E86C1
    ArrowColor #117A65
}

class Usuario {
    - id: String
    - abas: String
    + selecionarAba()
}

class Abas {
    - ajuda: String
    - consultaRecarga: String
    - atualizarLinhas: String
    - mostrarMapa: String
    + exibirConteudo()
}

class Sistema {
    + processarConsulta()
    + atualizarInformacoes()
}

class Aplicativo {
    + iniciar()
    + finalizar()
}

Usuario "1" --> "1" Aplicativo : "interage"
Aplicativo "1" --> "*" Sistema : "verifica"
Aplicativo "1" --> "*" Abas : "exibe"

@enduml

