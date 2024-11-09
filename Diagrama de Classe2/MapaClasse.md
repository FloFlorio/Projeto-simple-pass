```plantuml
@startUML

class Usuario {
    - id: String
    - pesquisa: String
}

class Mapa {
    - Mapa
    + mostrarMapa():
}

class Sistema {
    - dadosMapa
    + verificarAPI():
    + validaLocalizacao()
    + consultaCaminho()
}

class Caminho {
    - distancia: float
    - estacoes: List<Estacao>
    - duracao: int
    + consultaCaminhoPorNome()
    + consultaCaminhoPorMapa()
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