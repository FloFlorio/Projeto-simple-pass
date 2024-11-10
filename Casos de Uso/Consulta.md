```plantuml
@startuml
left to right direction
actor Usuário
actor Sistema
rectangle Consulta/Recarga {
Usuário -- (Escolher entr TOP e bilhete único)
Usuário -- (Ver saldo disponível)
Usuário -- (Ver Cota remanescente)
Usuário -- (Recarregar o saldo)
Usuário -- (Escolher método de pagamento)
(Conectar APIs do Bilhete Único e TOP) -- Sistema
}
@enduml
´´´