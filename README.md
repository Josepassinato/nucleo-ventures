# 🚀 Núcleo Ventures - Autonomous AI Directory Framework

**Transforme seu negócio em uma diretoria 100% autônoma de IA que funciona 24/7 sem parar.**

Núcleo Ventures é um framework completo que permite criar uma equipe de agentes de IA com "alma", capazes de tomar decisões, executar ações, gerenciar pagamentos e otimizar operações de forma totalmente autônoma. Perfeito para lojas, serviços, produtos digitais e físicos.

---

## 🎯 O Que Você Consegue Fazer

Com Núcleo Ventures, você terá:

- **Diretoria Autônoma**: CEO, CMO, CFO, COO, CPO, CHRO, Coach, Analista e Otimizador trabalhando juntos
- **Decisões Inteligentes**: Agentes com "alma" que sentem estresse, pressão, proatividade e orgulho
- **Automação Total**: Vendas, marketing, pagamentos, atendimento e otimização 24/7
- **Cara Humana**: 95% das interações parecem humanas (nomes reais, e-mails, WhatsApp, atrasos naturais)
- **Navegação Web Autônoma**: Agentes conseguem pesquisar, fazer login, preencher formulários e coletar dados
- **Conformidade Legal**: LGPD (Brasil) e CCPA (EUA) integradas
- **Dashboard Executivo**: Visualize tudo em tempo real com 2 designs diferentes

---

## 📊 Arquitetura

```
┌─────────────────────────────────────────────────────────────┐
│                    Dashboard Executivo                       │
│                  (React 19 + Tailwind 4)                     │
└──────────────────────┬──────────────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────────────┐
│                  Backend (FastAPI/tRPC)                      │
│              (Autenticação OAuth + PostgreSQL)               │
└──────────────────────┬──────────────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────────────┐
│                  Orquestrador de Agentes                     │
│                 (CrewAI + Groq + Gemini)                     │
└──────────────────────┬──────────────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────────────┐
│              Ferramentas de Integração                       │
│  Mercado Livre | Amazon | Stripe | Twilio | Gmail | etc     │
└─────────────────────────────────────────────────────────────┘
```

---

## 🚀 Quick Start

### Instalação em 1 Linha

```bash
curl -fsSL https://raw.githubusercontent.com/SEU-USUARIO/nucleo-ventures/main/install.sh | bash
```

Após a instalação, execute:

```bash
nucleo install
```

Isso abrirá um wizard interativo onde você:
1. Escolhe sua região (Brasil ou EUA)
2. Configura suas APIs (Mercado Livre/Amazon, Stripe, Gemini, etc)
3. Testa as conexões
4. Começa a usar!

### Instalação Manual

```bash
# Clone o repositório
git clone https://github.com/SEU-USUARIO/nucleo-ventures.git
cd nucleo-ventures

# Instale dependências
pip install -r nucleo_cli/requirements.txt
pnpm install

# Configure suas chaves de API
cp .env.example .env
# Edite .env com suas credenciais

# Inicie o dashboard
pnpm dev

# Em outro terminal, inicie o CLI
python nucleo_cli/install.py
```

---

## 📋 Estrutura do Projeto

```
nucleo-ventures/
├── README.md                    # Este arquivo
├── GETTING_STARTED.md           # Guia de início rápido
├── LICENSE                      # Licença (MIT ou Proprietária)
├── .env.example                 # Variáveis de ambiente
├── .gitignore
│
├── install.sh                   # Script de instalação em 1 linha
│
├── nucleo_cli/                  # CLI interativo (Python)
│   ├── install.py              # Wizard de configuração
│   ├── requirements.txt
│   ├── setup.py
│   └── README.md
│
├── nucleo_dashboard/            # Dashboard executivo (React)
│   ├── client/                 # Frontend React 19
│   ├── server/                 # Backend tRPC
│   ├── drizzle/                # Migrations de banco de dados
│   ├── package.json
│   └── README.md
│
├── nucleo/                      # Estrutura de agentes
│   ├── agentes/                # Perfis de cada agente
│   ├── mecanismos/             # Sistema de "alma"
│   ├── seguranca/              # Protocolos de segurança
│   ├── ferramentas/            # Navegação autônoma
│   ├── stack/                  # Stack técnica
│   └── README.md
│
├── docs/                        # Documentação
│   ├── GETTING_STARTED.md      # Guia rápido
│   ├── API_KEYS_GUIDE.md       # Como obter credenciais
│   ├── DEPLOYMENT.md           # Deploy em produção
│   ├── ARCHITECTURE.md         # Visão geral técnica
│   ├── API_REFERENCE.md        # Referência de APIs
│   ├── TROUBLESHOOTING.md      # Soluções de problemas
│   └── FAQ.md                  # Perguntas frequentes
│
└── .github/
    └── workflows/              # CI/CD (opcional)
```

---

## 🔑 Credenciais Necessárias

Para começar, você precisará de:

| Serviço | Região | Propósito | Obter |
|---------|--------|----------|-------|
| **Mercado Livre** | Brasil | E-commerce | [Developer Console](https://developers.mercadolivre.com.br) |
| **Amazon** | EUA | E-commerce | [Seller Central](https://developer.amazon.com) |
| **Stripe** | Ambos | Pagamentos | [Dashboard](https://dashboard.stripe.com) |
| **Google Gemini** | Ambos | IA (Grátis!) | [AI Studio](https://aistudio.google.com/app/apikey) |
| **Twilio** | Ambos | SMS/WhatsApp | [Console](https://console.twilio.com) |
| **Gmail** | Ambos | E-mail | [Google Cloud](https://console.cloud.google.com) |

Veja o guia completo em [API_KEYS_GUIDE.md](docs/API_KEYS_GUIDE.md).

---

## 💡 Como Funciona

### 1. Agentes com "Alma"

Cada agente tem características humanas simuladas:

```python
# Exemplo: CEO Lucas Mendes
{
  "nome": "Lucas Mendes",
  "role": "CEO",
  "estresse": 45,           # 0-100 (acima de 70 pede ajuda)
  "proatividade": 65,       # Tenta soluções fora da caixa
  "orgulho": 80,            # Se importa com qualidade
  "medo_de_falhar": 70      # Evita erros críticos
}
```

### 2. Supervisão Cruzada

Agentes se monitoram mutuamente. Erros graves bloqueiam APIs até aprovação do dono.

### 3. Navegação Autônoma

Agentes conseguem:
- Pesquisar no Google
- Fazer login em sites
- Preencher formulários
- Coletar dados e screenshots
- Tudo sem intervenção humana

### 4. Dashboard em Tempo Real

Visualize:
- Receita gerada
- Performance de cada agente
- Histórico de ações
- Alertas críticos
- Leaderboard de performance

---

## 🌍 Regiões Suportadas

### 🇧🇷 Brasil
- **E-commerce**: Mercado Livre
- **Pagamentos**: Stripe (Real)
- **Conformidade**: LGPD
- **Comunicação**: WhatsApp, SMS, Gmail
- **Agentes**: Nomes brasileiros

### 🇺🇸 Estados Unidos
- **E-commerce**: Amazon
- **Pagamentos**: Stripe (Dólar)
- **Conformidade**: CCPA
- **Comunicação**: WhatsApp, SMS, Gmail
- **Agentes**: Nomes americanos

---

## 📈 Casos de Uso

### E-commerce
Seu negócio de loja online funciona 24/7:
- Agentes monitoram estoque
- Respondem clientes automaticamente
- Otimizam preços em tempo real
- Geram relatórios diários

### Serviços
Sua agência de serviços escala sem contratar:
- Agentes prospectam clientes
- Fazem orçamentos automaticamente
- Agendam reuniões
- Acompanham projetos

### Produtos Digitais
Seu SaaS cresce exponencialmente:
- Agentes fazem onboarding de usuários
- Respondem suporte 24/7
- Analisam feedback
- Sugerem melhorias

---

## 🔐 Segurança

- **Criptografia AES-256**: Todas as chaves de API
- **LGPD/CCPA**: Conformidade total
- **Auditoria Completa**: Tudo é logado
- **Kill Switch**: Botão de emergência para parar tudo
- **Validação de Erros**: Bloqueia ações perigosas

---

## 💰 Preços

### Modelo de Assinatura

| Plano | Preço | Negócios | Suporte |
|-------|-------|----------|---------|
| **Starter** | R$ 99/mês | 1 | Email |
| **Pro** | R$ 299/mês | 5 | Email + Chat |
| **Enterprise** | R$ 999/mês | Ilimitado | Dedicado |

### Modelo de Licença Única

- **Licença Perpétua**: R$ 2.999 (pague uma vez)
- **Suporte Anual**: R$ 499 (opcional)

---

## 📚 Documentação

- [Getting Started](docs/GETTING_STARTED.md) - Comece em 5 minutos
- [API Keys Guide](docs/API_KEYS_GUIDE.md) - Como obter cada credencial
- [Deployment](docs/DEPLOYMENT.md) - Deploy em VPS/Cloud
- [Architecture](docs/ARCHITECTURE.md) - Visão técnica completa
- [API Reference](docs/API_REFERENCE.md) - Endpoints e procedures
- [Troubleshooting](docs/TROUBLESHOOTING.md) - Solução de problemas
- [FAQ](docs/FAQ.md) - Perguntas frequentes

---

## 🤝 Suporte

- **Email**: support@seu-dominio.com
- **Discord**: [Comunidade Núcleo](https://discord.gg/seu-servidor)
- **Docs**: [docs.seu-dominio.com](https://docs.seu-dominio.com)
- **Issues**: [GitHub Issues](https://github.com/SEU-USUARIO/nucleo-ventures/issues)

---

## 📄 Licença

Este projeto está sob licença **MIT** (ou Proprietária, conforme sua escolha).

Veja [LICENSE](LICENSE) para detalhes.

---

## 🎓 Créditos

Desenvolvido por **[Seu Nome/Empresa]**

Tecnologias:
- **Frontend**: React 19, Tailwind CSS 4, Framer Motion
- **Backend**: FastAPI, tRPC, Express
- **IA**: CrewAI, Groq, Google Gemini
- **Database**: PostgreSQL, Drizzle ORM
- **Navegação**: Playwright, Browser Use

---

## 🚀 Roadmap

- [ ] Integração com mais plataformas de e-commerce
- [ ] Suporte a mais idiomas
- [ ] Marketplace de plugins
- [ ] Versão mobile
- [ ] Integração com WhatsApp Business API
- [ ] Analytics avançado
- [ ] Webhooks customizados

---

## 💬 Feedback

Tem sugestões? Encontrou um bug? Abra uma [issue no GitHub](https://github.com/SEU-USUARIO/nucleo-ventures/issues)!

---

**Transforme seu negócio em uma máquina de lucro autônoma. Comece agora! 🚀**

```bash
curl -fsSL https://raw.githubusercontent.com/SEU-USUARIO/nucleo-ventures/main/install.sh | bash
```
