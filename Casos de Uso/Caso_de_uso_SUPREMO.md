```plantuml
@startuml
left to right direction

actor Usuário

package "Gestão de Saldo" {
    rectangle ConsultaRecarga {
        Usuário --> (Recargar Saldo)
        Usuário --> (Consultar Saldo)
        Usuário --> (Escolher entre TOP e bilhete único)
        Usuário --> (Inserir as informações necessárias)
        (Validar as informações de acesso) <<include>>
    }

    rectangle "Consulta de API" as ConsultaAPI {
        (Conectar APIs do Bilhete Único e TOP)
        (Conectar APIs de Bancos e Bilhete Único/TOP para pagamento)
    }
    
    ConsultaRecarga -[hidden]-> ConsultaAPI
}

package "Informações de Transporte" {
    rectangle AtualizaçãoLinhas {
        Usuário --> (Ver linhas disponíveis no momento)
        (Fornecer status das linhas em tempo real) <<include>>
    }

    rectangle MapaMetro {
        Usuário --> (Ver mapa completo das linhas ferroviárias)
        Usuário --> (Pesquisar por nome de estações)
        Usuário --> (Visualizar uma linha específica)
        Usuário --> (Baixar o mapa para uso offline)
        (Exibir o mapa completo do metrô) <<include>>
    }
}

package "Suporte e Feedback" {
    Usuário -- (Procurar sua dúvida pelo FAQ)
    Usuário -- (Reportar bugs do app)
    Usuário -- (Dar feedbacks e sugestões)
    
}
@enduml
