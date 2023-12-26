# LDAP

## Instalação

sudo apt-get install slapd ldap-utils

## Configuração

Incluir o(s) nome(s) e o conteúdo do(s) arquivo(s) de configuração.

- Criar duas OU: `vendedores` e `rh`;
- Mover o grupo `sobrenome1` e seus membros para a OU `vendedores`;
- Mover os grupo `sobrenome2` e seus membros para a OU `rh`.

sudo dpkg-reconfigure slapd
    Escolha o modo de configuração (MDB é uma boa opção moderna).
    Insira o nome de domínio (dc=example,dc=com).

criar um ldif "ous.ldif" em /etc/ldap:

dn: ou=vendedores,dc=example,dc=com
objectClass: organizationalUnit
ou: vendedores

dn: ou=rh,dc=example,dc=com
objectClass: organizationalUnit
ou: rh

#MEMBROS (membros.ldif)

#Membros para o grupo sobrenome1 na OU vendedores
dn: cn=usuario1,ou=people,dc=example,dc=com
objectClass: inetOrgPerson
cn: usuario1
sn: sobrenome1
memberOf: cn=sobrenome1,ou=grupos,dc=example,dc=com

#Membros para o grupo sobrenome2 na OU rh
dn: cn=usuario2,ou=people,dc=example,dc=com
objectClass: inetOrgPerson
cn: usuario2
sn: sobrenome2
memberOf: cn=sobrenome2,ou=grupos,dc=example,dc=com

#comando p/adicionar os membros 
ldapadd -x -D "cn=admin,dc=example,dc=com" -W -f membros.ldif

#verificar se os membros foram adicionados corretamente 
ldapsearch -x -H ldap://localhost:389 -b "dc=example,dc=com" -D "cn=admin,dc=example,dc=com" -W -s sub "(objectClass=*)"

#MOVER GRUPOS (movegroup.ldif)

#Mover sobrenome1 para a OU vendedores
dn: cn=sobrenome1,ou=grupos,dc=example,dc=com
changetype: modrdn
newrdn: cn=sobrenome1
deleteoldrdn: 1
newsuperior: ou=vendedores,dc=example,dc=com

#Mover sobrenome2 para a OU rh
dn: cn=sobrenome2,ou=grupos,dc=example,dc=com
changetype: modrdn
newrdn: cn=sobrenome2
deleteoldrdn: 1
newsuperior: ou=rh,dc=example,dc=com

#Mover membros de sobrenome1 para a OU vendedores
dn: cn=usuario1,ou=people,dc=example,dc=com
changetype: modrdn
newrdn: cn=usuario1
deleteoldrdn: 1
newsuperior: ou=vendedores,dc=example,dc=com

#Mover membros de sobrenome2 para a OU rh
dn: cn=usuario2,ou=people,dc=example,dc=com
changetype: modrdn
newrdn: cn=usuario2
deleteoldrdn: 1
newsuperior: ou=rh,dc=example,dc=com


#Em seguida, execute o seguinte comando para aplicar as alterações:
ldapmodify -x -D cn=admin,dc=example,dc=com -W -f move_groups.ldif

## Teste


