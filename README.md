# Docker and Ansible Sample (nginx, MySQL, Laravel, Next.js)

This is a sample for deploying a Laravel and Next.js application in an environment built with Docker and Ansible.

Everything will be installed on a single server.

The environment is constructed using versions that contain vulnerabilities.

## Components

| Component | Version |                           Vulnerability                           | Note |
|:----------|:-------:|:-----------------------------------------------------------------:|:-----|
| nginx    | 1.22.0 | [CVE-2022-41741](https://www.cve.org/CVERecord?id=CVE-2022-41741) |    |
| PHP      | 8.2.7  |  [CVE-2023-3823](https://www.cve.org/CVERecord?id=CVE-2023-3823)  |    |
| Composer | latest |                                                                   |    |
| Laravel  |  8.x   | [CVE-2022-40482](https://www.cve.org/CVERecord?id=CVE-2022-40482) |    |
| Node.js  | 18.x.x |                                                                   |    |
| npm      | 10.x.x |                                                                   |    |
| Next.js  | 12.0.8 | [CVE-2022-21721](https://www.cve.org/CVERecord?id=CVE-2022-21721) |    |

# Usage

1. Start the container and enter the web container.

    ```shell
    docker compose up -d
    docker exec -it web /bin/bash
    ```
2. Inside the web container, run the following commands.

    You can choose project type from the following.

    ```shell
    cd /opt/ansible
    ansible-playbook install.yml
    ansible-playbook deploy.yml
    ```

3. Access https://localhost:8443/ .
