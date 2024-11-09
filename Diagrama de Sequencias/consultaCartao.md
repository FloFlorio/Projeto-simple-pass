# Diagrama de Sequencia: Consultar Saldo


```plantuml
@startuml

actor Usuario 
participant Aplicativo
participant Sistema_interno
boundary interface_externa
participant Sistema_externo_trans


ref over Usuario, Aplicativo, Sistema_interno : ValidaCredencialSequencia
activate Usuario
activate Aplicativo

alt credenciais validas
    
    
    Usuario -> Aplicativo : Pede saldo de um cartão
    Aplicativo -> interface_externa : consultaCartao()
    activate interface_externa
    interface_externa -> Sistema_externo_trans : consultaCartao()
    activate Sistema_externo_trans

    Sistema_externo_trans --> interface_externa : infomação do cartao
    deactivate Sistema_externo_trans
    interface_externa --> Aplicativo : infomação do cartao
    deactivate interface_externa
    Aplicativo --> Usuario : Apresenta informações 

    |||
else credenciais não validas
    Aplicativo --> Usuario : Informa tipo de erro
    |||
end

@enduml
