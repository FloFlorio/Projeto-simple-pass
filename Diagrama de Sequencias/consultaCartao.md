# Diagrama de Sequencia: Consultar Saldo


```plantuml
@startuml

actor Usuario as U #lightblue
participant Aplicativo as A #lightgreen
participant Servidor as SI #lightyellow
boundary interface_externa as IE #lightgrey
participant API_SPTRANS as SET #lightcoral

activate U
activate A

alt credenciais validas
    U -> A : Pede saldo de um cartão
    A -> IE : consultaCartao()
    activate IE
    IE -> SET : consultaCartao()
    activate SET

    SET --> IE : Informação do cartão
    deactivate SET
    IE --> A : Informação do cartão
    deactivate IE
    A --> U : Apresenta informações

else credenciais não validas
    A --> U : Informa tipo de erro
end

deactivate A
deactivate U

@enduml
