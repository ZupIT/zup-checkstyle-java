# Instruções de implantação
Essas instruções são baseadas nas instruções para implantar no Repositório Central usando o Maven . Observe que isso é apenas para uso interno do Zup.

Depois de implementá-lo, você poderá implantar usando os seguintes comandos:

```
# deploy snapshot version
mvn clean deploy # -Prelease to test signing

# make and deploy a release
mvn release:clean release:prepare -Prelease
mvn release:perform -Prelease
```

