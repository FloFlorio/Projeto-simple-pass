# Diagrama de Sequencia: Consultar Saldo


```plantuml
@startuml

actor Usuario como U #lightblue
control SistemaInterno como SI #lightgreen
boundary interface_externa como IE #lightgrey
entity API_SPTRANS como SET #lightcoral

activate U
activate SI

alt credenciais validas
    U -> SI : Pede saldo de um cartão
    SI -> IE : consultaCartao()
    activate IE
    IE -> SET : consultaCartao()
    activate SET

    SET --> IE : Informação do cartão
    deactivate SET
    IE --> SI : Informação do cartão
    deactivate IE
    SI --> U : Apresenta informações

else credenciais não validas
    SI --> U : Informa tipo de erro
end

deactivate SI
deactivate U

@enduml

