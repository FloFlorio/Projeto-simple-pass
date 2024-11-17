# Diagrama de Sequencia: Validamento de credenciais


```plantuml
@startuml

actor Usuario como U #lightblue
control SistemaInterno como SI #lightgreen

loop 5 times
    activate U
    U -> SI : Login e senha

    SI -> SI : validaCredenciais()

    alt credenciais validas
        SI --> U : Permite entrar em acesso privado
    else credenciais não validas
        SI --> U : Informa tipo de erro
    end
end

deactivate SI
deactivate U

@enduml


