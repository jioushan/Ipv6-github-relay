# 一個IPv6環境下 Github proxy_Use Docker

## 1.此項目運作在單棧IPv6 VM中,如您擁有雙棧網路,請自行替換Nginx.config文件中

```bash
    resolver [2001:4860:4860::6464] [2001:4860:4860::6444] ipv6=on;
to 
    resolver [2606:4700:4700::1001] [2606:4700:4700::1111] ipv6=on;

```

## 2.此項目使用compose.yml+nginx 反向代理構建,由於Caddy暫不支持,所採用Nginx.
## 3.此項目用於任何Ipv6單棧服務器/設備 請求Github相關文件時,無法訪問Github帶來的煩惱.

## 4. 如何使用
   對於Linux用戶請自行設定hosts文件將以下domain解析指向您的雙棧網路IP Address

```bash
github.com
api.github.com
codeload.github.com
ghcr.io
pkg.github.com npm.pkg.github.com maven.pkg.github.com nuget.pkg.github.com rubygems.pkg.github.com
uploads.github.com
objects.githubusercontent.com www.objects.githubusercontent.com release-assets.githubusercontent.com gist.githubusercontent.com repository-images.githubusercontent.com camo.githubusercontent.com private-user-images.githubusercontent.com avatars0.githubusercontent.com avatars1.githubusercontent.com avatars2.githubusercontent.com avatars3.githubusercontent.com cloud.githubusercontent.com desktop.githubusercontent.com support.github.com
support-assets.githubassets.com github.githubassets.com opengraph.githubassets.com github-registry-files.githubusercontent.com github-cloud.githubusercontent.com

```

Exmpore:

```bash
#### /etc/hosts
1.1.1.1 one.one.one.one
```

## build&Debug

```bash
docker compose up -d
docker compose up -d --force-recreate
docker compose logs -f
tcpdump -n -i any port 443 and ip6
```

