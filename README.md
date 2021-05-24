## Introdução ao Apache Velocity

# 1. Visão Geral
Velocity é um mecanismo de modelagem baseado em Java.

É uma estrutura da web de código aberto projetada para ser usada como um componente de visualização na arquitetura MVC e fornece uma alternativa para algumas tecnologias existentes, como JSP.

O Velocity pode ser usado para gerar arquivos XML, SQL, PostScript e muitos outros formatos baseados em texto.

Neste artigo, exploraremos como ele pode ser usado para criar páginas da web dinâmicas.

# 2. Como funciona a velocidade
A classe principal do Velocity é o VelocityEngine.

Ele orquestra todo o processo de leitura, análise e geração de conteúdo usando modelo de dados e modelo de velocidade.

Simplificando, aqui estão as etapas que precisamos seguir para qualquer aplicação típica de velocidade:

- Inicialize o motor de velocidade;
- Leia o template;
- Coloque o modelo de dados no objeto de contexto;
- Mesclar o modelo com os dados do contexto e renderizar a visualização.

Vejamos um exemplo seguindo estas etapas simples:

```
VelocityEngine velocityEngine = new VelocityEngine();
velocityEngine.init();
   
Template t = velocityEngine.getTemplate("index.vm");
    
VelocityContext context = new VelocityContext();
context.put("name", "World");
    
StringWriter writer = new StringWriter();
t.merge( context, writer );
```

# 3. Dependências Maven
Para trabalhar com o Velocity, precisamos adicionar as seguintes dependências ao nosso projeto Maven:

```
<dependency>
    <groupId>org.apache.velocity</groupId>
    <artifactId>velocity</artifactId>
    <version>1.7</version>
    </dependency>
<dependency>
     <groupId>org.apache.velocity</groupId>
     <artifactId>velocity-tools</artifactId>
     <version>2.0</version>
</dependency>
```

A versão mais recente de ambas as dependências pode estar aqui: ferramentas de velocidade e velocidade.

# 4. Linguagem do modelo de velocidade
Velocity Template Language (VTL) fornece a maneira mais simples e limpa de incorporar o conteúdo dinâmico em uma página da web usando referências VTL.

A referência VTL no modelo de velocidade começa com $ e é usada para obter o valor associado a essa referência. A VTL também fornece um conjunto de diretivas que podem ser usadas para manipular a saída do código Java. Essas diretivas começam com #.

### 4.1. Referências
Existem três tipos de referências em velocidade, variáveis, propriedades e métodos:

- variáveis - definidas na página usando a diretiva #set ou valor retornado do campo do objeto Java:

```
#set ($message="Hello World")
```

- propriedades - referem-se a campos dentro de um objeto; eles também podem se referir a um método getter da propriedade:

```
$customer.name
```

- métodos - referem-se ao método no objeto Java:

```
$customer.getName()
```

O valor final resultante de cada referência é convertido em uma string quando ele é processado na saída final.

### 4.2. Diretivas
A VTL fornece um rico conjunto de diretivas:

set - pode ser usado para definir o valor de uma referência; este valor pode ser atribuído a uma variável ou referência de propriedade:

```
#set ($message = "Hello World")
#set ($customer.name = "Brian Mcdonald")
```
- condicionais - as diretivas #if, #elseif e #else fornecem uma maneira de gerar o conteúdo com base em verificações condicionais:

```
#if($employee.designation == "Manager")
    <h3> Manager </h3>
#elseif($employee.designation == "Senior Developer")
    <h3> Senior Software Engineer </h3>
#else
    <h3> Trainee </h3>
#end
```

