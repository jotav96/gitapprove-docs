# GitApprove - Sistema de Aprovação de Commits em Equipe

![NPM Version](https://img.shields.io/npm/v/gitapprove)
![NPM Downloads](https://img.shields.io/npm/dm/gitapprove)
![License](https://img.shields.io/npm/l/gitapprove)

Sistema profissional de aprovação colaborativa de commits integrado ao GitHub, com interface web moderna e CLI.

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

- ✅ **Autenticação GitHub OAuth** - Login direto com conta GitHub
- ✅ **Aprovação em Equipe** - TODOS os membros do time precisam aprovar
- ✅ **Interface Web Moderna** - Dashboard profissional com tema claro/escuro
- ✅ **CLI Global** - Comando `gitapprove` instalado via npm
- ✅ **Tokens Permanentes** - Token individual por usuário (formato: gat_...)
- ✅ **Push Automático** - Envia para GitHub quando todos aprovarem
- ✅ **Docker Completo** - MySQL + Backend + Frontend containerizados
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

- **�� Web App:** https://gitapprove.koyeb.app
- **📖 Workflow Completo:** [WORKFLOW.md](./WORKFLOW.md)
- **🚀 Início Rápido:** [QUICKSTART.md](./QUICKSTART.md)
- **📦 NPM Package:** https://www.npmjs.com/package/gitapprove
- **❓ FAQ:** [FAQ.md](./FAQ.md)
- **📜 Changelog:** [CHANGELOG.md](./CHANGELOG.md)

## 💻 Uso Básico

### 1. Desenvolva Normalmente

```bash
cd seu-projeto
git add .
git commit -m "feat: nova funcionalidade"
```

### 2. Envie para Aprovação (NÃO use git push!)

```bash
gitapprove upload
```

### 3. Aguarde Aprovação

- Time revisa no dashboard: https://gitapprove.koyeb.app/dashboard/pending
- Quando TODOS aprovarem, push é automático para o GitHub

### 4. Aprove Commits dos Colegas

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

## 🤝 Contribuindo

Este é um projeto em desenvolvimento ativo. Para reportar bugs ou sugerir melhorias:

- Abra uma issue neste repositório
- Entre em contato via GitHub

## 📄 Licença

ISC License - Veja [LICENSE](./LICENSE) para mais detalhes

## 👨‍💻 Autor

**José Vitor** (@jotav96)
- GitHub: https://github.com/jotav96
- NPM: https://www.npmjs.com/~jotav96

---

**🎯 Lembre-se: Use `gitapprove upload` ao invés de `git push`!**

📖 **[Leia o Guia Completo de Workflow →](./WORKFLOW.md)**
