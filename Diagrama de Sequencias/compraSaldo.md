
```plantuml
@startuml

actor Usuario como U #lightblue
control SistemaInterno como SI #lightgreen
boundary interface_externa como IE #lightgrey
entity API_Banco como SEB #lightcoral

activate U
activate SI
ref over U, SI : ValidaCredencialSequencia

U -> SI : Informa quantidade de passagens

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

    SI --> U : Recibo e mensagem de confirmação

else compra não efetuada
    SI --> U : Informa erro na compra
end

deactivate SI
deactivate U

@enduml



