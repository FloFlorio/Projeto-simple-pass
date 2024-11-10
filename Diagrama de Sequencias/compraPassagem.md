# Diagrama de Sequencia: Compra de passagem

```plantuml
@startuml

actor Usuario as U #lightblue
participant Aplicativo as A #lightgreen
participant Servidor as SI #lightyellow
boundary interface_externa as IE #lightgrey
participant API_SPTRANS as SET #lightcoral

activate U
activate A
ref over U, A, SI : ValidaCredencialSequencia

alt credenciais validas
    U -> A : Informa quantidade de passagens

    alt Saldo disponível na conta
    A -> IE : Compra de passagens
    IE -> SET : ComprarPassagem()
    SET --> IE : compra resposta
    IE --> A : compra resposta

        alt Compra Ok
            A ->> SI : atualizaDados()
            activate SI
            SI ->> A : mensagem de confirmação
            deactivate SI
            A --> U : mensagem de confirmação

        |||
        else Compra não Ok
            A --> U : Informa tipo de erro
        end
        |||

    else Saldo indisponível na conta
    A --> U : Saldo indisponível
    end
    |||

else credenciais não validas
    A --> U : Informa tipo de erro
    
end
|||

@enduml
