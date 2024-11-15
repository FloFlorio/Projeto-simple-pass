```plantuml
@startuml
left to right direction

actor Usuário
actor Api_metro_cptm as "Api metrô e CPTM"
actor Api_banco as "Api Bancos"

rectangle "SimplePass" {
    Usuário --> (Recargar Saldo)
    
    Usuário --> (Consultar Saldo)
    Usuário --> (Consultar Cota)
    Usuário --> (Escolher vizualização entre TOP e bilhete único)
    
    
    Usuário --> (Ver linhas disponíveis no momento)
    (Fornecer status das linhas em tempo real) <<include>>
    Usuário --> (Ver mapa completo das linhas ferroviárias)
    Usuário --> (Pesquisar por nome de estações)
    Usuário --> (Visualizar uma linha específica)
    Usuário --> (Baixar o mapa para uso offline)
    (Fornecer o mapa completo do metrô) <<include>>

    (Recargar Saldo) <-- Api_banco
    (Consultar Cota) <-- Api_banco
    (Consultar Saldo) <-- Api_banco
    (Fornecer o mapa completo do metrô) <-- Api_metro_cptm
    (Fornecer status das linhas em tempo real) <-- Api_metro_cptm
}
    
@enduml
