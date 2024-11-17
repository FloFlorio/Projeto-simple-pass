```plantuml
@startuml

actor Usuario as U #lightblue
control SistemaInterno as SI #lightgreen
entity API as API #lightgrey

U -> SI : visualizarStatusLinhas()
SI -> API : obterStatusLinhas()

alt Dados atualizados
    API --> SI : Novos status das linhas
    SI -> SI : atualizarDados()
    SI --> U : Exibir status atualizado das linhas
else Dados não atualizados
    API --> SI : Dados sem alterações
    SI --> U : Exibir mensagem "Dados atualizados recentemente"
end

@enduml


