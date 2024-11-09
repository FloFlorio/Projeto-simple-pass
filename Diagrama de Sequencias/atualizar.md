```plantuml
@startuml
actor Usuario
participant Aplicativo
participant Sistema
participant API

Usuario -> Aplicativo: visualizarStatusLinhas()
Aplicativo -> Sistema: solicitarDadosAtualizados()
Sistema -> API: obterStatusLinhas()

alt Dados atualizados
    API --> Sistema: Novos status das linhas
    Sistema -> Sistema: atualizarDados()
    Sistema --> Aplicativo: Dados atualizados
    Aplicativo -> Usuario: Exibir status atualizado das linhas
else Dados não atualizados
    API --> Sistema: Dados sem alterações
    Sistema --> Aplicativo: Dados inalterados
    Aplicativo -> Usuario: Exibir mensagem "Dados atualizados recentemente"
end

@enduml