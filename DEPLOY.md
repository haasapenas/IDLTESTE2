# Guia de Deploy - Cloudflare Pages

Este guia detalha como fazer o deploy do Sistema de Avisos de Jogos no Cloudflare Pages.

## Pré-requisitos

- Conta no Cloudflare
- Repositório Git com o código do projeto
- Node.js 18+ instalado localmente (para testes)

## Método 1: Deploy via Dashboard (Recomendado)

### Passo 1: Preparar o Repositório

1. Faça upload de todos os arquivos do projeto para um repositório Git (GitHub, GitLab, etc.)
2. Certifique-se de que o arquivo `package.json` está na raiz do projeto

### Passo 2: Conectar ao Cloudflare Pages

1. Acesse [Cloudflare Pages](https://pages.cloudflare.com/)
2. Clique em **"Create a project"**
3. Selecione **"Connect to Git"**
4. Autorize o Cloudflare a acessar seu repositório
5. Selecione o repositório do projeto

### Passo 3: Configurar o Build

Configure as seguintes opções:

- **Project name**: `sistema-avisos-jogos`
- **Production branch**: `main` (ou sua branch principal)
- **Framework preset**: `React`
- **Build command**: `pnpm run build`
- **Build output directory**: `dist`
- **Root directory**: `/` (deixe vazio se o projeto está na raiz)

### Passo 4: Variáveis de Ambiente (Opcional)

Se quiser usar o Supabase em produção:

1. Vá para **Settings** > **Environment variables**
2. Adicione as variáveis:
   - `VITE_SUPABASE_URL`: `https://cxbdwkbxwbvnrzbdmdil.supabase.co`
   - `VITE_SUPABASE_ANON_KEY`: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImN4YmR3a2J4d2J2bnJ6YmRtZGlsIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NTU4MTE2NDEsImV4cCI6MjA3MTM4NzY0MX0.amxneQMa1cIDqQhhLqFjTZEEjxuk7Bm9beFhnApl274`

### Passo 5: Deploy

1. Clique em **"Save and Deploy"**
2. Aguarde o build completar (geralmente 2-5 minutos)
3. Acesse a URL fornecida pelo Cloudflare

## Método 2: Deploy via Wrangler CLI

### Passo 1: Instalar Wrangler

```bash
npm install -g wrangler
```

### Passo 2: Autenticar

```bash
wrangler login
```

### Passo 3: Build Local

```bash
pnpm install
pnpm run build
```

### Passo 4: Deploy

```bash
wrangler pages deploy dist --project-name sistema-avisos-jogos
```

## Configurações Avançadas

### Custom Domain

1. No dashboard do Cloudflare Pages, vá para **Custom domains**
2. Clique em **"Set up a custom domain"**
3. Digite seu domínio e siga as instruções

### Redirects e Headers

Crie um arquivo `_redirects` na pasta `public/` se precisar de redirects customizados:

```
/*    /index.html   200
```

## Troubleshooting

### Build Falha

- Verifique se todas as dependências estão no `package.json`
- Confirme que o comando de build está correto
- Verifique os logs de build no dashboard

### Aplicação não Carrega

- Verifique se o `build output directory` está configurado como `dist`
- Confirme que o arquivo `index.html` está na pasta `dist` após o build

### Problemas com Supabase

- Verifique se as variáveis de ambiente estão configuradas corretamente
- Confirme que as URLs do Supabase estão corretas
- O sistema funciona em modo local mesmo sem Supabase

## Credenciais de Teste

Para testar o login com Supabase:

- **Email**: usuario@exemplo.com
- **Senha**: senha123

## Suporte

- [Documentação Cloudflare Pages](https://developers.cloudflare.com/pages/)
- [Documentação Vite](https://vitejs.dev/guide/static-deploy.html)
- [Documentação React](https://react.dev/learn/start-a-new-react-project)

