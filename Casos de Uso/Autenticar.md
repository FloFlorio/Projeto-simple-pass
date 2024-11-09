```plantuml
@startuml
left to right direction
actor Usuário
actor Sistema
rectangle Consulta/Recarga {
Usuário -- (Ter um documento ou \nbilhete de transporte publico)
Usuário -- (Inserir as informações necessárias)
(Solicitar um identificador) -- Sistema
(Solcitar senha) -- Sistema
(Validar informações) -- Sistema
}
@enduml
´´´