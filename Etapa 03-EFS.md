# Criação  Amazon EFS (Elastic File System)

## Conceitos básicos :
O Amazon EFS é um sistema de arquivos escalável, elástico e totalmente gerenciado, que permite compartilhar dados entre várias instâncias EC2 simultaneamente, como se fosse um pendrive em rede (NFS).
🔹 Diferente do EBS (ligado a uma instância), o EFS pode ser montado em várias EC2 ao mesmo tempo, ideal para ambientes como WordPress com múltiplas instâncias.

---
#### Abra o painel principal da AWS e pesquise por EFS

Clique em File systems
<img src="https://github.com/user-attachments/assets/b940c290-c511-436c-b4dd-752d60b7ac27" alt="Image 5">

<img src="https://github.com/user-attachments/assets/9378a141-d816-46de-8404-29af0bc2e297" alt="Image 4">

<img src="https://github.com/user-attachments/assets/3ddbf688-da87-4f13-bfa6-556ec39bcff8" alt="Image 3">

<img src="https://github.com/user-attachments/assets/fa73b210-1bcd-40bd-b240-41e3c9c540d5" alt="Image 2">

<img src="https://github.com/user-attachments/assets/0dece95f-21e1-46a9-b2f2-231cbf0f3572" alt="Image 1">

 ### Configuração da Rede para o EFS
Importante: Certifique-se de selecionar apenas subnets privadas neste processo.

Escolha a VPC previamente criada.

Para a Zona de Disponibilidade us-east-1a:

Selecione a subnet privada correspondente.

Atribua o Security Group do EFS: efs.

Para a Zona de Disponibilidade us-east-1b:

Selecione a subnet privada correspondente.

Atribua novamente o Security Group do EFS: efs.


