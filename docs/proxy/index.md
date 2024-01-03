# PROXY

Um servidor proxy desempenha várias funções em uma rede, atuando como intermediário entre os clientes e os servidores. O servidor proxy pode ser configurado para impor políticas de controle de acesso, restringindo ou permitindo o acesso a determinados recursos da Internet.

## Instalação

O comando para instalar o proxy é `apt-get install squid`.

## Configuração

Incluir o(s) nome(s) e o conteúdo do(s) arquivo(s) de configuração.

Fazer a configuração de 4 ACLs distintas, conforme a atividade passada em sala de aula.

---------------------------------------------------------------------------------------
Os testes desse serviço foram realizados na máquina real.

Por segurança, uma cópia do arquivo `/squid.conf` foi criada, chamado de `/squid.conf.backup`.

[![backup](https://i.im.ge/2024/01/03/3XNX18.backup.png)](https://im.ge/i/3XNX18)

Configuração das 4 ACLs do arquivo `/etc/squid/squid.conf`:

[![acl](https://i.im.ge/2024/01/04/3XWjEx.acl.png)](https://im.ge/i/3XWjEx)

Para fazer a ACL do url_regex fiz a seguinte configuração no arquivo `registro.txt`:

[![registrostxt](https://i.im.ge/2024/01/04/3XWigc.registrostxt.png)](https://im.ge/i/3XWigc)

Reiniciar o serviço Squid para aplicar as alterações com o comando `service squid restart`.

Configuração do Firefox para receber o serviço proxy com o IP da máquina real:

[![conf](https://i.im.ge/2024/01/03/3XNpvp.conf.png)](https://im.ge/i/3XNpvp)

## Teste

### O domínio do gov.br foi bloqueado.

[![gov](https://i.im.ge/2024/01/04/3XY0ef.gov.png)](https://im.ge/i/3XY0ef)

### O navegador Firefox foi bloqueado.

[![firefoxbloqueado](https://i.im.ge/2023/12/29/xxGnRx.firefoxbloqueado.png)](https://im.ge/i/xxGnRx)

### Todos os sites foram bloqueados devido a hora.

[![hora](https://i.im.ge/2024/01/03/3X31sW.hora.png)](https://im.ge/i/3X31sW)

### O facebook  foi bloqueado.

[![face](https://i.im.ge/2024/01/04/3XWyrz.face.png)](https://im.ge/i/3XWyrz)

Registro dos arquivos de log:

[![log](https://i.im.ge/2024/01/04/3XZAzm.log.png)](https://im.ge/i/3XZAzm)