## Launch Template  
### Criação Launch Template  (parte 1)

1. Abra o **painel principal da AWS**.
2. No campo de busca, digite **EC2** e selecione o serviço.
3. No menu lateral esquerdo, vá até a seção **Instances** e clique em **Launch templates**.

> ⚠️ Essa etapa é essencial para que possamos lançar instâncias EC2 com configurações pré-definidas nos próximos passos!

<img src="https://github.com/user-attachments/assets/f7897045-1ec7-4a7e-85df-52c7979ece5b" alt="Image">

---
### Criação do Launch Template (parte 2)

4. Clique no botão **Create launch template**.


<img src="https://github.com/user-attachments/assets/62a1633f-2952-45f6-ba7f-88c365efb61c" alt="Image">

---
### Criação do Launch Template (Parte 2)

1. **Escolha um nome para o Launch Template**  
   Você pode optar por qualquer nome que preferir. Para este exemplo, usamos:  
   **Nome do Template**: `MyTemplateWordPress`.

2. **Dê uma descrição ao template**  
   Adicione uma descrição breve para identificar o propósito do template. Exemplo:  
   **Descrição**: `Template `.

3. **Marque o checkbox**  
   Marque a opção conforme necessário. No caso, marque o checkbox para **"Enable "Associate with Auto Scaling group"** (ou similar, dependendo da sua configuração).

<img src="https://github.com/user-attachments/assets/991e638a-cc75-4dc2-9fb3-cb964c4b70fe" alt="Image">

---

### Criação do Launch Template (Parte 4)

1. **Selecione o Sistema Operacional**  
   No campo de escolha do sistema operacional, selecione **Ubuntu** para a instância. Isso definirá a base do seu ambiente.

2. **Escolha o Tipo da Instância**  
   Para o tipo de instância, selecione **t2.micro**, que é adequado para projetos pequenos e se enquadra dentro do plano gratuito da AWS.

3. **Selecione a Key Pair**  
   Em **Key pair**, selecione a chave que será usada para acessar a instância de forma segura via SSH. Se você ainda não tiver uma chave configurada, pode criar uma nova na AWS.

### Criação do Launch Template (Parte 5)

1. **Configuração da Subnet**  
   Em **Subnet**, selecione **Don't include in launch template**. Isso indica que a seleção da subnet será configurada manualmente quando a instância for lançada, permitindo mais flexibilidade para ajustes futuros.

2. **Configuração do Firewall**  
   Em **Firewall**, selecione **Select existing security group** para utilizar um security group já criado.  
   - Em seguida, selecione o **security group da instância**: **ec2_SG**. Esse grupo de segurança garantirá as permissões adequadas para a instância.

<img src="https://github.com/user-attachments/assets/fbeb118a-2218-4c9d-b8db-15cfb04de7fe" alt="Image">


<img src="https://github.com/user-attachments/assets/062f7e88-2686-450d-8eea-4cf3e4d37975" alt="Image">

---
### Criação do Launch Template (Parte 6)

### Criação do Launch Template (Parte 6)

1. **Adicionar Tags**  
   Clique em **Add new tag** para incluir as tags necessárias ao seu template.  
   - **Importante**: Por questões de segurança, não posso compartilhar os valores exatos das tags. No entanto, é fundamental adicionar tags relevantes para organização e rastreabilidade dos seus recursos na AWS.

As tags são cruciais para manter seus recursos bem organizados e facilitar a gestão, especialmente em projetos com múltiplos ambientes ou recursos.

<img src="https://github.com/user-attachments/assets/88767fe8-7f8a-4795-8321-dc39b7cf32c1" alt="Image">

---
```bash
#!/bin/bash

# Variáveis
EFS_FILE_SYSTEM_ID="<seu_file_id>"  
DB_HOST="<seu_host_do_banco_de_dados>"  
DB_NAME="<seu_nome_do_banco_de_dados>"  
DB_USER="<seu_usuario_do_banco>"  
DB_PASSWORD="<sua_senha_do_banco>"  
DOCKER_COMPOSE_VERSION="v2.34.0"
PROJECT_DIR="/home/ec2-user/projeto-docker"
EFS_MOUNT_DIR="/mnt/efs"  

# Atualizações e instalações básicas
yum update -y
yum install -y aws-cli

# Instalação e configuração do Docker
yum install -y docker
service docker start
systemctl enable docker
usermod -a -G docker ec2-user

# Instalação do Docker Compose
curl -SL https://github.com/docker/compose/releases/download/${DOCKER_COMPOSE_VERSION}/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose

# Instalação e montagem do EFS
yum install -y amazon-efs-utils
mkdir -p ${EFS_MOUNT_DIR}
mount -t efs ${EFS_FILE_SYSTEM_ID}:/ ${EFS_MOUNT_DIR}
echo "${EFS_FILE_SYSTEM_ID}:/ ${EFS_MOUNT_DIR} efs defaults,_netdev 0 0" >> /etc/fstab

# Permissões corretas para WordPress (usuário 33 = www-data no container)
chown -R 33:33 ${EFS_MOUNT_DIR}

# Preparação do projeto
mkdir -p ${PROJECT_DIR}
cd ${PROJECT_DIR}

# docker-compose.yml
cat > docker-compose.yml <<EOL
version: '3.7'
services:
  wordpress:
    image: wordpress:latest
    container_name: wordpress
    environment:
      WORDPRESS_DB_HOST: ${DB_HOST}
      WORDPRESS_DB_NAME: ${DB_NAME}
      WORDPRESS_DB_USER: ${DB_USER}
      WORDPRESS_DB_PASSWORD: ${DB_PASSWORD}
    ports:
      - 80:80
    volumes:
      - ${EFS_MOUNT_DIR}:/var/www/html

volumes:
  wordpress_data:
EOL

# Inicialização do WordPress
docker-compose up -d
```
