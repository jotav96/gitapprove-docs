# 🔄 Fluxo de Trabalho Correto - GitApprove

## ⚠️ **IMPORTANTE: NÃO USE `git push` DIRETAMENTE!**

O GitApprove foi criado para **IMPEDIR** que código não revisado vá para o GitHub. Se você usar `git push` diretamente, o sistema é completamente contornado.

---

## ✅ Fluxo Correto de Trabalho

### 📋 Passo a Passo Completo

#### 1️⃣ **Desenvolva Normalmente**

```bash
# Trabalhe no seu projeto
cd seu-projeto

# Faça alterações nos arquivos
vim arquivo.js

# Adicione ao staging
git add arquivo.js

# Faça o commit LOCALMENTE
git commit -m "feat: adicionar nova funcionalidade"
```

⚠️ **PARE AQUI! NÃO faça `git push`!**

---

#### 2️⃣ **Envie para Aprovação com GitApprove**

```bash
# Use o CLI do GitApprove ao invés de git push
gitaprove upload
```

**O que acontece:**
- ✅ Seu commit é enviado para o sistema GitApprove
- ✅ Status fica como **PENDING** (pendente)
- ✅ Todos os membros do time são notificados
- ✅ O código **NÃO vai para o GitHub ainda**

---

#### 3️⃣ **Aguarde Aprovação da Equipe**

**Você (autor do commit):**
- ❌ **NÃO pode aprovar** seu próprio commit
- ⏳ Aguarda que TODOS os membros do time aprovem
- 👀 Pode acompanhar o progresso no dashboard

**Seus colegas de time:**
1. Acessam https://gitapprove.koyeb.app/dashboard/pending
2. Revisam seu código
3. Clicam em **✓ Aprovar** ou **✗ Rejeitar**
4. Podem deixar comentários

---

#### 4️⃣ **Sistema Faz Push Automático**

Quando **TODOS os membros aprovarem**:

```
✅ Todos aprovaram!
    ↓
🚀 Sistema faz git push automaticamente
    ↓
📧 Código aparece no GitHub
    ↓
✨ Commit está no repositório!
```

**Você NÃO precisa fazer nada!** O push é automático.

---

## 🚫 O Que NÃO Fazer

### ❌ **NUNCA faça isso:**

```bash
git push origin main        # ❌ ERRADO! Pula o sistema de aprovação
git push origin feature     # ❌ ERRADO! Vai direto pro GitHub
git push -f origin main     # ❌ ERRADO! Ainda pior!
```

**Por quê não?**
- Seu código vai direto para o GitHub **SEM REVISÃO**
- Outros desenvolvedores não podem revisar
- Todo o propósito do GitApprove é perdido
- O time perde controle sobre o que entra no repo

---

## ✅ Comandos Permitidos

### **Durante o desenvolvimento:**

```bash
git status              # ✅ Ver status dos arquivos
git add arquivo.js      # ✅ Adicionar arquivos
git commit -m "..."     # ✅ Fazer commit local
git log                 # ✅ Ver histórico
git diff                # ✅ Ver diferenças
git checkout -b feat    # ✅ Criar branch
```

### **Para enviar código:**

```bash
gitaprove upload        # ✅ ÚNICO comando para enviar código
gitaprove list          # ✅ Ver seus commits pendentes
gitaprove whoami        # ✅ Ver seu status
```

### **Para revisar código dos colegas:**

```bash
# Use o dashboard web:
https://gitapprove.koyeb.app/dashboard/pending

# Ou via CLI (se disponível):
gitaprove list          # Ver commits pendentes
gitaprove approve <hash> # Aprovar commit
gitaprove reject <hash>  # Rejeitar commit
```

---

## 📖 Cenário Real - Exemplo Completo

### **Situação:** João precisa adicionar uma nova feature

#### **João (Desenvolvedor):**

```bash
# 1. Cria branch local
git checkout -b feature/nova-api

# 2. Desenvolve a funcionalidade
vim src/api/reports.js

# 3. Testa localmente
npm test

# 4. Adiciona e commita
git add src/api/reports.js
git commit -m "feat: adicionar endpoint de relatórios

- Endpoint GET /api/reports
- Filtros por data
- Exportação CSV"

# 5. ENVIA PARA APROVAÇÃO (não usa git push!)
gitaprove upload

# Output:
# ✓ Commit enviado para aprovação!
# ⏳ Aguardando 2 aprovação(ões)
# 👀 Acompanhe em: https://gitapprove.koyeb.app/dashboard
```

**João agora espera. Ele NÃO pode fazer mais nada com este commit.**

---

#### **Maria (Tech Lead):**

```bash
# Acessa o dashboard
# https://gitapprove.koyeb.app/dashboard/pending

# Vê o commit de João:
# 📝 feat: adicionar endpoint de relatórios
# 👤 Por: João Silva
# ⏳ Aprovações: 0/2

# Maria revisa o código
# Clica: ✓ Aprovar
# Adiciona comentário: "LGTM! Excelente implementação"
```

**Status agora: Aprovações 1/2**

---

#### **Pedro (Senior Dev):**

```bash
# Pedro também acessa o dashboard
# Revisa o código de João
# Clica: ✓ Aprovar
# Comentário: "Approved! Bom trabalho no tratamento de erros"
```

**Status agora: Aprovações 2/2 ✅ COMPLETO!**

---

#### **Sistema GitApprove (Automático):**

```bash
# Sistema detecta que todos aprovaram
# Executa automaticamente:

git push origin feature/nova-api

# ✅ Código vai para o GitHub
# 📧 João recebe notificação: "Seu commit foi aprovado e enviado!"
```

---

#### **João (Final):**

```bash
# João atualiza seu repositório local
git pull origin feature/nova-api

# Pronto! O código está no GitHub E foi revisado por toda a equipe
```

---

## 🎯 Regras de Ouro

### ✅ **SEMPRE:**

1. ✅ Use `gitaprove upload` para enviar commits
2. ✅ Aguarde aprovação de TODOS os membros do time
3. ✅ Revise commits dos seus colegas rapidamente
4. ✅ Deixe comentários construtivos nas revisões
5. ✅ Use `git pull` depois que seu commit for aprovado

### ❌ **NUNCA:**

1. ❌ Use `git push` diretamente
2. ❌ Force push (`git push -f`)
3. ❌ Aprove seus próprios commits (sistema bloqueia)
4. ❌ Contorne o sistema usando outro método
5. ❌ Compartilhe seu token com outros

---

## 🔒 Proteções do Sistema

O GitApprove tem várias proteções:

### **1. Auto-aprovação bloqueada**
- ❌ Você não pode aprovar seus próprios commits
- 📊 Sistema rastreia quem é o autor

### **2. Aprovação unânime obrigatória**
- ⏳ TODOS os membros precisam aprovar
- 🚫 Um único "rejeitar" cancela o commit

### **3. Histórico completo**
- 📝 Todas as ações são registradas
- 👥 Você pode ver quem aprovou/rejeitou
- 💬 Comentários são preservados

### **4. Tokens pessoais**
- 🔑 Cada usuário tem seu próprio token
- 🚫 Não pode usar token de outra pessoa
- 🔄 Tokens podem ser revogados

---

## 📊 Acompanhamento de Status

### **Ver seus commits pendentes:**

```bash
gitaprove list
```

**Output:**
```
📋 Commits Pendentes:

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
feat: adicionar endpoint de relatórios
👤 Você (João Silva)
⏳ Aprovações: 1/2
📅 2 horas atrás
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### **Ver no Dashboard:**

https://gitapprove.koyeb.app/dashboard/pending

- 🟢 Verde = Seus commits (você NÃO pode aprovar)
- 🔵 Azul = Commits de colegas (você PODE aprovar)
- ✓ Aprovado = Você já aprovou
- ⏳ Pendente = Aguardando sua aprovação

---

## 💡 Dicas e Boas Práticas

### **Para Desenvolvedores:**

1. **Commits pequenos e atômicos**
   - Um commit = uma funcionalidade
   - Mais fácil de revisar

2. **Mensagens claras**
   ```bash
   git commit -m "feat: adicionar autenticação OAuth
   
   - Implementar login com GitHub
   - Adicionar middleware de sessão
   - Testes unitários incluídos"
   ```

3. **Teste antes de enviar**
   - Rode `npm test` antes de `gitaprove upload`
   - Evita commits rejeitados

4. **Não acumule commits**
   - Envie um commit por vez
   - Facilita a revisão

### **Para Revisores:**

1. **Revise rapidamente**
   - Não deixe o time esperando
   - Bloqueie 30min por dia para revisões

2. **Seja construtivo**
   - ✅ "Sugiro refatorar esta função para melhorar legibilidade"
   - ❌ "Este código está horrível"

3. **Teste localmente se possível**
   ```bash
   git fetch
   git checkout feature/branch-do-colega
   npm test
   ```

4. **Use rejeição com sabedoria**
   - Explique claramente o motivo
   - Sugira melhorias específicas

---

## 🆘 Troubleshooting

### **"Meu commit está pendente há muito tempo"**

**Causas:**
- Algum membro do time não revisou ainda
- Membro está de férias/ausente

**Solução:**
1. Veja quem ainda não aprovou no dashboard
2. Entre em contato com a pessoa
3. Se urgente, tech lead pode adicionar temporariamente ao time

---

### **"Fiz git push por engano, e agora?"**

**O que aconteceu:**
- Código foi direto para o GitHub
- Pulou o processo de revisão

**Solução:**
1. **Reverta o commit:**
   ```bash
   git revert HEAD
   git push origin main
   ```

2. **Envie corretamente:**
   ```bash
   git add .
   git commit -m "feat: [mesma funcionalidade]"
   gitaprove upload
   ```

3. **Avise o time** sobre o erro

---

### **"Meu commit foi rejeitado"**

**O que fazer:**

1. **Veja o motivo:**
   - Dashboard → Histórico → Detalhes
   - Leia os comentários dos revisores

2. **Corrija o problema:**
   ```bash
   # Faça as alterações necessárias
   git add .
   git commit -m "fix: corrigir problemas apontados na revisão"
   ```

3. **Envie novamente:**
   ```bash
   gitaprove upload
   ```

---

## 📚 Comandos de Referência Rápida

### **Setup Inicial (uma vez):**

```bash
# Instalar CLI
npm install -g gitapprove

# Obter token em: https://gitapprove.koyeb.app/dashboard/settings
gitaprove config --token gat_seu_token_aqui

# Verificar
gitaprove whoami
```

### **Fluxo Diário:**

```bash
# 1. Desenvolver
git add .
git commit -m "mensagem"

# 2. Enviar para aprovação
gitaprove upload

# 3. Ver status
gitaprove list

# 4. Depois de aprovado, atualizar
git pull
```

### **Revisão de Código:**

```bash
# Ver commits pendentes
gitaprove list

# No dashboard:
# https://gitapprove.koyeb.app/dashboard/pending
# Clicar em ✓ Aprovar ou ✗ Rejeitar
```

---

## 🎓 Resumo Final

### **Lembre-se:**

1. 🚫 **NUNCA use `git push` diretamente**
2. ✅ **SEMPRE use `gitaprove upload`**
3. 👥 **AGUARDE aprovação de TODOS**
4. 🤖 **Sistema faz push automático**
5. 📊 **Acompanhe no dashboard**

### **Fluxo Simples:**

```
Código → git commit → gitaprove upload → Time aprova → Push automático → GitHub
```

---

## 🔗 Links Úteis

- **Dashboard:** https://gitapprove.koyeb.app
- **Gerar Token:** https://gitapprove.koyeb.app/dashboard/settings
- **Ver Pendentes:** https://gitapprove.koyeb.app/dashboard/pending
- **Histórico:** https://gitapprove.koyeb.app/dashboard/history
- **NPM Package:** https://www.npmjs.com/package/gitapprove

---

## 💬 Precisa de Ajuda?

- **Issues:** https://github.com/jotav96/GitApprove/issues
- **Email:** Contate o administrador do sistema

---

**Desenvolvido com ❤️ para equipes que valorizam code review**
