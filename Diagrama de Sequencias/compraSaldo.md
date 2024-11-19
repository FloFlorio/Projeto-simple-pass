```plantuml
@startuml

actor Usuario as U #lightblue
control SistemaInterno as SI #lightgreen
entity API_Banco as SEB #lightcoral

activate U
activate SI
ref over U, SI : ValidaCredencialSequencia

U -> SI : Informa quantidade de passagens

U -> SI : compraSaldo()

SI -> SEB : requisicaoPagamento()
activate SEB
SEB --> SI : Resposta do pagamento
deactivate SEB
SI -> SEB : requisicaoConfirmacaoPagamento()
activate SEB
SEB --> SI : Confirmação de pagamento
deactivate SEB

SI --> U : situação compra

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


