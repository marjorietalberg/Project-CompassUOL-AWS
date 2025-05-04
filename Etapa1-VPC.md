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
