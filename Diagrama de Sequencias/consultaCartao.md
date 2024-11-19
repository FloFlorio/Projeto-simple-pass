# Diagrama de Sequencia: Consultar Saldo


```plantuml
@startuml

actor Usuario as U #lightblue
control SistemaInterno as SI #lightgreen
entity API_SPTRANS as SET #lightcoral

activate U
activate SI

alt credenciais validas
    U -> SI : Pede saldo de um cartão
    SI -> SET : consultaCartao()
    activate SET

    SET --> SI : Informação do cartão
    deactivate SET
    SI --> U : Apresenta informações

else credenciais não validas
    SI --> U : Informa tipo de erro
end

deactivate SI
deactivate U

@enduml




