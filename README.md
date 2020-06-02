# Guias de Estilo - Yellow Panda Games

<img src="ypg-logo.png" alt="" width="200"/>

Para cada linguagem de programação a qual a Yellow Panda faz uso em seus projetos, 
estarão listadas aqui seus respectivos guias de estilos.

No caso de linguagens utilizadas em nossos projetos as quais não estejam aqui 
descritas, devem ser utilizados as convenções mais amplamente aceitas por suas
respectivas comunidades.

No índice abaixo você poderá encontrar todos os guias de estilos os quais a Yellow Panda
utiliza em seus projetos assim como seu respectivos arquivos .editorconfig.

- [O que é um guia de estilo](#faq-guias)
- [O que é um .editorConfig](#faq-editorconfig)

# Índice

- C Sharp (C#)
    - [Guia de Estilo](c-sharp/README.md)
    - [.editorConfig](c-sharp/.editorconfig)

- C++
    - [Guia de Estilo]()
    - [.editorConfig]()

- JavaScript
    - [Guia de Estilo]()
    - [.editorConfig]()

# FAQ

## Guias de estilo <a id="faq-guias"></a>

Muitas empresas ou projetos possuem um guia de estilo (style guide): uma série de 
convenções (às vezes arbitrárias) sobre como estilizar código. Fica bem mais fácil 
de entender uma base de código quando todo o seu código está formatado em um estilo 
consistente.

“Estilo” abrange muitos assuntos, desde “usar camelCase para nome de variáveis”
a “nunca utilize variáveis globais” ou “nunca utilize exceções”.
###### Traduzido e modificado de http://google.github.io/styleguide/. ######

## Arquivos “.editorconfig” <a id="faq-editorconfig"></a>

O projeto EditorConfig consiste de um formato/extensão de arquivo (.editorconfig) para definir estilos de código e uma coleção de plugins para editores de texto os quais permitem eles lerem este formato de arquivo.

### Como funcionam?

Ao abrir um arquivo, a IDE ou um plugin EditorConfig procura por um arquivo nomeado .editorconfig no diretório do arquivo aberto e também em seus diretórios pais. A procura pelo arquivo .editorconfig para quando o diretório raiz do projeto é alcançado ou quando um arquivo .editorconfig com a flag “root=true” é encontrado.
###### Traduzido e modificado de http://editorconfig.org. ######

### Onde colocar estes arquivos?

Em projetos Unity por exemplo os arquivos .editorconfig geralmente são encontrados na raiz do projeto. Porém podem ser colocados em qualquer diretório do projeto.

### Como utilizar?

IDEs como Rider e Visual Studio possuem suporte nativo para arquivos .editorconfig. Já alguns editores como VS Code e Sublime Text necessitam de plugins.

Com a IDE e/ou plugin instalados o usuário pode configurar para que seu editor de texto formata automaticamente os arquivos ou somente lhe avise quando alguma parte do código não esteja de acordo com o arquivo .editorconfig.