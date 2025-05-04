<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/e46be03e-7677-4e8b-accc-c6b8d4cddf7b" alt="Image" width="1200" height="auto"></td>
    <td>
      <h1>🚀 Projeto: Deploy de WordPress com AWS</h1>
      <div align="center">
        <a href="https://skillicons.dev">
          <img src="https://skillicons.dev/icons?i=aws,linux,docker,wordpress,mysql" alt="My Skills" />
        </a>
      </div>
    </td>
  </tr>
</table>



## Descrição do Projeto

Este projeto tem como objetivo implantar uma aplicação WordPress em uma infraestrutura escalável e segura na AWS, utilizando contêineres Docker ou Containerd, banco de dados gerenciado via RDS, armazenamento compartilhado com EFS e distribuição de tráfego com Load Balancer.

## ✅ Etapas do Projeto
### 1. 🖥️ Criação e Configuração da Instância EC2
Criar uma instância 

Configurar grupo de segurança para permitir apenas porta 22 (SSH) e 80 ou 8080 (HTTP).

Associar uma role com permissões de acesso ao EFS e RDS.

Anotar o ID da instância para uso posterior no Load Balancer.

---

## 2. 📦 Instalação do Docker ou Containerd via user_data.sh
Utilizar um script de inicialização automática para provisionar o ambiente assim que a instância for criada:

---

## 3. 🛢️ Criação do Banco de Dados MySQL com Amazon RDS
Criar uma instância RDS com engine MySQL.

Definir:

Nome do banco

Usuário e senha

Endpoint do banco

Ajustar o grupo de segurança da RDS para permitir conexões somente da EC2.

---

## 4. 📁 Criação do Sistema de Arquivos com Amazon EFS
Criar um sistema EFS regional.

Criar pontos de montagem nas zonas de disponibilidade usadas.

Associar o EFS ao VPC usado pela EC2.

---
## 5. 📂 Montagem do EFS na Instância EC2

---

## 6. ⚙️ Configuração do docker-compose ou Dockerfile para WordPress
Criar um arquivo docker-compose.yml com as variáveis do banco e montagem do volume EFS:

---

## 7. 🚀 Deploy do WordPress com Conexão ao RDS e Volume EFS

---
## 8. ⚖️ Criação do Load Balancer (Classic ou Application)
Criar um Load Balancer.

Associar a instância EC2 como destino.

Configurar a porta 80 ou 8080.

Associar um DNS amigável (opcional).

---
## 9. 🌐 Configuração de Regras de Segurança
Permitir entrada HTTP apenas via Load Balancer.

Impedir acesso público direto à instância EC2 (bloquear IP público).

Garantir que o tráfego de internet passe apenas pelo Load Balancer.

---
## 10. 🧪 Teste de Funcionamento da Aplicação WordPress
Acessar a URL do Load Balancer.

Confirmar o carregamento da tela de instalação ou login do WordPress.

Verificar persistência de dados (testar volume EFS e banco RDS).
