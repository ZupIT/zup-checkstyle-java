![Checkstyle](imgs/checkstyle.png)
 
 
 
 ### Tópicos - ZUP Checkstyle

:small_blue_diamond: [Descrição do projeto](#descrição-do-projeto)

:small_blue_diamond: [Introdução](#introdução)

:small_blue_diamond: [Arquivo de Checkstyle](#arquivo-de-checkstyle)

:small_blue_diamond: [Pré-requisitos](#pré-requisitos)

:small_blue_diamond: [Configurar seu projeto para usar Checkstyle](#configurar-seu-projeto-para-usar-Checkstyle)

:small_blue_diamond: [Checando seu projeto com maven](#Checando-seu-projeto-com-maven)

:small_blue_diamond: [Instalando e configurando o plugin CheckStyle-IDEA no IntelliJ](#Instalando-o-plugin-CheckStyle-IDEA-no-IntelliJ)

:small_blue_diamond: [Instalando e configurando o plugin CheckStyle no Eclipse](#Instalando-o-plugin-Checkstyle-no-Eclipse)

:small_blue_diamond: [Artigos relevantes](#Artigos-relevantes)

:small_blue_diamond: [Outros Checkstyles](#outros-checkstyles)

 
# Descrição do projeto
Este projeto tem como objetivo servir todos Devs da Zup a implementaremn boas práticas de convenção de código em projetos Java. 
O checkstyle é uma ferramenta que auxilia seu projeto a seguir uma convenção de código configurada por desenvolvedores. 
O objetivo é garantir a legibilidade e fácil leitura e manutenção do código.

<p align="center">

 ![Badge](https://img.shields.io/static/v1?label=java&message=checked&color=blue&style=flat-square&logo=java)
 
 ![Badge](https://img.shields.io/static/v1?label=codecoverage&message=100%&color=green&style=flat-square&logo=shell)
 
 ![Badge](http://img.shields.io/static/v1?label=STATUS&message=PRONTO%20PARA%20USO&color=RED&style=flat-square)
 
</p>


## Introdução
Checkstyle é um analisador estático de código para checar se o código fonte está de acordo com as regras de codificação. Esta ferramenta de código fonte aberto ajuda nas boas práticas de programação na qual melhora-se a qualidade do código, re-usabilidade, clareza, entre outros fatores. O Checkstyle se preocupa com a apresentação do código, portanto não analisa se a lógica do seu código está correta.

É possível verificar, por exemplo:

- Comentários Javadoc;
- Códigos duplicados;
- Número de Colunas (tamanho da linha);
- Cabeçalhos obrigatórios;
- Convenções nos nomes dos atributos e métodos;
- Limite no número de parâmetros;
- A utilização dos pacotes importados nas classes;
- Os espaços entre caracteres e entre operadores;
- Números mágicos;
- Boas práticas no desenvolvimento de classes e métodos;
- E muitos mais detalhes e padrões.

Portanto, pode-se verificar que o Checkstyle garante que o seu código atende a padrões e que há um bom nível de codificação.

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

- Este arquivo fornece a configuração padrão de estilo de códigos da Zup.


Segue exemplo de como ele pode ficar dentro do seu projeto.
 - lembrando que você pode criar um diretório exclusivo para armazenar o arquivo de checkstyle, contanto que esteja dentro do seu projeto.
 a localização exata dele será utilizada mais abaixo.
 
 ![Checkstyle Into your Project](imgs/checkstyle-into-project-1.png)



### Configurando pom.xml (Maven):

Neste exemplo, vamos explorar a configuração do checkstyle com *Maven*.

Busque em seu arquivo *pom.xml* o trecho 
```
<properties>
...
</properties>
```
É possível que seu projeto não contenha esta tag `<properties>`, neste caso você pode adicionar, ele deve ficar na raiz do *pom.xml*, no mesmo nível do 
seu `<artifactId>` que define o id do seu artefato (projeto java).
 
Dentro de `<properties>`, adicione a chave para indicar a versão do plugin checkstyle para maven.
 
`<checkstyle-maven-plugin.version>3.1.1</checkstyle-maven-plugin.version>`

Em nosso caso, será a versão 3.1.1.

Deverá ficar assim:
```
<properties>
    <checkstyle-maven-plugin.version>3.1.1</checkstyle-maven-plugin.version>
</properties>
```

Caso seu projeto já contenha outras configurações no `<properties>`, esta deverá ser mais uma delas.


Na sequência, procure pela área de `<build><plugins>` do seu *pom.xml* - Caso não exista, você pode criar esta na raiz do seu *pom.xml* e adicionar conforme exemplo abaixo (Já configurando o plugin do checkstyle):

```
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
```

#### Explicação do plugin checkstyle para maven:

Para quem é chegado no Maven, você pode notar que o plugin define um novo Goal (mojo) chamado de *<goal>check</goal>*, este goal vai ser executado durante a fase de validação do build do projeto, definido na tag *<phase>validate</phase>*, ou seja durante a validação, ele fará a checagem do código usando o arquiovo de checkstyle definido pela chave `<configLocation>checkstyle.xml</configLocation>`.
- Note que a chave *<configLocation>* aponta para o arquivo checkstyle.xml, que em nosso exemplo está na raiz do projeto, se estivesse em um diretório mais interno, devemos usar um caminho relativo (sem barras no inicio) para indicar onde o arquivo *checkstyle.xml* se encontra em nosso projeto.
 
Na sequencia do *<configLocation>* podemos ver outras tags importantes que informam o comportamento do plugin checkstyle ao analisar nosso código:

`<consoleOutput>true</consoleOutput>`
- Informa que ele deve imprimir no console o resultado da checagem.

`<failsOnError>false</failsOnError>`
- Informa que se caso de *Erros* durante a checagem de estilo, o plugin deve impedir o build do projeto até que o código seja ajustado.

`<failOnViolation>true</failOnViolation>`
- Informa que se caso de *Violações* de estilo, o plugin deve impedir o build do projeto até que o código seja ajustado.

`<violationSeverity>warning</violationSeverity>`
- Define qual o nível de severidade para *Violações* de estilo, e este nível define diretamente se a configuração da tag `<failOnViolation>true</failOnViolation>` impedirá ou não o build.
<a href="https://maven.apache.org/plugins/maven-checkstyle-plugin/check-mojo.html#violationSeverity"> Outros Níveis </a>


### Relátorios do Checkstyle

Na mesma linha do plugin maven, é possível configurar como a execução do plugin deve gerar relatórios no console ou na sua IDE.
Para isso, basta incluir na raiz do seu *pom.xml* a seguinte configuração, note que ela contém a maioria das tags também definidas no plugin do checkstyle maven para o build da aplicação.

```
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
 ````
Com isso, você está pronto para garantir que seu código sempre estará de acordo com a convenção de código adotada por nós Zuppers.


Para mais detalhes sobre o plugin maven, confira <a href="https://maven.apache.org/plugins/maven-checkstyle-plugin">aqui</a>


## Checando seu projeto com maven

Para rodar a checagem do seu projeto, basta usar este comando maven no shell/console:

```
# mvn checkstyle:check
```

- Feito isto... se projeto estiver 100% o relatório não trará nenhum resutado além da informação de sucesso.

- Em caso de violações do checkstyle por seu código, será exibido um relatório como este:

![Report](imgs/checkstyle-report-1.png)

Perceba que no relatório são apontados quais violações ocorrem, em que arquivos de código e em quais linhas elas ocorrem - facilitando muito a adaptação do seu código à convenção de estilo da Zup.


## Instalando o plugin CheckStyle-IDEA no IntelliJ

Podemos utilizar o plugin <a href="https://plugins.jetbrains.com/plugin/1065-checkstyle-idea">CheckStyle-IDEA</a> para auxiliar a formatação de código na IDE. Para configurar é muito simples, primeiro instale o plugin através do link acima ou no próprio IntelliJ
em **File -> Settings -> Plugins:**

![Report](imgs/checkstyle-ide-plugin-intellij.png)

### Configurando o plugin CheckStyle-IDEA

Após a instalação, precisamos importar as configurações definidas no arquivo checkstyle.xml dentro do plugin CheckStyle-IDEA. Navegue até **File -> Settings -> Tools -> Checkstyle** e em **Configuration File** clique em **Add** (sinal de **+** à direita), indique o caminho do seu
checkstyle.xml e clique em next.

![Report](imgs/checkstyle-ide-intellij-import-config.png)

Com o arquivo importado, **não se esqueça de deixar selecionado como Active**:

![Report](imgs/checkstyle-ide-intellij-config-file.png)

Agora vamos adicionar o mesmo arquivo de checkstyle nas configurações do próprio IntelliJ, assim 
quando utilizarmos os atalhos de formatação padrão ele automaticamente buscará Checkstyle Zup.
Dentro de settings, vá até **Editor -> Code Style -> Java** e importe o arquivo conforme imagem 
abaixo:

![Report](imgs/checkstyle-ide-intellij-import-config-code-style.png)

Finalizadas essas configurações, no rodapé do IntelliJ aparecerá a opção de CheckStyle e ao clicar 
a tela abaixo será apresentada. Neste ponto, em **Rules** selecione a que você importou nos passos 
anteriores e execute a verificação. O plugin indicará os problemas encontrados e aqueles relacionados a formatação de código poderão ser facilmente corrigidos com o bom e velho **CTRL + ALT + L** :)

![Report](imgs/checkstyle-ide-plugin-intellij-setting-rules.png)


## Instalando o plugin Checkstyle no Eclipse

Para instalar o plugin Checkstyle no Eclipse navegue até **Help -> Eclipse Marketplace**, na janela que 
abrir pesquise por **checkstyle** e instale o Checkstyle Plug-in abaixo:

![Report](imgs/checkstyle-ide-plugin-eclipse.png)

### Configurando o plugin CheckStyle

Feita a instalação vá até **Window -> Preferences** e pesquise por **Checkstyle**. Na janela que 
aparecer clique em **New**:

![Report](imgs/checkstyle-ide-plugin-eclipse-config.png)

Na janela de adição de novo Check Configuration na caixa suspensa **Type** selecione **External
Configuration File** e importe o XML do checkstyle. Dê um nome de sua preferência, clique em 
**Ok** e marque-o como default:

![Report](imgs/checkstyle-ide-eclipse-setcheck.png)

Novamente em **Window -> Preferences** pesquise por **Formatter** e acesse o resultado dentro
do tópico de Java. Nele crie um novo profile, pode ser baseado em qualquer uma das configurações
e clique em **Ok**.

![Report](imgs/checkstyle-ide-eclipse-formatter.png)

Feito isso clique em **Edit** para editar o profile que você acabou de criar, na caixa suspensa
**Tab Policy** deixe selecionada a opção **Spaces only**:

![Report](imgs/checkstyle-ide-eclipse-tab-policy.png)

Feito isso, reinicie o Eclipse. Após reiniciá-lo clique com o botão direito do mouse em um arquivo
Java e vá até a opção **Checkstyle -> Check Code with Checkstyle** e a verificação será feita e os 
pontos a serem corrigidos serão levantados:

![Report](imgs/checkstyle-ide-eclipse-check-code.png)

A partir deste ponto basta selecionar todo o código com **CTRL + A** e depois clicar com o botão
direito do mouse e selecionar a opção **Apply Checkstyle fixes**. O próprio plugin fará algumas 
correções conforme configurado. Para correções adicionais de formatação selecione novamente o código clique com o botão direito do mouse indo até **Source -> Format**. Aplicados os dois passos
de formatação acima execute novamente a verificação do arquivo com o **Checkstyle -> Check Code with Checkstyle** e observe que alguns tipos de correções relacionadas a formatação foram
realizadas:

![Report](imgs/checkstyle-ide-eclipse-after-check-code.png)

Pronto! Agora o código está formatado conforme as regras do checkstyle. Lembre-se que algumas
das modificações sugeridas pelo ``` # mvn checkstyle:check ``` devem ser feitas manualmente pois
os plugins ainda não conseguem atendê-las.


## Artigos relevantes

 - [Java com Checkstyle](https://www.devmedia.com.br/java-com-checkstyle/26043)
 - [How to Centralize your Checkstyle Configuration with Maven](https://codeburst.io/how-to-centralize-your-checkstyle-configuration-with-maven-7575eacd7295)



### Mais Checkstyles:
- https://github.com/spotify/spotify-checkstyle-config
- https://github.com/sevntu-checkstyle/sevntu.checkstyle
- https://github.com/singhalkul/java-quality-checks/blob/master/config/checkstyle/checkstyle.xml
- https://checkstyle.sourceforge.io/google_style.html
