# PROXY

## Instalação

sudo apt-get install squid

## Configuração

Incluir o(s) nome(s) e o conteúdo do(s) arquivo(s) de configuração.

Fazer a configuração de 4 ACLs distintas, conforme a atividade passada em sala de aula.

sudo cp /etc/squid/squid.conf /etc/squid/squid.conf.original

sudo nano /etc/squid/squid.conf: fazer as alterações necessárias

Ao final, fazer sudo systemctl restart squid

## Teste

O passo a passo está descrito neste link de acesso: "https://docs.google.com/document/d/1rUNPMU8IirR8rC96YmhlbqYzylUSZ7HZYEk9MhGwvGY/edit#heading=h.wdi57ya9muv4".
