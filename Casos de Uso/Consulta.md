```plantuml
@startuml
left to right direction
actor Usuário
actor Sistema as "API's Bilhete Único/TOP"
rectangle Consulta {
Usuário -- (Escolher entre TOP e bilhete único)
Usuário -- (Ver saldo disponível)
Usuário -- (Ver Cota remanescente)
(Conectar APIs do Bilhete Único e TOP) -- Sistema
}
@enduml
´´´