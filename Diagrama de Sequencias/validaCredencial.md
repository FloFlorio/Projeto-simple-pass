# Diagrama de Sequencia: Validamento de credenciais


```plantuml
@startuml

actor Usuario 
participant Aplicativo
participant Sistema_interno


loop  >5 times
    activate Usuario
    Usuario -> Aplicativo : Login e senha


    activate Aplicativo
    Aplicativo -> Sistema_interno : validaCredenciais()
    activate Sistema_interno
    Sistema_interno --> Aplicativo : Validação de Crendencial
    deactivate Sistema_interno

    alt credenciais validas
        
        Aplicativo --> Usuario : Permite entrar em acesso privado

        |||
    else credenciais não validas
        Aplicativo --> Usuario : Informa tipo de erro
        |||
    end
end


@enduml
