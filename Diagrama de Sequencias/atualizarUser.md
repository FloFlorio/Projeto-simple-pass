```plantuml

@startuml

actor Usuario
participant Aplicativo
participant Sistema_interno
boundary interface_externa

activate Usuario
activate Aplicativo

Usuario -> Aplicativo : Reporta situação da linha 
Aplicativo -> Sistema_interno : processaFeedback()
activate Sistema_interno

alt feedback válido
    Sistema_interno --> Aplicativo : mostrarFeedback()
    deactivate Sistema_interno

    Aplicativo --> Usuario : Confirmar feedback enviado
    Aplicativo -> interface_externa : Notifica sobre nova situação
else feedback inválido
    Sistema_interno --> Aplicativo : Informa erro no feedback
    deactivate Sistema_interno

    Aplicativo --> Usuario : Informa erro no envio
end

@enduml
