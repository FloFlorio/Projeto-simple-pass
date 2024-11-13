```plantuml
@startuml
skinparam class {
    BackgroundColor #F4F4F4
    BorderColor #2E86C1
    ArrowColor #117A65
}

class Usuario {
    + visualizarStatusLinhas()
    + mostrarFeedback()
    + comprarPassagem()
    + consultaCartao()
    + selecionarAba()
}

class InterfaceUsuario {
    + exibirConteudo()
    + mostrarMapa()
    + exibirStatusLinhas()
}

class Aplicativo {
    + iniciar()
    + finalizar()
}

class ControladorDeAplicativo {
    + processarConsulta()
    + atualizarInformacoes()
    + processarRecarga()
}

class Sistema {
    + verificarAPI()
    + validaLocalizacao()
}

class ProcessadorDePagamento {
    + requisitarPagamento()
    + requisitarLiquidacao()
}

class GerenciadorDeDados {
    + atualizarDados()
    + processarFeedback()
}

class Mapa {
    + consultaCaminho()
}

class Caminho {
    + consultaCaminhoPorNome()
    + consultaCaminhoPorMapa()
}

Usuario --> InterfaceUsuario : interage
InterfaceUsuario --> Aplicativo : usa para iniciar e finalizar
Aplicativo --> ControladorDeAplicativo : delega operações
ControladorDeAplicativo --> Sistema : coordena dados
ControladorDeAplicativo --> GerenciadorDeDados : acessa dados
ControladorDeAplicativo --> ProcessadorDePagamento : realiza pagamento
ControladorDeAplicativo --> Mapa : consulta rota

@enduml
