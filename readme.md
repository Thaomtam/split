# SSL
```
apt install -y socat
curl https://get.acme.sh | sh
source ~/.bashrc
acme.sh --upgrade --auto-upgrade
acme.sh --set-default-ca --server letsencrypt

acme.sh --issue -d EXAMPLE.COM --standalone --keylength ec-256

acme.sh --install-cert -d EXAMPLE.COM --ecc \
--fullchain-file /etc/ssl/private/fullchain.cer \
--key-file /etc/ssl/private/private.key

chown -R nobody:nogroup /etc/ssl/private
```
# INSTALL XRAY
```
bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ install
```
# INSTALL NGINX
```
apt install -y gnupg2 ca-certificates lsb-release ubuntu-keyring && curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor > /usr/share/keyrings/nginx-archive-keyring.gpg && echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] http://nginx.org/packages/mainline/ubuntu `lsb_release -cs` nginx" > /etc/apt/sources.list.d/nginx.list && echo -e "Package: *\nPin: origin nginx.org\nPin: release o=nginx\nPin-Priority: 900\n" > /etc/apt/preferences.d/99nginx && apt update -y && apt install -y nginx && mkdir -p /etc/systemd/system/nginx.service.d && echo -e "[Service]\nExecStartPost=/bin/sleep 0.1" > /etc/systemd/system/nginx.service.d/override.conf && systemctl daemon-reload
```
# INSTALL CONFIG XRAY && NGINX
```
curl -Lo /usr/local/etc/xray/config.json https://raw.githubusercontent.com/Thaomtam/split/refs/heads/main/config.json && curl -Lo /etc/nginx/nginx.conf https://raw.githubusercontent.com/Thaomtam/split/refs/heads/main/nginx.conf
```
# START XRAY && NGINX
```
systemctl restart xray && systemctl restart nginx && sleep 0.2 && systemctl status xray && systemctl status nginx
```
THOI-TIET
