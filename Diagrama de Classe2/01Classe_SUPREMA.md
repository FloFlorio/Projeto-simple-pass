```plantuml
@startuml
skinparam class {
    BackgroundColor #F4F4F4
    BorderColor #2E86C1
    ArrowColor #117A65
}

Class Usuário{
    - id: String
    + validarUsuario()
}

class Bilhete {
    -saldo: float
    -cotaRestante: float
    -historicoRecargas: List<Recarga>
    + atualizarDados()
}

class Estações {
    - nome: String
    - local: String
    - descrição: String
}

class Atualizações_Linhas{
    - status: String
    - tempoEstimado: int
    + obterStatusLinhas()
}

class Mapa {
    - Mapa
    + mostrarMapa():
}

class Caminho {
    - distancia: float
    - estacoes: List<Estacao>
    - duracao: int
    + consultaCaminhoPorNome()
    + consultaCaminhoPorMapa()
}

class Recarga {
    -valor: float
    -data: String
    + recarregarValor()
}

class Consulta {
    -valor: float
    + verificarSaldo()
    + consultarCota()
}

Usuário --> Bilhete 
Usuário --> Estações 
Usuário --> Atualizações_Linhas 
Usuário --> Mapa
Usuário --> Caminho 
Usuário --> Recarga
Usuário --> Consulta
Mapa --> Caminho
Mapa --> Estações
Bilhete --> Recarga
Bilhete --> Consulta

@enduml
