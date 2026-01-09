# IPv6 環境向け GitHub プロキシ — Docker 使用
## 本プロジェクトは IPv6 シングルスタック VM 上で動作します。デュアルスタック環境をお使いの場合は、`nginx.config` 内の以下の設定を置き換えてください。
```bash
    resolver [2001:4860:4860::6464] [2001:4860:4860::6444] ipv6=on;
を以下に変更します。 
    resolver [2606:4700:4700::1001] [2606:4700:4700::1111] ipv6=on;

```

## 2.本プロジェクトは compose.yml + Nginx リバースプロキシ を使用して構築されています。 Caddy は現時点で本構成に対応していないため、Nginx を採用しています。

## 3.本プロジェクトは、IPv6 シングルスタックのサーバー／デバイスにおいてGitHub 関連リソースへアクセスできない問題を解決することを目的としています。

## 4. 使用方法
   Linux ユーザーは、以下のドメインを デュアルスタックネットワークの IP アドレス に向けて `hosts` ファイルを設定してください。
   
```
github.com
api.github.com
codeload.github.com
ghcr.io
pkg.github.com npm.pkg.github.com maven.pkg.github.com nuget.pkg.github.com rubygems.pkg.github.com
uploads.github.com
objects.githubusercontent.com www.objects.githubusercontent.com release-assets.githubusercontent.com gist.githubusercontent.com repository-images.githubusercontent.com camo.githubusercontent.com private-user-images.githubusercontent.com avatars0.githubusercontent.com avatars1.githubusercontent.com avatars2.githubusercontent.com avatars3.githubusercontent.com cloud.githubusercontent.com desktop.githubusercontent.com support.github.com
support-assets.githubassets.com github.githubassets.com opengraph.githubassets.com github-registry-files.githubusercontent.com github-cloud.githubusercontent.com
```
れい:
# /etc/hosts
1.1.1.1 one.one.one.one


