# SMB

O Samba permite que sistemas operacionais como Linux atuem como servidores ou clientes em uma rede que utiliza o protocolo SMB/CIFS, predominantemente associado a sistemas operacionais Windows.

## Instalação

Foi feita uma integração do Linux Alpine com o Windows 7. Realize o comando `apk add samba` para instalar o samba.

## Configuração

Incluir o(s) nome(s) e o conteúdo do(s) arquivo(s) de configuração.

1. Criar 2 grupos para dois de seus sobrenomes;
2. Criar 4 usuários, dois para cada um dos sobrenomes;
3. Compartilhar duas pastas com dois de seus sobrenome, compartilhado para o grupo com o sobrenome correspondente.
------------------------------------------------------------------------------------------------------------------

Criação da conta Administrador:

[![adm](https://i.im.ge/2023/12/29/xxJpgr.adm.png)](https://im.ge/i/xxJpgr)

Configuração do domínio e atribução de IPv4:

[![dominioip](https://i.im.ge/2023/12/29/xxJh1G.dominioip.png)](https://im.ge/i/xxJh1G)

Configuração do arquivo `/etc/samba/smb.conf`:

[![smb-conf](https://i.im.ge/2023/12/29/xxVctf.smb-conf.png)](https://im.ge/i/xxVctf)

Criação de grupos e usuários:

[![groupuser](https://i.im.ge/2023/12/29/xxJA29.groupuser.png)](https://im.ge/i/xxJA29)

Cada sobrenome está em um grupo diferente:

[![samba](https://i.im.ge/2024/01/03/3Mioif.samba.png)](https://im.ge/i/3Mioif)

Cada grupo só consegue acessar a pasta na qual está inserido.

[![acessorestrito](https://i.im.ge/2023/12/29/xxJBvc.acessorestrito.png)](https://im.ge/i/xxJBvc)

## Teste

Listando os 2 grupos criados através do terminal:

[![gruposlista](https://i.im.ge/2023/12/29/xxJIAc.gruposlista.png)](https://im.ge/i/xxJIAc)

Listando os membros dos 2 grupos criados através do terminal:

[![samba-tool_listmembers](https://i.im.ge/2023/12/29/xxVCTC.samba-tool-listmembers.png)](https://im.ge/i/xxVCTC)