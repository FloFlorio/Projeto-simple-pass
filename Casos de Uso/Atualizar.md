```plantuml
@startuml
left to right direction
actor Usuário
actor Sistema
rectangle AtualizaçãoLinhas {
Usuário -- (Ver linhas disponíveis no momento)
(API para fornecer em tempo real status das linhas\n[operação normal, redução de velocidade e paralisação]) -- Sistema
}
@enduml
´´´