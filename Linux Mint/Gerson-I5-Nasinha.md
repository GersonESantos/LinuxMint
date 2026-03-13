
##  Git
### 1. Instalação do Git

No terminal, execute:

Bash

```
sudo apt update
sudo apt install -y git
```

### 2. Configuração de Identidade (Crucial)

Lembra que você mencionou que usa o usuário **GersonESantos**? Vamos configurar isso agora para que seus "commits" fiquem registrados corretamente.

Substitua o e-mail abaixo pelo e-mail que você usa no seu GitHub:

Bash

```
# Configurar seu nome de usuário do GitHub
git config --global user.name "GersonESantos"

# Configurar seu e-mail do GitHub
git config --global user.email "12121732@aluno.newtonpaiva.br"

# Definir 'main' como o nome padrão da branch inicial (padrão moderno)
git config --global init.defaultBranch main
```

### 3. Gerar Chave SSH (Opcional, mas recomendado)

Para não ter que digitar sua senha toda vez que fizer um `push`, o ideal é usar uma chave SSH.

1. Gere a chave (aperte Enter em todas as perguntas):
    
    Bash
    
    ```
    ssh-keygen -t ed25519 -C "seu-email@exemplo.com"
    ```
    
2. Copie a chave gerada:
    
    Bash
    
    ```
    cat ~/.ssh/id_ed25519.pub
    ```
    
3. **Ação:** Copie esse texto que começa com `ssh-ed25519...` e cole no seu perfil do GitHub em **Settings -> SSH and GPG keys**.
    

---

## 2. Instalar o VS Code (Via Repositório Oficial)

Abra o terminal e execute este bloco de comandos:

Bash

```
# 1. Baixar a chave de confiança da Microsoft
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -D -o root -g root -m 644 packages.microsoft.gpg /etc/apt/keyrings/packages.microsoft.gpg

# 2. Adicionar o repositório do VS Code
sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'

# 3. Atualizar e instalar o Code
rm -f packages.microsoft.gpg
sudo apt update
sudo apt install -y code
```

---
## 3 Docker

Execute estes comandos para preparar o terreno e instalar o motor que rodará os bancos.

Bash

```
# 1. Atualizar e instalar dependências básicas
sudo apt update && sudo apt install -y ca-certificates curl gnupg

# 2. Configurar Chave GPG do Docker
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# 3. Adicionar Repositório Docker (Base Noble/24.04)
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu noble stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# 4. Instalar o Docker
sudo apt update && sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# 5. Permissão de Usuário (Evita usar sudo no docker)
sudo usermod -aG docker $USER

# ⚠️ PARE AQUI: Reinicie o computador agora para validar a permissão.
```

---
