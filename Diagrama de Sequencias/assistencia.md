```plantuml

@startuml

actor Usuario 
participant Aplicativo
participant Sistema_interno
boundary interface_externa
participant Sistema_externo_suporte

activate Usuario
activate Aplicativo

Usuario -> Aplicativo : Solicita assistência
Aplicativo -> Sistema_interno : identificaProblema()
activate Sistema_interno

alt problema comum
    Sistema_interno --> Aplicativo : Solução para problema comum
    deactivate Sistema_interno
    Aplicativo --> Usuario : Informa solução

else problema não comum
    Sistema_interno --> Aplicativo : Redireciona para suporte
    deactivate Sistema_interno

    Aplicativo -> Sistema_externo_suporte : solicitaSuporte()
    activate Sistema_externo_suporte

    Sistema_externo_suporte --> Aplicativo : Instruções para contato
    deactivate Sistema_externo_suporte

    Aplicativo --> Usuario : Informa como entrar em contato com suporte
end

@enduml
