# Changelog

Todas as mudanças notáveis neste projeto serão documentadas neste arquivo.

O formato é baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/),
e este projeto adere ao [Semantic Versioning](https://semver.org/lang/pt-BR/).

## [2.1.3] - 2024-11-12

### ✨ Adicionado
- **Push Automático via OAuth!** - Sistema agora usa token GitHub OAuth salvo automaticamente no login
- Validação de repositórios vazios com mensagem de erro clara e instruções
- Push direto via GitHub API (sem necessidade de clone)
- Detecção automática de branch vazia (404) com instruções de inicialização

### 🔧 Corrigido
- Repositório npm corrigido de `gitapprove-docs` (privado) para `GitApprove` (público)
- Mensagens de erro melhoradas para repositórios sem commits
- Tratamento de erro 404 ao tentar push em repo vazio

### 📝 Alterado
- Documentação atualizada com fluxo OAuth automático
- README.md com ênfase no push sem configuração manual
- FAQ expandido com perguntas sobre OAuth e repos vazios
- CLI-INSTALL.md atualizado com diferença entre token OAuth e token CLI

### 🗑️ Removido
- Endpoints de debug (`/api/debug/*`) - 9 arquivos, ~459 linhas
- Arquivos de teste da raiz - 29 arquivos (migration-*.sql, test-*.*, etc)
- Script check-tokens.js obsoleto

## [2.1.2] - 2024-11-10

### 🔧 Corrigido
- Correção de bugs no sistema de aprovação
- Melhorias na sincronização de times

## [2.1.0] - 2024-11-08

### ✨ Adicionado
- Sistema de times e membros
- Dashboard com estatísticas
- Filtros de commits por status
- Gestão de colaboradores GitHub

### 🔧 Corrigido
- Performance na listagem de commits
- Sincronização com repositórios GitHub

## [2.0.1] - 2024-11-05

### 🔧 Corrigido
- Correções de bugs menores
- Melhorias na estabilidade do CLI

## [2.0.0] - 2024-11-01

### ✨ Adicionado
- CLI global via npm
- Sistema de aprovação colaborativa
- Interface web moderna
- Autenticação GitHub OAuth
- Tokens permanentes (gat_...)
- Dashboard de commits
- Sistema de notificações
- Docker Compose completo

### 🔧 Corrigido
- Primeira versão estável

## [1.0.0] - 2024-10-15

### ✨ Adicionado
- Versão inicial do projeto
- Conceito básico de aprovação de commits

---

## Tipos de Mudanças

- `✨ Adicionado` - Para novas funcionalidades
- `🔧 Corrigido` - Para correções de bugs
- `📝 Alterado` - Para mudanças em funcionalidades existentes
- `🗑️ Removido` - Para funcionalidades removidas
- `🔒 Segurança` - Para correções de vulnerabilidades
- `📚 Documentação` - Para mudanças apenas na documentação

---

**Desenvolvido por José Vitor**
