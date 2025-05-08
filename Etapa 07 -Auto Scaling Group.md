### Criação do Auto Scaling Group (Parte 1)

1. **Abra o painel principal da AWS**: Acesse o console da AWS e, na barra de pesquisa superior, digite "**Auto Scaling Groups**".
   
2. **Selecione "Auto Scaling Groups"**: Nos resultados de pesquisa, clique em **Auto Scaling Groups**, que é a opção responsável por gerenciar a escalabilidade automática de suas instâncias EC2.
   
   Essa etapa irá levar você à página de grupos de escalabilidade, onde poderá visualizar, configurar e gerenciar suas instâncias EC2 de maneira eficiente.

3. **Clique em "Create Auto Scaling Group"**: Na tela que se abrirá, procure pelo botão **Create Auto Scaling Group** no canto superior direito e clique nele para começar a configuração do seu grupo de escalabilidade.

Essa ação dará início ao processo de criação de um grupo de escalabilidade, essencial para garantir que a quantidade de instâncias EC2 possa ser ajustada automaticamente de acordo com a demanda do seu aplicativo.

 <img src="https://github.com/user-attachments/assets/0eafd1e0-70af-4cc0-a8e6-f4d38786d834" alt="Image">
<img src="https://github.com/user-attachments/assets/326e9b7b-c68a-4d15-9bb8-5d8dcbc13902" alt="Image">

---
4. **Nome do Auto Scaling Group**:
   - Nome sugerido: `grupo-project` (você pode escolher o nome que preferir).

5. **Selecione o Launch Template**:
   - Escolha o template criado nas etapas anteriores.

6. **Versão**:
   - Selecione a versão **Default**.

<img src="https://github.com/user-attachments/assets/6600938e-1166-4e88-8332-da6d7d9da9db" alt="Image">

---

7. **Clique em "Next"**:
   - Após selecionar as configurações, clique em **Next** para continuar o processo.

<img src="https://github.com/user-attachments/assets/20f87c83-be00-485f-9a8e-ab6fb6301650" alt="Image">

---

8. **Selecione a VPC criada nas etapas anteriores**:
   - Escolha a VPC que você configurou nas etapas anteriores.

9. **Selecione as subnets privadas**:
   - Escolha as subnets privadas para o Auto Scaling Group.

10. **Selecione "Balanced best effort"**:
    - Essa opção equilibra desempenho e custo.

11. **Clique em "Next"**:
    - Prossiga para a próxima etapa.

<img src="https://github.com/user-attachments/assets/611f2364-d6e5-4a67-8bcf-a549bbabf8b5" alt="Image">
<img src="https://github.com/user-attachments/assets/745dc0d5-7e1b-43d9-a93a-05fd226abc38" alt="Image">

---
1. **Selecione "Attach to an existing load balancer"**:
   - Marque essa opção para associar o Auto Scaling Group a um Load Balancer existente.

2. **Selecione "Choose from Classic Load Balancers"**:
   - Escolha essa opção para visualizar os Classic Load Balancers disponíveis.

3. **Selecione o Load Balancer criado nas etapas anteriores**:
   - Selecione o Load Balancer que foi configurado em etapas anteriores do processo.

<img src="https://github.com/user-attachments/assets/82638904-9ed4-4b1a-aa0d-cf633b7df850" alt="Image">

---
4. **Selecione "No VPC Lattice service to attach"**:
   - Escolha esta opção para não associar nenhum serviço do VPC Lattice ao Auto Scaling Group.

<img src="https://github.com/user-attachments/assets/25f5f770-1877-4059-bbe2-6fb14cf834ca" alt="Image">

---
5. **Health check grace period**:
   - Selecione o tempo desejado, sendo o valor padrão de 300 segundos.

6. **Marque o checkbox**:
   - **Turn on Elastic Load Balancing health checks**.

7. **Clique em Next** para continuar.

<img src="https://github.com/user-attachments/assets/09d5eb71-9141-4417-9a0f-518720fa7bb7" alt="Image">

---
8. **Desired capacity**:
   - Coloque o valor **2**.

9. **Min desired capacity**:
   - Coloque o valor **2**.

10. **Max desired capacity**:
    - Coloque o valor **4**.

11. **Selecione**: 
    - **No scaling policies**.

12. **Clique em Next** para continuar.

<img src="https://github.com/user-attachments/assets/33bc2a57-efb3-4065-a50f-21ed13de87d0" alt="Image">
<img src="https://github.com/user-attachments/assets/ebdd2080-68e0-4ce6-b960-18b42ccbb134" alt="Image">
<img src="https://github.com/user-attachments/assets/113f0e4a-c1d6-4828-95ec-6b2195572e3a" alt="Image">

---
13. **Marque o checkbox** Enable group metrics collection within CloudWatch
14. **Clique em Next**

<img src="https://github.com/user-attachments/assets/cf64d019-6c95-4ef2-927f-b45fbea4a6dd" alt="Image">










