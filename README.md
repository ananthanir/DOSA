# DOSA

## Run Dosa App
```
docker compose up -d
```

## SSH Key and Github

Enter the following command `ssh-keygen -t ed25519 -C "recognizable tag"`

Provide key file location and password.

Next addd the ssh key file to the ssh agent. Run the agent using `eval "$(ssh-agent -s)"`

Then add the key `ssh-add ~/.ssh/id_ed25519` provide the password given when generating the ssh key.

Now read the generated ssh key file using `cat ~/.ssh/id_ed25519.pub`

Finally select and copy the contents of the id_ed25519.pub file, and add it to github ssh key section

## Nginx Config

Create a file with ur domain name at
```
/etc/nginx/sites-available/
```
With the following config
```
server {
    server_name hashgamegsf.kba.ai;

    location / {
        proxy_pass http://localhost:YOUR_APP_PORT; # Replace with your application's port
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```
Create a link
```
ln -s /etc/nginx/sites-available/your-config /etc/nginx/sites-enabled/
```

Check config
```
nginx -t
```

Restart Nginx
```
systemctl restart nginx
```
Install certbot
```
apt install certbot python3-certbot-nginx
```
Run certbor
```
certbot --nginx -d hashgamegsf.kba.ai
```

## Firewall UFW

Rules
```
ufw allow 22
ufw allow 8080
```
Enable Firewall
```
ufw enable
```
Check rules and status
```
ufw status
```