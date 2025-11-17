# Procedimento para Instalação de Distribuições GNU/Linux  
**Autor:** Daniel  
**Descrição:** Documento conciso descrevendo o processo de instalação de distribuições GNU/Linux em computadores físicos e/ou máquinas virtuais.

---

## 1. Preparação do Ambiente

### 1.1 Obtenção da Imagem ISO  
I. Acesse o site oficial da distribuição (ex.: Ubuntu, Fedora, Debian...);
II. Baixe a versão estável recomendada;
III. (Opcional) Valide o checksum da ISO para garantir que o arquivo não foi corrompido.

### 1.2 Criação da Mídia de Instalação  
Para instalar o sistema em um computador físico, é necessário criar um pendrive inicializável (*bootable*). As ferramentas abaixo cumprem exatamente esse papel:

- **Rufus:** aplicativo para Windows que grava imagens ISO em pendrives, criando uma mídia de boot de forma rápida e simples;
- **Ventoy:** ferramenta que permite copiar várias ISOs para um único pendrive, sem necessidade de regravar o dispositivo toda vez. O pendrive passa a exibir um menu com todas as ISOs disponíveis;  
- **Balena Etcher:** software multiplataforma (Windows, macOS, Linux) focado em gravação segura e simples de ISOs em pendrives.

**Para que elas servem neste caso:**  
Esses programas convertem a ISO baixada em um pendrive inicializável, que será utilizado para iniciar o computador e executar o instalador da distribuição GNU/Linux, não são os únicos meios,
porém são os melhores e mais confiavéis.

---

## 2. Instalação em Computador Físico

### 2.1 Configurações da BIOS/UEFI  
I. Acesse a BIOS/UEFI pressionando *Del*, *F2*, *F10* ou *Esc* ao ligar o computador;
II. Ajuste as seguintes opções, se necessário:  
   - Ativar modo **UEFI**;
   - Desativar **Secure Boot** caso a distribuição não seja compatível.  
III. Defina o pendrive como primeira opção na lista de dispositivos de boot.

### 2.2 Processo de Instalação  
I. Inicie o sistema pelo pendrive;
II. Escolha “Instalar” ou “Experimentar” (dependendo da distro);
III. Configure idioma, teclado e fuso horário;
IV. Selecione o tipo de particionamento:  
   - **Automático:** recomendado para usuários iniciantes;
   - **Manual:** permite definir partições personalizadas como `/`, `/home` e `swap`.
V. Confirme as opções e aguarde o término da instalação;
VI. Remova o pendrive e reinicie o computador.

---

## 3. Instalação em Máquina Virtual

### 3.1 Seleção da Ferramenta  
Softwares de virtualização recomendados:  
- **VirtualBox;**  
- **VMware Workstation Player;**  
- **GNOME Boxes.**

### 3.2 Criação da Máquina Virtual  
1. Crie uma nova VM e selecione a ISO como mídia de boot; 
2. Defina os recursos:  
   - **CPU:** pelo menos 2 núcleos; 
   - **RAM:** 2–4 GB (varia conforme a distribuição);
   - **Disco:** mínimo de 20 GB.  
3. Habilite aceleração de hardware (VT-x/AMD-V) se disponível.

### 3.3 Processo de Instalação  
1. Inicie a máquina virtual;
2. Siga os mesmos passos da instalação em hardware físico;
3. Após instalar, adicione as ferramentas de integração da VM (ex.: *Guest Additions*) para melhorar desempenho e compatibilidade.

---

## 4. Pós-Instalação

1. Execute a atualização inicial:  
   ```bash
   sudo apt update && sudo apt upgrade   ->   # Debian/Ubuntu  
   sudo dnf update              ->            # Fedora  
   sudo pacman -Syu           ->              # Arch Linux  
