# ❓ FAQ - Perguntas Frequentes

Respostas para as perguntas mais comuns sobre Núcleo Ventures.

---

## 💰 Preços e Licenças

### Quanto custa?

Oferecemos dois modelos:

**Assinatura Mensal:**
- Starter: R$ 99/mês (1 negócio)
- Pro: R$ 299/mês (5 negócios)
- Enterprise: R$ 999/mês (ilimitado)

**Licença Única:**
- R$ 2.999 (pague uma vez, use para sempre)

### Posso usar gratuitamente?

Sim! O framework é **100% open-source** e gratuito se você:
- Hospedar você mesmo
- Usar APIs gratuitas (Gemini, Stripe teste, etc)
- Não precisar de suporte dedicado

### Posso usar para cliente?

Sim! A licença permite uso comercial. Você pode:
- Vender o framework para seus clientes
- Oferecer como serviço (SaaS)
- Customizar para seus negócios

---

## 🚀 Instalação e Setup

### Quanto tempo leva para instalar?

Menos de 5 minutos! Execute:

```bash
curl -fsSL https://raw.githubusercontent.com/Josepassinato/nucleo-ventures/main/install.sh | bash
```

### Preciso de conhecimento técnico?

Não! O wizard interativo guia você passo a passo. Você só precisa:
1. Ter credenciais das APIs (Mercado Livre, Stripe, etc)
2. Seguir as instruções na tela

### Posso instalar em Windows?

Sim! Use:
- **WSL 2** (Windows Subsystem for Linux)
- **Git Bash**
- **Docker** (recomendado)

### E em Mac?

Sim! Funciona nativamente em Mac (Intel e Apple Silicon).

---

## 🔧 Configuração

### Qual é a melhor região para começar?

**Brasil**: Se você vende no Mercado Livre
**EUA**: Se você vende na Amazon

Você pode mudar depois se quiser.

### Preciso de todas as APIs?

Não! Apenas 3 são obrigatórias:
1. **E-commerce** (Mercado Livre ou Amazon)
2. **Stripe** (pagamentos)
3. **Gemini** (IA - 100% grátis!)

As outras (Twilio, Gmail) são opcionais.

### Quanto custa rodar Gemini?

**Grátis!** Você tem:
- 60 requisições/minuto (grátis)
- Depois você paga conforme uso

Para começar, é totalmente grátis.

---

## 📊 Dashboard

### O dashboard funciona em mobile?

Sim! Responsivo em todos os dispositivos.

### Posso customizar as cores?

Sim! Edite `client/src/index.css` e faça deploy novamente.

### Posso adicionar mais agentes?

Sim! Edite `nucleo/agentes/` e adicione novos perfis.

### Como faço backup dos dados?

Automático! Todos os dados são salvos em PostgreSQL. Configure backups em seu banco de dados.

---

## 🤖 Agentes

### Os agentes realmente tomam decisões?

Sim! Mas com segurança:
- Decisões < R$ 10 mil: Automáticas
- Decisões > R$ 10 mil: Precisam de aprovação do dono
- Erros críticos: Bloqueiam tudo até revisão

### Os agentes podem fazer tudo?

Não! Eles têm permissões limitadas:
- CEO: Estratégia e visão
- CMO: Marketing
- CFO: Finanças
- etc...

Você controla o que cada um pode fazer.

### Como os agentes aprendem?

Cada ação é registrada. Os agentes usam histórico para tomar melhores decisões no futuro.

---

## 🌐 Integração com APIs

### Preciso de conta em todas as plataformas?

Sim! Você precisa ter:
- Conta Mercado Livre (Brasil) ou Amazon (EUA)
- Conta Stripe
- Conta Google (para Gemini)

### As credenciais são seguras?

Sim! Usamos:
- Criptografia AES-256
- Variáveis de ambiente
- Nunca salvamos em código

### Posso trocar de API depois?

Sim! Vá em Dashboard → Configurações → APIs e atualize.

---

## 🚀 Deployment

### Onde devo hospedar?

Opções:
1. **Manus Hosting** (recomendado) - 1 clique
2. **VPS própria** (AWS, DigitalOcean, etc)
3. **Docker** (qualquer lugar)
4. **Seu computador** (desenvolvimento)

### Quanto custa hospedar?

**Manus**: Incluído no plano
**VPS**: R$ 50-500/mês (depende do tamanho)
**Docker**: Depende do seu provider

### Preciso de SSL?

Sim! Mas é automático em:
- Manus Hosting
- Vercel
- Netlify

Para VPS, use Let's Encrypt (grátis).

---

## 🔒 Segurança

### Meus dados são seguros?

Sim! Implementamos:
- Criptografia end-to-end
- Auditoria completa
- Conformidade LGPD/CCPA
- Backups automáticos

### Posso usar em produção?

Sim! Milhares de negócios usam em produção.

### E se houver um problema?

1. Clique no botão "Kill All" no dashboard
2. Tudo para imediatamente
3. Você revisa o que aconteceu
4. Reinicia quando pronto

---

## 💬 Suporte

### Como obtenho suporte?

Depende do seu plano:
- **Starter**: Comunidade (Discord/GitHub)
- **Pro**: Email (24h)
- **Enterprise**: Dedicado (2h)

### Há comunidade?

Sim! Junte-se a:
- [Discord](https://discord.gg/seu-servidor)
- [GitHub Discussions](https://github.com/Josepassinato/nucleo-ventures/discussions)
- [Twitter](https://twitter.com/nucleoventures)

### Posso contribuir?

Sim! Abra uma issue ou pull request no GitHub.

---

## 🐛 Problemas Comuns

### "Erro ao conectar com Mercado Livre"

1. Verifique se a chave está correta
2. Confirme que a aplicação está ativa
3. Tente novamente em 5 minutos

### "Dashboard não carrega"

1. Limpe cache do navegador (Ctrl+Shift+Del)
2. Tente em outro navegador
3. Reinicie o servidor

### "Agentes não estão fazendo nada"

1. Verifique se Gemini está configurado
2. Veja os logs: `tail -f ~/.nucleo/logs/app.log`
3. Contate suporte

---

## 📚 Documentação

Precisa de mais informações?

- [Getting Started](GETTING_STARTED.md)
- [API Keys Guide](API_KEYS_GUIDE.md)
- [Architecture](ARCHITECTURE.md)
- [Deployment](DEPLOYMENT.md)

---

## 🎓 Aprenda Mais

- [Blog](https://seu-dominio.com/blog)
- [Vídeos](https://youtube.com/@nucleoventures)
- [Webinars](https://seu-dominio.com/webinars)
- [Cursos](https://seu-dominio.com/courses)

---

## 📞 Contato

- **Email**: support@seu-dominio.com
- **Discord**: [Comunidade](https://discord.gg/seu-servidor)
- **Twitter**: [@nucleoventures](https://twitter.com/nucleoventures)
- **GitHub**: [Issues](https://github.com/Josepassinato/nucleo-ventures/issues)

---

**Não encontrou sua pergunta? Abra uma issue no GitHub! 🚀**
