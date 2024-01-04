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

![Alt text](backup.png)

Configuração das 4 ACLs do arquivo `/etc/squid/squid.conf`:

![Alt text](acl.png)

Para fazer a ACL do url_regex fiz a seguinte configuração no arquivo `registro.txt`:

![Alt text](registrostxt.png)

Reiniciar o serviço Squid para aplicar as alterações com o comando `service squid restart`.

Configuração do Firefox para receber o serviço proxy com o IP da máquina real:

![Alt text](conf.png)

## Teste

### O domínio do gov.br foi bloqueado.

![Alt text](gov.png)

### O navegador Firefox foi bloqueado.

![Alt text](firefoxbloqueado.png)

### Todos os sites foram bloqueados devido a hora.

![Alt text](hora.png)

### O facebook  foi bloqueado.

![Alt text](face.png)

Registro dos arquivos de log:

![Alt text](log.png)