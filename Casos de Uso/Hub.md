```plantuml
@startuml
left to right direction
actor Usuário
actor Sistema
rectangle SimplePass {
    Usuário --> (Consultar/Recargar Saldo)
    Usuário --> (Atualizar Linhas em Tempo Real)
    Usuário --> (Consultar Mapa do Metrô)
    Usuário --> (Solicitar Assistência)
    (Atualizar as linhas) <-- Sistema
    (Prestar suporte ao usuário) <-- Sistema
}
@enduml
