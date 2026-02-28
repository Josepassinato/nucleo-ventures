# 🏗️ Architecture - Núcleo Ventures

Visão técnica completa da arquitetura do Núcleo Ventures.

---

## 📊 Visão Geral

```
┌──────────────────────────────────────────────────────────────┐
│                  CAMADA DE APRESENTAÇÃO                       │
│              Dashboard Executivo (React 19)                   │
│         V1 Premium (Verde-Esmeralda) + V2 Ousado (Azul)      │
└──────────────────────┬───────────────────────────────────────┘
                       │ tRPC + WebSocket
┌──────────────────────▼───────────────────────────────────────┐
│                  CAMADA DE API                                │
│          Backend (Express + tRPC + FastAPI)                   │
│     Autenticação OAuth | Autorização RBAC | Validação        │
└──────────────────────┬───────────────────────────────────────┘
                       │ SQL Queries
┌──────────────────────▼───────────────────────────────────────┐
│                  CAMADA DE DADOS                              │
│          PostgreSQL + Drizzle ORM                             │
│     Agentes | Configurações | Histórico | Auditoria          │
└──────────────────────┬───────────────────────────────────────┘
                       │
┌──────────────────────▼───────────────────────────────────────┐
│              CAMADA DE ORQUESTRAÇÃO                           │
│            CrewAI + Groq + Gemini                             │
│    Coordena agentes, executa tarefas, gerencia fluxos         │
└──────────────────────┬───────────────────────────────────────┘
                       │
┌──────────────────────▼───────────────────────────────────────┐
│              CAMADA DE FERRAMENTAS                            │
│  Navegação Web | APIs | Pagamentos | E-commerce | Comunicação│
│ Playwright | Stripe | Mercado Livre | Amazon | Twilio | Gmail│
└──────────────────────────────────────────────────────────────┘
```

---

## 🔄 Fluxo de Dados

### 1. Usuário Dissemina Visão

```
Usuário digita visão no Dashboard
         ↓
Frontend envia via tRPC
         ↓
Backend recebe e valida
         ↓
Salva em banco de dados
         ↓
Envia para CrewAI
```

### 2. CrewAI Processa

```
CrewAI recebe visão
         ↓
Decomposição em tarefas
         ↓
Atribui a agentes
         ↓
Agentes executam em paralelo
```

### 3. Agentes Executam

```
Cada agente:
  1. Recebe tarefa
  2. Consulta Gemini
  3. Usa ferramentas (navegação, APIs)
  4. Coleta dados
  5. Reporta resultado
         ↓
Resultados são salvos em BD
         ↓
Dashboard atualiza em tempo real
```

---

## 🗂️ Estrutura de Diretórios

### Frontend (`client/src/`)

```
client/src/
├── pages/
│   ├── Home.tsx              # Dashboard V1
│   ├── DashboardV2.tsx       # Dashboard V2
│   ├── OnboardingPage.tsx    # Wizard de configuração
│   └── NotFound.tsx
├── components/
│   ├── DashboardHeader.tsx
│   ├── HeroBlock.tsx
│   ├── StatusCards.tsx
│   ├── OrganizationalChart.tsx
│   ├── ActionTimeline.tsx
│   ├── DashboardFooter.tsx
│   ├── DashboardLayout.tsx
│   ├── AIChatBox.tsx
│   ├── Map.tsx
│   └── ui/                   # shadcn/ui components
├── hooks/
│   ├── useAgents.ts
│   ├── useActions.ts
│   ├── useVision.ts
│   ├── useMetrics.ts
│   └── useAuth.ts
├── contexts/
│   ├── I18nContext.tsx
│   └── ThemeContext.tsx
├── lib/
│   └── trpc.ts              # tRPC client
├── const.ts
├── App.tsx
├── main.tsx
└── index.css
```

### Backend (`server/`)

```
server/
├── _core/
│   ├── index.ts             # Express server
│   ├── context.ts           # tRPC context
│   ├── trpc.ts              # tRPC setup
│   ├── oauth.ts             # Manus OAuth
│   ├── llm.ts               # Gemini integration
│   ├── llm.ts               # Image generation
│   ├── voiceTranscription.ts # Speech-to-text
│   ├── map.ts               # Google Maps
│   ├── notification.ts      # Notificações
│   ├── env.ts               # Variáveis de ambiente
│   ├── cookies.ts           # Session management
│   └── systemRouter.ts      # System procedures
├── db.ts                    # Database helpers
├── routers.ts               # tRPC procedures
├── storage.ts               # S3 integration
└── auth.logout.test.ts      # Tests
```

### Database (`drizzle/`)

```
drizzle/
├── schema.ts                # Table definitions
├── relations.ts             # Foreign keys
├── migrations/              # SQL migrations
└── meta/                    # Migration metadata
```

### Agentes (`nucleo/`)

```
nucleo/
├── agentes/
│   ├── lucas_mendes_ceo.md
│   ├── mariana_oliveira_cmo.md
│   ├── pedro_lima_cfo.md
│   ├── carla_santos_coo.md
│   ├── rafael_torres_cpo.md
│   ├── ana_costa_chro.md
│   ├── ze_carvalho_coach.md
│   ├── dani_ferreira_dados.md
│   ├── beto_rocha_otimizador.md
│   └── joao_silva_humano.md
├── mecanismos/
│   └── alma.json            # Sistema de alma
├── seguranca/
│   └── protocolos.json      # Segurança
├── ferramentas/
│   └── navegacao_autonoma/  # Playwright + Browser Use
├── stack/
│   └── tecnologias.json     # Stack técnica
└── config/
    └── projeto.json         # Configuração geral
```

---

## 🔐 Autenticação & Autorização

### Fluxo OAuth

```
1. Usuário clica "Login"
        ↓
2. Frontend redireciona para Manus OAuth
        ↓
3. Usuário faz login
        ↓
4. Manus retorna para /api/oauth/callback
        ↓
5. Backend valida token
        ↓
6. Cria sessão JWT
        ↓
7. Frontend salva cookie
        ↓
8. Acesso garantido ✅
```

### Controle de Acesso (RBAC)

```
Roles disponíveis:
  - user: Acesso básico ao dashboard
  - admin: Acesso completo + gerenciamento

Exemplo de proteção:
  publicProcedure       # Qualquer um
  protectedProcedure    # Usuário autenticado
  adminProcedure        # Apenas admin
```

---

## 💾 Banco de Dados

### Tabelas Principais

| Tabela | Propósito | Campos |
|--------|-----------|--------|
| `users` | Usuários | id, openId, name, email, role, createdAt |
| `agents` | Agentes IA | id, name, role, stress, proactivity, performance |
| `integrations` | APIs configuradas | id, userId, service, credentials (encrypted) |
| `actions` | Histórico de ações | id, agentId, action, status, timestamp |
| `visions` | Visões disseminadas | id, userId, content, status, createdAt |
| `audit_logs` | Auditoria | id, userId, action, details, timestamp |

### Migrations

```bash
# Criar nova migration
pnpm db:push

# Gerar migrations
drizzle-kit generate

# Aplicar migrations
drizzle-kit migrate
```

---

## 🤖 Sistema de Agentes

### Estrutura de um Agente

```typescript
interface Agent {
  id: string;
  name: string;
  role: "ceo" | "cmo" | "cfo" | "coo" | "cpo" | "chro" | "coach" | "analyst" | "optimizer";
  
  // Alma (simulação de emoções)
  stress: number;           // 0-100
  proactivity: number;      // 0-100
  pride: number;            // 0-100
  fear_of_failure: number;  // 0-100
  
  // Performance
  kpi_score: number;        // 0-10
  performance_history: PerformanceRecord[];
  
  // Configuração
  system_prompt: string;
  tools: Tool[];
  permissions: Permission[];
}
```

### Ciclo de Vida de uma Tarefa

```
1. Tarefa é criada
        ↓
2. Agente recebe tarefa
        ↓
3. Consulta Gemini para estratégia
        ↓
4. Usa ferramentas disponíveis
        ↓
5. Coleta dados
        ↓
6. Executa ações
        ↓
7. Reporta resultado
        ↓
8. Resultado é salvo em BD
        ↓
9. Dashboard atualiza
```

---

## 🔧 Ferramentas Disponíveis

### Navegação Web

```typescript
navegar_site({
  instrucao: "Pesquise concorrentes no Google",
  url_inicial: "https://google.com",
  max_passos: 20,
  salvar_screenshot: true
})
```

### APIs de E-commerce

```typescript
// Mercado Livre (Brasil)
mercado_livre.listar_produtos()
mercado_livre.criar_anuncio()
mercado_livre.atualizar_preco()

// Amazon (EUA)
amazon.listar_produtos()
amazon.criar_anuncio()
amazon.atualizar_estoque()
```

### Pagamentos

```typescript
stripe.criar_checkout_session()
stripe.processar_pagamento()
stripe.gerar_fatura()
```

### Comunicação

```typescript
twilio.enviar_sms()
twilio.enviar_whatsapp()
gmail.enviar_email()
```

---

## 📊 Dashboard em Tempo Real

### WebSocket

```typescript
// Backend envia atualizações
io.emit("agent:update", {
  agentId: "lucas_mendes",
  stress: 65,
  lastAction: "Analisando concorrentes"
});

// Frontend recebe
socket.on("agent:update", (data) => {
  updateAgentStatus(data);
});
```

### Atualização de Métricas

```
Cada 30 segundos:
  1. Backend coleta métricas
  2. Calcula KPIs
  3. Envia via WebSocket
  4. Dashboard atualiza gráficos
```

---

## 🔄 Fluxo Completo: Exemplo

### Cenário: Aumentar Vendas em 50%

```
1. Usuário clica "Disseminar Visão"
   Input: "Quero aumentar vendas em 50% este mês"

2. Frontend envia para backend
   POST /api/trpc/vision.disseminate
   Body: { content: "..." }

3. Backend salva em BD
   INSERT INTO visions (userId, content, status)

4. Envia para CrewAI
   crew.kickoff(vision)

5. CrewAI decompõe em tarefas:
   - Tarefa 1: CMO faz análise de mercado
   - Tarefa 2: CMO cria campanha Instagram
   - Tarefa 3: CFO otimiza preços
   - Tarefa 4: COO melhora atendimento

6. Agentes executam em paralelo:
   CMO:
     - Pesquisa concorrentes (navegação web)
     - Cria posts (Gemini)
     - Publica no Instagram (API)
   
   CFO:
     - Analisa vendas (BD)
     - Calcula novos preços (Gemini)
     - Atualiza preços (Mercado Livre API)
   
   COO:
     - Revisa processos (BD)
     - Cria scripts de atendimento (Gemini)
     - Treina equipe (Twilio)

7. Resultados são salvos
   INSERT INTO actions (agentId, action, status, result)

8. Dashboard atualiza em tempo real
   - Gráficos de performance
   - Timeline de ações
   - Status de agentes

9. Usuário vê tudo acontecendo
   "CMO está criando campanha..."
   "CFO atualizou preços..."
   "COO melhorou atendimento..."

10. Após 24h, resultado:
    "Vendas aumentaram 52%! 🎉"
```

---

## 🚀 Deployment

### Desenvolvimento Local

```bash
# Terminal 1: Backend
pnpm dev

# Terminal 2: Frontend (automático)
# Acessa em http://localhost:3000
```

### Produção (VPS)

```bash
# Build
pnpm build

# Start
NODE_ENV=production node dist/index.js

# Com PM2 (recomendado)
pm2 start dist/index.js --name "nucleo-ventures"
```

### Manus Hosting

```bash
# Publicar via UI
1. Clique em "Publish"
2. Aguarde 1-2 minutos
3. Acesse em: https://seu-dominio.manus.space
```

---

## 📈 Monitoramento

### Logs

```bash
# Ver logs em tempo real
tail -f ~/.nucleo/logs/app.log

# Ver erros
grep ERROR ~/.nucleo/logs/app.log
```

### Métricas

```
Dashboard → Métricas:
  - Requisições/segundo
  - Tempo de resposta
  - Taxa de erro
  - Uso de memória
  - Uso de CPU
```

---

## 🔒 Segurança

### Criptografia

```typescript
// Credenciais são criptografadas AES-256
const encrypted = encrypt(apiKey, masterKey);
await db.insert(integrations).values({ credentials: encrypted });
```

### Auditoria

```typescript
// Todas as ações são logadas
await auditLog({
  userId: user.id,
  action: "vision.disseminate",
  details: { visionId, content },
  timestamp: new Date()
});
```

### Rate Limiting

```typescript
// Protege contra abuso
app.use(rateLimit({
  windowMs: 15 * 60 * 1000,  // 15 minutos
  max: 100                     // 100 requisições
}));
```

---

## 📚 Tecnologias

| Camada | Tecnologia | Versão |
|--------|-----------|--------|
| Frontend | React | 19 |
| Styling | Tailwind CSS | 4 |
| Animations | Framer Motion | 12 |
| Backend | Express | 4 |
| RPC | tRPC | 11 |
| Database | PostgreSQL | 15+ |
| ORM | Drizzle | 0.44 |
| Auth | Manus OAuth | - |
| AI | Gemini 1.5 | Flash/Pro |
| Orchestration | CrewAI | Latest |
| Web Scraping | Playwright | Latest |
| Payments | Stripe | Latest |

---

## 🔗 Referências

- [tRPC Documentation](https://trpc.io)
- [Drizzle ORM](https://orm.drizzle.team)
- [CrewAI](https://crewai.com)
- [Playwright](https://playwright.dev)
- [Stripe API](https://stripe.com/docs/api)

---

**Parabéns! Você entende a arquitetura do Núcleo Ventures! 🚀**
