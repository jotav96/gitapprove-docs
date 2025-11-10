# Changelog

Todas as mudanças notáveis neste projeto serão documentadas neste arquivo.

## [2.0.1] - 2025-11-10

### Changed
- Removido link para repositório privado do GitHub
- Links atualizados para apontar para gitapprove.koyeb.app
- Melhorias na documentação

## [2.0.0] - 2025-11-10

### Added
- 🎉 Primeira versão pública do CLI no NPM
- Comando `gitapprove` instalável globalmente
- Autenticação via token permanente (formato gat_)
- Upload de commits para aprovação
- Listagem de commits pendentes
- Aprovação/rejeição via CLI
- Configuração de servidor customizado

### Features
- ✅ Upload automático de commits
- ✅ Aprovação colaborativa em equipe
- ✅ Push automático após todas as aprovações
- ✅ Interface web moderna
- ✅ Dashboard com estatísticas
- ✅ Gestão de times
- ✅ Histórico completo
- ✅ GitHub OAuth integration

### CLI Commands
```bash
gitapprove config --token <token>
gitapprove config --server <url>
gitapprove whoami
gitapprove upload
gitapprove upload -n <number>
gitapprove list
gitapprove list --all
gitapprove approve <hash>
gitapprove reject <hash> -c "comment"
```

### Technical Stack
- Next.js 14.2.33
- React 18
- TypeScript
- Tailwind CSS
- MySQL 8.0
- NextAuth.js
- Docker

### Deploy Options
- Koyeb (Free tier)
- Fly.io (Free tier)
- Railway (Free tier)
- Oracle Cloud (Always Free)
- VPS próprio

---

## Formato

O formato é baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/),
e este projeto adere ao [Semantic Versioning](https://semver.org/lang/pt-BR/).

### Tipos de mudanças
- **Added** - Novas funcionalidades
- **Changed** - Mudanças em funcionalidades existentes
- **Deprecated** - Funcionalidades que serão removidas
- **Removed** - Funcionalidades removidas
- **Fixed** - Correção de bugs
- **Security** - Correções de segurança
