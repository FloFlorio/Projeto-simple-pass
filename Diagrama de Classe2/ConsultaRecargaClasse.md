```plantuml
@startuml

class Usuario {
    - id: String
    - opcoesPagina
    + comprarPassagem()
    + comprarSaldo()
    + consultaCartao()
}

class Bilhete {
    -saldo: float
    -cotaRestante: float
    -historicoRecargas: List<Recarga>
}

class Recarga {
    -valor: float
    -data: String
}

class Sistema {
    + requisaoPagamento()
    + requisaoLiquidacao()
    + validaCredencial()
}

class Aplicativo {
    + atualizarDados()
}

Usuario --> Aplicativo : "interage"
Aplicativo --> Sistema : "verifica"
Aplicativo --> Bilhete : "consulta"
Bilhete --> Recarga : "contém"
Sistema --> Bilhete : "processa recarga"

@enduml