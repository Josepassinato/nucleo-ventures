# 🚀 Deployment - Guia Completo

Como colocar Núcleo Ventures em produção.

---

## 📋 Opções de Deployment

| Opção | Custo | Tempo | Dificuldade | Recomendação |
|-------|-------|-------|-------------|--------------|
| **Manus Hosting** | Incluído | 1 min | Muito Fácil | ⭐⭐⭐⭐⭐ |
| **Docker** | Variável | 5 min | Fácil | ⭐⭐⭐⭐ |
| **VPS (AWS/DigitalOcean)** | R$ 50-500/mês | 30 min | Médio | ⭐⭐⭐ |
| **Vercel** | Grátis-$20/mês | 10 min | Fácil | ⭐⭐⭐ |
| **Seu Computador** | Grátis | 2 min | Muito Fácil | ⭐ (dev only) |

---

## 🌟 Opção 1: Manus Hosting (Recomendado)

### Passo 1: Fazer Build

```bash
cd /home/ubuntu/nucleo_dashboard
pnpm build
```

### Passo 2: Publicar

1. Abra o Management UI
2. Clique em "Publish" (canto superior direito)
3. Aguarde 1-2 minutos

### Passo 3: Acessar

Seu site estará em: `https://nucleodash-clnpgnbz.manus.space`

### Vantagens:
- ✅ 1 clique para publicar
- ✅ SSL automático
- ✅ CDN global
- ✅ Backups automáticos
- ✅ Domínio customizado incluído

---

## 🐳 Opção 2: Docker

### Passo 1: Criar Dockerfile

```dockerfile
FROM node:22-alpine

WORKDIR /app

COPY package.json pnpm-lock.yaml ./
RUN npm install -g pnpm && pnpm install --frozen-lockfile

COPY . .

RUN pnpm build

ENV NODE_ENV=production
EXPOSE 3000

CMD ["node", "dist/index.js"]
```

### Passo 2: Build da Imagem

```bash
docker build -t nucleo-ventures:latest .
```

### Passo 3: Rodar Container

```bash
docker run -p 3000:3000 \
  -e DATABASE_URL=postgresql://... \
  -e GEMINI_API_KEY=... \
  nucleo-ventures:latest
```

### Passo 4: Deploy em Produção

**Opção A: Docker Hub**
```bash
docker tag nucleo-ventures:latest seu-usuario/nucleo-ventures:latest
docker push seu-usuario/nucleo-ventures:latest
```

**Opção B: Railway**
```bash
railway link
railway up
```

**Opção C: Render**
```bash
# Conecte seu GitHub
# Render detecta Dockerfile automaticamente
```

---

## ☁️ Opção 3: VPS (AWS/DigitalOcean)

### Passo 1: Criar VPS

**DigitalOcean:**
1. Crie um Droplet (Ubuntu 22.04, 2GB RAM)
2. Conecte via SSH

**AWS:**
1. Crie uma EC2 (t3.small, Ubuntu 22.04)
2. Configure security group (portas 80, 443, 3000)

### Passo 2: Instalar Dependências

```bash
# Update sistema
sudo apt update && sudo apt upgrade -y

# Instalar Node.js
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt install -y nodejs

# Instalar pnpm
npm install -g pnpm

# Instalar PostgreSQL
sudo apt install -y postgresql postgresql-contrib

# Instalar Nginx (reverse proxy)
sudo apt install -y nginx

# Instalar PM2 (process manager)
sudo npm install -g pm2
```

### Passo 3: Clonar e Configurar

```bash
# Clone repositório
git clone https://github.com/Josepassinato/nucleo-ventures.git
cd nucleo-ventures

# Instale dependências
pnpm install

# Configure .env
cp .env.example .env
nano .env  # Edite com suas credenciais

# Build
pnpm build
```

### Passo 4: Configurar PM2

```bash
# Crie arquivo ecosystem.config.js
cat > ecosystem.config.js << 'EOF'
module.exports = {
  apps: [{
    name: 'nucleo-ventures',
    script: './dist/index.js',
    instances: 'max',
    exec_mode: 'cluster',
    env: {
      NODE_ENV: 'production',
      PORT: 3000
    }
  }]
};
EOF

# Inicie com PM2
pm2 start ecosystem.config.js

# Configure para iniciar automaticamente
pm2 startup
pm2 save
```

### Passo 5: Configurar Nginx

```bash
# Crie arquivo de configuração
sudo nano /etc/nginx/sites-available/nucleo-ventures

# Cole:
server {
    listen 80;
    server_name seu-dominio.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}

# Ative o site
sudo ln -s /etc/nginx/sites-available/nucleo-ventures /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
```

### Passo 6: SSL com Let's Encrypt

```bash
# Instale Certbot
sudo apt install -y certbot python3-certbot-nginx

# Gere certificado
sudo certbot --nginx -d seu-dominio.com

# Renovação automática
sudo systemctl enable certbot.timer
```

### Passo 7: Monitorar

```bash
# Ver status
pm2 status

# Ver logs
pm2 logs nucleo-ventures

# Reiniciar
pm2 restart nucleo-ventures
```

---

## ✈️ Opção 4: Vercel

### Passo 1: Conectar GitHub

1. Acesse https://vercel.com
2. Clique em "New Project"
3. Selecione seu repositório

### Passo 2: Configurar Build

Vercel detecta automaticamente. Se não, configure:

```
Build Command: pnpm build
Output Directory: dist
```

### Passo 3: Variáveis de Ambiente

1. Vá em Settings → Environment Variables
2. Adicione todas as variáveis do `.env`

### Passo 4: Deploy

Clique em "Deploy" e aguarde!

---

## 💻 Opção 5: Seu Computador (Desenvolvimento)

### Passo 1: Instalar Dependências

```bash
# Node.js
# Baixe de https://nodejs.org

# PostgreSQL
# Baixe de https://www.postgresql.org/download/

# Git
# Baixe de https://git-scm.com
```

### Passo 2: Clonar e Configurar

```bash
git clone https://github.com/Josepassinato/nucleo-ventures.git
cd nucleo-ventures
pnpm install
cp .env.example .env
nano .env
```

### Passo 3: Rodar

```bash
# Terminal 1: Backend
pnpm dev

# Terminal 2: Frontend (automático)
# Acessa em http://localhost:3000
```

---

## 🔄 Atualizações

### Atualizar em Produção

```bash
# Pull das mudanças
git pull origin main

# Instale novas dependências
pnpm install

# Rode migrations
pnpm db:push

# Rebuild
pnpm build

# Reinicie
pm2 restart nucleo-ventures
```

---

## 📊 Monitoramento

### Logs

```bash
# PM2
pm2 logs nucleo-ventures

# Nginx
sudo tail -f /var/log/nginx/error.log

# Aplicação
tail -f ~/.nucleo/logs/app.log
```

### Métricas

```bash
# CPU e Memória
pm2 monit

# Requisições
pm2 web  # Acessa em http://localhost:9615
```

### Alertas

Configure alertas para:
- CPU > 80%
- Memória > 85%
- Erros > 10/min
- Tempo de resposta > 2s

---

## 🔒 Segurança em Produção

### Checklist

- [ ] SSL/HTTPS ativado
- [ ] Firewall configurado
- [ ] Backups automáticos
- [ ] Logs centralizados
- [ ] Rate limiting ativado
- [ ] CORS configurado
- [ ] Variáveis de ambiente seguras
- [ ] Senhas fortes
- [ ] 2FA ativado
- [ ] Monitoramento ativo

### Backup

```bash
# PostgreSQL
pg_dump nucleo_ventures > backup.sql

# Restaurar
psql nucleo_ventures < backup.sql

# Automático com cron
0 2 * * * pg_dump nucleo_ventures | gzip > /backups/db-$(date +\%Y\%m\%d).sql.gz
```

---

## 🆘 Troubleshooting

### "Erro 502 Bad Gateway"

1. Verifique se aplicação está rodando: `pm2 status`
2. Veja logs: `pm2 logs`
3. Reinicie: `pm2 restart nucleo-ventures`

### "Conexão recusada no banco"

1. Verifique DATABASE_URL
2. Confirme que PostgreSQL está rodando
3. Teste conexão: `psql $DATABASE_URL`

### "Certificado SSL expirado"

```bash
sudo certbot renew --dry-run
sudo certbot renew
```

### "Memória alta"

1. Verifique se há memory leaks
2. Reinicie aplicação: `pm2 restart nucleo-ventures`
3. Aumente RAM da VPS

---

## 📈 Escalabilidade

### Quando Escalar

- **Usuários**: > 1000
- **Requisições**: > 1000/seg
- **Dados**: > 100GB

### Como Escalar

1. **Horizontal**: Adicione mais servidores
2. **Vertical**: Aumente recursos (CPU, RAM)
3. **Cache**: Use Redis para cache
4. **CDN**: Use Cloudflare para assets

---

## 💰 Custos Estimados

| Opção | Custo Mensal | Setup |
|-------|-------------|-------|
| Manus | Incluído | Grátis |
| Docker (DigitalOcean) | R$ 50-200 | Grátis |
| VPS (AWS) | R$ 100-500 | Grátis |
| Vercel | R$ 0-500 | Grátis |
| Seu PC | R$ 0 | Grátis |

---

## ✅ Checklist de Deploy

- [ ] Build local funciona
- [ ] Testes passam
- [ ] .env configurado
- [ ] Database migrado
- [ ] SSL/HTTPS ativo
- [ ] Domínio apontando
- [ ] Backups configurados
- [ ] Monitoramento ativo
- [ ] Logs centralizados
- [ ] Alertas configurados

---

**Pronto para colocar em produção? 🚀**
