# 🚀 Getting Started - Núcleo Ventures

Comece a usar Núcleo Ventures em menos de 5 minutos.

---

## ⚡ Instalação Rápida (1 linha)

```bash
curl -fsSL https://raw.githubusercontent.com/SEU-USUARIO/nucleo-ventures/main/install.sh | bash
```

Isso vai:
1. ✅ Verificar se você tem Python 3.8+
2. ✅ Instalar todas as dependências
3. ✅ Criar o comando `nucleo` no seu terminal
4. ✅ Abrir o wizard de configuração

---

## 🎯 Passo a Passo

### Passo 1: Escolha Sua Região

```bash
nucleo install
```

Você verá:
```
🚀 Núcleo Ventures
Escolha sua região:

1) 🇧🇷 Brasil (Mercado Livre, LGPD, Real)
2) 🇺🇸 EUA (Amazon, CCPA, Dólar)

Qual é a sua? [1 ou 2]:
```

Escolha **1** para Brasil ou **2** para EUA.

### Passo 2: Configure E-commerce

Você vai precisar de credenciais:

**Se escolheu Brasil (Mercado Livre):**
1. Acesse: https://developers.mercadolivre.com.br
2. Crie uma aplicação
3. Copie: **Client ID** e **Client Secret**
4. Cole no wizard

**Se escolheu EUA (Amazon):**
1. Acesse: https://developer.amazon.com
2. Vá para Seller Central
3. Copie: **Access Key** e **Secret Key**
4. Cole no wizard

### Passo 3: Configure Pagamentos (Stripe)

1. Acesse: https://dashboard.stripe.com/apikeys
2. Copie: **Secret Key** e **Publishable Key**
3. Cole no wizard

### Passo 4: Configure IA (Gemini)

1. Acesse: https://aistudio.google.com/app/apikey
2. Clique em "Create API Key"
3. Copie a chave
4. Cole no wizard

**Bom saber**: Gemini é **100% grátis** até 60 requisições/minuto!

### Passo 5: Configure Comunicação (Opcional)

Você pode configurar depois, mas é recomendado:

**Twilio** (SMS/WhatsApp):
- Acesse: https://console.twilio.com
- Copie: Account SID e Auth Token

**Gmail** (E-mail):
- Acesse: https://console.cloud.google.com
- Crie credenciais OAuth

### Passo 6: Pronto! 🎉

Após completar o wizard:

```
✅ Todas as configurações salvas!
✅ Conexões testadas com sucesso
✅ Dashboard pronto em: http://localhost:3000

Próximo passo: Acesse o dashboard e comece a usar!
```

---

## 📊 Primeiro Uso

### Abra o Dashboard

```bash
# Inicie o servidor (se não estiver rodando)
pnpm dev

# Abra no navegador
http://localhost:3000
```

Você verá:

```
┌─────────────────────────────────────────┐
│         🚀 Núcleo Ventures              │
│      Diretoria Autônoma de IA           │
├─────────────────────────────────────────┤
│                                         │
│  Receita Hoje:     R$ 18.472            │
│  Performance:      +12,4% vs ontem      │
│                                         │
│  Agentes Ativos:   8/8                  │
│  Estresse Médio:   45%                  │
│  Saúde do Negócio: 87%                  │
│                                         │
└─────────────────────────────────────────┘
```

### Dissemine uma Visão

Clique em "Disseminar Visão" e digite:

```
"Quero aumentar vendas em 50% este mês. Foque em 
marketing no Instagram, otimize preços e melhore 
o atendimento ao cliente."
```

Seus agentes vão:
1. 🎯 Analisar a visão
2. 📊 Criar plano de ação
3. 🚀 Executar automaticamente
4. 📈 Reportar progresso

---

## 🔧 Troubleshooting

### "Comando `nucleo` não encontrado"

```bash
# Reinstale
curl -fsSL https://raw.githubusercontent.com/SEU-USUARIO/nucleo-ventures/main/install.sh | bash

# Ou adicione manualmente ao PATH
export PATH="$PATH:$HOME/.nucleo/bin"
```

### "Erro ao conectar com Mercado Livre"

1. Verifique se a chave está correta
2. Acesse: https://developers.mercadolivre.com.br
3. Confirme que a aplicação está ativa
4. Tente novamente

### "Gemini retorna erro 429"

Você atingiu o limite de 60 requisições/minuto. Espere 1 minuto e tente novamente.

Para aumentar o limite:
1. Acesse: https://aistudio.google.com/app/apikey
2. Clique em "Upgrade to Gemini 1.5 Pro" (pago)

### "Dashboard não abre"

```bash
# Verifique se a porta 3000 está livre
lsof -i :3000

# Se estiver ocupada, use outra porta
PORT=3001 pnpm dev
```

---

## 📚 Próximos Passos

Depois de configurar:

1. **Leia a documentação**: [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)
2. **Customize os agentes**: [nucleo/agentes/](nucleo/agentes/)
3. **Configure webhooks**: [docs/API_REFERENCE.md](docs/API_REFERENCE.md)
4. **Deploy em produção**: [docs/DEPLOYMENT.md](docs/DEPLOYMENT.md)

---

## 💬 Precisa de Ajuda?

- **FAQ**: [docs/FAQ.md](docs/FAQ.md)
- **Troubleshooting**: [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md)
- **Email**: support@seu-dominio.com
- **Discord**: [Comunidade](https://discord.gg/seu-servidor)

---

## 🎓 Aprenda Mais

- [Como obter credenciais](docs/API_KEYS_GUIDE.md)
- [Arquitetura técnica](docs/ARCHITECTURE.md)
- [Referência de APIs](docs/API_REFERENCE.md)
- [Deploy em VPS](docs/DEPLOYMENT.md)

---

**Parabéns! Você está pronto para transformar seu negócio em uma máquina de lucro autônoma! 🚀**
