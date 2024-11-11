```plantuml
@startuml
left to right direction 
actor Usuário
actor Sistema as "APIs de Bancos e Bilhete Único/TOP"
rectangle Recarga {
    Usuário --> (Escolher entre TOP e bilhete único)
    Usuário --> (Recarregar o saldo)
    Usuário --> (Escolher método de pagamento)
    Sistema --> (Conectar APIs do Bilhete Único e TOP)
}
@enduml
