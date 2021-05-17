# Instalar Ubuntu Server no Windows (WSL 2)

Requisitos:

- Windows 10 atualizado (versão usada nesse manual 20H2);
- Computador com suporte a virtualização (hyper-v);
- WSL 2.

## Passos para instalação

Habilitar o Windows Subsystem for Linux
```bash
PS C:\> Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
![img](/images/01.png)

Habilitar o recurso de máquina virtual (necessário para o WSL2)
```bash
PS C:\> Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform
```
![img](/images/02.png)

Baixar e instalar pacote de atualização para o [Kernel do Linux](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)
Obs.: link para versão 64bits

Instalar Ubuntu 20.04 via Microsoft store
![img](/images/03.png)

![img](/images/04.png)

![img](/images/05.png)

![img](/images/06.png)

Mudar o Ubuntu para WSL 2
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
## Edite o .bashrc para trocar o bash pelo zsh
```bash
 $ vim .bashrc
 # inserir no início do arquivo
 if test -t 1; then
   exec zsh
   fi
```
## Testando zsh
```bash
 $ zsh
```
![img](/images/07.png)

## Instalar o oh-mu-zsh
```bash
 $ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Mudar o tema do zsh
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
 c:\>.\install.ps1
# reativar política de execução
c:\> set-executionpolicy remotesigned (n)
```

## Alterar a fonte padrão para Ubuntu Mono derivative Powerlin
Acesse as propriedades e mude a fonte conforme as imagens abaixo:

![img](/images/08.png)

![img](/images/09.png)

![img](/images/10.png)


# Integrando ao VS Code

https://code.visualstudio.com/docs/?dv=win

Após a instalação, o vscode vai sugerir instalar a extensão WSL
![img](/images/11.png)

## Abra o terminal e modifique a fonte conforme imagem abaixo:

![img](/images/12.png)

![img](/images/13.png)

![img](/images/14.png)

```bash
"editor.fontFamily": "'Ubuntu Mono derivative Powerline',Consolas, 'Courier New', monospace",
```

## Abrindo um diretório do Ubuntu dentro do VSCODE
![img](/images/15.png)

![img](/images/16.png)

## Repositório git
Perceba que, ao modificar qualquer arquivo, o **VSCODE** e o **zsh** irão acompanhar o status do repositório.

![img](/images/17.png)

![img](/images/18.png)

