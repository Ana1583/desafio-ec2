# Comandos úteis

## SSH (Linux / macOS)
# Ajustar permissão da chave
chmod 400 nome-da-minha-chave.pem

# Conectar (exemplo Amazon Linux)
ssh -i nome-da-minha-chave.pem ec2-user@<IP_PUBLICO>

## Para Ubuntu
ssh -i nome-da-minha-chave.pem ubuntu@<IP_PUBLICO>

## Criar filesystem e montar EBS
sudo mkfs -t ext4 /dev/xvdf
sudo mkdir /mnt/data
sudo mount /dev/xvdf /mnt/data

## Atualizar sistema
# Amazon Linux
sudo yum update -y

# Ubuntu
sudo apt update && sudo apt upgrade -y

## Exemplo de git (se for usar localmente depois)
git init
git add .
git commit -m "feat: adicionar arquivos do laboratório EC2"
git remote add origin https://github.com/<SEU_USUARIO>/ec2-lab.git
git branch -M main
git push -u origin main
