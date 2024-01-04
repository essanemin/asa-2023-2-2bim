# DHCP

O DHCP é um protocolo de rede utilizado para atribuir dinamicamente configurações de rede a dispositivos quando eles se conectam a uma rede. Além do endereço IP, o DHCP fornece informações como o endereço do gateway padrão.

## Instalação

Utilizei o Linux Alpine como servidor para um cliente Windows.

O comando utilizado foi `apk add dnsmasq`.

## Configuração

Incluir o(s) nome(s) e o conteúdo do(s) arquivo(s) de configuração.

- Distribuir um intervalo (*range* em inglês) de endereços IP; (15 pontos)
- Reservar 2 endereços (IP fixo) fora do intervalo do item anterior. (5 pontos)

---------------------------------------------------------------------------------

Configurações do arquivo `/etc/dnsmasq.d/asa.conf`:

![Alt text](image.png)

Arquivo `/etc/network/interfaces`:

[![interfaces](https://i.im.ge/2023/12/30/x825q0.interfaces.png)](https://im.ge/i/x825q0)

Após isso, pare o samba através do comando `rc-service samba stop`.

Comando para reiniciar o dnsmasq `rc-service dnsmasq restart`.

Altere as permissões do arquivo /var/log/.

Uma opção é usando o comando `chmod 777 /var/log/`, por exemplo.

No Windows, mude as configurações para que o dhcp fique ativado.

[![automatico](https://i.im.ge/2023/12/30/x8DTaa.automatico.png)](https://im.ge/i/x8DTaa)

## Teste

Arquivo de log sendo atualizado:

[![tailflog](https://i.im.ge/2023/12/30/xgkimG.tailflog.png)](https://im.ge/i/xgkimG)

O comando `ipconfig /release` deve ser executado para deletar os IPs já atribuídos à maquina anteriormente e `ipconfig /renew` para atribuir novos IPs de acordo com a configuração planejada.


Máquina 1

[![opaaa](https://i.im.ge/2024/01/03/3M8MfL.opaaa.png)](https://im.ge/i/3M8MfL)

Máquina 2

[![renew](https://i.im.ge/2024/01/03/3M8X8a.renew.png)](https://im.ge/i/3M8X8a)

Os IPs foram atribuídos fora do intervalo (range).