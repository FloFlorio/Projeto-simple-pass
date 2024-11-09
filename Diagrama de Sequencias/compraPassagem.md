# Diagrama de Sequencia: Compra de passagem

```plantuml
@startuml

actor Usuario 
participant Aplicativo
participant Sistema_interno
boundary interface_externa
participant Sistema_externo_trans

activate Usuario
activate Aplicativo
ref over Usuario, Aplicativo, Sistema_interno : ValidaCredencialSequencia


alt credenciais validas
    Usuario -> Aplicativo : Informa quantidade de passagens

    alt Saldo disponível na conta
    Aplicativo -> interface_externa : Compra de passagens
    interface_externa -> Sistema_externo_trans : ComprarPassagem()
    Sistema_externo_trans --> interface_externa : compra resposta
    interface_externa --> Aplicativo : compra resposta

        alt Compra Ok
            Aplicativo ->> Sistema_interno : atualizaDados()
            activate Sistema_interno
            Sistema_interno ->> Aplicativo : mensagem de confirmação
            deactivate Sistema_interno
            Aplicativo --> Usuario : mensagem de confirmação

        |||
        else Compra não Ok
            Aplicativo --> Usuario : Informa tipo de erro
        end
        |||

    else Saldo indisponível na conta
    Aplicativo --> Usuario : Saldo indisponível
    end
    |||

else credenciais não validas
    Aplicativo --> Usuario : Informa tipo de erro
    
end
|||

@enduml
