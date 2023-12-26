# DHCP


## Instalação

apt-get install isc-dhcp-server

## Configuração

Incluir o(s) nome(s) e o conteúdo do(s) arquivo(s) de configuração.

- Distribuir um intervalo (*range* em inglês) de endereços IP; (15 pontos)
- Reservar 2 endereços (IP fixo) fora do intervalo do item anterior. (5 pontos)

---------------------------------------------------------------------------------

Verificar endereçamento IP atual das interfaces de rede "ifconfig"

nano /etc/systemd/network:


Utilizar o "reboot"

nano /etc/dhcp/dhcpd.conf:

authoritative;

subnet 10.147.58.0 netmask 255.255.255.0 {
    range 10.147.58.100 10.147.58.200;
    option routers 10.147.58.194;
    option domain-name-servers 8.8.8.8, 8.8.4.4;
    option domain-name "daymesquita.com";

    host pc1 {
        fixed-address 10.147.58.10;
    }

    host pc2 {
        fixed-address 10.147.58.20;
    }
}


Ao final, usar o "sudo systemctl restart isc-dhcp-server" e também "etc/init.d/isc-dhcp-server start".

reiniciar as interfaces de rede com ifdown e ifup.

## Teste

