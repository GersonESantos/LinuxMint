---
title: "Infraestrutura como Código: Introdução ao Terraform"
curso: DevOps e Automação de Infraestrutura
author: Gemini AI
data_estudo: 2026-03-03
linguagem:
  - HCL (HashiCorp Configuration Language)
tecnologias:
  - Terraform
  - AWS/Azure/GCP
  - Docker
assuntos:
  - Infrastructure as Code (IaC)
  - Provisionamento de Recursos
  - Gerenciamento de Estado
status: 🔴 Inicio
tags:
  - terraform
  - devops
  - iaac
  - cloud
---



![[Pasted image 20260303180234.png]]
#  O que é Terraform?🏗️



O Terraform é uma ferramenta de infraestrutura como código que permite criar, alterar e versionar recursos na nuvem e locais de forma segura e eficiente.


#### terraform [Link ](https://developer.hashicorp.com/terraform/intro)
#### [Git ]()
#### [YOUTUBE ]()
#### [GitHub Desktop ]()


**Conceito Principal:** O Terraform é uma ferramenta de **Infraestrutura como Código (IaC)** criada pela HashiCorp. Ele permite que você defina, por meio de arquivos de configuração, toda a sua infraestrutura (servidores, bancos de dados, redes) em vez de criá-los manualmente clicando em portais.

## Conteúdo da Aula

- **Infraestrutura como Código (IaC) [O Coração do Terraform]:** Em vez de você instalar o SQL Server manualmente no seu Nasinha-I5, você escreve um arquivo de texto dizendo "eu quero um SQL Server com X de memória". O Terraform lê esse arquivo e cria tudo para você.
- **Como ele funciona (Fluxo de Trabalho):**
    1. **Write (Escrever):** Você escreve arquivos `.tf` usando a linguagem HCL.
    2. **Plan (Planejar):** O Terraform mostra o que ele vai criar antes de realmente fazer (comando `terraform plan`).
    3. **Apply (Aplicar):** Ele cria a infraestrutura no provedor escolhido (`terraform apply`).
- **Principais Características:**
    - **Declarativo:** Você diz *o que* quer (ex: "quero 2 servidores"), e o Terraform descobre *como* fazer.
    - **Multi-Cloud:** Funciona com Azure (da Microsoft), AWS, Google Cloud e até com Docker local.
    - **State File:** Ele guarda um "arquivo de estado" para saber exatamente o que já foi criado e o que mudou.
- **Por que é importante para DevOps?**
    - **Reprodutibilidade:** Você pode destruir seu ambiente no Linux e recriá-lo em segundos com o mesmo comando.
    - **Versionamento:** Como a infraestrutura é código, ela vai para o seu **GitHub** (`GersonESantos`).

## Performance/Conclusão

O Terraform transforma o trabalho de um administrador de sistemas em um trabalho de desenvolvedor. Para o seu cenário, imagine poder configurar todo o seu ambiente de banco de dados e pastas do OneDrive no Linux apenas rodando um script. É a ferramenta essencial para quem quer trabalhar com Nuvem (Cloud) e automação em escala profissional.

[[Terraform em 10 Minutos]]