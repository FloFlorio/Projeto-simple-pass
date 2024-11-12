```plantuml

@startuml

actor Usuario as U #lightblue
participant Aplicativo as A #lightgreen
participant Servidor as SI #lightyellow
boundary interface_externa as IE #lightgrey
participant API_SPTRANS as SET #lightcoral

activate U
activate A

U -> A : Reporta situação da linha 
A -> SI : processaFeedback()
activate SI

alt feedback válido
    SI --> A : mostrarFeedback()
    SI -> IE : Notifica sobre nova situação
    deactivate SI
    activate IE
     IE -> SET : Notifica sobre nova situação
    deactivate IE

    A --> U : Confirmar feedback enviado
    
   

else feedback inválido
    activate SI
    SI --> A : Informa erro no feedback
    deactivate SI

    A --> U : Informa erro no envio
end

deactivate A
deactivate U

@enduml

