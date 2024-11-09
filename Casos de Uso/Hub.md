```plantuml
@startuml
left to right direction
actor Usuário
actor Sistema
rectangle SimplePass {
Usuário -- (Consulta e Recarga de Saldo)
Usuário -- (Ver atualização das Linhas em Tempo Real)
Usuário -- (Mapa do Metrô)
Usuário -- (Assistência ao Usuário)
(API atualiza as linhas) -- Sistema
(I.A para suporte ao usuário) -- Sistema
}
@enduml
´´´