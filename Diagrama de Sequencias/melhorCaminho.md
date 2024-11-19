```plantuml


@startuml

actor Usuario as U #lightblue
control SistemaInterno as SI #lightgreen
entity API_SPTRANS as SEM #lightcoral

ref over U, SI : ValidaCredencialSequencia
activate U
activate SI

alt localizacao por pesquisa
    U -> SI : Pesquisa nome do lugar
    SI -> SI : validaLocalizacao()

    alt localizacao encontrada
        SI -> SEM : consultaCaminhoPorNome()
        activate SI
        deactivate SEM
        SEM --> SI : Melhor caminho encontrado
        SI --> U : Apresenta melhor caminho

    else localizacao não encontrada
        SI --> U : Informa que a localização não foi encontrada
    end

else localizacao pelo mapa
    U -> SI : Seleciona local no mapa
    SI -> SI : validaLocalizacao()

    SI -> SEM : consultaCaminhoPorMapa()
    activate SEM

    SEM --> SI : Melhor caminho encontrado
    SI --> U : Apresenta melhor caminho
end

deactivate SI
deactivate U

@enduml
