![Checkstyle](imgs/checkstyle.png)
 
 
# ZUP CHECKSTYLE JAVA
Este repositório tem como objetivo servir todos Devs da Zup a implementaremn boas práticas de convenção de código em projetos Java. 
O checkstyle é uma ferramenta que auxilia seu projeto a seguir uma convenção de código configurada por desenvolvedores. 
O objetivo é garantir a legibilidade e fácil leitura e manutenção do código.

![Badge](https://img.shields.io/static/v1?label=java&message=checked&color=blue&style=flat-square&logo=java)
![Badge](https://img.shields.io/static/v1?label=codecoverage&message=100%&color=green&style=flat-square&logo=shell)


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


## Arquivo padrão do Zup Checkstyle
- /src/main/resources/checkstyle.xml

Este é o arquivo que você fará download para seu projeto. Nos próximos tópicos abordaremos como configurar o checkstyle em seu projeto Java.
 
 

## Configuração de Uso do Zup Checkstyle

Copie este arquivo para dentro do seu projeto:
https://github.com/ZupIT/zup-checkstyle-java/blob/master/src/main/resources/checkstyle.xml

- Este arquivo fornece uma configuração padrão para o estilo de verificação de códigos da Zup.

Para usá-lo, configure seu POM.XML o maven-checkstyle-plugin da seguinte maneira:



# Código de conduta
Este projeto segue o [Código de Conduta Aberto] [código de conduta]. Ao participar, espera-se que você respeite esse código.

[código de conduta]: https://github.com/klyff/zup-code-of-conduct/blob/master/code-of-conduct.md

## Artigos relevantes

 - [Java com Checkstyle](https://www.devmedia.com.br/java-com-checkstyle/26043)
 - [How to Centralize your Checkstyle Configuration with Maven](https://codeburst.io/how-to-centralize-your-checkstyle-configuration-with-maven-7575eacd7295)


### Mais Checkstyles:
- https://github.com/singhalkul/java-quality-checks/blob/master/config/checkstyle/checkstyle.xml
