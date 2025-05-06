# ✅ Etapas Finais do Projeto Wordpress na AWS
### 🔧 1. Acessar a EC2 via Terminal
No terminal local, execute:
```bash
ssh -i "chaveprojeto.pem" ubuntu@3.92.15.199
```

💡 Substitua chaveprojeto.pem e o IP de acordo como está o seu , esté é um exemplo 

# ✅ Etapas : montar o EFS na EC2 e rodar o WordPress
Passo 1: Verificar a conectividade com o EFS
Para garantir que a sua EC2 está se comunicando corretamente com o EFS, vamos verificar a resolução do nome DNS do EFS:
```bash
nslookup fs-063444ada6f544931.efs.us-east-1.amazonaws.com

```
Isso deve retornar o endereço IP correspondente ao seu sistema de arquivos EFS. Caso contrário, há algo errado com a configuração de rede, e você pode precisar revisar as regras de segurança ou de rede.

---

🔧 1. Montar o EFS na sua instância EC2
No terminal da sua EC2 (já conectada):

Instalar utilitário NFS (caso não tenha):
```bash
sudo apt update && sudo apt install -y nfs-common

```
### Criar diretório de montagem:
```bash
sudo mkdir -p /mnt/efs

```
### Montar o EFS:
```bash
sudo mount -t nfs4 -o nfsvers=4.1 fs-063444ada6f544931.efs.us-east-1.amazonaws.com:/ /mnt/efs

```
### Verificar se montou corretamente:
```bash
df -hT | grep efs
```
(Opcional) Adicionar ao /etc/fstab para montar sempre que reiniciar:
```bash
echo "fs-063444ada6f544931.efs.us-east-1.amazonaws.com:/ /mnt/efs nfs4 defaults,_netdev 0 0" | sudo tee -a /etc/fstab
```
---
# 🐳 2. Criar o docker-compose.yml usando seu RDS e EFS
Crie o arquivo:
```bash
nano docker-compose.yml
```
```bash
```
