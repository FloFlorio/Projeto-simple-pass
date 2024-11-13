```plantuml
@startuml
skinparam class {
    BackgroundColor #F4F4F4
    BorderColor #2E86C1
    ArrowColor #117A65
}

class VisualizarStatusLinhas {
    + exibirStatus()
}

class MostrarFeedback {
    + coletarFeedback()
    + exibirFeedback()
}

class ComprarPassagem {
    + iniciarCompra()
    + concluirCompra()
}

class ConsultaCartao {
    + verificarSaldo()
    + consultarCota()
}

class SelecionarAba {
    + escolherAba()
    + exibirConteudo()
}

VisualizarStatusLinhas --> ConsultaCartao : depende de
MostrarFeedback --> VisualizarStatusLinhas : utiliza para obter status
ComprarPassagem --> ConsultaCartao : verifica saldo antes
SelecionarAba --> VisualizarStatusLinhas : exibe status
SelecionarAba --> MostrarFeedback : solicita feedback

@enduml

