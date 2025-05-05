# 🔐 Etapa 2 – Criação dos Security Groups (Grupos de Segurança)
## 🎯 Objetivo:
Controlar o tráfego de entrada e saída entre:

EC2 (WordPress)

Load Balancer

RDS (MySQL)

EFS (sistema de arquivos compartilhado)

---
⚙️ 2. SG - Load Balancer

| Tipo           | Protocolo | Porta | Origem                            |
| -------------- | --------- | ----- | --------------------------------- |
| HTTP           | TCP       | 80    | `sg-loadbalancer`                 |
| HTTPS          | TCP       | 443   | `sg-loadbalancer` (se usar SSL)   |
| SSH (opcional) | TCP       | 22    | Seu IP local (ex: `177.x.x.x/32`) |
| EFS            | TCP       | 2049  | `sg-efs`                          |
| MySQL          | TCP       | 3306  | `sg-rds`                          |

---
## 🔐 1. Security Group: loadbalancer-wp

| Tipo                            | Protocolo | Porta | Origem      |
| ------------------------------- | --------- | ----- | ----------- |
| HTTP                            | TCP       | 80    | `0.0.0.0/0` |
| HTTPS (se usar SSL futuramente) | TCP       | 443   | `0.0.0.0/0` |

| Tipo              | Protocolo | Porta | Destino              |
| ----------------- | --------- | ----- | -------------------- |
| Todos os tráfegos | -         | -     | `0.0.0.0/0` (padrão) |



---

## 🔐 2. Security Group: wordpress-ec2

| Tipo         | Protocolo | Porta | Origem                                                    |
| ------------ | --------- | ----- | --------------------------------------------------------- |
| HTTP         | TCP       | 80    | `loadbalancer-wp`                                         |
| NFS          | TCP       | 2049  | `efs-estaticos-wp` *(se tiver)*                           |
| MySQL/Aurora | TCP       | 3306  | `rds-mysql` (se usar como origem para health check/teste) |

| Tipo              | Protocolo | Porta | Destino              |
| ----------------- | --------- | ----- | -------------------- |
| Todos os tráfegos | -         | -     | `0.0.0.0/0` (padrão) |



