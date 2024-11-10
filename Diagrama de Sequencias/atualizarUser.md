```plantuml

@startuml

actor Usuario as U #lightblue
participant Aplicativo as A #lightgreen
participant Sistema_interno as SI #lightyellow
boundary interface_externa as IE #lightgrey

activate U
activate A

U -> A : Reporta situação da linha 
A -> SI : processaFeedback()
activate SI

alt feedback válido
    SI --> A : mostrarFeedback()
    deactivate SI

    A --> U : Confirmar feedback enviado
    A -> IE : Notifica sobre nova situação
else feedback inválido
    SI --> A : Informa erro no feedback
    deactivate SI

    A --> U : Informa erro no envio
end

@enduml

