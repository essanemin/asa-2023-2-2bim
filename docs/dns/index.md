# DNS

## Instalação

sudo apt-get install bind9 bind9utils bind9-doc

## Configuração

Incluir o(s) nome(s) e o conteúdo do(s) arquivo(s) de configuração.

Cinco registros (4 pontos cada):

- 3 do tipo A (Endereços);
- 2 do tipo CNAME (`www` e `docs`);

---------------------------------------------------------------------------------

sudo nano /etc/default/bind9:

- . . .
OPTIONS="-u bind -4"

sudo systemctl restart bind9

sudo nano /etc/bind/named.conf.options:

- options {
    directory "/var/cache/bind";

    // Forwarders para servidores DNS públicos do Google
    forwarders {
        8.8.8.8;
        8.8.4.4;
    };

    // Permitir consultas recursivas para clientes confiáveis
    recursion yes;

    // Definir uma acl para endereços IP confiáveis
    acl "trusted" {
        localhost;
        192.168.1.0/24;  // Substitua pelo seu intervalo de rede
    };

    // Opções adicionais de segurança
    allow-query { any; };
    allow-recursion { trusted; };
    allow-transfer { none; };

    // Limitar o tamanho do cache
    max-cache-size 100M;

    // Logging
    logging {
        channel default_syslog {
            syslog daemon;
            severity dynamic;
        };
        category default {
            default_syslog;
        };
    };
};


nano /etc/bind/named.conf.local:

- zone "example.com" {
    type master;
    file "/etc/bind/db.example.com";
};


nano /etc/bind/db.example.com:

$TTL 604800
@       IN      SOA     ns1.example.com. admin.example.com. (
                    2022122501      ; Serial
                    604800          ; Refresh
                    86400           ; Retry
                    2419200         ; Expire
                    604800 )        ; Negative Cache TTL

@       IN      NS      ns1.example.com.
@       IN      A       192.168.1.10
@       IN      A       192.168.1.20
@       IN      A       192.168.1.30
www     IN      CNAME   example.com.
docs    IN      CNAME   example.com.


sudo nano /etc/resolv.conf:

- nameserver 127.0.0.1

Checar a sintaxe: "named-checkconf"

sudo service bind9 restart

## Teste


