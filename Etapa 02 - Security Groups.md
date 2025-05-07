# 🔐 Etapa: Criação dos Security Groups
No projeto, serão criados 4 Security Groups (SGs), cada um responsável por isolar e proteger um componente específico da arquitetura:

> 🖥️ Instâncias EC2

> 🗄️ Banco de Dados (RDS MySQL)

> 📁 Elastic File System (EFS)

> 🌐 Load Balancer (CLB)

---
1. **Abra o painel principal da AWS** e pesquise por **Security Groups** na barra de pesquisa.
2. **Clique em "Security Groups"** na seção de rede.
3. **Clique em "Create Security Group"** no canto superior direito.

<img src="https://github.com/user-attachments/assets/d2eb7d39-6a47-4e12-8d17-529c4ed31a5f" alt="Image">

<img src="https://github.com/user-attachments/assets/bb2b40e6-b916-45c4-91b0-0af7a17a321f" alt="Image">

---
### 📝 Observações

- **Nomes Personalizados**: Você tem a liberdade de escolher os nomes que desejar para os Security Groups. No entanto, os exemplos que estou documentando são os que utilizei para manter a consistência ao longo do projeto.
  
---

### 🔐 SG 1 - **Instâncias EC2**

Este é o Security Group destinado a controlar o tráfego de rede para as **Instâncias EC2** do seu projeto.

#### Etapas para Criar o SG das Instâncias EC2:

1. **Nome do Security Group**: Defina o nome como `ec2-sg` (ou o nome que preferir).
2. **Descrição**: Insira uma descrição simples como `ec2`.
3. **VPC**: Selecione a **VPC** que foi criada nas etapas anteriores do projeto, garantindo que todas estarão dentro da mesma rede .


<img src="https://github.com/user-attachments/assets/7c57d5d2-b3be-42e6-bb31-25ebd7f72448" alt="Image">

---
### 🔐 SG 2 - **Banco de Dados (RDS)**

Este é o **Security Group** destinado ao seu **Banco de Dados RDS**, que irá controlar o tráfego de rede entre o RDS e as instâncias EC2, garantindo a comunicação segura.

#### Etapas para Criar o SG do Banco de Dados:

1. **Nome do Security Group**: Defina o nome como `rds-SG` (ou o nome que preferir).
2. **Descrição**: Insira uma descrição simples como `banco de dados`.
3. **VPC**: Selecione a **VPC** criada nas etapas anteriores para garantir que o Security Group esteja associado à mesma rede.
4. **Clique em**: `Create security group` para finalizar a criação do Security Group.
<img src="https://github.com/user-attachments/assets/9cacb32f-45ec-4b02-bbcc-647b47355a6a" alt="Image">

---
### 🔐 SG 3 - **Elastic File System (EFS)**

Este **Security Group** é responsável pelo controle de acesso à rede do **Elastic File System (EFS)**, garantindo que o tráfego entre os containers e o EFS esteja protegido.



#### Etapas para Criar o SG do Elastic File System:

1. **Nome do Security Group**: Defina o nome como `efs-sg` (ou o nome que preferir).
2. **Descrição**: Insira uma descrição como `efs`.
3. **VPC**: Selecione a **VPC** que foi criada nas etapas anteriores, garantindo que o Security Group esteja na mesma rede.
4. **Clique em**: `Create security group` para concluir a criação do Security Group.


<img src="https://github.com/user-attachments/assets/34215fad-eb42-479a-aba1-63f0537cd17d" alt="Image">

---

### 🔐 SG 4 - **Load Balancer (LB)**

Este **Security Group** será responsável por controlar o tráfego de rede do **Load Balancer (LB)**, gerenciando a distribuição de requisições entre as instâncias EC2 e garantindo a segurança do tráfego que chega ao seu serviço.

#### Etapas para Criar o SG do Load Balancer:

1. **Nome do Security Group**: Defina o nome como `lb-sg` (ou o nome que preferir).
2. **Descrição**: Insira uma descrição como `-Load-Balancer`.
3. **VPC**: Selecione a **VPC** criada nas etapas anteriores para garantir que o Security Group esteja associado à mesma rede.
4. **Clique em**: `Create security group` para finalizar a criação do Security Group.

🔒 **Importante**: Este Security Group controlará o tráfego que chega ao seu Load Balancer, permitindo que o tráfego da internet seja redirecionado para as instâncias EC2 corretas, de acordo com as regras configuradas.


<img src="https://github.com/user-attachments/assets/d2f92fed-7fb0-49ff-99d7-1bb6662ba0d9" alt="Image">


---






<img src="https://github.com/user-attachments/assets/08626e35-f284-4895-a75e-8017fe75ebd5" alt="Image">
