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
