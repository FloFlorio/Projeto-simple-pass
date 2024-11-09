```plantuml
@startUML

class Usuario {
    - id: String
    - pesquisa: String
}

class Mapa {
    - Mapa
}

class Sistema {
    - dadosMapa
}

class Caminho {
    - distancia: float
    - estacoes: List<Estacao>
    - duracao: int
}

class Estações {
    - nome: String
    - local: String
    - descrição: String
}

class Aplicativo {
}

Usuario --> Aplicativo : "interage"
Aplicativo --> Sistema : "verifica"
Aplicativo --> Mapa : "exibe"
Mapa --> Sistema : "obtém dados"
Mapa --> Caminho : "encontra"
Caminho --> Estações : "contém"

@endUMLs