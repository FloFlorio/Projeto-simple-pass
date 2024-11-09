```plantuml
@startuml

class Usuario {
    - id: String
    + acessarAbaAtualizacao(): void
}

class AbaAtualizacao {
    - linhas: String
    - Status: String
}

class Sistema {
    + verificarAPI(): boolean
    + atualizarDadosLinhas(): void
    + obterDadosLinhas(): List<Linha>
}

class Linha {
    - status: String
    - tempoEstimado: int
    + getStatus(): String
    + getTempoEstimado(): int
}

class Aplicativo {
    + iniciar(): void
    + mostrarAbaAtualizacao(aba: AbaAtualizacao): void
}

Usuario --> Aplicativo : "interage"
Aplicativo --> Sistema : "verifica"
AbaAtualizacao --> Sistema : "obtém dados"
AbaAtualizacao --> Linha : "exibe"

@enduml
