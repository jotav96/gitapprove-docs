# GitApprove - Sistema de Aprovação de Commits em Equipe

![NPM Version](https://img.shields.io/npm/v/gitapprove)
![NPM Downloads](https://img.shields.io/npm/dm/gitapprove)
![License](https://img.shields.io/npm/l/gitapprove)

Sistema profissional de aprovação colaborativa de commits integrado ao GitHub, com interface web moderna e **push automático via OAuth**.

## ⚠️ IMPORTANTE: NÃO USE `git push`!

**O GitApprove substitui o `git push` tradicional.** Ao invés de fazer push diretamente, você envia commits para aprovação da equipe:

```bash
# ❌ NÃO FAÇA ISSO
git push origin main

# ✅ FAÇA ISSO
gitapprove upload
```

**📖 [Leia o Guia Completo de Workflow →](./WORKFLOW.md)**

---

## 🚀 Features

- ✅ **Push Automático via OAuth** - GitHub token salvo automaticamente no login!
- ✅ **Aprovação em Equipe** - TODOS os membros do time precisam aprovar
- ✅ **Interface Web Moderna** - Dashboard profissional com tema claro/escuro
- ✅ **CLI Global** - Comando `gitapprove` instalado via npm (v2.1.3)
- ✅ **Tokens CLI Permanentes** - Token individual por usuário (formato: gat_...)
- ✅ **GitHub API Direct** - Push sem clone via API REST
- ✅ **Docker Ready** - Deploy facilitado com containers
- ✅ **Gestão de Times** - Adicione colaboradores e gerencie equipes

## 📦 Instalação Rápida

```bash
# Instalar CLI globalmente
npm install -g gitapprove

# Obter token em: https://gitapprove.koyeb.app/dashboard/settings
gitapprove config --token gat_seu_token_aqui

# Verificar configuração
gitapprove whoami
```

## 🎯 Links Importantes

- **🌐 Web App:** https://gitapprove.koyeb.app
- **📖 Workflow Completo:** [WORKFLOW.md](./WORKFLOW.md)
- **🚀 Início Rápido:** [QUICKSTART.md](./QUICKSTART.md)
- **📦 NPM Package:** https://www.npmjs.com/package/gitapprove
- **🐙 Repositório:** https://github.com/jotav96/GitApprove
- **❓ FAQ:** [FAQ.md](./FAQ.md)
- **📜 Changelog:** [CHANGELOG.md](./CHANGELOG.md)

## 💻 Uso Básico

### 1. Faça Login no Dashboard (OAuth Automático)

1. Acesse https://gitapprove.koyeb.app
2. Clique em **"Login com GitHub"**
3. Autorize o aplicativo
4. **GitHub token OAuth salvo automaticamente!** 🎉

### 2. Gere seu Token CLI

1. **Dashboard** → **Configurações** (⚙️)
2. **Gerar Token CLI**
3. Copie o token (formato: `gat_...`)
4. Configure no CLI

### 3. Desenvolva Normalmente

```bash
cd seu-projeto
git add .
git commit -m "feat: nova funcionalidade"
```

### 4. Envie para Aprovação (NÃO use git push!)

```bash
gitapprove upload
```

### 5. Aguarde Aprovação

- Time revisa no dashboard: https://gitapprove.koyeb.app/dashboard/pending
- Quando TODOS aprovarem, **push automático via OAuth para GitHub!**

### 6. Aprove Commits dos Colegas

```bash
# Via CLI
gitapprove list
gitapprove approve <hash>

# Ou via Web
# Acesse: https://gitapprove.koyeb.app/dashboard/pending
```

## 📚 Documentação Completa

| Documento | Descrição |
|-----------|-----------|
| **[WORKFLOW.md](./WORKFLOW.md)** | 📖 Guia completo do fluxo de trabalho |
| **[QUICKSTART.md](./QUICKSTART.md)** | 🚀 Tutorial de início rápido |
| **[CLI-INSTALL.md](./CLI-INSTALL.md)** | 💻 Instalação e configuração do CLI |
| **[FAQ.md](./FAQ.md)** | ❓ Perguntas frequentes |
| **[CHANGELOG.md](./CHANGELOG.md)** | 📜 Histórico de versões |

## 🔐 Configuração de Times

Para que os commits apareçam no dashboard, você precisa:

1. Criar um time no dashboard
2. Vincular seus projetos ao time
3. Adicionar membros ao time

**Sem um time configurado, os commits não aparecerão para ninguém!**

Acesse: https://gitapprove.koyeb.app/dashboard/teams

## 🛠️ Comandos CLI

```bash
# Configuração
gitapprove config --token <TOKEN>
gitapprove whoami

# Workflow
gitapprove upload                # Enviar commits para aprovação
gitapprove list                  # Ver commits pendentes
gitapprove approve <hash>        # Aprovar commit
gitapprove reject <hash>         # Rejeitar commit

# Ajuda
gitapprove --help
```

## ✨ Como Funciona o Push Automático via OAuth

1. **Login com GitHub** → Sistema recebe token OAuth com permissão `repo`
2. **Token salvo automaticamente** → Armazenado no banco de dados
3. **Commit aprovado** → Sistema detecta aprovação unânime
4. **Push via GitHub API** → Usa token OAuth para push direto (sem clone!)
5. **Commit no GitHub** → Aparece com autor original preservado

**Nenhuma configuração manual de tokens! Tudo automático! 🚀**

## 🤝 Contribuindo

Este é um projeto em desenvolvimento ativo. Para reportar bugs ou sugerir melhorias:

- Abra uma issue neste repositório
- Entre em contato via GitHub

## 📄 Licença

MIT License - Veja [LICENSE](./LICENSE) para mais detalhes

## 👨‍💻 Autor

**José Vitor** (@jotav96)
- GitHub: https://github.com/jotav96
- NPM: https://www.npmjs.com/~jotav96

---

**🎯 Lembre-se: Use `gitapprove upload` ao invés de `git push`!**

📖 **[Leia o Guia Completo de Workflow →](./WORKFLOW.md)**
