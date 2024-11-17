```plantuml

@startuml

actor Usuario como U #lightblue
control SistemaInterno como SI #lightgreen
boundary interface_externa como IE #lightgrey
entity API_SPTRANS como SEM #lightcoral

ref over U, SI : ValidaCredencialSequencia
activate U
activate SI

alt localizacao por pesquisa
    U -> SI : Pesquisa nome do lugar
    SI -> SI : validaLocalizacao()

    alt localizacao encontrada
        SI -> IE : consultaCaminhoPorNome()
        activate IE
        IE -> SEM : consultaCaminho()
        activate SEM

        SEM --> IE : Melhor caminho
        deactivate SEM
        IE --> SI : Melhor caminho encontrado
        deactivate IE
        SI --> U : Apresenta melhor caminho

    else localizacao não encontrada
        SI --> U : Informa que a localização não foi encontrada
    end

else localizacao pelo mapa
    U -> SI : Seleciona local no mapa
    SI -> SI : validaLocalizacao()

    SI -> IE : consultaCaminhoPorMapa()
    activate IE
    IE -> SEM : consultaCaminho()
    activate SEM

    SEM --> IE : Melhor caminho
    deactivate SEM
    IE --> SI : Melhor caminho encontrado
    deactivate IE
    SI --> U : Apresenta melhor caminho
end

deactivate SI
deactivate U

@enduml

