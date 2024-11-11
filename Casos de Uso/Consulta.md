```plantuml
@startuml
left to right direction
actor Usuário
actor Sistema as "APIs Bilhete Único/TOP"
rectangle Consulta {
    Usuário --> (Escolher entre TOP e bilhete único)
    Usuário --> (Ver saldo disponível)
    Usuário --> (Ver Cota remanescente)
    Sistema --> (Conectar APIs do Bilhete Único e TOP)
}
@enduml
