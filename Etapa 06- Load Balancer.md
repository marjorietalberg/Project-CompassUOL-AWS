# Load Balancer 
> O Load Balancer será responsável por distribuir o tráfego de rede de maneira eficiente entre as instâncias EC2 que estão rodando o WordPress. Ele vai garantir que:

> Alta disponibilidade: Se uma instância falhar, o tráfego será redirecionado para outras instâncias saudáveis.

> Balanceamento de carga: O tráfego de entrada será equilibrado entre as instâncias EC2, evitando sobrecarga em uma única instância.

> Escalabilidade: O LB facilitará a integração com Auto Scaling, que permite aumentar ou diminuir a quantidade de instâncias EC2 automaticamente de acordo com a demanda de tráfego.

---
### ✅ Etapa 1 – Criação do Load Balancer (LB)
Abra o painel principal da AWS e pesquise por Load Balancers.

Clique em "Load balancers" no menu à esquerda.

Clique em "Create Load Balancer".



<img src="https://github.com/user-attachments/assets/fe6e854d-1057-4663-8b93-5a886c3c7c0a" alt="Image">

<img src="https://github.com/user-attachments/assets/b1f2d70d-4b6a-4d71-b159-aba819c7301c" alt="Image">

---
### ✅ Etapa 2
 Clique na setinha ao lado de "Classic Load Balancer - previous generation" para expandir as opções e, em seguida, selecione Classic Load Balancer.

 Clique em "Create" para iniciar a criação do Load Balancer.
 
<img src="https://github.com/user-attachments/assets/4c29c7e8-fdd5-4d9d-8b38-4854e5cc1739" alt="Image">
<img src="https://github.com/user-attachments/assets/c7ee3658-e83b-41de-8df7-16086943555c" alt="Image">

---
### ✅ Etapa 3
Nesta etapa, você deve atribuir um nome ao Load Balancer. Abaixo, coloquei o nome que utilizei como exemplo:


<img src="https://github.com/user-attachments/assets/b98d13c1-9617-4b4d-9eb9-e9b6f403d806" alt="Image">

---

### ✅ Etapa 4
Em Scheme, selecione Internet-facing, para garantir que o Load Balancer será acessível pela internet.

Em VPC, selecione a VPC que foi criada nas etapas anteriores para garantir que o Load Balancer esteja na rede correta.


<img src="https://github.com/user-attachments/assets/a3e4f281-6c47-46d8-accc-baf813707674" alt="Image">

---

### ✅ Etapa 5
🌐 Criação do LB 
Marque o checkbox para a us-east-1a para incluir essa zona de disponibilidade.

Marque o checkbox para a us-east-1b para incluir também essa zona de disponibilidade.

Selecione a subnet pública da us-east-1a para a configuração de rede.

Selecione a subnet pública da us-east-1b para garantir alta disponibilidade.


<img src="https://github.com/user-attachments/assets/1e11070b-01a0-4b80-8073-0fd843571204" alt="Image">

---

### ✅ Etapa 6

1. Em **Ping Path**, insira o caminho: `/index.php`.

   - **Explicação**: O **Ping Path** é o caminho utilizado pelo Load Balancer para verificar se a aplicação está respondendo corretamente. No caso de uma aplicação WordPress, o arquivo `/index.php` é uma boa escolha, pois é o arquivo principal que é chamado para renderizar a página inicial do site. Quando o Load Balancer tenta acessar esse caminho, ele verifica se a aplicação está funcionando corretamente. Se o arquivo não for encontrado ou o servidor não responder, a instância será considerada "não saudável".

2. Em **Response Timeout**, defina o valor como **5** segundos.
   
3. Em **Interval**, defina o valor como **15** segundos.
   
4. Em **Unhealthy Threshold**, defina o valor como **2**.

5. Em **Healthy Threshold**, defina o valor como **3**.
   

<img src="https://github.com/user-attachments/assets/249fb2ca-b45a-4045-b0d6-c3e844c3ac1b" alt="Image">

---
### ✅ Etapa 7
#### Clique em Create load balancer
<img src="https://github.com/user-attachments/assets/f5144f4a-886b-44aa-a4a8-690308650639" alt="Image">

---
