```plantuml
@startuml
left to right direction
actor Usuário
actor Sistema
rectangle Ajuda {
Usuário -- (Procurar sua dúvida pelo FAQ)
Usuário -- (Reportar bugs do app)
Usuário -- (Dar feedbacks e sugestões)
(I.A responsável por guiar o usuário para \nsolução do seu problema) -- Sistema
(Redirecionar o usuário de forma segura) -- Sistema
}
@enduml
´´´