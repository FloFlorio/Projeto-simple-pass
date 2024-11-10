# Diagrama de Sequencia: Validamento de credenciais


```plantuml
@startuml

actor Usuario as U #lightblue
participant Aplicativo as A #lightgreen
participant Servidor as SI #lightyellow

loop  >5 times
    activate U
    U -> A : Login e senha

    activate A
    A -> SI : validaCredenciais()
    activate SI
    SI --> A : Validação de Credenciais
    deactivate SI

    alt credenciais validas
        A --> U : Permite entrar em acesso privado
        |||
    else credenciais não validas
        A --> U : Informa tipo de erro
        |||
    end
end

@enduml

