
# 🌐  Criação da VPC Personalizada
> A VPC será responsável por:

> Criar um ambiente seguro e controlado para a aplicação WordPress;

> Permitir o tráfego de internet apenas pelo Load Balancer, evitando IPs públicos nas instâncias;

> Conectar de forma privada a instância EC2, o banco de dados RDS e o armazenamento EFS;

> Garantir que os componentes da infraestrutura fiquem organizados e em sub-redes apropriadas (públicas ou privadas).


### 🔹 Etapa 1 - Acesse o serviço de VPC

1. No Console da AWS, pesquise por **VPC** no campo de busca.
2. Clique em **VPC Dashboard** (Painel de VPC).
3. Em seguida, clique em **Create VPC**.

<img src="https://github.com/user-attachments/assets/a53e1b82-c09b-4fe5-b1c8-924baf2a5f60" alt="Image">
<img src="https://github.com/user-attachments/assets/61462f2f-99c2-4459-b558-3686c3ab5993" alt="Image">

---
### 🔹 Etapa 2 - Configuração da VPC

1. Em **Name tag**, insira um nome para sua VPC.  
   _Exemplo_: `vpc-project2`

2. Em **IPv4 CIDR block**, defina o bloco de endereços IP.  
   _Exemplo_: `10.0.0.0/16`

 <img src="https://github.com/user-attachments/assets/39ce202a-8176-4b62-94a4-133b8a3616ef" alt="Image">

---

### 🔹 Etapa 2 - Configuração de Sub-redes e Zonas de Disponibilidade

Durante a criação da VPC, configure os seguintes parâmetros para garantir uma infraestrutura balanceada e segura:

- **Availability Zones (AZs)**:  
  ➤ Selecione **2** zonas de disponibilidade  
  ✅ *Importante: Certifique-se de que sejam* `us-east-1a` *e* `us-east-1b`

- **Número de subnets públicas**:  
  ➤ Selecione **2**

- **Número de subnets privadas**:  
  ➤ Selecione **2**

- **NAT Gateways**:  
  ➤ Selecione **1 por AZ** (para permitir que as instâncias em subnets privadas acessem a internet de forma segura)

- **VPC Endpoints**:  
  ➤ Selecione **None** (nenhum endpoint será criado nesta etapa)

---
<img src="https://github.com/user-attachments/assets/68343ab7-5dc3-4701-b1b8-fb82e91f2a28" alt="Image">

<img src="https://github.com/user-attachments/assets/6afe4c23-ca1d-477c-a1ee-d9b8b2875d07" alt="Image">

 🟩 Etapa Final

- Clique no botão **Create VPC**

---

### ✅ Se tudo estiver correto, confirme clicando em **Create VPC**.

📎 **Dica**:  
Você poderá visualizar e editar essa VPC em **VPC > Your VPCs** assim que ela for criada com sucesso.

 ---

  <img src="https://github.com/user-attachments/assets/b533d40d-1358-4991-88d5-a1379dd26523" alt="Image">
  
--- 

###  📌 **Resultado esperado**:  
Ao final desta configuração, você terá uma VPC com:
- 2 AZs distintas,
- 2 subnets públicas,
- 2 subnets privadas,
- 2 NAT Gateways (1 por AZ),
- Preparada para distribuir sua aplicação com alta disponibilidade e segurança de rede.
