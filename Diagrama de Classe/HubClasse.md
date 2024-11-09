```plantuml
@startuml

class Usuario {
    - id: String
    + selecionarAba(): void
}

class Abas {
    - ajuda: String
    - consultaRecarga: String
    - atualizarLinhas: String
    - mostrarMapa: String
    + mostrarAjuda(): void
    + realizarConsultaRecarga(): void
    + atualizarLinhas(): void
    + mostrarMapa(): void
}

class Sistema {
    + verificarOperacao(): boolean
}

class Aplicativo {
    + iniciar(): void
    + direcionarUsuario(aba: Abas): void
}

Usuario --> Aplicativo : "interage"
Aplicativo --> Sistema : "verifica"
Aplicativo --> Abas : "exibe"

@enduml

