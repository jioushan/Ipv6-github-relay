# An IPv6 Environment GitHub Proxy — Using Docker
## 1.This project runs on a single-stack IPv6 VM.
If you are using a dual-stack network, please changes the following line in the `nginx.config` file:
```bash
    resolver [2001:4860:4860::6464] [2001:4860:4860::6444] ipv6=on;
to 
    resolver [2606:4700:4700::1001] [2606:4700:4700::1111] ipv6=on;

```

## 2.This project is built using compose.yml + Nginx reverse proxy.

## 3.Since Caddy does not currently support this scenario, Nginx is used instead.
This project is intended for any IPv6 single-stack server/device to solve issues where GitHub-related resources are inaccessible.

## 4. How to use
   For Linux system, please modify your hosts file to resolve the following domains to your dual-stack network IP address:
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

Exmpore

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
