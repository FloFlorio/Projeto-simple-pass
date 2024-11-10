```plantuml
@startuml
left to right direction
actor Usuário
actor Sistema as  "API's Metrô e CPTM"
rectangle AtualizaçãoLinhas {
Usuário -- (Ver linhas disponíveis no momento)
(Fornecer em tempo real status das linhas\n[operação normal, redução de velocidade e paralisação]) -- Sistema
}
@enduml
´´´