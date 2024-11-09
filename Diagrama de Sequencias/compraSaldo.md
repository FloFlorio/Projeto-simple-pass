# Diagrama de Sequencia: Compra de saldo

```plantuml
@startuml

actor Usuario 
participant Aplicativo
participant Sistema_interno
boundary interface_externa
participant Sistema_externo_Bancos

activate Usuario
activate Aplicativo
ref over Usuario, Aplicativo, Sistema_interno : ValidaCredencialSequencia


Usuario -> Aplicativo : Informa quantidade de passagens

Aplicativo -> Sistema_interno : compraSaldo()
activate Sistema_interno
Sistema_interno -> interface_externa : compraSaldo()
activate interface_externa

interface_externa -> Sistema_externo_Bancos : requisicaoPagamento()
activate Sistema_externo_Bancos
Sistema_externo_Bancos --> interface_externa : Resposta do pagamento
deactivate Sistema_externo_Bancos
interface_externa -> Sistema_externo_Bancos : requisicaoConfirmacaoPagamento()
activate Sistema_externo_Bancos
Sistema_externo_Bancos --> interface_externa : Confirmação de pagamento
deactivate Sistema_externo_Bancos

interface_externa --> Sistema_interno : situação compra
deactivate interface_externa


alt compra efetuada

    Sistema_interno -> Sistema_interno : gerarRecibo()
    activate Sistema_interno
    Sistema_interno --> Sistema_interno :  Recibo
    deactivate Sistema_interno

    Sistema_interno --> Aplicativo : Recibo
    deactivate Sistema_interno

    Aplicativo --> Usuario : Recibo e mensagem de confimação
    
    

|||
else compra não efetuada

|||
end


@enduml
