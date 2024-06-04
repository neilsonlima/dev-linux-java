Para criar um projeto Spring Boot simples de "Hello World" usando apenas o terminal do Linux, você pode seguir os passos abaixo:

#### Passo 1. Instalação do SDKMAN e JDK

1. **Instalar o SDKMAN**:
   
   ```sh
   curl -s "https://get.sdkman.io" | bash
   source "$HOME/.sdkman/bin/sdkman-init.sh"
   ```

2. **Verificar a instalação do SDKMAN**:
   
   ```sh
   sdk version
   ```

3. **Listar as versões disponíveis do JDK**:
   
   ```sh
   sdk list java
   ```
      
4. **Instalar o JDK** (substitua `17.0.11-amzn` pela versão desejada):
   
   ```sh
   sdk install java 17.0.11-amzn
   ```

5. **Definir a versão instalada como padrão**:
   
   ```sh
   sdk default java 17.0.11-amzn
   ```
   
6. **Instalar o Spring Boot CLI**:
   
   ```sh
   sdk install springboot
   ```

#### Passo 2. Configuração da Variável de Ambiente JAVA_HOME

1. **Encontrar o caminho do JDK**:
   
   ```sh
   sdk env
   ```

2. **Definir a variável `JAVA_HOME`**:

   Edite o arquivo `~/.bashrc`:

   ```sh
   nano ~/.bashrc
   ```

   Adicione as seguintes linhas ao final do arquivo:

   ```sh
   export JAVA_HOME=$HOME/.sdkman/candidates/java/current
   export PATH=$JAVA_HOME/bin:$PATH
   ```

   Salve e feche o arquivo. Para aplicar as mudanças, execute:

   ```sh
   source ~/.bashrc
   ```

#### Passo 3. Criação e Execução do Projeto Spring Boot

1. **Criar o Projeto com Dependências**:

   ```sh
   spring init --build=gradle --dependencies=web,devtools,actuator my-hello-world
   cd my-hello-world
   ```

   Isso criará um novo diretório chamado `my-hello-world` com a estrutura básica de um projeto Spring Boot.

#### Passo 4. Editar o Código Fonte

1. **Abrir o arquivo `MyHelloWorldApplication.java`**:
   
   Use o editor de texto de sua preferência (como `nano`, `vim` ou `gedit`):

   ```sh
   nano src/main/java/com/example/demo/MyHelloWorldApplication.java
   ```

2. **Adicionar o código do controlador**:

   Adicione o seguinte código ao arquivo `MyHelloWorldApplication.java`:

   ```java
   package com.example.demo;

   import org.springframework.boot.SpringApplication;
   import org.springframework.boot.autoconfigure.SpringBootApplication;
   import org.springframework.web.bind.annotation.GetMapping;
   import org.springframework.web.bind.annotation.RestController;

   @SpringBootApplication
   public class MyHelloWorldApplication {

       public static void main(String[] args) {
           SpringApplication.run(MyHelloWorldApplication.class, args);
       }

       @RestController
       class HelloWorldController {
           @GetMapping("/")
           public String hello() {
               return "Hello, World!";
           }
       }
   }
   ```

2. **Compilar o Projeto**:

   ```sh
   ./gradlew build
   ```

3. **Executar o Projeto**:

   ```sh
   ./gradlew bootRun
   ```

#### 5. Testar a Aplicação

Abra o navegador ou use `curl` para acessar a aplicação:

```sh
curl http://localhost:8080/
```

Você deverá ver a mensagem "Hello, World!" retornada pelo seu aplicativo Spring Boot.

#### Passo 6. Estrutura Final do Projeto

A estrutura final do projeto deve ser semelhante a esta:

```
my-hello-world
├── mvnw
├── mvnw.cmd
├── pom.xml
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com
│   │   │       └── example
│   │   │           └── demo
│   │   │               └── MyHelloWorldApplication.java
│   │   └── resources
│   │       └── application.properties
│   └── test
│       ├── java
│       └── resources
└── target
```
Seguindo este roteiro, você terá o Java instalado corretamente usando o SDKMAN, configurará a variável de ambiente `JAVA_HOME` e criará e executará um projeto Spring Boot usando Gradle no Ubuntu.
