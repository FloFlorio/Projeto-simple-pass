```plantuml
@startuml
left to right direction 
actor Usuário
actor Sistema as "API's de Bancos e Bilhete Único/TOP"
rectangle Recarga {
Usuário -- (Escolher entr TOP e bilhete único)
Usuário -- (Recarregar o saldo)
Usuário -- (Escolher método de pagamento)
(Conectar APIs do Bilhete Único e TOP) -- Sistema
}
@enduml
´´´