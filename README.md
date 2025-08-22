# Sistema de Avisos de Jogos

Sistema de cronômetro para avisos de jogos desenvolvido em React com Supabase.

## Funcionalidades

- ⏱️ Cronômetro VOD com controle de tempo
- 📅 Calendário para visualização de jogos
- ⚙️ Gerenciamento de jogos (adicionar, editar, remover)
- 🔐 Autenticação com Supabase (opcional)
- 💾 Modo local com localStorage (fallback)

## Tecnologias

- React 19
- Vite
- Tailwind CSS
- shadcn/ui
- Supabase
- React Hot Toast
- Lucide Icons

## Deploy no Cloudflare Pages

### Opção 1: Via Dashboard do Cloudflare

1. Acesse o [Cloudflare Pages](https://pages.cloudflare.com/)
2. Clique em "Create a project"
3. Conecte seu repositório Git
4. Configure as seguintes opções:
   - **Framework preset**: React
   - **Build command**: `pnpm run build`
   - **Build output directory**: `dist`
   - **Node.js version**: 20

### Opção 2: Via Wrangler CLI

```bash
# Instalar Wrangler globalmente
npm install -g wrangler

# Fazer login no Cloudflare
wrangler login

# Deploy do projeto
wrangler pages deploy dist --project-name sistema-avisos-jogos
```

### Configuração de Variáveis de Ambiente

Se estiver usando Supabase, configure as seguintes variáveis no Cloudflare Pages:

- `VITE_SUPABASE_URL`: URL do seu projeto Supabase
- `VITE_SUPABASE_ANON_KEY`: Chave anônima do Supabase

## Desenvolvimento Local

```bash
# Instalar dependências
pnpm install

# Executar em modo desenvolvimento
pnpm run dev

# Build para produção
pnpm run build

# Preview do build
pnpm run preview
```

## Estrutura do Projeto

```
src/
├── components/          # Componentes React
│   ├── ui/             # Componentes UI (shadcn/ui)
│   ├── Calendario.jsx  # Componente do calendário
│   ├── Cronometro.jsx  # Componente do cronômetro
│   ├── GerenciarJogos.jsx # Gerenciamento de jogos
│   └── LoginForm.jsx   # Formulário de login
├── contexts/           # Contextos React
│   └── AuthContext.jsx # Contexto de autenticação
├── hooks/              # Hooks customizados
│   └── useJogos.js     # Hook para gerenciar jogos
├── lib/                # Utilitários e serviços
│   ├── jogosService.js # Serviço de jogos
│   └── supabase.js     # Configuração do Supabase
├── App.jsx             # Componente principal
├── App.css             # Estilos principais
└── main.jsx            # Ponto de entrada
```

## Configuração do Supabase

Para usar com Supabase, execute o SQL fornecido em `supabase-setup.sql` no seu projeto Supabase.

## Credenciais de Teste

Para testar o sistema com Supabase, use as seguintes credenciais:

- **Email**: usuario@exemplo.com
- **Senha**: senha123

## Modo Local

O sistema funciona automaticamente em modo local usando localStorage quando o Supabase não está configurado ou não está disponível.

