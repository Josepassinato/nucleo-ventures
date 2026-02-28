# 🔑 Guia Completo de Credenciais

Aprenda como obter cada chave de API necessária para rodar Núcleo Ventures.

---

## 🇧🇷 BRASIL

### Mercado Livre

**O que é**: Plataforma de e-commerce onde você vende produtos.

**Como obter**:

1. Acesse: https://developers.mercadolivre.com.br
2. Clique em "Criar aplicação"
3. Preencha:
   - Nome: `Nucleo Ventures`
   - Descrição: `Automação de vendas`
   - Tipo: `Web`
4. Clique em "Criar"
5. Você verá:
   - **Client ID**: Copie
   - **Client Secret**: Copie (guarde bem!)

**Onde colar no Núcleo**:
```bash
nucleo install
# Passo 2: E-commerce
# Cole o Client ID
# Cole o Client Secret
```

**Documentação**: https://developers.mercadolivre.com.br/pt_br/autenticacao

---

### Stripe (Brasil)

**O que é**: Processador de pagamentos (aceita cartão de crédito, Pix, etc).

**Como obter**:

1. Acesse: https://dashboard.stripe.com
2. Faça login ou crie conta
3. Vá em: Settings → API Keys
4. Você verá:
   - **Secret Key**: Começa com `sk_live_`
   - **Publishable Key**: Começa com `pk_live_`
5. Copie ambas

**Onde colar no Núcleo**:
```bash
nucleo install
# Passo 3: Pagamentos
# Cole o Secret Key
# Cole o Publishable Key
```

**Documentação**: https://stripe.com/docs/keys

**Importante**: Use a chave de PRODUÇÃO (`sk_live_`), não a de teste (`sk_test_`).

---

### Google Gemini (Brasil)

**O que é**: IA que gerencia seu negócio (100% grátis!).

**Como obter**:

1. Acesse: https://aistudio.google.com/app/apikey
2. Clique em "Create API Key"
3. Escolha projeto ou crie um novo
4. Clique em "Create API key in new project"
5. Copie a chave

**Onde colar no Núcleo**:
```bash
nucleo install
# Passo 4: IA
# Cole a API Key
```

**Documentação**: https://ai.google.dev/docs

**Limite Grátis**: 60 requisições/minuto (suficiente para começar!)

---

### Twilio (Brasil)

**O que é**: Envia SMS e WhatsApp automaticamente.

**Como obter**:

1. Acesse: https://console.twilio.com
2. Faça login ou crie conta
3. Vá em: Account → API Keys & tokens
4. Você verá:
   - **Account SID**: Copie
   - **Auth Token**: Copie (guarde bem!)
5. Copie ambas

**Onde colar no Núcleo**:
```bash
nucleo install
# Passo 5: Comunicação
# Cole o Account SID
# Cole o Auth Token
```

**Documentação**: https://www.twilio.com/docs/usage/api

**Preço**: Começa grátis com crédito de teste.

---

### Gmail (Brasil)

**O que é**: Envia e-mails automaticamente.

**Como obter**:

1. Acesse: https://console.cloud.google.com
2. Crie um novo projeto (ou use existente)
3. Vá em: APIs & Services → Credentials
4. Clique em: "Create Credentials" → "OAuth 2.0 Client IDs"
5. Escolha: "Desktop application"
6. Clique em "Create"
7. Você verá:
   - **Client ID**: Copie
   - **Client Secret**: Copie
8. Baixe o JSON

**Onde colar no Núcleo**:
```bash
nucleo install
# Passo 5: Comunicação
# Cole o Client ID
# Cole o Client Secret
```

**Documentação**: https://developers.google.com/gmail/api/guides

---

## 🇺🇸 UNITED STATES

### Amazon Seller Central

**O que é**: Plataforma de e-commerce onde você vende produtos.

**Como obter**:

1. Acesse: https://developer.amazon.com
2. Faça login com conta Amazon
3. Vá em: Seller Central
4. Vá em: Settings → User Permissions
5. Clique em: "Generate MWS Auth Token"
6. Você verá:
   - **Seller ID**: Copie
   - **MWS Auth Token**: Copie
7. Vá em: Settings → API Keys
8. Você verá:
   - **Access Key**: Copie
   - **Secret Key**: Copie

**Onde colar no Núcleo**:
```bash
nucleo install
# Passo 2: E-commerce
# Cole o Access Key
# Cole o Secret Key
```

**Documentação**: https://docs.developer.amazon.com/sp-api/docs/sp-api-overview

---

### Stripe (EUA)

**O que é**: Processador de pagamentos (aceita cartão de crédito, Apple Pay, etc).

**Como obter**:

1. Acesse: https://dashboard.stripe.com
2. Faça login ou crie conta (use endereço dos EUA)
3. Vá em: Settings → API Keys
4. Você verá:
   - **Secret Key**: Começa com `sk_live_`
   - **Publishable Key**: Começa com `pk_live_`
5. Copie ambas

**Onde colar no Núcleo**:
```bash
nucleo install
# Passo 3: Pagamentos
# Cole o Secret Key
# Cole o Publishable Key
```

**Documentação**: https://stripe.com/docs/keys

**Importante**: Use a chave de PRODUÇÃO (`sk_live_`), não a de teste (`sk_test_`).

---

### Google Gemini (EUA)

**O que é**: IA que gerencia seu negócio (100% grátis!).

**Como obter**:

1. Acesse: https://aistudio.google.com/app/apikey
2. Clique em "Create API Key"
3. Escolha projeto ou crie um novo
4. Clique em "Create API key in new project"
5. Copie a chave

**Onde colar no Núcleo**:
```bash
nucleo install
# Passo 4: IA
# Cole a API Key
```

**Documentação**: https://ai.google.dev/docs

**Limite Grátis**: 60 requisições/minuto (suficiente para começar!)

---

### Twilio (EUA)

**O que é**: Envia SMS e WhatsApp automaticamente.

**Como obter**:

1. Acesse: https://console.twilio.com
2. Faça login ou crie conta
3. Vá em: Account → API Keys & tokens
4. Você verá:
   - **Account SID**: Copie
   - **Auth Token**: Copie (guarde bem!)
5. Copie ambas

**Onde colar no Núcleo**:
```bash
nucleo install
# Passo 5: Comunicação
# Cole o Account SID
# Cole o Auth Token
```

**Documentação**: https://www.twilio.com/docs/usage/api

**Preço**: Começa grátis com crédito de teste.

---

### Gmail (EUA)

**O que é**: Envia e-mails automaticamente.

**Como obter**:

1. Acesse: https://console.cloud.google.com
2. Crie um novo projeto (ou use existente)
3. Vá em: APIs & Services → Credentials
4. Clique em: "Create Credentials" → "OAuth 2.0 Client IDs"
5. Escolha: "Desktop application"
6. Clique em "Create"
7. Você verá:
   - **Client ID**: Copie
   - **Client Secret**: Copie
8. Baixe o JSON

**Onde colar no Núcleo**:
```bash
nucleo install
# Passo 5: Comunicação
# Cole o Client ID
# Cole o Client Secret
```

**Documentação**: https://developers.google.com/gmail/api/guides

---

## ✅ Checklist de Configuração

### Antes de Começar

- [ ] Escolhi minha região (Brasil ou EUA)
- [ ] Tenho conta em todas as plataformas necessárias
- [ ] Copiei todas as chaves em um arquivo seguro

### Credenciais Obrigatórias

- [ ] E-commerce (Mercado Livre ou Amazon)
- [ ] Stripe
- [ ] Gemini

### Credenciais Opcionais (Recomendadas)

- [ ] Twilio
- [ ] Gmail

---

## 🔒 Segurança

### Boas Práticas

1. **Nunca compartilhe suas chaves**
   - Não coloque em repositórios públicos
   - Não envie por e-mail
   - Não mostre em screenshots

2. **Use variáveis de ambiente**
   ```bash
   export STRIPE_SECRET_KEY="sk_live_..."
   export GEMINI_API_KEY="..."
   ```

3. **Rotacione chaves regularmente**
   - A cada 3 meses, gere novas chaves
   - Delete as antigas

4. **Monitore uso**
   - Acesse os dashboards regularmente
   - Procure por atividades suspeitas

---

## 🆘 Problemas Comuns

### "Chave inválida"

1. Verifique se copiou corretamente (sem espaços)
2. Confirme que é a chave de PRODUÇÃO (não teste)
3. Gere uma nova chave

### "Acesso negado"

1. Verifique as permissões da aplicação
2. Confirme que a conta tem acesso
3. Tente fazer login novamente

### "Limite de requisições atingido"

1. Aguarde 1 minuto
2. Considere fazer upgrade para plano pago
3. Otimize o código para fazer menos requisições

---

## 📞 Suporte

Precisa de ajuda?

- **Email**: support@seu-dominio.com
- **Discord**: [Comunidade](https://discord.gg/seu-servidor)
- **Docs**: [docs.seu-dominio.com](https://docs.seu-dominio.com)

---

**Parabéns! Você tem todas as credenciais necessárias. Agora execute `nucleo install` e comece! 🚀**
