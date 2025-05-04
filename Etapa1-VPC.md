# 🌐 Etapa 1 – Criação da VPC Personalizada
## 🛠️ Objetivo
Criar uma VPC personalizada com sub-redes públicas e privadas, tabela de rotas, gateway de internet e NAT Gateway, preparada para suportar:

EC2 para WordPress (em sub-rede pública ou privada com acesso via Load Balancer)

RDS (em sub-rede privada)

EFS (em ambas)

Load Balancer (em sub-rede pública)

---
## 🧱 Estrutura da VPC

| Componente       | Detalhes                                      |
| ---------------- | --------------------------------------------- |
| VPC              | CIDR: `10.0.0.0/16`                           |
| Sub-rede pública | CIDR: `10.0.1.0/24` (AZ a)                    |
| Sub-rede privada | CIDR: `10.0.2.0/24` (AZ a)                    |
| Internet Gateway | Associado à VPC                               |
| Tabela de Rotas  | Pública: rota para IGW; Privada: NAT Gateway  |
| NAT Gateway      | Em sub-rede pública (acesso outbound privado) |

---
## 🔧 Passo a Passo (via Console AWS)

### 1. Criar a VPC
Ir para VPC > Your VPCs > Create VPC



<img src="https://github.com/user-attachments/assets/a67695f8-e825-4556-a77d-85f6aece8a08" alt="Image 5" width="800" height="auto">

---


<img src="https://github.com/user-attachments/assets/1e85ba37-28f6-4bec-81a6-aee1ea0e03f2" alt="Image 4" width="800" height="auto">

---



<img src="https://github.com/user-attachments/assets/0042af2b-a3a4-4cca-84ff-d8bbf12050bc" alt="Image 3" width="800" height="auto">
---

##  3. Criar Sub-redes
Criar 1 sub-rede pública: subnet-publica-a → 10.0.1.0/24 (AZ a)

Criar 1 sub-rede privada: subnet-privada-a → 10.0.2.0/24 (AZ a)

<img src="https://github.com/user-attachments/assets/a4b84bcf-5769-40e6-a875-a8edff42eed4" alt="Image 2" width="800" height="auto">

---

<img src="https://github.com/user-attachments/assets/9cec2c4e-cfb4-4d84-b071-181d79774334" alt="Image 1" width="800" height="auto">

