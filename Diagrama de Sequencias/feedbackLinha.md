```plantuml

@startuml

actor Usuario como U #lightblue
control SistemaInterno como SI #lightgreen
boundary interface_externa como IE #lightgrey
entity API_SPTRANS como SET #lightcoral

activate U
activate SI

U -> SI : Reporta situação da linha 
SI -> SI : processaFeedback()

alt feedback válido
    SI -> IE : Notifica sobre nova situação
    activate IE
    IE -> SET : Notifica sobre nova situação
    deactivate IE

    SI --> U : Confirmar feedback enviado

else feedback inválido
    SI --> U : Informa erro no envio
end

deactivate SI
deactivate U

@enduml


