```plantuml
@startuml
left to right direction
actor Usuário
actor Sistema as "APIs Metrô e CPTM"
rectangle MapaMetro {
    Usuário --> (Ver mapa completo das linhas ferroviárias)
    Usuário --> (Pesquisar por nome de estações)
    Usuário --> (Visualizar uma linha específica)
    Usuário --> (Baixar o mapa para uso offline)
    Sistema --> (Exibir o mapa completo do metrô)
}
@enduml
