```plantuml
@startuml
actor Usuario as U #lightblue
control SistemaInterno as SI #lightgreen

activate U
activate SI

U -> SI : Solicita assistência

alt Problema comum
    SI --> U : Solução para problema comum

else Problema não comum
    SI --> U : Redireciona para suporte manual
end

deactivate SI
deactivate U
@enduml
