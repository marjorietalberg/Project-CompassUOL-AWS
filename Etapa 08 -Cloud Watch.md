### 🚀 Criação do Automatic Scaling (Parte 1)

1. Acesse o painel da **AWS** e vá até **EC2 > Auto Scaling Groups**.  
2. Marque o checkbox correspondente ao seu **Auto Scaling Group (ASG)**.  
3. No canto inferior da tela, clique em **Automatic scaling**.  
4. Selecione **Create dynamic scaling policy**.
 <img src="https://github.com/user-attachments/assets/970a9f23-e60f-490e-9ab9-858e423fe626" alt="Image">
 
 ---
### 📈 Criação do CloudWatch Alarm (Parte 1)

1. No painel principal da **AWS**, pesquise por **CloudWatch**.  
2. No menu lateral, clique em **Alarms**.


<img src="https://github.com/user-attachments/assets/ea3af3de-44a7-4cfc-87fe-b500fb326863" alt="Image">

---

#### Clique em Select metric

<img src="https://github.com/user-attachments/assets/ff41511d-9e68-4d92-8396-a92f1e258428" alt="Image">

---

3. Clique em **EC2** para visualizar métricas relacionadas às instâncias.
<img src="https://github.com/user-attachments/assets/187fee9e-4075-4c90-ad7b-7441dcb67bd1" alt="Image">

---
#### Clique em By Auto Scaling Group

<img src="https://github.com/user-attachments/assets/713a5cdd-7401-4b88-9acd-ec3559a97f28" alt="Image">

---

<img src="https://github.com/user-attachments/assets/8d370840-5597-48d9-9fe2-b3bb448fb45b" alt="Image">

---
### 4. Selecione **CPUUtilization**  
### 5. Clique em **Select metric**

<img src="https://github.com/user-attachments/assets/daec444b-d2eb-4f95-a877-5ca8138de5f9" alt="Image">

---

<img src="https://github.com/user-attachments/assets/832e0973-d72a-4215-87a3-10ed1a325a9e" alt="Image">

---
### Criação CW (parte 12)

1. Em **Alarm state trigger**, selecione **In alarm**  
2. Em **Send a notification to**, selecione **EC2 Auto Scaling group**  
3. Escolha o Auto Scaling Group criado anteriormente  
4. Selecione a opção para aplicar às **2 instâncias**

<img src="https://github.com/user-attachments/assets/62689e31-5db1-4463-84b7-45dd7f09309d" alt="Image">

---

<img src="https://github.com/user-attachments/assets/95061448-e1cd-4b90-84e5-62b5fd026c8d" alt="Image">

---

<img src="https://github.com/user-attachments/assets/e566e487-dca5-4969-a011-3e4df8622681" alt="Image">

---

<img src="https://github.com/user-attachments/assets/b2ff69ea-0a5e-40b7-b5b4-92e7816d0cce" alt="Image">

> ⚠️ **Observações Importantes**

✅ Após finalizar, você verá uma **mensagem de sucesso**.  
⏳ Aguarde até que o estado do seu alarme mude para **OK** — isso indica que ele foi configurado corretamente.  
🎯 Seguindo todos esses passos, o CloudWatch Alarm estará pronto e funcional!










