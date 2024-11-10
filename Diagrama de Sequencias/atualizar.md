```plantuml
@startuml

actor Usuario as U #lightblue
participant Aplicativo as A #lightgreen
participant Sistema as SI #lightyellow
participant API as API #lightgrey

U -> A: visualizarStatusLinhas()
A -> SI: solicitarDadosAtualizados()
SI -> API: obterStatusLinhas()

alt Dados atualizados
    API --> SI: Novos status das linhas
    SI -> SI: atualizarDados()
    SI --> A: Dados atualizados
    A -> U: Exibir status atualizado das linhas
else Dados não atualizados
    API --> SI: Dados sem alterações
    SI --> A: Dados inalterados
    A -> U: Exibir mensagem "Dados atualizados recentemente"
end

@enduml
