# SMB

## Instalação

sudo apt-get install samba

## Configuração

Incluir o(s) nome(s) e o conteúdo do(s) arquivo(s) de configuração.

1. Criar 2 grupos para dois de seus sobrenomes;
2. Criar 4 usuários, dois para cada um dos sobrenomes;
3. Compartilhar duas pastas com dois de seus sobrenome, compartilhado para o grupo com o sobrenome correspondente.

Verificar se o samba está em execução: sudo systemctl status smbd

Habilitar e iniciar o serviço Samba:
sudo systemctl enable smb
sudo systemctl start smb

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.original

sudo nano /etc/samba/smb.conf: fazer as alterações necessárias

Ao final, fazer sudo systemctl restart smb

## Teste
O passo a passo está descrito neste link de acesso: "https://docs.google.com/document/d/1Y41UaWcyG1GvI4zyIJoto8SdVDU5CjxKfEcLytPQa_I/edit".
