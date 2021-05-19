# Instalar Ubuntu Server no Windows (WSL 2)

Requisitos:

- Windows 10 atualizado (versão usada nesse manual 20H2);
- Computador com suporte a virtualização (hyper-v);
- WSL 2.

## Passos para instalação

### Habilitar o Windows Subsystem for Linux
```bash
PS C:\> Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
![](/images/01.png)

### Habilitar o recurso de máquina virtual (necessário para o WSL2)
```bash
PS C:\> Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform
```
![](/images/02.png)

### Baixar e instalar pacote de atualização para o [Kernel do Linux](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)
_Obs.: link para versão 64bits_

### Instalar Ubuntu 20.04 via Microsoft store
![](/images/03.png)

![](/images/04.png)

![](/images/05.png)

![](/images/06.png)

### Mudar o Ubuntu para WSL 2
```bash
c:\> wsl -l -v
NAME  STATE  VERSION
* Ubuntu-20.04  Stopped  1

c:\> wsl --set-version Ubuntu-20.04 2

c:\> wsl -l -v
NAME  STATE  VERSION
* Ubuntu-20.04  Stopped  2
```

# Instalar o zsh no Ubuntu

```bash
 $ sudo apt install zsh
```
## Editar o .bashrc e trocar o bash pelo zsh
```bash
 $ vim .bashrc
 # inserir no início do arquivo
 if test -t 1; then
   exec zsh
   fi
```
## Testar o zsh
```bash
 $ zsh
```
![](/images/07.png)

## Instalar o oh-my-zsh
```bash
 $ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Modificar o tema do zsh
```bash
 $ vim .bashrc
 # substitua
 # ZSH_THEME="robbyrussell"
 #por
 ZSH_THEME="agnoster"
```

## Instalar fontes
Ainda dentro do Ubuntu execute:
```bash
 $ git clone https://github.com/powerline/fonts.git
 $ mkdir /mnt/c/fontes
 $ cp -r fonts /mnt/c/fontes
 $ rm -rfv fonts
```
Via Powershell execute
```bash
 c:\>cd fontes\fonts
# desativar a politica de execução de script
 c:\> set-executionpolicy remotesigned (y)
# instalar as fontes
 c:\>.\install.ps1
# reativar política de execução
c:\> set-executionpolicy remotesigned (n)
```

## Alterar a fonte padrão para Ubuntu Mono derivative Powerlin
Acesse as propriedades e mude a fonte conforme as imagens abaixo:

![](/images/08.png)

![](/images/09.png)

![](/images/10.png)


# Integrar o ubuntu ao VS Code

[Download VSCODE](https://code.visualstudio.com/docs/?dv=win)

Após a instalação, o vscode vai sugerir instalar a extensão WSL
![](/images/11.png)

## Abrir o terminal e modificar a fonte conforme imagem abaixo:
![](/images/12.png)

![](/images/13.png)

![](/images/14.png)

```bash
"editor.fontFamily": "'Ubuntu Mono derivative Powerline',Consolas, 'Courier New', monospace",
```

## Abrir um diretório do Ubuntu dentro do VSCODE
![](/images/15.png)

![](/images/16.png)

## Repositório git
Perceba que, ao modificar qualquer arquivo, o **VSCODE** e o **zsh** irão acompanhar o status do repositório.
![](/images/17.png)

![](/images/18.png)


## Fontes:

- [Thomas Maurer - Install WSL 2 on Windows 10](https://www.thomasmaurer.ch/2019/06/install-wsl-2-on-windows-10/#:~:text=Install%20WSL%202%201%20Enable%20the%20Windows%20Subsystem,4%20Configure%20the%20distro%20to%20use%20WSL%202)

- [Microsoft - Guia de instalação wsl2](https://docs.microsoft.com/pt-br/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package)
