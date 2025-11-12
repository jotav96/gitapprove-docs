# GitApprove

**Sistema de Aprovação de Commits para GitHub** com autenticação automática e push via OAuth.

GitApprove é uma ferramenta que adiciona um processo de revisão e aprovação de código **antes** que os commits cheguem ao GitHub. Perfeito para times que querem garantir que todo código seja revisado antes de ser mergeado.

## 🎯 O Que é GitApprove?

- **Revisão obrigatória**: Nenhum código vai para o GitHub sem aprovação
- **Push automático**: Commits aprovados são enviados automaticamente via OAuth
- **Interface web**: Dashboard bonito para revisar e aprovar commits
- **CLI poderoso**: Ferramenta de linha de comando para desenvolvedores
- **Times e projetos**: Organize seus repositórios e colaboradores
- **Autenticação simplificada**: Login automático sem configuração manual

## 🚀 Instalação Rápida

```bash
# 1. Instalar CLI globalmente
npm install -g gitapprove

# 2. Fazer login (abre navegador automaticamente)
gitapprove login

# 3. Pronto! Comece a usar
gitapprove upload owner/repo
```

**É isso!** Token salvo automaticamente, sem edição de arquivos. ✨

## 📖 Como Funciona

### Fluxo Tradicional (sem GitApprove):
```
Desenvolvedor → git push → GitHub ✅
```
❌ Código não revisado vai direto para produção!

### Fluxo com GitApprove:
```
Desenvolvedor → gitapprove upload → Dashboard de Revisão → Time Aprova → Push Automático → GitHub ✅
```
✅ Todo código é revisado antes de ir para o GitHub!

## 💻 Uso Diário

### Para Desenvolvedores

```bash
# Fazer commits normalmente
git add .
git commit -m "feat: nova funcionalidade"

# ⚠️ NÃO USE "git push"! Use o GitApprove:
gitapprove upload owner/repo

# Ou especifique uma branch
gitapprove upload owner/repo --branch develop

# Ver seus commits pendentes
gitapprove list

# Ver status
gitapprove status
```

### Para Revisores

Acesse o dashboard: **https://gitapprove.koyeb.app/dashboard**

1. Veja commits pendentes
2. Revise o código e arquivos modificados
3. Aprove ou rejeite com comentários
4. Sistema faz push automático quando todos aprovarem!

## 📚 Documentação Completa

- **[Guia Rápido (QUICKSTART.md)](./QUICKSTART.md)** - Comece em 5 minutos
- **[Perguntas Frequentes (FAQ.md)](./FAQ.md)** - Dúvidas comuns
- **[Changelog (CHANGELOG.md)](./CHANGELOG.md)** - Histórico de versões

## 🔑 Comandos do CLI

```bash
# Autenticação
gitapprove login              # Login automático (abre navegador)

# Enviar commits
gitapprove upload owner/repo                    # Branch main (padrão)
gitapprove upload owner/repo -b develop         # Branch develop
gitapprove upload owner/repo --branch feature   # Branch feature

# Consultas
gitapprove list               # Commits pendentes
gitapprove list --all         # Todos os commits
gitapprove status             # Ver estatísticas

# Utilidades
gitapprove update-check       # Verificar atualizações
gitapprove --help             # Ajuda completa
gitapprove --version          # Versão instalada
```

## 🌟 Recursos Principais

### ✅ Push Automático via OAuth
- Commits aprovados são enviados automaticamente para o GitHub
- Usa o token OAuth do dono do projeto
- Sem necessidade de configurar deploy keys ou tokens manualmente
- Funciona com repositórios privados

### 👥 Sistema de Times
- Organize colaboradores por projeto
- Todos os membros do time precisam aprovar
- Autor não pode aprovar o próprio commit
- Estatísticas de aprovação em tempo real

### 📊 Dashboard Completo
- Interface web moderna e intuitiva
- Visualize arquivos modificados (diff completo)
- Histórico de commits e aprovações
- Notificações de status

### 🔒 Segurança
- Autenticação via GitHub OAuth
- Tokens seguros e criptografados
- Permissões granulares por projeto
- Auditoria completa de aprovações

## 🛠️ Configuração de Projetos

### 1. Criar Projeto no Dashboard
- Acesse https://gitapprove.koyeb.app/dashboard/projects
- Conecte seu repositório GitHub
- Configure o time de revisão

### 2. Proteger Branch no GitHub (Recomendado)
Para garantir que ninguém faça push direto:

```bash
# No seu repositório local
git config branch.main.pushRemote no-push

# Ou via GitHub:
# Settings → Branches → Add rule
# ✅ Require pull request reviews
# ✅ Require status checks
```

### 3. Configurar Webhooks (Opcional)
Para notificações automáticas de aprovações e rejeições.

## 🌐 Links Úteis

- **Dashboard**: https://gitapprove.koyeb.app
- **NPM Package**: https://npmjs.com/package/gitapprove
- **Documentação**: https://github.com/jotav96/gitapprove-docs
- **Issues**: https://github.com/jotav96/GitApprove/issues

## ⚠️ Importante

### ❌ Nunca use `git push` diretamente
Isso pula todo o processo de revisão!

### ✅ Sempre use `gitapprove upload`
O sistema faz o push automaticamente após aprovação.

### 🔄 Se o push automático falhar
1. Faça logout e login novamente no dashboard
2. Isso renova o token OAuth do GitHub
3. Tente aprovar novamente

## 🤝 Contribuindo

Encontrou um bug? Tem uma sugestão?

- Abra uma issue: https://github.com/jotav96/GitApprove/issues
- Envie um PR (depois de aprovado no GitApprove, claro! 😄)

## 📝 Licença

MIT License - Use livremente em projetos pessoais e comerciais.

## 🎓 Casos de Uso

### Times de Desenvolvimento
- Code review obrigatório antes do merge
- Garantir qualidade do código
- Auditoria de quem aprovou cada commit

### Projetos Open Source
- Múltiplos mantenedores revisando contribuições
- Processo transparente de aprovação
- Histórico completo de decisões

### Empresas
- Compliance e auditoria
- Separação de responsabilidades
- Controle de qualidade de código

---

**Desenvolvido com ❤️ para melhorar a qualidade do código e facilitar revisões em equipe.**

Comece agora: `npm install -g gitapprove && gitapprove login`
