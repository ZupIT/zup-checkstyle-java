![Checkstyle](imgs/checkstyle.png)
# ZUP JAVA CHECKSTYLE
Este repositório tem como objetivo servir todos Devs Java da Zup a implementar boas práticas de convenção de código em projetos Java. O checkstyle é uma ferramenta que auxilia seu projeto a seguir uma convenção de código configurada por desenvolvedores. O objetivo é garantir a legibilidade do código

## Introdução
Checkstyle é um analisador estático de código para checar se o código fonte está de acordo com as regras de codificação. Esta ferramenta de código fonte aberto ajuda nas boas práticas de programação na qual melhora-se a qualidade do código, re-usabilidade, clareza, entre outros fatores. O Checkstyle se preocupa com a apresentação do código, portanto não analisa se a lógica do seu código está correta.

É possível verificar, por exemplo:

Comentários Javadoc;
Cabeçalhos obrigatórios;
Convenções nos nomes dos atributos e métodos;
Limite no número de parâmetros;
A utilização dos pacotes importados nas classes;
Os espaços entre caracteres;
Boas práticas no desenvolvimento de classes;
Código duplicado;
E muitos mais.
Portanto, pode-se verificar que o Checkstyle garante que o seu código atende a padrões e garante que há um bom nível de codificação.

![Checkstyle](imgs/todo-checkstyle.gif)


## Status do Projeto

Neste projeto foram criados inicialmente um arquivo de checkstyle:
- /src/main/resources/checkstyle.xml


O checkstyle.xml faz uma analise de estilo básica mas que já visa qualidade de escrita.
 São verificados itens como quantidade de colunas/caracteres por linha (180),
 espaços entre valores e operadores, Quebra de linha após abertura de bloco {} e estrutura, definição de constantes, blocos vazios, estilo de declaração de listas e arrays, declaração de variaveis multiplas e ordem de modificadores, e faz uma tratativa melhorada sobre os magicnumbers deixando-os mais flexiveis.
 
 

## Configuração de Uso do Zup Checkstyle

Copie este arquivo para dentro do seu projeto:
https://github.com/ZupIT/zup-checkstyle-java/blob/master/src/main/resources/checkstyle.xml

- Este arquivo fornece uma configuração padrão para o estilo de verificação de códigos da Zup.

Para usá-lo, configure seu POM.XML o maven-checkstyle-plugin da seguinte maneira:

````
 <artifactId>projeto-zup-plugin</artifactId>
 <version>0.1.0-SNAPSHOT</version>
 ...
 <properties>
     <java.version>14</java.version>
     <checkstyle-maven-plugin.version>3.1.1</checkstyle-maven-plugin.version>
 </properties>

   <reporting>
      <plugins>
          <plugin>
              <groupId>org.apache.maven.plugins</groupId>
              <artifactId>maven-checkstyle-plugin</artifactId>
              <version>3.1.1</version>
              <configuration>
                  <configLocation>${project.basedir}/checkstyle.xml</configLocation>
                  <encoding>UTF-8</encoding>
                  <consoleOutput>true</consoleOutput>
                  <failsOnError>true</failsOnError>
                  <linkXRef>true</linkXRef>
                  <failOnViolation>true</failOnViolation>
                  <enableFilesSummary>true</enableFilesSummary>
              </configuration>
          </plugin>
      </plugins>
  </reporting>
     
 <build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-checkstyle-plugin</artifactId>
            <version>${checkstyle-maven-plugin.version}</version>
            <executions>
                <execution>
                    <id>validate</id>
                    <phase>validate</phase>
                    <configuration>
                        <configLocation>checkstyle.xml</configLocation>
                        <encoding>UTF-8</encoding>
                        <consoleOutput>true</consoleOutput>
                        <failsOnError>false</failsOnError>
                        <failOnViolation>true</failOnViolation>
                        <violationSeverity>warning</violationSeverity>
                    </configuration>
                    <goals>
                        <goal>check</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
````

Consulte os [documentos do maven-checkstyle-plugin] (https://maven.apache.org/plugins/maven-checkstyle-plugin/check-mojo.html) 
para obter mais informações sobre o significado dos parâmetros de configuração.

Internamente, temos a configuração acima na seção `<pluginManagement />` de um 
pom principal da Zup, o que significa que os projetos precisam apenas especificar o seguinte em seus
Seção `<build> <plugins>`:

````
   <plugin>
      <artifactId> maven-checkstyle-plugin </artifactId>
   </plugin>
````

## Configuração

### Supressões

A configuração do plugin checkstyle que você obtém de `zup_checks.xml` diz para 
opcionalmente, procure um arquivo chamado `suppressions.xml`, conforme
[Documentos do SuppressionFilter] (http://checkstyle.sourceforge.net/config_filters.html#SuppressionFilter). 
Isso significa que você pode configurar supressões fornecendo esse arquivo no seu
caminho de classe do projeto ou no diretório atual em que você o constrói - note 
para projetos com vários módulos, provavelmente é uma boa ideia usar algo
como [esta solução] (http://stackoverflow.com/a/19690484/1659929) para compartilhar
a configuração entre cada submódulo.


# Código de conduta
Este projeto segue o [Código de Conduta Aberto] [código de conduta]. Ao participar, espera-se que você respeite esse código.

[código de conduta]: https://github.com/klyff/zup-code-of-conduct/blob/master/code-of-conduct.md

## Artigos relevantes

 - [Java com Checkstyle](https://www.devmedia.com.br/java-com-checkstyle/26043)
 - [How to Centralize your Checkstyle Configuration with Maven](https://codeburst.io/how-to-centralize-your-checkstyle-configuration-with-maven-7575eacd7295)


### Mais Checkstyles:
- https://github.com/singhalkul/java-quality-checks/blob/master/config/checkstyle/checkstyle.xml
