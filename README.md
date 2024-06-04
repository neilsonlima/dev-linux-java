Para criar um projeto Spring Boot simples de "Hello World" usando apenas o terminal do Linux, você pode seguir os passos abaixo:

### Passo 1: Instalar o SDKMAN e o Spring Boot CLI

1. **Instalar o SDKMAN**:
   O SDKMAN é uma ferramenta para gerenciar versões do Java e outras ferramentas de desenvolvimento.
   
   ```sh
   curl -s "https://get.sdkman.io" | bash
   source "$HOME/.sdkman/bin/sdkman-init.sh"
   ```

2. **Instalar o Spring Boot CLI**:
   
   ```sh
   sdk install springboot
   ```

### Passo 2: Criar o Projeto Spring Boot

1. **Criar a estrutura básica do projeto**:
   
   ```sh
   spring init --dependencies=web my-hello-world
   cd my-hello-world
   ```

   Isso criará um novo diretório chamado `my-hello-world` com a estrutura básica de um projeto Spring Boot.

### Passo 3: Editar o Código Fonte

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

### Passo 4: Compilar e Executar o Projeto

1. **Compilar o projeto**:
   
   O projeto criado pelo Spring Boot CLI já vem configurado com o Maven Wrapper, então você pode usar o comando abaixo para compilar:

   ```sh
   ./mvnw clean install
   ```

2. **Executar o projeto**:
   
   Após a compilação, você pode executar o aplicativo:

   ```sh
   ./mvnw spring-boot:run
   ```

### Passo 5: Testar a Aplicação

Abra o navegador ou use `curl` para acessar a aplicação:

```sh
curl http://localhost:8080/
```

Você deverá ver a mensagem "Hello, World!" retornada pelo seu aplicativo Spring Boot.

### Passo 6: Estrutura Final do Projeto

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

Seguindo esses passos, você terá criado um projeto Spring Boot simples de "Hello World" usando apenas o terminal do Linux.
