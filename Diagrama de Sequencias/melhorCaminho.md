```plantuml

@startuml

actor Usuario 
participant Aplicativo
participant Sistema_interno
boundary interface_externa
participant Sistema_externo_mapa

ref over Usuario, Aplicativo, Sistema_interno : ValidaCredencialSequencia
activate Usuario
activate Aplicativo

alt localizacao por pesquisa
    Usuario -> Aplicativo : Pesquisa nome do lugar
    Aplicativo -> Sistema_interno : validaLocalizacao()
    activate Sistema_interno

    alt localizacao encontrada
        Sistema_interno --> Aplicativo : Localizacao validada
        deactivate Sistema_interno

        Aplicativo -> interface_externa : consultaCaminhoPorNome()
        activate interface_externa
        interface_externa -> Sistema_externo_mapa : consultaCaminho()
        activate Sistema_externo_mapa

        Sistema_externo_mapa --> interface_externa : Melhor caminho
        deactivate Sistema_externo_mapa
        interface_externa --> Aplicativo : Melhor caminho encontrado
        deactivate interface_externa
        Aplicativo --> Usuario : Apresenta melhor caminho

    else localizacao não encontrada
        deactivate Sistema_interno
        Aplicativo --> Usuario : Informa que a localização não foi encontrada
    end

else localizacao pelo mapa
    Usuario -> Aplicativo : Seleciona local no mapa
    Aplicativo -> Sistema_interno : validaLocalizacao()
    activate Sistema_interno

    Sistema_interno --> Aplicativo : Localizacao validada
    deactivate Sistema_interno

    Aplicativo -> interface_externa : consultaCaminhoPorMapa()
    activate interface_externa
    interface_externa -> Sistema_externo_mapa : consultaCaminho()
    activate Sistema_externo_mapa

    Sistema_externo_mapa --> interface_externa : Melhor caminho
    deactivate Sistema_externo_mapa
    interface_externa --> Aplicativo : Melhor caminho encontrado
    deactivate interface_externa
    Aplicativo --> Usuario : Apresenta melhor caminho
end

@enduml



