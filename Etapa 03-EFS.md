# Criação  Amazon EFS (Elastic File System)

## Conceitos básicos :
O Amazon EFS é um sistema de arquivos escalável, elástico e totalmente gerenciado, que permite compartilhar dados entre várias instâncias EC2 simultaneamente, como se fosse um pendrive em rede (NFS).
🔹 Diferente do EBS (ligado a uma instância), o EFS pode ser montado em várias EC2 ao mesmo tempo, ideal para ambientes como WordPress com múltiplas instâncias.

---
### Criação do EFS (parte 1)

1. **Abra o painel principal da AWS e pesquise por EFS**:
   - No menu de pesquisa da AWS, digite "EFS" para encontrar o serviço Elastic File System.
   
2. **Clique em File systems**:
   - Ao encontrar o serviço Elastic File System, clique na opção **File systems** no menu à esquerda. Isso o levará à interface onde você pode gerenciar todos os sistemas de arquivos EFS existentes ou criar novos.

<img src="https://github.com/user-attachments/assets/b940c290-c511-436c-b4dd-752d60b7ac27" alt="Image 5">

<img src="https://github.com/user-attachments/assets/9378a141-d816-46de-8404-29af0bc2e297" alt="Image 4">

---
### Criação do EFS (parte 3)

1. **Dê um nome para o file system**:
   - Escolha um nome para o seu sistema de arquivos EFS. 

2. **Selecione a VPC criada anteriormente**:
   - Na seção de configurações de rede, selecione a **VPC** que você criou nas etapas anteriores. Isso garantirá que o EFS esteja conectado à rede correta da sua infraestrutura.

<img src="https://github.com/user-attachments/assets/3ddbf688-da87-4f13-bfa6-556ec39bcff8" alt="Image 3">

---
### Criação do EFS (parte 4)

1. **Confira o nome do seu EFS**:
   - Verifique se o nome do sistema de arquivos está correto. Se desejar, você pode alterar o nome para outro de sua preferência.

2. **Em "File system type"**, selecione **Regional**:
   - Escolha o tipo de sistema de arquivos como **Regional**. Isso significa que o EFS será acessível em todas as zonas de disponibilidade (AZs) dentro da região selecionada.

3. **Desabilite o checkbox "Enable automatic backups"**:
   - Para evitar custos adicionais e manter o controle sobre os backups, desmarque a opção **Enable automatic backups**. Dessa forma, o backup automático não será ativado para o sistema de arquivos EFS.

<img src="https://github.com/user-attachments/assets/fa73b210-1bcd-40bd-b240-41e3c9c540d5" alt="Image 2">

---

4. **Em "Throughput mode"**, selecione **Bursting**:
   - O modo **Bursting** é o mais adequado para a maioria dos casos de uso, permitindo que o sistema de arquivos aumente temporariamente a taxa de transferência conforme necessário, com base no armazenamento utilizado.

5. **Em "Performance mode"**, selecione **General Purpose (Recommended)**:
   - O **General Purpose** é o modo de desempenho recomendado para a maioria dos casos de uso. Ele oferece baixa latência e alta taxa de I/O, ideal para sistemas de arquivos que exigem alta performance e acessos frequentes.

<img src="https://github.com/user-attachments/assets/0dece95f-21e1-46a9-b2f2-231cbf0f3572" alt="Image 1">

---
### Criação do EFS (parte 5)

1. **Selecione as subnets privadas**:
   - **Selecione a VPC criada anteriormente**: Escolha a VPC que foi configurada nas etapas anteriores.
   
2. **Selecione as Availability Zones (AZs)**:
   - **Selecione us-east-1a** e **us-east-1b**.

3. **Selecione as subnets privadas**:
   - **Selecione a subnet privada da us-east-1a**: Escolha a subnet privada na AZ us-east-1a.
   - **Selecione a subnet privada da us-east-1b**: Escolha a subnet privada na AZ us-east-1b.

4. **Escolha o Security Group do EFS**:
   - Selecione o **Security Group do EFS**: `efs_SG`.

5. **Clique em "Next"** para continuar a configuração.
<img src="https://github.com/user-attachments/assets/c5b64129-b108-4df0-8791-454c8ce4172b" alt="Image">

---
### Na página que abrir, só clique em **next**
<img src="https://github.com/user-attachments/assets/930b191a-60ca-4046-a95d-c58198ebeecb" alt="Image">

---

> ⚠️ **Importante!**
> 
> Anote o **ID do File System** gerado após a criação do EFS.
> 
> 📝 **Você vai precisar dessa informação no script de inicialização (`UserData`) da sua instância EC2**, para montar o EFS corretamente. 
> 
> Exemplo do formato: `fs-12345678`

<img src="https://github.com/user-attachments/assets/85b26625-7d94-4311-94dc-8a55290dae86" alt="Image">
