```plantuml

@startuml

actor Usuario as U #lightblue
control SistemaInterno as SI #lightgreen
entity API_SPTRANS as SET #lightcoral

activate U
activate SI

U -> SI : Reporta situação da linha 
SI -> SI : processaFeedback()

alt feedback válido
    SI -> SET : Notifica sobre nova situação
    activate SET

    SI --> U : Confirmar feedback enviado

else feedback inválido
    SI --> U : Informa erro no envio
end

deactivate SI
deactivate U

@enduml




