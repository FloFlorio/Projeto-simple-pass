```plantuml
@startuml
skinparam class {
    BackgroundColor #F4F4F4
    BorderColor #2E86C1
    ArrowColor #117A65
}

class Usuario {
    - id: String
    - opcoesPagina
    + comprarPassagem()
    + comprarSaldo()
    + consultaCartao()
    + validaCredenciais()
}

class Bilhete {
    - saldo: float
    - cotaRestante: float
    - historicoRecargas: List_Recarga
    + atualizarDados()
}

class Recarga {
    - valor: float
    - data: String
}

class Sistema {
    + requisaoPagamento()
    + requisaoLiquidacao()
}

class Aplicativo {
    + iniciar()
    + finalizar()
}

Usuario "1" --> "1" Aplicativo : interage
Aplicativo "1" --> "*" Sistema : verifica
Aplicativo "1" --> "1" Bilhete : consulta
Bilhete "1" --> "*" Recarga : contém
Sistema "1" --> "1" Bilhete : processa recarga

@enduml
