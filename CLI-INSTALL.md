# Instalação do GitApprove CLI

## 📦 Instalação via NPM

```bash
npm install -g gitapprove
```

## ✅ Verificar Instalação

```bash
gitapprove --version
# Deve retornar: 2.0.1 (ou superior)

gitapprove --help
# Lista todos os comandos disponíveis
```

## ⚙️ Configuração Inicial

### 1. Obter Token de Acesso

1. Acesse: https://gitapprove.koyeb.app
2. Faça login com sua conta GitHub
3. Vá em **Configurações** (⚙️)
4. Clique em **Gerar Meu Token**
5. Copie o token (formato: `gat_...`)

### 2. Configurar CLI

```bash
# Configurar token
gitapprove config --token gat_seu_token_aqui

# Configurar servidor (opcional - padrão: gitapprove.koyeb.app)
gitapprove config --server https://gitapprove.koyeb.app

# Verificar configuração
gitapprove whoami
```

## 🚀 Primeiro Uso

```bash
# Entre em um projeto Git
cd ~/seu-projeto

# Faça um commit normalmente
git add .
git commit -m "feat: minha feature"

# Envie para aprovação (NÃO faça git push)
gitapprove upload

# Sucesso! Agora aguarde aprovação do time
```

## 🔧 Comandos Disponíveis

### Configuração
```bash
gitapprove config --token <token>    # Definir token
gitapprove config --server <url>     # Definir servidor
gitapprove whoami                    # Ver usuário logado
```

### Upload de Commits
```bash
gitapprove upload                    # Enviar último commit
gitapprove upload -n 3               # Enviar últimos 3 commits
gitapprove upload -b develop         # Enviar de branch específica
```

### Listar Commits
```bash
gitapprove list                      # Listar pendentes
gitapprove list --all                # Listar todos (incluindo aprovados/rejeitados)
```

### Aprovar/Rejeitar (via CLI)
```bash
gitapprove approve <hash>                    # Aprovar
gitapprove reject <hash> -c "precisa testes" # Rejeitar com motivo
```

## 📂 Onde o CLI Armazena Configurações

**Linux/Mac:**
```
~/.gitapprove/config.json
```

**Windows:**
```
C:\Users\SeuUsuario\.gitapprove\config.json
```

**Formato do arquivo:**
```json
{
  "token": "gat_...",
  "server": "https://gitapprove.koyeb.app"
}
```

## 🔄 Atualizar CLI

```bash
npm update -g gitapprove
```

## 🗑️ Desinstalar

```bash
npm uninstall -g gitapprove
```

## ❓ Troubleshooting

### Comando não encontrado

```bash
# Verifique se npm global está no PATH
npm config get prefix

# Adicione ao PATH (se necessário)
# Linux/Mac: export PATH="$PATH:$(npm config get prefix)/bin"
# Windows: adicione nas variáveis de ambiente
```

### Token inválido

```bash
# Gere novo token no dashboard
# Configure novamente
gitapprove config --token gat_novo_token
gitapprove whoami  # Valida
```

### Erro de conexão

```bash
# Verifique URL do servidor
gitapprove config --server https://gitapprove.koyeb.app

# Teste conexão
curl https://gitapprove.koyeb.app/api/health
```

## 📚 Próximos Passos

- [Guia Rápido](./QUICKSTART.md)
- [FAQ](./FAQ.md)
- [Voltar ao README](./README.md)

---

**Desenvolvido por José Vitor**
