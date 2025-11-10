# GitApprove - Sistema de Aprovação de Commits em Equipe

![NPM Version](https://img.shields.io/npm/v/gitapprove)
![NPM Downloads](https://img.shields.io/npm/dm/gitapprove)
![License](https://img.shields.io/npm/l/gitapprove)

Sistema profissional de aprovação colaborativa de commits integrado ao GitHub, com interface web moderna e CLI.

## 🚀 Features

- ✅ **Autenticação GitHub OAuth** - Login direto com conta GitHub
- ✅ **Aprovação em Equipe** - TODOS os membros do time precisam aprovar
- ✅ **Interface Web Moderna** - Dashboard profissional com tema claro/escuro
- ✅ **CLI Global** - Comando `gitapprove` instalado via npm
- ✅ **Tokens Permanentes** - Token individual por usuário (formato: gat_...)
- ✅ **Push Automático** - Envia para GitHub quando todos aprovarem
- ✅ **Docker Completo** - MySQL + Backend + Frontend containerizados
- ✅ **Gestão de Times** - Adicione colaboradores e gerencie equipes

## 📦 Instalação

### CLI (Linha de Comando)

```bash
npm install -g gitapprove
```

### Sistema Completo

O código-fonte completo está disponível mediante solicitação.  
Entre em contato para acesso ao repositório privado.

## 🎯 Acesso ao Sistema

- **Web App:** https://gitapprove.koyeb.app
- **Documentação:** https://github.com/jotav96/gitapprove-docs
- **NPM Package:** https://www.npmjs.com/package/gitapprove

## 💻 Como Usar o CLI

### 1. Configure o Token

```bash
# Obtenha seu token em: https://gitapprove.koyeb.app/dashboard/settings
gitapprove config --token gat_seu_token_aqui

# Configure o servidor (se usar instalação própria)
gitapprove config --server http://seu-servidor:3202

# Verifique a configuração
gitapprove whoami
```

### 2. Envie Commits para Aprovação

```bash
# No seu projeto Git
cd ~/meu-projeto

# Faça suas alterações normalmente
git add arquivo.js
git commit -m "feat: adicionar nova funcionalidade"

# IMPORTANTE: NÃO faça git push ainda!

# Envie para aprovação da equipe
gitapprove upload

# O commit fica pendente até TODOS os membros aprovarem
```

### 3. Aprove Commits da Equipe

Acesse o dashboard web e:
1. Vá em **Pendentes**
2. Revise o código dos colegas
3. Clique em **✓ Aprovar** ou **✗ Rejeitar**
4. Quando todos aprovarem, o push é automático!

## 🔧 Comandos CLI

```bash
# Configuração
gitapprove config --token <token>     # Configurar token de acesso
gitapprove config --server <url>      # Configurar URL da API
gitapprove whoami                     # Ver informações do usuário

# Enviar commits
gitapprove upload                     # Enviar último commit
gitapprove upload -n 3                # Enviar últimos 3 commits

# Consultar status
gitapprove list                       # Listar todos os commits
gitapprove list --all                 # Incluir aprovados/rejeitados

# Aprovação (via CLI - opcional)
gitapprove approve <hash>             # Aprovar commit
gitapprove reject <hash> -c "motivo"  # Rejeitar commit
```

## 🏗️ Arquitetura

### Stack Tecnológica

- **Frontend:** Next.js 14 + React 18 + TypeScript + Tailwind CSS
- **Backend:** Next.js API Routes + MySQL 8.0
- **CLI:** Node.js package (npm)
- **Deploy:** Docker + Koyeb
- **Auth:** GitHub OAuth (NextAuth.js)

### Fluxo de Trabalho

```
Developer → git commit → gitapprove upload → Sistema GitApprove
                                                      ↓
                                          Time revisa e aprova
                                                      ↓
                                          git push automático → GitHub
```

## 📊 Exemplo de Uso

### Cenário: Time de 3 Desenvolvedores

**João faz uma feature:**
```bash
git commit -m "feat: adicionar endpoint de relatórios"
gitapprove upload
```

**Maria e Pedro aprovam via web:**
- Dashboard → Pendentes → Revisar código → ✓ Aprovar

**Sistema faz push automático:**
- Quando todos aprovam → `git push origin main`
- Commit aparece no GitHub automaticamente!

## 🔐 Segurança

- ✅ OAuth 2.0 com GitHub
- ✅ Tokens permanentes e revogáveis
- ✅ Bloqueio de auto-aprovação
- ✅ Histórico completo de ações
- ✅ Sem armazenamento de senhas

## 📚 Recursos

- [Guia de Instalação CLI](./CLI-INSTALL.md)
- [Guia Rápido](./QUICKSTART.md)
- [FAQ - Perguntas Frequentes](./FAQ.md)
- [Changelog](./CHANGELOG.md)

## 🤝 Contribuindo

Sugestões e feedback são bem-vindos:

1. Abra uma [Issue](https://github.com/jotav96/gitapprove-docs/issues)
2. Descreva sua sugestão ou problema
3. Aguarde resposta da equipe

## 📝 Licença

MIT License

## 👤 Autor

**José Vitor**
- GitHub: [@jotav96](https://github.com/jotav96)
- NPM: [gitapprove](https://www.npmjs.com/package/gitapprove)
- Email: jotavstorebr@gmail.com

## 📞 Suporte

- **Issues:** https://github.com/jotav96/gitapprove-docs/issues
- **NPM:** https://www.npmjs.com/package/gitapprove
- **Web App:** https://gitapprove.koyeb.app

## 🎉 Agradecimentos

Tecnologias utilizadas:
- Next.js 14
- TypeScript
- Tailwind CSS
- NextAuth.js
- MySQL 8.0
- Docker

---

**Desenvolvido com ❤️ por José Vitor**

🌟 **Se gostou do projeto, dê uma estrela!** 🌟
