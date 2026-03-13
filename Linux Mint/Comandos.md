No Linux Mint, existem várias formas de ver a configuração da sua máquina, desde um resumo visual bonito até detalhes técnicos profundos. Como você está no **Nasinha-I5**, aqui estão as melhores opções:

## tldr.sh/ [Link ](https://tldr.sh/)
## [[linux_devops_guide_marialazara.pdf]]

## 1. O Jeito "Visual" (Neofetch)

O Linux Mint geralmente já vem com o `neofetch` ou permite instalar rápido. Ele mostra o logo do Mint e um resumo (CPU, GPU, Memória, Kernel) direto no terminal.

- **Comando:**
    
    Bash
    
    ```
    neofetch
    ```
    
- _Se não estiver instalado:_ `sudo apt install neofetch`
    

---

## 2. Informações do Sistema (Modo Gráfico)

Se você prefere janelas em vez de comandos:

1. Abra o **Menu Inicial**.
    
2. Digite **Informações do Sistema** (ou _System Reports_).
    
3. Lá você verá o modelo do processador, quantidade de RAM e versão do Kernel de forma bem organizada.
    

---

## 3. Detalhes Técnicos via Terminal (O mais completo)

Para ver tudo — desde o barramento da placa-mãe até os detalhes do processador — use o `inxi`. Ele é o padrão ouro no Mint.

- **Resumo rápido:**
    
    Bash
    
    ```
    inxi -F
    ```
    
- **Apenas CPU e RAM:**
    
    Bash
    
    ```
    inxi -C -m
    ```
    

---

## 4. Ver apenas o Processador (Útil para o seu i5)

Se quiser ver os núcleos e a velocidade do seu i5 em tempo real:

Bash

```
lscpu
```

---

## 5. Ver Memória RAM

Para ver quanto de RAM está sendo usada agora e o total disponível:

Bash

```
free -h
```

---

## 6. Localização de Arquivos (O comando `find`)
Essencial para encontrar suas notas do Obsidian ou scripts SQL perdidos.
- **Buscar por nome na Home:** `find ~ -name "queries.sql"`
- **Buscar pastas (ex: sua pasta OBS):** `find /home -type d -name "OBS"`
- **Buscar arquivos alterados nos últimos 2 dias:** `find . -mtime -2`
- **Buscar ignorando Maiúsculas/Minúsculas:** `find . -iname "repo2026"`
- **Buscar ignorando Maiúsculas/Minúsculas:** `sudo find / -iname "*null*" 2>/dev/null`
- **Buscar ignorando Maiúsculas/Minúsculas:** `find . -iname "repo2026"`



Bash

```
sudo find / -iname "*null*" 2>/dev/null
```

---

## 🔍 O que cada parte faz:

- **`sudo`**: Necessário para que o `find` consiga entrar em pastas do sistema (como `/root` ou `/etc`) onde o seu usuário comum não tem acesso.
    
- **`/`**: Indica para começar a busca na **raiz** do sistema (o disco inteiro).
    
- **`-iname`**: Faz a busca pelo nome, mas **ignora** se as letras são maiúsculas ou minúsculas (acha `null`, `Null`, `NULL`).
    
- **`"*null*"`**: Os asteriscos são "coringas". Eles garantem que o comando encontre arquivos como `dev-null`, `null_config.txt`, etc.
    
- **`2>/dev/null`**: **O pulo do gato!** Isso esconde as centenas de mensagens de "Permissão Negada" que apareceriam na tela, deixando apenas os resultados reais que você quer ver.
    
head app.log
tail app.log

---

## 💡 Dica de Troubleshooting (Cenário DevOps)

Se você está procurando por erros de **"valor nulo"** dentro de arquivos de configuração (e não no nome do arquivo), o comando muda para o `grep`:

Bash

```
sudo grep -rnw /etc -e "null" 2>/dev/null
```

_Isso vai procurar a palavra "null" **dentro** de todos os arquivos na pasta `/etc` (onde ficam as configurações do Linux)._

---

## 🚀 Próximo Passo

Como você está configurando o **Azure Data Studio** e o **SQL Server**, você gostaria que eu mostrasse como usar o `find` para localizar exatamente onde o SQL Server guarda os arquivos de log de erro (`ERRORLOG`) no Linux? Isso é essencial para o seu "Dicionário de Programador"!
-

## 💡 Dica de DevOps/Admin:

Como você está montando seu ambiente de estudos, é legal rodar o `inxi -F` e salvar o resultado em uma nota no seu **Obsidian**. Assim, você tem documentado exatamente o hardware do seu **Nasinha-I5** para comparar o desempenho quando começar a rodar bancos de dados mais pesados ou Docker!

**Conseguiu ver as especificações? Qual a geração do seu i5 e quanto de RAM o Nasinha tem?** Posso te ajudar a otimizar o SQL Server se a memória for um pouco limitada!

---
title: "Guia de Comandos: Hardware e Busca no Linux"
curso: Administração de Sistemas Linux
author: Gemini AI
data_estudo: 2026-03-03
linguagem:
  - Bash
tecnologias:
  - Neofetch
  - Inxi
  - Find
assuntos:
  - Monitoramento de Hardware
  - Gestão de Memória
  - Localização de Arquivos
status: 🔴 Inicio
tags:
  - linux
  - terminal
  - hardware
  - devops
---

# Título da Aula: Hardware e Localização de Arquivos no Nasinha-I5 🖥️

![Capa do Estudo](https://img.youtube.com/vi/v_XF_S_5Y6M/maxresdefault.jpg)

**Conceito Principal:** Dominar a visualização do hardware e a localização precisa de arquivos é essencial para o troubleshooting e para manter a organização entre os ambientes Windows e Linux.

## Conteúdo da Aula

### 1. O Jeito "Visual" (Neofetch)
Mostra o logo da distribuição e um resumo estético do hardware.
- **Comando:** `neofetch`
- **Instalação:** `sudo apt install neofetch`

### 2. Informações do Sistema (Modo Gráfico)
Para visualização via interface (GUI):
1. Abra o **Menu Inicial**.
2. Digite **Informações do Sistema**.

### 3. Detalhes Técnicos (inxi)
O "padrão ouro" para relatórios detalhados no Mint.
- **Resumo Completo:** `inxi -F`
- **CPU e RAM:** `inxi -C -m`

### 4. Processador e Memória
- **Detalhes da CPU:** `lscpu` (mostra núcleos, threads e cache).
- **Uso de RAM:** `free -h` (exibe o uso em formato legível: MB/GB).

### 5. Localização de Arquivos (O comando `find`)
Essencial para encontrar suas notas do Obsidian ou scripts SQL perdidos.
- **Buscar por nome na Home:** `find ~ -name "queries.sql"`
- **Buscar pastas (ex: sua pasta OBS):** `find /home -type d -name "OBS"`
- **Buscar arquivos alterados nos últimos 2 dias:** `find . -mtime -2`
- **Buscar ignorando Maiúsculas/Minúsculas:** `find . -iname "repo2026"`

## Performance/Conclusão

Saber "quem é" a sua máquina (Hardware) e "onde estão" os seus dados (Find) reduz drasticamente o tempo de resposta em incidentes. Para o seu fluxo com o **OneDrive**, o `find` será seu melhor amigo para validar se a sincronização realmente colocou os arquivos no caminho correto: `/home/gerson-pessoal/OneDrive/OBS`.


**Navegação e Manipulação de Arquivos e Diretórios**

- **`pwd`**: Mostra o caminho absoluto de onde você está atualmente dentro da estrutura de diretórios do sistema.
- **`cd`**: Usado para mudar de diretório (entrar ou sair de pastas).
- **`ls`**: Lista as pastas e arquivos contidos no diretório atual.
- **`ls -la`**: Lista os conteúdos com informações detalhadas, permitindo diferenciar o que é arquivo (representado por um tracinho `-`) do que é diretório (representado pela letra `d`), além de exibir as permissões, tamanho e dono.
- **`find`**: Procura e localiza arquivos ou pastas específicas através de um nome. Quando acrescido de **`2>/dev/null`**, ele oculta os erros de "permissão negada" para facilitar a visualização dos resultados.
- **`mkdir`**: Cria uma nova pasta/diretório.
- **`touch`**: Cria um arquivo vazio.
- **`cp`**: Copia um arquivo de um caminho para o outro.
- **`mv`**: Move um arquivo de lugar ou serve para renomeá-lo.

**Visualização e Edição de Conteúdo**

- **`cat`**: Lê e exibe todo o conteúdo de um arquivo diretamente na tela do terminal.
- **`head`**: Mostra apenas as 10 primeiras linhas de um arquivo grande, sem a necessidade de carregá-lo por completo.
- **`tail`**: Mostra as 10 últimas linhas de um arquivo.
- **`tail -f`**: Exibe o final de um arquivo em tempo real, sendo excelente para acompanhar logs gerados interativamente.
- **`nano`**: Editor de texto interno do terminal (comparado ao Word do Linux). Para salvar alterações usa-se `Ctrl + O` e para sair, `Ctrl + X`.
- **`diff`**: Compara o conteúdo de dois arquivos e indica quais são as diferenças exatas entre eles, sendo ótimo para comparar arquivos de configuração e backups.

**Sistema, Processos e Recursos**

- **`clear`** (ou atalho **`Ctrl + L`**): Limpa a tela cheia do terminal.
- **`whoami`**: Informa qual é o usuário atualmente logado no sistema.
- **`uname`** (e **`uname -a`**): Exibe informações básicas e gerais sobre o sistema operacional, arquitetura e o kernel.
- **`df -h`**: Mostra a utilização dos volumes e partições de disco da máquina em um formato legível para humanos (Gigabytes, Megabytes).
- **`free -h`**: Mostra os detalhes de utilização e disponibilidade da memória da máquina de forma humanizada.
- **`ps aux`**: Lista todos os processos e serviços que estão rodando ativamente na máquina no momento.
- **`kill`**: Mata/encerra um processo a partir do seu ID (PID).

**Filtros e Operadores**

- **`|` (Pipe)**: Pega a saída (resultado) do primeiro comando e insere como entrada no próximo comando.
- **`grep`**: Filtra informações específicas em meio a um texto longo (usado geralmente junto com o pipe, ex: `ps aux | grep billing` para encontrar apenas processos com o nome billing).
- **`>` (Sinal de Maior)**: Direciona e insere o retorno/saída de um comando para dentro de um arquivo (ex: exportar linhas de log para um arquivo `.txt` usando `tail app.log > erros.txt`).

**Permissões**

- **`chmod`**: Comando para modificar permissões de arquivos. Ele funciona com base em valores numéricos (4 = ler, 2 = escrever, 1 = executar).
    - **Exemplos aplicados**: `chmod 777` concede permissão total (leitura, escrita e execução) a todos os usuários, enquanto `chmod 644` permite que o dono do arquivo leia e escreva, e os demais (grupo e outros) apenas leiam.

**Atalhos Úteis e Comandos Extras**

- **`Ctrl + C`**: Cancela ou finaliza a exibição de um processo preso na tela (como para sair da exibição em tempo real do `tail -f`).
- **`exit`**: Sai da sessão atual do servidor ou do contêiner e retorna à máquina local.

**Comandos Docker (Ambiente)**

- Apesar de não ser o foco de Linux puro, para rodar e gerenciar o ambiente de testes foram mostrados:
- **`docker ps`**: Lista os contêineres ativos.
- **`docker ps -a`**: Lista o histórico de todos os contêineres (inclusive os inativos).
- **`docker rm <ID>`**: Remove e destrói um contêiner de vez.