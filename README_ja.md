# DockerとAnsibleのサンプル (nginx, MySQL, Laravel, Next.js)

DockerとAnsibleで構築した環境に、LaravelとNext.jsアプリケーションをデプロイするサンプルです。

サーバ1台に全て入れます。

脆弱性を含むバージョンで構築します。

## 構成

| 構成物      | バージョン  |                                脆弱性                                | 備考 |
|:---------|:------:|:-----------------------------------------------------------------:|:---| 
| nginx    | 1.22.0 | [CVE-2022-41741](https://www.cve.org/CVERecord?id=CVE-2022-41741) |    |
| PHP      | 8.2.7  |  [CVE-2023-3823](https://www.cve.org/CVERecord?id=CVE-2023-3823)  |    |
| Composer | latest |                                                                   |    |
| Laravel  |  8.x   | [CVE-2022-40482](https://www.cve.org/CVERecord?id=CVE-2022-40482) |    |
| Node.js  | 18.x.x |                                                                   |    |
| npm      | 10.x.x |                                                                   |    |
| Next.js  | 12.0.8 | [CVE-2022-21721](https://www.cve.org/CVERecord?id=CVE-2022-21721) |    |

# 使用方法

1. コンテナを起動し、webコンテナに入る。

    ```shell
    docker compose up -d
    docker exec -it web /bin/bash
    ```

2. webコンテナ内で以下のコマンドを実行する。

    ```shell
    cd /opt/ansible
    ansible-playbook install.yml
    ansible-playbook deploy.yml
    ```

3. https://localhost:8443/ にアクセスする。
