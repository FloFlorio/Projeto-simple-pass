# Diagrama de Sequencia: Compra de passagem

```plantuml
@startuml

actor Usuario as U #lightblue
control SistemaInterno as SI #lightgreen
boundary interface_externa as IE #lightgrey
entity API_SPTRANS as SET #lightcoral

activate U
activate SI
ref over U, SI : ValidaCredencialSequencia

alt credenciais validas
    U -> SI : Informa quantidade de passagens

    alt Saldo disponível na conta
    SI -> IE : Compra de passagens
    IE -> SET : ComprarPassagem()
    SET --> IE : compra resposta
    IE --> SI : compra resposta

        alt Compra Ok
            SI ->> SI : atualizaDados()
            SI --> U : mensagem de confirmação

        else Compra não Ok
            SI --> U : Informa tipo de erro
        end

    else Saldo indisponível na conta
    SI --> U : Saldo indisponível
    end

else credenciais não validas
    SI --> U : Informa tipo de erro
    
end

deactivate SI
deactivate U

@enduml


