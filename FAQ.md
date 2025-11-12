# ❓ FAQ - Perguntas Frequentes

## 📦 Instalação e Setup

### Como instalar o GitApprove CLI?

```bash
npm install -g gitapprove
```

Requer Node.js 14+ e npm.

### Como fazer login?

```bash
gitapprove login
```

O CLI abre automaticamente o navegador em https://gitapprove.koyeb.app/dashboard/cli-auth. Clique em "Gerar Código", cole no terminal, pronto!

### Preciso editar arquivos de configuração manualmente?

**Não!** O token é salvo automaticamente após o `gitapprove login`. O arquivo `~/.gitaprove/config.json` é criado e gerenciado pelo CLI.

### E se eu já estiver logado e executar `gitapprove login` novamente?

O CLI detecta e pergunta se você quer fazer logout primeiro:
```
⚠️  Você já está autenticado!
👤 Usuário atual: seu-username
Deseja fazer logout e autenticar novamente? (s/N):
```

### Onde fica o arquivo de configuração?

```bash
~/.gitaprove/config.json
```

Contém:
```json
{
  "apiUrl": "https://gitapprove.koyeb.app",
  "token": "gat_seu_token_aqui",
  "username": "seu-username"
}
```

### Como atualizar o CLI?

```bash
npm update -g gitapprove

# Ou verificar se há atualizações
gitapprove update-check
```

---

## 🔐 Autenticação e Segurança

### Qual a diferença entre token CLI e token OAuth do GitHub?

- **Token CLI** (`gat_...`): Para autenticar o CLI com o GitApprove
- **Token OAuth**: Obtido automaticamente no login web, usado para push automático

Você **não precisa** gerenciar o token OAuth manualmente!

### Meu token CLI expira?

Não! Os tokens CLI são permanentes. Mas você pode gerar um novo a qualquer momento com `gitapprove login`.

### Como revogar meu token?

Faça login novamente:
```bash
gitapprove login
```

Isso gera um novo token e invalida o anterior automaticamente.

### É seguro armazenar o token em texto plano?

O token fica em `~/.gitaprove/config.json` com permissões de leitura apenas para seu usuário (Unix/Linux). Trate-o como senha - não commite em repositórios públicos.

### Posso usar o mesmo token em múltiplos computadores?

Tecnicamente sim, mas **não é recomendado**. Cada máquina deveria ter seu próprio token. Execute `gitapprove login` em cada computador.

---

## 💻 Uso Diário

### Como enviar commits para aprovação?

```bash
# Fazer commits normalmente
git add .
git commit -m "feat: nova funcionalidade"

# Enviar para aprovação (NÃO use git push!)
gitapprove upload owner/repo
```

### Como enviar para uma branch específica?

```bash
gitapprove upload owner/repo --branch develop
gitapprove upload owner/repo -b feature/login
```

Se não especificar, usa `main` como padrão.

### Posso enviar múltiplos commits de uma vez?

Sim! Todos os commits locais não enviados serão incluídos:

```bash
git commit -m "feat: A"
git commit -m "fix: B"
git commit -m "docs: C"

gitapprove upload owner/repo
# Envia os 3 commits!
```

### Como ver meus commits pendentes?

```bash
gitapprove list              # Apenas pendentes
gitapprove list --all        # Todos (aprovados, rejeitados, pendentes)
```

### Como ver estatísticas?

```bash
gitapprove status
```

Mostra:
- Usuário logado
- Total de commits enviados
- Aprovados/Rejeitados/Pendentes
- Taxa de aprovação

### E se eu cometer um erro no commit?

Você pode:
1. **Antes de enviar**: `git commit --amend` ou `git reset`
2. **Depois de enviar**: Rejeite seu próprio commit no dashboard e envie um novo

---

## 👥 Times e Aprovações

### Quantas aprovações são necessárias?

**Todos os membros do time** (exceto o autor) precisam aprovar.

Exemplo: Time com 4 pessoas
- Autor envia commit
- 3 outros membros precisam aprovar
- Quando o 3º aprovar → push automático!

### Posso aprovar meu próprio commit?

**Não!** O sistema bloqueia auto-aprovação para garantir revisão por pares.

### O que acontece quando todos aprovam?

1. Status muda para "Aprovado"
2. Sistema faz `git push` automaticamente para o GitHub
3. Todos recebem notificação
4. Commit aparece no GitHub com o autor original preservado

### E se alguém rejeitar?

- Commit fica com status "Rejeitado"
- Desenvolvedor vê o motivo no CLI ou dashboard
- Precisa fazer correções e enviar novo commit
- O commit rejeitado não pode ser reaprovado

### Posso adicionar comentários ao aprovar?

Sim! Comentários são opcionais ao aprovar, mas **obrigatórios** ao rejeitar.

---

## 🚀 Push Automático

### Como funciona o push automático?

Quando todos aprovam:
1. Sistema busca o token OAuth do GitHub do dono do projeto
2. Usa a GitHub API para criar o commit
3. Preserva autor original, mensagem e arquivos
4. Marca commit como "pushed" no banco

### O push automático falhou, e agora?

**Solução:**
1. Dono do projeto: Logout + Login no dashboard web
2. Isso renova o token OAuth do GitHub
3. Tente aprovar novamente

### Posso fazer push manual?

Sim, mas **não é recomendado**:
```bash
gitapprove push
```

Use apenas se o push automático falhar repetidamente.

### O push respeita o autor original do commit?

Sim! O commit no GitHub aparece com:
- Autor original
- Data original  
- Mensagem original
- Arquivos exatos

### Funciona com repositórios privados?

Sim! O token OAuth tem permissão completa de `repo`.

---

## 🔧 Projetos e Configuração

### Como criar um projeto?

1. Acesse https://gitapprove.koyeb.app/dashboard/projects
2. Clique em "Criar Novo Projeto"
3. Selecione seu repositório GitHub
4. Configure o time
5. Salve!

### Posso ter múltiplos projetos?

Sim! Cada repositório pode ser um projeto separado.

### Como adicionar membros ao time?

Dashboard → Projetos → Seu Projeto → Time → Adicionar Membro

### Preciso criar branch no GitHub antes de enviar commits?

Sim! A branch precisa existir no repositório remoto. Se não existir, crie:

```bash
git checkout -b nova-branch
git push -u origin nova-branch
```

Depois você pode usar `gitapprove upload owner/repo -b nova-branch`.

### Como proteger branch no GitHub?

Recomendado para forçar uso do GitApprove:

```bash
# Método 1: Git local
git config branch.main.pushRemote no-push

# Método 2: GitHub Settings
# github.com/owner/repo/settings/branches
# Add rule → Require pull request reviews
```

---

## 🐛 Problemas Comuns

### ❌ "Invalid token"

**Causa:** Token expirado ou inválido

**Solução:**
```bash
gitapprove login
```

### ❌ "Unauthorized"

**Causa:** Não está autenticado ou token inválido

**Solução:**
```bash
rm ~/.gitaprove/config.json
gitapprove login
```

### ❌ "Nenhum commit local para enviar"

**Causa:** Não há commits não enviados

**Solução:**
```bash
# Ver se tem commits
git log origin/main..HEAD

# Se não houver, faça novos commits
git add .
git commit -m "mensagem"
```

### ❌ "Você não é membro do time"

**Causa:** Não está no time do projeto

**Solução:** Peça ao dono do projeto para adicionar você ao time.

### ❌ "Commit already processed"

**Causa:** Tentando aprovar commit já aprovado/rejeitado

**Solução:** Verifique o status no dashboard. Se foi rejeitado, envie novo commit.

### ❌ CLI não abre o navegador

**Causa:** Sistema não suporta `open` command

**Solução:** Abra manualmente:
```
https://gitapprove.koyeb.app/dashboard/cli-auth
```

### ❌ Push automático falha sempre

**Causas possíveis:**
1. Token OAuth expirado → Logout/Login no dashboard
2. Branch protegida no GitHub → Ajuste regras
3. Permissões insuficientes → Verifique token OAuth

---

## 🌿 Branches e Workflow

### Qual é a branch padrão?

`main` - mas você pode especificar qualquer branch com `--branch`.

### Posso usar com Git Flow?

Sim! Exemplo:

```bash
# Feature branches
gitapprove upload owner/repo -b feature/login

# Develop
gitapprove upload owner/repo -b develop

# Release
gitapprove upload owner/repo -b release/v2.0.0

# Hotfix
gitapprove upload owner/repo -b hotfix/critical-bug
```

### Como funciona com pull requests?

GitApprove **substitui** pull requests. O fluxo é:

- ❌ Tradicional: Branch → PR → Review → Merge
- ✅ GitApprove: Branch → Upload → Approve → Push automático

### Posso usar GitApprove e PRs juntos?

Tecnicamente sim, mas **não é recomendado**. São dois sistemas de revisão. Escolha um:
- **GitApprove**: Revisão antes do push
- **PRs**: Revisão depois do push

---

## 🎯 Casos de Uso

### Meu time é pequeno (2 pessoas). Vale a pena?

Sim! Mesmo com 2 pessoas, garante que:
- Ninguém faz push sem revisão
- Código é sempre visto por 2 pares de olhos
- Histórico de aprovações está documentado

### Trabalho sozinho. Posso usar?

Tecnicamente sim, mas o valor é limitado. GitApprove brilha com times de 2+ pessoas.

### Como usar em projetos open source?

1. Crie projeto no GitApprove
2. Adicione mantenedores ao time
3. Contribuidores externos: envie PRs normais no GitHub
4. Mantenedores internos: usam GitApprove

### Funciona com monorepos?

Sim! Cada monorepo é um projeto. Todos os commits vão para o mesmo repositório.

### Posso usar em CI/CD?

Sim! Configure o token CLI como secret:

```yaml
# GitHub Actions exemplo
- name: Upload to GitApprove
  run: |
    echo '{"apiUrl":"https://gitapprove.koyeb.app","token":"${{ secrets.GITAPPROVE_TOKEN }}"}' > ~/.gitaprove/config.json
    gitapprove upload owner/repo
```

---

## 📊 Dashboard Web

### Como acessar o dashboard?

https://gitapprove.koyeb.app/dashboard

Faça login com GitHub OAuth.

### Posso aprovar pelo dashboard?

Sim! É a forma mais comum. Veja o diff completo dos arquivos e aprove/rejeite.

### Como ver histórico de aprovações?

Dashboard → Histórico

Veja todos os commits, quem aprovou, quando, e comentários.

### Recebo notificações?

Sim, no dashboard. Notificações por email estão em desenvolvimento.

---

## 🔄 Atualizações

### Como saber se há nova versão?

```bash
gitapprove update-check
```

Ou o CLI verifica automaticamente a cada execução (não intrusivo).

### Como atualizar?

```bash
npm update -g gitapprove
```

### Onde vejo o changelog?

[CHANGELOG.md](./CHANGELOG.md) ou https://npmjs.com/package/gitapprove

---

## 🆘 Suporte

### Onde reportar bugs?

https://github.com/jotav96/GitApprove/issues

### Como pedir novas features?

Abra uma issue com a tag `enhancement`.

### Há suporte oficial?

Projeto open source comunitário. Suporte via issues e discussões no GitHub.

### Posso contribuir?

Sim! PRs são bem-vindos. Veja [CONTRIBUTING.md](./CONTRIBUTING.md) (quando criado).

---

## 💡 Dicas Avançadas

### Alias úteis

```bash
# ~/.bashrc ou ~/.zshrc
alias gap='gitapprove upload'
alias gal='gitapprove list'  
alias gas='gitapprove status'
alias galogin='gitapprove login'
```

### Ver commits antes de enviar

```bash
git log origin/main..HEAD --oneline
git diff origin/main..HEAD --stat
```

### Múltiplos repositórios

Se trabalha em vários repos, crie scripts:

```bash
# upload-all.sh
gitapprove upload org/repo1
gitapprove upload org/repo2
gitapprove upload org/repo3
```

### Integração com IDEs

Configure task no VS Code:

```json
{
  "label": "GitApprove Upload",
  "type": "shell",
  "command": "gitapprove upload owner/repo",
  "problemMatcher": []
}
```

---

**Não encontrou sua pergunta?** Abra uma issue: https://github.com/jotav96/GitApprove/issues
