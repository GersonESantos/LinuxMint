# 🗺️ Mapa de Particionamento - Linux Mint (HD 1TB)

**Equipamento:** Xeon | ASUS H81M-E | ST1000 (1TB)
**Estratégia:** Separação de Sistema (Root) e Dados/Apps (Home) para resiliência a falhas.

---

## 📊 Tabela de Partições Recomendada

| Ordem | Partição | Ponto de Montagem | Tamanho | Formato | Função |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | **EFI/Boot** | `/boot/efi` | **512 MB** | FAT32 | Inicialização (BIOS/GRUB) |
| 2 | **Sistema (SO)** | `/` | **80 GB** | EXT4 | Motor do Linux Mint e Drivers |
| 3 | **Swap** | `[swap]` | **16 GB** | SWAP | Memória Virtual para Docker/Xeon |
| 4 | **Dados/Apps** | `/home` | **~900 GB** | EXT4 | Porto Seguro (Projetos, SQL, Obsidian) |

---

## 🛠️ Notas de Instalação (Checklist)

### 1. Na BIOS (Após trocar a CR2032):
- [ ] **SATA Mode:** AHCI (Obrigatório)
- [ ] **CSM (Boot):** Enabled (UEFI and Legacy)
- [ ] **CPU Fan Speed:** Ignore (se houver erro de cooler)

### 2. No Instalador do Mint:
- Escolher a opção **"Opção Avançada"** (Something Else).
- Criar a tabela de partição como **GPT**.
- Instalar o carregador de inicialização (GRUB) no disco inteiro (`/dev/sda`).

### 3. Pós-Instalação (Segurança):
- O `/home` separado permite que, em uma futura reinstalação, você formate apenas a partição de **80GB (/)**.
- Seus containers Docker e bancos de dados SQL Server ficam protegidos na `/home`.

---
**Data da última configuração:** 2026-03-12