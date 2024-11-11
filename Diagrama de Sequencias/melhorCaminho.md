```plantuml

@startuml

actor Usuario as U #lightblue
participant Aplicativo as A #lightgreen
participant Servidor as SI #lightyellow
boundary interface_externa as IE #lightgrey
participant API_SPTRANS as SEM #lightcoral

ref over U, A, SI : ValidaCredencialSequencia
activate U
activate A

alt localizacao por pesquisa
    U -> A : Pesquisa nome do lugar
    A -> SI : validaLocalizacao()
    activate SI

    alt localizacao encontrada
        SI --> A : Localizacao validada
        deactivate SI

        A -> IE : consultaCaminhoPorNome()
        activate IE
        IE -> SEM : consultaCaminho()
        activate SEM

        SEM --> IE : Melhor caminho
        deactivate SEM
        IE --> A : Melhor caminho encontrado
        deactivate IE
        A --> U : Apresenta melhor caminho

    else localizacao não encontrada
        deactivate SI
        A --> U : Informa que a localização não foi encontrada
    end

else localizacao pelo mapa
    U -> A : Seleciona local no mapa
    A -> SI : validaLocalizacao()
    activate SI

    SI --> A : Localizacao validada
    deactivate SI

    A -> IE : consultaCaminhoPorMapa()
    activate IE
    IE -> SEM : consultaCaminho()
    activate SEM

    SEM --> IE : Melhor caminho
    deactivate SEM
    IE --> A : Melhor caminho encontrado
    deactivate IE
    A --> U : Apresenta melhor caminho
end

deactivate A
deactivate U

@enduml
