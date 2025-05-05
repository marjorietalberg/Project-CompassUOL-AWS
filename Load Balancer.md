# Passo a Passo para Criar um Load Balancer (ALB)
## ✅ Pré-requisitos
Antes de começar, verifique:

Você tem 2 ou mais sub-redes públicas (em zonas de disponibilidade diferentes).

As instâncias EC2 que deseja balancear estão rodando na VPC.

As portas 80 (HTTP) estão abertas no grupo de segurança das instâncias.

Você já criou ou vai criar um Auto Scaling Group (opcional, mas ideal para produção).

## 1️⃣ Acesse o Console AWS > EC2 > Load Balancers
2️⃣ Clique em "Create Load Balancer"
Escolha:
✅ Application Load Balancer

Ideal para aplicações web (HTTP/HTTPS)

