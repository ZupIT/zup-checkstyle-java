![Checkstyle](imgs/checkstyle.png)
 
 
 ### Tópicos - ZUP Checkstyle

:small_blue_diamond: [Descrição do projeto](#descrição-do-projeto)

:small_blue_diamond: [Introdução](#introdução)

:small_blue_diamond: [Arquivo de Checkstyle](#arquivo-de-checkstyle)

:small_blue_diamond: [Pré-requisitos](#pré-requisitos)

:small_blue_diamond: [Configurar seu projeto para usar Checkstyle](#configurar-seu-projeto-para-usar-Checkstyle)

:small_blue_diamond: [Checando seu projeto com maven](#Checando-seu-projeto-com-maven)

:small_blue_diamond: [Artigos relevantes](#Artigos-relevantes)

:small_blue_diamond: [Outros Checkstyles](#outros-checkstyles)

 
# Descrição do projeto
Este projeto tem como objetivo servir todos Devs da Zup a implementaremn boas práticas de convenção de código em projetos Java. 
O checkstyle é uma ferramenta que auxilia seu projeto a seguir uma convenção de código configurada por desenvolvedores. 
O objetivo é garantir a legibilidade e fácil leitura e manutenção do código.

<p align="center">
 ![Badge](https://img.shields.io/static/v1?label=java&message=checked&color=blue&style=flat-square&logo=java)
 ![Badge](https://img.shields.io/static/v1?label=codecoverage&message=100%&color=green&style=flat-square&logo=shell)
 ![Badge](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=RED&style=flat-square)
</p>

## Introdução
Checkstyle é um analisador estático de código para checar se o código fonte está de acordo com as regras de codificação. Esta ferramenta de código fonte aberto ajuda nas boas práticas de programação na qual melhora-se a qualidade do código, re-usabilidade, clareza, entre outros fatores. O Checkstyle se preocupa com a apresentação do código, portanto não analisa se a lógica do seu código está correta.

É possível verificar, por exemplo:

- Comentários Javadoc;
- Cabeçalhos obrigatórios;
- Convenções nos nomes dos atributos e métodos;
- Limite no número de parâmetros;
- A utilização dos pacotes importados nas classes;
- Os espaços entre caracteres;
- Boas práticas no desenvolvimento de classes;
- Código duplicado;
- E muitos mais detalhes e padrões.

Portanto, pode-se verificar que o Checkstyle garante que o seu código atende a padrões e garante que há um bom nível de codificação.

![Todo](imgs/todo-checkstyle.gif)


## Arquivo de Checkstyle

<a href="https://github.com/ZupIT/zup-checkstyle-java/blob/master/src/main/resources/checkstyle.xml">
/src/main/resources/checkstyle.xml
</a>


- Este é o arquivo que você fará download para seu projeto. Nos próximos tópicos abordaremos como configurar o checkstyle em seu projeto Java.
 
## Pré-requisitos

- Java 8+
- Maven 3+
- Um Projeto Java :smile:


## Configurar seu projeto para usar Checkstyle


Copie este arquivo para dentro do seu projeto:
https://github.com/ZupIT/zup-checkstyle-java/blob/master/src/main/resources/checkstyle.xml

Segue exemplo de como ele pode ficar dentro do seu projeto.
 - lembrando que voce pode criar um diretório exclusivo para armazenar o arquivo de checkstyle, contanto que esteja dentro do seu projeto.
 a localização exata dele será utilizada mais abaixo.
 
 ![Checkstyle Into your Project](imgs/checkstyle-into-project-1.png)


- Este arquivo fornece uma configuração padrão para o estilo de verificação de códigos da Zup.

Para usá-lo, configure seu POM.XML o maven-checkstyle-plugin da seguinte maneira:


## Checando seu projeto com maven



## Artigos relevantes

 - [Java com Checkstyle](https://www.devmedia.com.br/java-com-checkstyle/26043)
 - [How to Centralize your Checkstyle Configuration with Maven](https://codeburst.io/how-to-centralize-your-checkstyle-configuration-with-maven-7575eacd7295)


### Mais Checkstyles:
- https://github.com/singhalkul/java-quality-checks/blob/master/config/checkstyle/checkstyle.xml
