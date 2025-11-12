# Guia Rápido - GitApprove

## 🚀 Início Rápido em 5 Minutos

### 1. Login no Dashboard (OAuth Automático!)
1. Acesse: https://gitapprove.koyeb.app
2. Clique em **"Login com GitHub"**
3. Autorize o aplicativo
4. **GitHub token OAuth salvo automaticamente!** 🎉

### 2. Gere seu Token CLI
1. **Dashboard** → **Configurações** (⚙️)
2. **Gerar Token CLI**
3. Copie o token (formato: `gat_...`)

### 3. Instale o CLI
```bash
npm install -g gitapprove
```

### 4. Configure
```bash
gitapprove config --token gat_seu_token
gitapprove whoami
```

### 5. Use!
```bash
cd ~/seu-projeto
git commit -m "feat: nova feature"
gitapprove upload
```

**Aguarde aprovação → Push automático via OAuth! 🚀**

## 📋 Fluxo de Trabalho Completo

### Para quem FAZ commits:

```bash
# 1. Trabalhe normalmente
git add arquivo.js
git commit -m "feat: adicionar login"

# 2. NÃO faça git push!

# 3. Envie para aprovação
gitapprove upload

# 4. Aguarde aprovações do time
gitapprove list

# 5. Quando aprovado, push é automático via OAuth!
```

### Para quem APROVA commits:

1. Acesse: https://gitapprove.koyeb.app/dashboard/pending
2. Veja commits dos colegas
3. Revise o código
4. Clique: ✓ Aprovar ou ✗ Rejeitar
5. Sistema faz push automático quando todos aprovarem

## 🎯 Comandos Mais Usados

```bash
# Ver seus commits pendentes
gitapprove list

# Enviar commit para aprovação
gitapprove upload

# Ver quem você é
gitapprove whoami

# Enviar múltiplos commits
gitapprove upload -n 3
```

## 💡 Dicas

✅ **Faça commits pequenos** - Mais fácil de revisar  
✅ **Mensagens claras** - Use conventional commits  
✅ **Não force push** - Aguarde aprovação  
✅ **Revise rápido** - Não deixe o time esperando  
✅ **Login regular** - Mantenha token OAuth válido

## ⚡ Como Funciona o Push Automático

```
Login GitHub → Token OAuth salvo → Commit aprovado → Push via API → Pronto!
```

**Nenhuma configuração manual! Totalmente automático! 🎉**

## ❌ Erros Comuns

### "Token CLI inválido"
```bash
# Gere novo token no dashboard e configure
gitapprove config --token gat_novo_token
```

### "Não é um repositório git"
```bash
# Execute dentro de uma pasta Git
cd ~/seu-projeto-git
gitapprove upload
```

### "Nenhum commit para enviar"
```bash
# Certifique-se que fez commit antes
git log  # Veja se tem commits
```

### "Push automático falhou"
```bash
# Token OAuth expirado - Faça logout e login novamente
# Ou repositório vazio - Faça push inicial manualmente
```

### "Repositório vazio"
Se o repo não tem commits ainda:
```bash
echo "# Meu Projeto" > README.md
git add README.md
git commit -m "Initial commit"
git push origin main

# Agora use GitApprove
gitapprove upload
```

## 📚 Próximos Passos

- [Workflow Completo](./WORKFLOW.md)
- [Instalação Completa](./CLI-INSTALL.md)
- [FAQ](./FAQ.md)
- [README Principal](./README.md)

---

**Desenvolvido por José Vitor**
