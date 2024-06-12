# nginx-lets-encrypt
##### update 
```
apt update
```
##### upgrade
```
sudo apt upgrade
```

##### PASSO 1 - configuração do nginx
```
sudo apt install nginx
```
> VERIFICAR O STATUS DO NGINX
```
service nginx status
```

##### PASSO 2 - liberar protocolo https no firewall
```
sudo ufw allow https
```

##### PASSO 3 - crie a configuração virtual host do domínio
```
sudo nano /etc/nginx/sites-enabled/nome-do-site
```

##### PASSO 4 - configurar certbot - clonar e mover o certbot para o diretório /opt
```
sudo git clone https://github.com/certbot/certbot /opt/certbot
```

##### PASSO 5 - executar a instalação através do certbot
```
sudo opt/certbot/certbot-auto --nginx
```

##### se tudo der certo obterá uma resposta semelhante a esta
>... Installation succeeded.Saving debug log to /var/log/letsencrypt.log


##### INFORME QUAL O WEBSITE QUE OCÊ DESEJA CONFIGURAR O SSL

##### se tudo der certo obterá uma resposta semelhante a esta
>Performing the following challenges:tls-sni-01 challenge for www.nome-do-site.comGenerating key (1024 bits):

##### PASSO 6 - reiniar o nginx e efetuar testes
```
sudo systemctl reaload nginx
```

##### opcional 
acessar o crontab e adicionar uma renovação automática do ssl
```
0 3 * * 1 /opt/certbot/certbot-auto --nginx renew --quiet --non-interactive >> /var/log/letsencrypt-renew.log
```
