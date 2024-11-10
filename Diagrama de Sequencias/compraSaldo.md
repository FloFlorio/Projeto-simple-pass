# Diagrama de Sequencia: Compra de saldo

```plantuml
@startuml

actor Usuario as U #lightblue
participant Aplicativo as A #lightgreen
participant Sistema_interno as SI #lightyellow
boundary interface_externa as IE #lightgrey
participant Sistema_externo_Bancos as SEB #lightcoral

activate U
activate A
ref over U, A, SI : ValidaCredencialSequencia

U -> A : Informa quantidade de passagens

A -> SI : compraSaldo()
activate SI
SI -> IE : compraSaldo()
activate IE

IE -> SEB : requisicaoPagamento()
activate SEB
SEB --> IE : Resposta do pagamento
deactivate SEB
IE -> SEB : requisicaoConfirmacaoPagamento()
activate SEB
SEB --> IE : Confirmação de pagamento
deactivate SEB

IE --> SI : situação compra
deactivate IE


alt compra efetuada

    SI -> SI : gerarRecibo()
    activate SI
    SI --> SI : Recibo
    deactivate SI

    SI --> A : Recibo
    deactivate SI

    A --> U : Recibo e mensagem de confirmação
    
    

|||
else compra não efetuada

|||
end

@enduml

