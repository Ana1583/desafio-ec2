# Notas do Laboratório EC2

## 1) Criação da instância
- AMI sugerida: Amazon Linux 2 (HVM) ou Ubuntu LTS.
- Tipo de instância: t2.micro (se for elegível ao free tier).
- Key pair: crie/baixe uma chave `.pem`. Mantenha segura.

## 2) Security Group (regras)
- Porta 22 (SSH): permitir somente do seu IP (recomendado) ou de qualquer lugar (0.0.0.0/0) apenas para testes.
- Porta 80 (HTTP): abrir se hospedar aplicação web.
- Porta 443 (HTTPS): abrir se necessário.

## 3) Conexão SSH (resumo)
- No Linux/macOS: `chmod 400 nome-da-minha-chave.pem` e `ssh -i nome-da-minha-chave.pem ec2-user@<IP_PUBLICO>`
- No Windows: usar PuTTY (converta .pem para .ppk) ou Windows Terminal com OpenSSH.

## 4) Anexar volume EBS
- Criar volume em Volumes → Actions → Attach volume.
- No Linux: `sudo mkfs -t ext4 /dev/xvdf` → `sudo mkdir /mnt/data` → `sudo mount /dev/xvdf /mnt/data`

## 5) Snapshot (backup)
- Console EC2 → Volumes → Actions → Create snapshot. Anote o ID do snapshot.

## 6) Monitoramento
- CloudWatch: verificar CPUUtilization, NetworkIn/Out; criar alarmes para thresholds.

## 7) Problemas comuns
- Erro de permissão ao usar chave PEM → aplicar `chmod 400`.
- Porta 22 bloqueada → ajustar Security Group.
- Erro de montagem EBS → verificar device name correto.

## 8) Insights / recomendações
- Documente comandos exatos para repetir o ambiente.
- Marque permissões da chave PEM e limite IPs no Security Group por segurança.
