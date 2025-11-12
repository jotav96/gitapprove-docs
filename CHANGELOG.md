# 📝 Changelog

Todas as mudanças notáveis do GitApprove CLI serão documentadas aqui.

O formato é baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/).

## [2.1.6] - 2025-11-12

### ✨ Melhorias Principais
- **Autenticação simplificada**: Removida necessidade de configuração manual do token
- **Login inteligente**: CLI detecta se já está autenticado e oferece opção de logout
- **Token permanente no banco**: Tokens CLI agora são salvos na tabela `cli_tokens` do banco de dados

### 🔧 Mudanças
- Comando `gitapprove login` agora verifica se já está autenticado antes de prosseguir
- Se já logado, mostra username atual e pergunta se quer fazer logout (padrão: Não)
- Token gerado via `/api/cli-auth` agora é salvo no banco de dados (formato: `gat_[random][timestamp][random]`)
- Um token por usuário (atualiza o existente se já houver)
- Help do CLI simplificado: removida seção de "configuração manual"
- README do CLI atualizado com fluxo de 3 passos simples

### 🐛 Correções
- **CRÍTICO**: Corrigido erro "Invalid token" ao executar `gitapprove upload`
  - Problema: Token gerado era Base64 temporário não salvo no banco
  - Solução: Token permanente `gat_` agora persiste no banco na tabela `cli_tokens`
- Removido comando bash `nano` acidentalmente inserido no arquivo TypeScript

### 📚 Documentação
- README: Fluxo simplificado de instalação (3 passos)
- Help interno: Removidas referências a configuração manual
- Seção "DICAS" adicionada explicando comportamento do token automático

### 🗑️ Removido
- Seção "Token de Acesso Pessoal" removida da página `/dashboard/settings`
- Botões "Gerar Meu Token" e "Regenerar Token" removidos
- Instruções de edição manual do `config.json` removidas da documentação

### 📦 Migração
**Usuários da v2.1.5 ou anterior:**
1. Execute `gitapprove login` novamente
2. Token antigo será automaticamente atualizado
3. Novo token funciona imediatamente com todas as APIs

**Não é necessário** remover `~/.gitaprove/config.json` manualmente.

## [2.1.5] - 2025-11-11

### ✨ Novo
- Verificador automático de atualizações ao iniciar CLI
- Comando `gitapprove update-check` para verificação manual
- Função `compareVersions()` para comparação semântica de versões
- Consulta à API do npm registry para verificar última versão

### 🔧 Mudanças
- Links da documentação apontam para `gitapprove-docs` (público)
- Repositório do package.json corrigido
- Keywords adicionadas: "oauth", "automation"

## [2.1.4] - 2025-11-11

### 🐛 Correções
- Links do CLI apontavam para repositório privado
- Corrigido para apontar para https://github.com/jotav96/gitapprove-docs

### 📚 Documentação
- README.md atualizado com links corretos
- Seção "Links" adicionada ao README

## [2.1.3] - 2025-11-11

### 🔧 Mudanças
- Configuração padrão do servidor alterada para `https://gitapprove.koyeb.app`
- Antes: `https://gitapprove.vercel.app`
- Arquivo `config.json` agora é criado automaticamente com valores padrão

### ✨ Melhorias
- Função `getConfig()` cria arquivo com defaults se não existir
- Usuário não precisa criar `config.json` manualmente

## [2.1.2] - 2025-11-10

### 🐛 Correções
- Correções gerais de bugs
- Melhorias de estabilidade

## [2.1.1] - 2025-11-09

### 🐛 Correções
- Correções de bugs menores
- Ajustes de performance

## [2.1.0] - 2025-11-08

### ✨ Novo
- **Push automático via OAuth**: Commits aprovados são enviados automaticamente ao GitHub
- Suporte a múltiplas branches com opção `--branch` ou `-b`
- Comando `gitapprove upload` aceita branch customizada
- Sistema de times obrigatório para projetos

### 🔧 Mudanças
- Branch padrão alterada para `main`
- Upload de commits agora envia conteúdo completo dos arquivos
- API `/api/commits/upload` atualizada

### 📚 Documentação
- Documentação sobre push automático adicionada
- Exemplos de uso com branches diferentes
- FAQ expandida com seção sobre OAuth

## [2.0.0] - 2025-11-05

### ✨ Novo
- **Sistema de Times**: Projetos agora requerem times configurados
- Aprovação por todos os membros do time (exceto autor)
- Interface web completamente reformulada
- Dashboard com estatísticas em tempo real

### 💥 Breaking Changes
- Projetos sem time não funcionam mais (migração necessária)
- API de aprovação alterada para considerar times
- Estrutura do banco de dados modificada

### 🔧 Mudanças
- Banco de dados migrado de MySQL para PostgreSQL/Neon
- Autenticação via NextAuth.js
- Interface moderna com Tailwind CSS

## [1.5.0] - 2025-10-20

### ✨ Novo
- Comando `gitapprove status` para ver estatísticas
- Comando `gitapprove list --all` para ver todos os commits
- Suporte a comentários em aprovações

### 🔧 Mudanças
- Melhorias na interface do CLI
- Cores e emojis para melhor UX
- Mensagens mais claras

## [1.0.0] - 2025-10-01

### ✨ Lançamento Inicial
- Comando `gitapprove upload` para enviar commits
- Comando `gitapprove list` para listar commits pendentes
- Comando `gitapprove approve/reject` para aprovar/rejeitar
- Comando `gitapprove config` para configurar token
- Dashboard web básico
- Sistema de aprovações simples (sem times)
- Autenticação com token manual

---

## 🔗 Links

- **NPM**: https://npmjs.com/package/gitapprove
- **GitHub**: https://github.com/jotav96/gitapprove-docs
- **Dashboard**: https://gitapprove.koyeb.app
- **Issues**: https://github.com/jotav96/GitApprove/issues

## 📋 Legendas

- ✨ **Novo**: Novas funcionalidades
- 🔧 **Mudanças**: Alterações em funcionalidades existentes
- 🐛 **Correções**: Bugs corrigidos
- 📚 **Documentação**: Melhorias na documentação
- 🗑️ **Removido**: Funcionalidades removidas
- 💥 **Breaking Changes**: Mudanças que quebram compatibilidade
- 📦 **Migração**: Instruções de migração
- ⚡ **Performance**: Melhorias de performance
- 🔒 **Segurança**: Correções de segurança
