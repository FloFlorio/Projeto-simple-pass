```plantuml
@startUML

class Usuario {
    - id: String
    + pesquisarEstacao(nome: String): void
    + escolherLocalidade(localidade: String): void
    + verHistoricoDePesquisas(): List<String>
}

class Mapa {
    + mostrarMapa(): void
    + buscarCaminho(origem: String, destino: String): List<Caminho>
}

class Sistema {
    + verificarAPI(): boolean
    + obterDadosMapa(): Mapa
}

class Caminho {
    - distancia: float
    - estacoes: List<Estacao>
    - duracao: int
}

class Estações {
    - nome: String
    - local: String
    + getEstacao(): String
    + getCaminho(): String
}
/' local possui o nome da rua, numero e as coordenadas do lugar '/

class Aplicativo {
    + iniciar(): void
    + mostrarMapa(map: Mapa): void
}

Usuario --> Aplicativo : "interage"
Aplicativo --> Sistema : "verifica"
Aplicativo --> Mapa : "exibe"
Mapa --> Sistema : "obtém dados"
Mapa --> Caminho : "encontra"
Caminho --> Estações : "contém"

@endUML
