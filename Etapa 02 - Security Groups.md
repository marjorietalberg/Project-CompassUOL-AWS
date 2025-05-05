# 🔐 Etapa 2 – Criação dos Security Groups (Grupos de Segurança)
## 🎯 Objetivo:
Controlar o tráfego de entrada e saída entre:

EC2 (WordPress)

Load Balancer

RDS (MySQL)

EFS (sistema de arquivos compartilhado)

---

# 🔐 1. Security Group: wordpress-ec2

| Tipo         | Protocolo | Porta | Origem                                                    |
| ------------ | --------- | ----- | --------------------------------------------------------- |
| HTTP         | TCP       | 80    | `loadbalancer-wp`                                         |
| NFS          | TCP       | 2049  | `efs-estaticos-wp` *(se tiver)*                           |
| MySQL/Aurora | TCP       | 3306  | `rds-mysql` (se usar como origem para health check/teste) |

| Tipo              | Protocolo | Porta | Destino              |
| ----------------- | --------- | ----- | -------------------- |
| Todos os tráfegos | -         | -     | `0.0.0.0/0` (padrão) |


<img src="https://github.com/user-attachments/assets/432d84d7-154f-420c-8681-9ebf89efba36" alt="Image 5" width="700">

<img src="https://github.com/user-attachments/assets/605e8f10-2216-43aa-81bd-985c28737591" alt="Image 4" width="700">

<img src="https://github.com/user-attachments/assets/20a8a6e2-6925-4869-8e95-61d678f86b8f" alt="Image 3" width="700">

<img src="https://github.com/user-attachments/assets/979c5a57-3942-4fea-8c6b-95a3a747c063" alt="Image 2" width="700">

<img src="https://github.com/user-attachments/assets/69a8e24b-6231-4b77-8239-c8637f6834d5" alt="Image 1" width="700">

---

# 🔐 2. Security Group: loadbalancer-wp

| Tipo                            | Protocolo | Porta | Origem      |
| ------------------------------- | --------- | ----- | ----------- |
| HTTP                            | TCP       | 80    | `0.0.0.0/0` |
| HTTPS (se usar SSL futuramente) | TCP       | 443   | `0.0.0.0/0` |

| Tipo              | Protocolo | Porta | Destino              |
| ----------------- | --------- | ----- | -------------------- |
| Todos os tráfegos | -         | -     | `0.0.0.0/0` (padrão) |

<img src="https://github.com/user-attachments/assets/c3a3b5d4-51c1-4ed5-a5a6-b24b58aa481d" alt="Image 1" width="700">
<img src="https://github.com/user-attachments/assets/b30969c5-a59a-4bc3-bd27-164861022795" alt="Image 2" width="700">
<img src="https://github.com/user-attachments/assets/8bb86f99-811f-404a-82be-09818bdbfb42" alt="Image 3" width="700">



---





# 🔐 3. Security Group: rds-mysql

### ✅ Entrada (Inbound):

| Tipo         | Protocolo | Porta | Origem          |
| ------------ | --------- | ----- | --------------- |
| MySQL/Aurora | TCP       | 3306  | `wordpress-ec2` |

### ✅ Saída (Outbound):

| Tipo              | Protocolo | Porta | Destino              |
| ----------------- | --------- | ----- | -------------------- |
| Todos os tráfegos | -         | -     | `0.0.0.0/0` (padrão) |

<img src="https://github.com/user-attachments/assets/4eeae423-5d50-48cf-b650-2a5bb3201095" alt="Image 3" width="700">
<img src="https://github.com/user-attachments/assets/bb3b5a37-9f98-4830-bee7-073214ed14fb" alt="Image 2" width="700">
<img src="https://github.com/user-attachments/assets/668e327f-713c-4187-a54c-28e050c7708b" alt="Image 1" width="700">



---
# 🔐 4. (Opcional) Security Group: efs-wordpress

### ✅ Entrada (Inbound):
| Tipo | Protocolo | Porta | Origem          |
| ---- | --------- | ----- | --------------- |
| NFS  | TCP       | 2049  | `wordpress-ec2` |

### ✅ Saída (Outbound):
| Tipo              | Protocolo | Porta | Destino              |
| ----------------- | --------- | ----- | -------------------- |
| Todos os tráfegos | -         | -     | `0.0.0.0/0` (padrão) |

<img src="https://github.com/user-attachments/assets/de21eb8b-d1d1-4e7e-bb69-f4b7be5b5e3f" alt="Image 3" width="700">
<img src="https://github.com/user-attachments/assets/b852c3ef-0333-4000-89e1-6d11131fb034" alt="Image 2" width="700">
<img src="https://github.com/user-attachments/assets/d3d1a7c4-59db-4330-9023-99940e58882e" alt="Image 1" width="700">





---


