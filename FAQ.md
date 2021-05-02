# FAQ

## git@github.com: Permission denied (publickey). fatal: Could not read from remote repository.

***Por que pego esse erro ao tentar clonar meu repositório?***

_Resposta 1: Faltou adicionar sua chave pública ao github._

_Resposta 2: Executou o git clone sem adicionar sua chave privada ao chave ao ssh-agent_

Para corrigir, execute na **cli (linha de comando)** do seu sistema operacional execute:
```bash
 $ eval `ssh-agent -s`
 $ ssh-add /home/{SEUHOME}/.ssh/{SUACHAVE}
```
No meu caso ficou assim:
```bash
$ eval `ssh-agent -s`
  Agent pid 19844
$ ssh-add /home/marden/.ssh/keygen_github
  Identity added: /home/marden/.ssh/keygen_github (meu.email@dominio.com)
```


## License
[MIT](https://choosealicense.com/licenses/mit/)
