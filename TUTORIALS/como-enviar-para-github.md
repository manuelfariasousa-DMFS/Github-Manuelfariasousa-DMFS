# Como enviar o projeto para o GitHub

Projeto: `Github-Manuelfariasousa-DMFS`
Conta: **manuelfariasousa-DMFS**
Repo: https://github.com/manuelfariasousa-DMFS/Github-Manuelfariasousa-DMFS

> ✅ **Estado atual:** repo já criado e ligado. O git já está autenticado
> via GitHub CLI (`gh`). Para o dia-a-dia salta para a secção
> [Alterações futuras](#alteracoes-futuras).

---

## Importante: a password NÃO chega

Desde **agosto de 2021** o GitHub deixou de aceitar a password da conta para
operações de `git` (push/pull por HTTPS). O servidor responde:

```
remote: Password authentication is not supported for Git operations.
```

A password serve **só** para entrar no site github.com. Para enviar código
precisas de **autenticar** uma destas formas:

1. **GitHub CLI (`gh`)** — login pelo browser. ← foi este o método usado.
2. **Personal Access Token (PAT)** — um "token" que substitui a password.

---

## Alterações futuras

Já está tudo ligado e autenticado. Para enviar mudanças:

```powershell
cd "D:\XAMPP\htdocs\Github-Manuelfariasousa-DMFS"
git add .
git commit -m "descrição da mudança"
git push
```

Sem pedir password — o `gh` trata da autenticação.

---

## Recuperar / refazer a ligação (se preciso)

Só necessário se mudares de PC, perderes o login, ou começares projeto novo.

### 1. Instalar o gh (uma vez por PC)

```powershell
winget install --id GitHub.cli
```

Fecha e reabre o terminal.

### 2. Login na conta DMFS (browser)

```powershell
gh auth login --hostname github.com --git-protocol https --web
```

- Mostra um código tipo `XXXX-XXXX`.
- Abre https://github.com/login/device
- Cola o código e autoriza.

⚠️ O browser tem de estar logado na conta **manuelfariasousa-DMFS**
(não outra conta). Confirma com:

```powershell
gh auth status
```

Deve dizer `Logged in ... account manuelfariasousa-DMFS`.

### 3. Ligar a pasta ao repo (se for repo novo)

```powershell
cd "D:\XAMPP\htdocs\Github-Manuelfariasousa-DMFS"
git init -b main
git add .
git commit -m "Primeiro commit"
gh repo create Github-Manuelfariasousa-DMFS --public --source=. --remote=origin --push
```

`gh repo create` cria o repo no GitHub **e** faz o primeiro push de uma vez.

---

## Alternativa — Personal Access Token (sem gh)

### 1. Criar o token

1. github.com → conta **manuelfariasousa-DMFS** → **Settings**.
2. **Developer settings** → **Personal access tokens** → **Tokens (classic)**.
3. **Generate new token (classic)**, marca scope **`repo`**, gera.
4. Copia o token (`ghp_...`). Só aparece uma vez.

### 2. Push

```powershell
git push
```

Quando pedir credenciais:
- **Username**: `manuelfariasousa-DMFS`
- **Password**: cola o **token** `ghp_...` (NÃO a password da conta)

---

## Resolver problemas

| Erro | Causa | Solução |
|------|-------|---------|
| `Password authentication is not supported` | usaste a password | usa `gh` ou token |
| `repository not found` | repo não existe / conta errada | confirma `gh auth status` |
| `remote origin already exists` | remote já configurado | `git remote -v` para ver; já está bem |
| `gh: command not found` | gh não instalado | secção "Recuperar" passo 1 |
| pede login outra vez | token expirou | repete `gh auth login` |

---

## Conteúdo do projeto

- `sugestoes.php` — formulário de sugestões (envia via formsubmit.co).
- `TUTORIALS/` — este guia.
