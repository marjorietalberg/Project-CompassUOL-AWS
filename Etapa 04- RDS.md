## Criação do Banco de Dados (RDS)

---

### Criação do BD (Parte 1)

1. Abra o painel principal da AWS.
2. Pesquise por **RDS**.
3. Clique em **Databases**.


<img src="https://github.com/user-attachments/assets/59d45327-cd83-4f9e-b05f-5cf1c5113f66" alt="Imagem 9">

<img src="https://github.com/user-attachments/assets/8a5738ae-1ed9-473e-b2c7-2faba0a7a7b3" alt="Imagem 8">

---
### Etapa 2 - Criação do Banco de Dados (RDS)

1. Selecione a opção **Standard create**.
2. Em **Engine options**, selecione **MySQL**.

<img src="https://github.com/user-attachments/assets/6fe01842-e527-4a86-be7d-b6ea8a8d88b9" alt="Imagem 7">

---
### Criação do Banco de Dados (RDS) - Parte 4

1. Em **Engine version**, selecione a versão mais recente do MySQL disponível.
 2. Selecione a opção **Free tier** para usar a camada gratuita oferecida pela AWS para bancos de dados RDS.
 3.Selecione a opção **Single-AZ DB instance deployment (1 instance)** para criar uma instância de banco de dados em uma única zona de disponibilidade. 
<img src="https://github.com/user-attachments/assets/4a1aeb76-e59e-4283-8e83-b4981c4de91e" alt="Imagem 6">

---

### Criação do Banco de Dados (RDS) - Parte 5

1. **Nome da Instância de Banco de Dados**:
   - **Escolha um nome único para a sua instância de banco de dados**. No meu exemplo, foi utilizado o nome `database-project1`. Você pode nomear conforme preferir, mas lembre-se de usar um nome que seja fácil de identificar e esteja de acordo com o seu projeto.

2. **Nome de Usuário para o Banco de Dados**:
   - **Defina o nome de usuário** que será utilizado para acessar o banco de dados. No exemplo, o nome de usuário escolhido foi `admin`. Este usuário será o responsável por gerenciar e configurar o banco de dados. 
   - **Certifique-se de usar um nome de usuário que seja fácil de lembrar**, mas também que seja seguro para evitar confusão com outros sistemas.

3. **Gerenciamento de Senha**:
   - **Selecione a opção “Self managed”** para o gerenciamento da senha. Isso significa que você será responsável por criar e gerenciar a senha para o banco de dados.
   - **Crie uma senha forte e segura**. A AWS exige que a senha tenha pelo menos 8 caracteres e contenha uma combinação de letras maiúsculas, minúsculas, números e caracteres especiais. Certifique-se de escolher uma senha que seja difícil de adivinhar, mas que você consiga lembrar.
   - **Repita a senha criada** no campo de confirmação para garantir que ambas as senhas coincidam e que você possa acessar o banco de dados sem problemas.

Ao concluir essa etapa, você terá configurado a instância do banco de dados com suas credenciais de acesso, garantindo que o banco de dados esteja pronto para ser utilizado no seu projeto.

<img src="https://github.com/user-attachments/assets/3e512c81-8fa0-404b-acda-b95d4d93c4ea" alt="Imagem 5">

---

### Criação do Banco de Dados (RDS) - Parte 6

1. **Seleção da Instância de Banco de Dados**:
   - **Escolha o tipo da instância** como `db.t3.micro`. Esse tipo de instância é ideal para workloads de baixo custo e testes, adequando-se ao uso da camada gratuita da AWS (Free Tier). Ele oferece uma boa relação custo-benefício para projetos pequenos ou em fase de desenvolvimento.
   
2. **Seleção do Armazenamento**:
   - **Selecione o tipo de armazenamento “gp3”**. O gp3 é um tipo de armazenamento SSD de uso geral, oferecendo desempenho mais consistente e previsível, além de ser mais econômico que o gp2. É a melhor escolha para a maioria das aplicações que não exigem um armazenamento extremamente rápido.
   
3. **Tamanho do Armazenamento**:
   - **Defina o tamanho do armazenamento como 20 GB**. Esse é o valor padrão para um banco de dados pequeno ou de testes. Caso seu projeto precise de mais espaço de armazenamento, você pode ajustar esse valor de acordo com suas necessidades.
   
4. **Habilitação do Autoscaling**:
   - **Habilite a opção de autoscaling**. O autoscaling permite que a capacidade de armazenamento seja aumentada automaticamente conforme o uso do banco de dados cresce. Com isso, você garante que o banco de dados não fique sem espaço quando a demanda de dados aumentar.
   
5. **Defina o valor máximo de armazenamento**:
   - **Deixe o valor máximo de armazenamento como 25 GB**. Isso significa que, caso a instância de banco de dados precise expandir para acomodar mais dados, ela pode crescer automaticamente até 25 GB, evitando que você precise monitorar o uso de espaço manualmente.

Essas configurações ajudam a garantir que o banco de dados tenha desempenho suficiente para o seu projeto, sem gastar recursos excessivos.

<img src="https://github.com/user-attachments/assets/f9e6d496-5e8a-48d8-bd84-6b341987bb95" alt="Imagem 4">

---
### Criação do Banco de Dados (RDS) - Parte 7

1. **Selecione "Don't connect to an EC2 compute resource"**: 
   - Isso significa que o banco de dados não será diretamente associado a uma instância EC2 específica. Essa configuração é útil quando você deseja que o banco de dados seja acessado de outras formas (como pelo Load Balancer ou diretamente da aplicação).

2. **Selecione "IPv4"**: 
   - A escolha de IPv4 garante que a instância do banco de dados terá um endereço IP acessível na rede.

3. **Selecione a VPC criada nas etapas anteriores**:
   - Escolher a VPC garante que o banco de dados estará dentro da rede virtual configurada anteriormente, garantindo segurança e controle sobre o tráfego.

4. **Selecione "Create new DB Subnet Group"**:
   - Isso cria um novo grupo de subnets para o banco de dados, garantindo que ele tenha a infraestrutura de rede correta (com subnets públicas ou privadas conforme necessário).

<img src="https://github.com/user-attachments/assets/8e293146-e330-4b50-bf2d-c47a3bf46b0e" alt="Imagem 3">

---
### Criação do Banco de Dados (RDS) - Parte 8

1. **Selecione "No"**: 
   - Isso indica que você não deseja habilitar o backup automatizado neste momento.

2. **Selecione "Choose existing"**:
   - Aqui, você escolherá um grupo de segurança já existente para o banco de dados.

3. **Selecione o security group do banco de dados: "rds_SG"**:
   - Escolha o security group criado anteriormente para o banco de dados, garantindo que as permissões e regras de acesso estejam corretas.

4. **Selecione "No preference"**:
   - Isso indica que não há preferência por uma zona específica de disponibilidade para a instância.

5. **Selecione "default"**:
   - Escolha a configuração padrão para a instância de banco de dados, como parâmetros de rede e backup.



<img src="https://github.com/user-attachments/assets/a72f4a16-af81-49f4-99cc-160f84b3b539" alt="Imagem 2">

---

<img src="https://github.com/user-attachments/assets/931a00c1-347e-46e5-9467-1380ffc96097" alt="Imagem 1">

### Clique em Create database

---
### Observações Importantes

- **Dê um nome para o seu banco de dados**: 
  - Nome sugerido: `BDproject`
  - **Importante**: Escolher um nome claro e padronizado para o banco de dados facilita a identificação e gerenciamento, evitando confusão durante o processo de configuração.

- **Desabilite o backup automático**:
  - **Importante**: Desabilitar o backup automático é uma medida necessária para evitar custos adicionais com o serviço de backup. Como o projeto está focado em configurar a infraestrutura, não há necessidade de backups automáticos nesse momento.
  - **Dica**: Essa configuração pode ser ajustada posteriormente, caso precise de backups regulares no futuro.

Essas etapas ajudam a garantir que sua instância de banco de dados esteja corretamente configurada e sem custos desnecessários durante a implementação inicial.



