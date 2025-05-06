

<div align="center">
  <table>
    <tr>
      <td align="center" style="padding-right: 10px;">
        <a href="https://skillicons.dev">
          <img src="https://skillicons.dev/icons?i=aws" alt="AWS Skills" width="150">
        </a>
      </td>
      <td align="left" style="vertical-align: middle;">
        <h1 style="display:inline; color:#FF4C4C;">🔐 Etapa 2  </h1>
        <h1 style="display:inline; color:#1E90FF;">Criação dos Security Groups (Grupos de Segurança)</h1>
      </td>
    </tr>
  </table>
</div>


## 🎯 Objetivo:
Controlar o tráfego de entrada e saída entre:

EC2 (WordPress)

Load Balancer

RDS (MySQL)

EFS (sistema de arquivos compartilhado)

---

<img src="https://github.com/user-attachments/assets/432d84d7-154f-420c-8681-9ebf89efba36" alt="Image 5" width="700">

<img src="https://github.com/user-attachments/assets/605e8f10-2216-43aa-81bd-985c28737591" alt="Image 4" width="700">


<img src="https://github.com/user-attachments/assets/8971a23e-af85-4453-84e0-99e78ce4c417" alt="Image 1" width="700">


  <img src="https://github.com/user-attachments/assets/a0eb2c2f-811e-4ab9-b9ea-a6018fb5d628" alt="Imagem 2" width="700">

  <img src="https://github.com/user-attachments/assets/f2e1a931-cf46-4b98-b72f-c242c11afc97" alt="Imagem 1" width="700">


### 📥 Regras de entrada (Inbound):
| Tipo | Porta | Origem         | Motivo                             |
|------|-------|----------------|------------------------------------|
| SSH  | 22    | Seu IP (ou Bastion) | Receber tráfego do Load Balancer |
| HTTP | 80    | lb_SG          | Acesso para manutenção             |
| NFS  | 2049  | efs_SG         | Montagem do EFS                    |



### 📤 Regras de saída (Outbound):

| Tipo        | Porta | Destino               | Motivo                                             |
|-------------|-------|------------------------|----------------------------------------------------|
| All traffic | All   | 0.0.0.0/0 (via NAT)    | Baixar pacotes, updates, conectar ao RDS, etc     |

---








# 🔐 2. Security Group: loadbalancer-wp
### 📥 INBOUND RULES
| Tipo | Porta | Origem     | Motivo                          |
|------|-------|------------|---------------------------------|
| HTTP | 80    | 0.0.0.0/0  | Receber tráfego da internet     |


### 📤 OUTBOUND RULES

| Tipo | Porta | Destino | Motivo                                |
|------|-------|---------|----------------------------------------|
| HTTP | 80    | ec2_SG  | Encaminhar requisições para EC2s      |

<img src="https://github.com/user-attachments/assets/c3a3b5d4-51c1-4ed5-a5a6-b24b58aa481d" alt="Image 1" width="700">
<img src="https://github.com/user-attachments/assets/b30969c5-a59a-4bc3-bd27-164861022795" alt="Image 2" width="700">
<img src="https://github.com/user-attachments/assets/8bb86f99-811f-404a-82be-09818bdbfb42" alt="Image 3" width="700">

### Recebe o tráfego da internet
Função: expõe o Load Balancer para acesso público (HTTP)

📥 Regras de entrada (Inbound):

Porta 80 (HTTP) – de 0.0.0.0/0 (acesso público)

Porta 443 (HTTPS) – opcional, se usar SSL

📤 Regras de saída (Outbound):

Todas as portas liberadas (0.0.0.0/0) – padrão do AWS SG



---





















# 🔐 3. Security Group: rds-mysql

### ✅ Entrada (Inbound):

| Tipo         | Protocolo | Porta | Origem          |
| ------------ | --------- | ----- | --------------- |
| MySQL/Aurora | TCP       | 3306  | `wordpress-ec2` |

### ✅ Saída (Outbound):

| Tipo        | Porta | Origem   | Motivo                       |
|-------------|-------|----------|------------------------------|
| MySQL/Aurora| 3306  | ec2      | Permitir acesso do WordPress |

<img src="https://github.com/user-attachments/assets/4eeae423-5d50-48cf-b650-2a5bb3201095" alt="Image 3" width="700">
<img src="https://github.com/user-attachments/assets/9c245968-46fe-460c-a262-88f83ab6161a" alt="Imagem">

<img src="https://github.com/user-attachments/assets/3b9d0a27-8ca3-49be-ac11-7adec1038326" alt="Imagem" width="700">



### Função: protege o banco de dados

📥 Regras de entrada (Inbound):

Porta 3306 (MySQL) – APENAS do SG da instância EC2 (sg-wordpress-ec2)


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


### Função: permite montagem de volume NFS

📥 Regras de entrada (Inbound):

Porta 2049 (NFS) – APENAS do SG da instância EC2

📤 Regras de saída (Outbound):

Todas as portas liberadas – padrão


---


