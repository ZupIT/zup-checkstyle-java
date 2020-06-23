Nota do Projeto
================================
Este projeto visa ser um manual vivo, iterativo, e em constante construção por todos os Zuppers.
Portanto, contribua! Deixe suas idéias e defenda o que deve ser levado em conta como padrão de códificação.


Visão geral do Checkstyle
================================

O Checkstyle é uma ferramenta de desenvolvimento que ajuda nós =programadores a escrever código Java(e outras linguagens) de forma aderente a um padrão de codificação.
As seguintes linhas são citadas no site oficial do Checkstyle :

- O Checkstyle é uma ferramenta de desenvolvimento para ajudar os programadores a escrever código Java que segue um padrão de codificação.

Ele automatiza o processo de verificação do código Java para poupar os humanos desta tarefa chata (mas importante). 
Isso o torna ideal para projetos que desejam aplicar um padrão de codificação.
Além disso, o Checkstyle pode ser usado para verificar muitos aspectos do seu código-fonte, como problemas no design de classes e métodos e no formato de layout. Para mais detalhes sobre as verificações, consulte a seção Verificações do site [https://maven.apache.org/plugins/maven-checkstyle-plugin/]

O estilo de verificação pode ser personalizado com vários parâmetros. 
Se você já possui um padrão de codificação existente, pode definir regras adequadas para o Checkstyle. Se você ainda não aplicou um estilo de codificação específico ao seu projeto, poderá usar os arquivos de configuração para verificar os padrões de codificação convencionais, como “Sun Java Code Conventions” e “Google Java Style”, que são utilizáveis ​​por padrão. 

Ao fazer isso, você pode incorporar um padrão de codificação no fluxo de trabalho do seu projeto com facilidade.
No Checkstyle, você usa um arquivo XML para descrever as regras. As verificações que seguem as regras descritas são fornecidas por comandos java e tarefas ant por padrão, mas são mais comumente usadas em projetos reais, incorporando no ambiente de desenvolvimento integrado (IDE) ou na ferramenta de construção.

Para incorporar o Checkstyle nos IDEs, você pode usar plug-ins fornecidos para vários IDEs. Com essas opções, você pode 
executar verificações em tempo real enquanto escreve o código-fonte.

Se você deseja incorporar o Checkstyle nas ferramentas de construção, use maven e gradle. Ambos são ferramentas de construção usadas com frequência e fornecem uma tarefa para o Checkstyle por padrão, que pode ser usada para facilitar a integração. Ao incorporar nas ferramentas de construção, você pode verificar se o código-fonte de um projeto está sempre em conformidade com o padrão de codificação.

No entanto, a integração em uma ferramenta de construção cria uma restrição muito forte: mesmo um pequeno problema impede que o código seja mesclado. Pode ser melhor usar serviços da Web dedicados a essa causa, como o SideCI, para projetos existentes com o Checkstyle ainda não implementado ou quando um padrão de codificação não é imposto de maneira tão estrita.
Como é possível verificar com um processo IDE e um IC (ferramenta de construção ou SideCI) usando um único arquivo XML, recomendamos que você incorpore os dois métodos de verificação em um projeto.


Configuração de Uso do Zup Checkstyle
================================


Este projeto fornece uma configuração padrão para o estilo de verificação de códigos da Zup.

Para usá-lo, configure seu maven-checkstyle-plugin da seguinte maneira:

````
   <plugin>
     <artifactId> projeto-zup-plugin </artifactId>
     <versão> 1.0.0 </ versão>
     <dependências>
       <dependência>
         <groupId> br.zup.com.projeto.plugin </groupId>
         <artifactId> projeto-zup-plugin </artifactId>
         <versão> 1.0.0 </version>
       </dependency>
       <dependência>
         <groupId> com.puppycrawl.tools </groupId>
         <artifactId> checkstyle </artifactId>
         <versão> 8.24 </ versão>
       </dependency>
     </dependencies>
     <configuração>
       <configLocation> zup_checks.xml </configLocation>
       
       <! - Os seguintes parâmetros são opcionais: ->
       <consoleOutput> true </consoleOutput>
       <failOnViolation> true </failOnViolation>
       <logViolationsToConsole> true </logViolationsToConsole>
       erro <violationSeverity> </violationSeverity>
     </configuration>
     <execuções>
       <execução>
         <id>validate</id>
         <phase>validate</phase>
         <objetivos>
           <goal>check</goal>
         </goals>
       </execution>
     </executions>
   </plugin>
````

Consulte os [documentos do maven-checkstyle-plugin] (https://maven.apache.org/plugins/maven-checkstyle-plugin/check-mojo.html) 
para obter mais informações sobre o significado dos parâmetros de configuração.

Internamente, temos a configuração acima na seção `<pluginManagement />` de um 
pom principal da Zup, o que significa que os projetos precisam apenas especificar o seguinte em seus
Seção `<build> <plugins>`:

`` ``
   <plugin>
      <artifactId> maven-checkstyle-plugin </artifactId>
   </plugin>
`` ``

# Configuração

## Supressões

A configuração do plugin checkstyle que você obtém de `zup_checks.xml` diz para 
opcionalmente, procure um arquivo chamado `suppressions.xml`, conforme
[Documentos do SuppressionFilter] (http://checkstyle.sourceforge.net/config_filters.html#SuppressionFilter). 
Isso significa que você pode configurar supressões fornecendo esse arquivo no seu
caminho de classe do projeto ou no diretório atual em que você o constrói - note 
para projetos com vários módulos, provavelmente é uma boa ideia usar algo
como [esta solução] (http://stackoverflow.com/a/19690484/1659929) para compartilhar
a configuração entre cada submódulo.

# IDEA support

Há um [arquivo de configuração para o IntelliJ IDEA] (src/main/resources/zup_checks.xml) que você pode importar para o seu projeto.

# Código de conduta
Este projeto segue o [Código de Conduta Aberto] [código de conduta]. Ao participar, espera-se que você respeite esse código.

[código de conduta]: https://github.com/klyff/zup-code-of-conduct/blob/master/code-of-conduct.md
