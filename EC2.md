


  <img src="https://github.com/user-attachments/assets/cbf9cef9-3ae4-42ce-8a16-3bcb9fa648e3" >

# 🚀 Configuração da EC2 
### ✅ Objetivo:
Provisionar uma instância EC2 para hospedar o container Docker com a aplicação WordPress.

---
📌 Observações:
A instância foi criada com Ubuntu para maior compatibilidade com pacotes Docker.

Será utilizada posteriormente para:

Instalar o Docker.

Configurar o container WordPress.

Conectar ao RDS MySQL.

Integrar ao EFS para arquivos estáticos.

---
# Passo a passo :
<p align="center">
  <img src="https://github.com/user-attachments/assets/31e3a61e-ba5a-4004-ae6d-96b9758b6f99" >
</p>


<p align="center">
  <img src="https://github.com/user-attachments/assets/4f3e9cbd-6863-4ed7-9a19-b2dd0ca300bf" >
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/2c694d32-88ec-42b9-88f4-2490f54c46c9" >
</p>


<p align="center">
  <img src="https://github.com/user-attachments/assets/35b08835-6b26-4444-a9f9-aff9018d0bfc" >
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/b9cd3db9-3beb-400d-9b9a-5e467581f8ec" >
</p>




<p align="center">
  <img src="https://github.com/user-attachments/assets/1a12b291-1b70-4caa-b6fc-a2b125dfe53d" >
</p>

---
### ✅ 1. Conectar na EC2 via terminal
 Dê permissão segura à sua chave (caso ainda não tenha feito)
```bash
chmod 400 chaveproject.pem
```
### ✅ 2. Conecte-se à sua EC2 com Ubuntu
```bash
ssh -i "chaveproject.pem" ubuntu@seu.ip

```

