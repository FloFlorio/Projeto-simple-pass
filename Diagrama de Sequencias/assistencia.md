```plantuml
@startuml

actor Usuario as U #lightblue
participant Aplicativo as A #lightgreen
participant Servidor as SI #lightyellow
participant Sistema_externo_suporte as SES #lightcoral

activate U
activate A

U -> A : Solicita assistência
A -> SI : identificaProblema()
activate SI

alt Problema comum
    SI --> A : Solução para problema comum
    deactivate SI
    A --> U : Informa solução

else Problema não comum
    SI --> A : Redireciona para suporte
    deactivate SI

    A -> SES : solicitaSuporte()
    activate SES

    SES --> A : Instruções para contato
    deactivate SES

    A --> U : Informa como entrar em contato com suporte
end

deactivate A
deactivate U

@enduml
