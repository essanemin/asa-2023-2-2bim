# DNS

O DNS converte nomes de domínio, como www.example.com, em endereços IP correspondentes, como 192.168.1.1. 

O DNS organiza os nomes de domínio em uma estrutura hierárquica, com domínios de nível superior (TLDs, como .com, .org) no topo, seguidos por domínios de segundo nível e assim por diante. 

## Instalação

Foi feita uma conexão por meio do samba entre um cliente Windows e um servidor Linux Alpine.

## Configuração

Incluir o(s) nome(s) e o conteúdo do(s) arquivo(s) de configuração.

Cinco registros (4 pontos cada):

- 3 do tipo A (Endereços);
- 2 do tipo CNAME (`www` e `docs`);

---------------------------------------------------------------------------------

Visão geral do Gerenciador de DNS

[![dnsgeral](https://i.im.ge/2024/01/03/xeG8t9.dnsgeral.png)](https://im.ge/i/xeG8t9)

A máquina xarope de ip 192.168.18.254, está sendo utilizada como gateway e servidor dns para a máquina Windows.

### Registros do tipo A

[![marley2222.png](https://i.im.ge/2024/01/03/3MuCWL.marley2222-png.png)](https://im.ge/i/3MuCWL)

[![propriedades](https://i.im.ge/2024/01/03/xeyFPM.propriedades.png)](https://im.ge/i/xeyFPM)

[![torre](https://i.im.ge/2024/01/03/xeRYxS.torre.png)](https://im.ge/i/xeRYxS)

### Registros do tipo CNAME

[![www](https://i.im.ge/2024/01/03/xe2xkW.www.png)](https://im.ge/i/xe2xkW)

[![docs](https://i.im.ge/2024/01/03/xe2pj6.docs.png)](https://im.ge/i/xe2pj6)

## Teste

Ping feito para os endereços tipo CNAME

[![cname](https://i.im.ge/2024/01/03/xe13g9.cname.png)](https://im.ge/i/xe13g9)

Ping para os endereços tipo A

[![marley](https://i.im.ge/2024/01/03/xeGyFa.marley.png)](https://im.ge/i/xeGyFa)

[![ifpar](https://i.im.ge/2024/01/03/xetFlT.ifpar.png)](https://im.ge/i/xetFlT)

[![paris](https://i.im.ge/2024/01/03/xeRXSF.paris.png)](https://im.ge/i/xeRXSF)