```plantuml
@startuml

class Usuario {
    - id: String
    - opcoesPagina
    + comprarPassagem()
    + comprarSaldo()
    + consultaCartao()
    + validaCredenciais()
}

class Bilhete {
    -saldo: float
    -cotaRestante: float
    -historicoRecargas: List<Recarga>
    + atualizarDados()
}

class Recarga {
    -valor: float
    -data: String
}

class Sistema {
    + requisaoPagamento()
    + requisaoLiquidacao()
}

class Aplicativo {
}

Usuario --> Aplicativo : "interage"
Aplicativo --> Sistema : "verifica"
Aplicativo --> Bilhete : "consulta"
Bilhete --> Recarga : "contém"
Sistema --> Bilhete : "processa recarga"

@enduml