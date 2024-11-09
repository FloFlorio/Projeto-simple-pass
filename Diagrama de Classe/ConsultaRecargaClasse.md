```plantuml
@startuml

class Usuario {
    - id: String
    + consultarSaldo(bilhete: Bilhete)
    + recarregarBilhete(bilhete: Bilhete, valor: float, formaPag: String)
}

class Bilhete {
    -saldo: float
    -cotaRestante: float
    -historicoRecargas: List<Recarga>
    +consultarSaldo(): float
    +consultarCotaRestante(): float
    +adicionarRecarga(recarga: Recarga)
}

class Recarga {
    -valor: float
    -data: String
    +getValor(): float
    +getData(): String
}

class Sistema {
    +verificarAPI(): boolean
    +processarRecarga(bilhete: Bilhete, valor: float): boolean
}

class Aplicativo {
    +iniciar()
    +mostrarSaldo(bilhete: Bilhete)
    +mostrarHistorico(bilhete: Bilhete)
}

Usuario --> Aplicativo : "interage"
Aplicativo --> Sistema : "verifica"
Aplicativo --> Bilhete : "consulta"
Bilhete --> Recarga : "contém"
Sistema --> Bilhete : "processa recarga"

@enduml