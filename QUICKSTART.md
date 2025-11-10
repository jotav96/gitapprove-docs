# Guia Rápido - GitApprove

## 🚀 Início Rápido em 5 Minutos

### 1. Instale o CLI
```bash
npm install -g gitapprove
```

### 2. Obtenha seu Token
1. Acesse: https://gitapprove.koyeb.app
2. Login com GitHub
3. Configurações → Gerar Token
4. Copie o token

### 3. Configure
```bash
gitapprove config --token gat_seu_token
gitapprove whoami
```

### 4. Use!
```bash
cd ~/seu-projeto
git commit -m "feat: nova feature"
gitapprove upload
```

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

# 5. Quando aprovado, push é automático!
```

### Para quem APROVA commits:

1. Acesse: https://gitapprove.koyeb.app/dashboard/pending
2. Veja commits dos colegas
3. Revise o código
4. Clique: ✓ Aprovar ou ✗ Rejeitar
5. Sistema faz push quando todos aprovarem

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

## ❌ Erros Comuns

### "Token inválido"
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

## 📚 Próximos Passos

- [Instalação Completa](./CLI-INSTALL.md)
- [FAQ](./FAQ.md)
- [README Principal](./README.md)

---

**Desenvolvido por José Vitor**
