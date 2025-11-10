# FAQ - Perguntas Frequentes

## 🤔 Geral

### O que é o GitApprove?
Sistema de aprovação colaborativa de commits. Todo commit precisa da aprovação de TODOS os membros do time antes de ir para o GitHub.

### É gratuito?
Sim! O CLI é open source (NPM) e o sistema pode ser auto-hospedado gratuitamente.

### Preciso pagar?
Não. Use a versão hospedada em https://gitapprove.koyeb.app gratuitamente ou instale em seu próprio servidor.

## 💻 CLI

### Como instalo o CLI?
```bash
npm install -g gitapprove
```

### Onde obtenho o token?
1. Acesse https://gitapprove.koyeb.app
2. Login com GitHub
3. Configurações → Gerar Token

### O token expira?
Não. Tokens são permanentes até serem revogados manualmente.

### Posso usar em múltiplos computadores?
Sim! Use o mesmo token em todos os computadores.

### Como atualizo o CLI?
```bash
npm update -g gitapprove
```

## 🔐 Segurança

### Meu código fica seguro?
Sim. Você faz login com GitHub OAuth. Não armazenamos senhas.

### Quem pode ver meus commits?
Apenas membros do seu time no GitApprove.

### Posso revogar meu token?
Sim, no dashboard: Configurações → Revogar Token

## 👥 Times e Aprovações

### Quantas pessoas precisam aprovar?
TODOS os membros do time (exceto o autor do commit).

### Posso aprovar meu próprio commit?
Não. O sistema bloqueia auto-aprovação.

### E se alguém rejeitar?
O commit fica com status "rejeitado" e não vai para o GitHub. O autor precisa corrigir e enviar novamente.

### Posso ter múltiplos times?
Sim! Cada projeto pode ter seu próprio time.

## 🚀 Workflow

### Qual é o fluxo correto?
```bash
1. git commit -m "..."
2. gitapprove upload  # NÃO faça git push
3. Time aprova via web
4. Push automático quando todos aprovarem
```

### E se eu fizer `git push` direto?
O commit vai para o GitHub normalmente, mas não passa pela aprovação do time.

### Posso enviar vários commits de uma vez?
Sim:
```bash
gitapprove upload -n 3  # Envia últimos 3 commits
```

### Como vejo status dos meus commits?
```bash
gitapprove list
```
Ou acesse: https://gitapprove.koyeb.app/dashboard/pending

## 🔧 Problemas Técnicos

### "Comando não encontrado"
```bash
# Reinstale globalmente
npm install -g gitapprove

# Verifique PATH
which gitapprove
```

### "Token inválido"
```bash
# Gere novo token e configure
gitapprove config --token gat_novo_token
```

### "Erro de conexão"
```bash
# Verifique servidor
gitapprove config --server https://gitapprove.koyeb.app

# Teste conexão
curl https://gitapprove.koyeb.app/api/health
```

### "Push automático falhou"
Verifique no dashboard web os logs de erro. Possíveis causas:
- Branch protegida no GitHub
- Sem permissão de push
- Conflito de merge

## 📊 Features

### Posso ver quem aprovou?
Sim! No dashboard web, clique em "Detalhes" do commit.

### Tem histórico de aprovações?
Sim. Dashboard → Histórico mostra todos os commits.

### Posso adicionar comentários?
Sim. Ao aprovar/rejeitar, você pode adicionar comentários.

### Tem notificações?
No momento, apenas via dashboard web. Email notifications em breve.

## 🌐 Deploy e Hospedagem

### Posso hospedar eu mesmo?
Sim! O sistema usa Docker. Solicite acesso ao código-fonte.

### Qual o requisito mínimo?
- 512MB RAM
- MySQL 8.0
- Node.js 18+
- Docker (opcional)

### Tem deploy gratuito?
Sim! Koyeb, Fly.io, Railway oferecem tier gratuito.

## 💡 Melhores Práticas

### Commits atômicos
Faça um commit = uma funcionalidade. Mais fácil de revisar.

### Mensagens claras
Use conventional commits:
```bash
feat: adicionar login
fix: corrigir bug no header
docs: atualizar README
```

### Revise rápido
Não deixe commits pendentes por muito tempo.

### Comunique-se
Use os comentários para dar feedback construtivo.

## 📞 Suporte

### Como reporto um bug?
Abra uma issue: https://github.com/jotav96/gitapprove-docs/issues

### Como sugiro uma feature?
Mesma URL acima, descreva sua sugestão.

### Tem Discord/Slack?
Em breve! Por enquanto use as issues do GitHub.

## 📚 Recursos

- [README Principal](./README.md)
- [Instalação CLI](./CLI-INSTALL.md)
- [Guia Rápido](./QUICKSTART.md)
- [NPM Package](https://www.npmjs.com/package/gitapprove)

---

**Tem outra dúvida? Abra uma [issue](https://github.com/jotav96/gitapprove-docs/issues)!**

**Desenvolvido por José Vitor**
