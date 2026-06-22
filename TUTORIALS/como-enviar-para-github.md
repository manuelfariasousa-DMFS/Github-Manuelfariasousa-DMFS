# Como enviar o projeto para o GitHub

Guia para colocar a pasta `Github-Manuelfariasousa-DMFS` no GitHub
(conta: **manuelfariasousa-DMFS**).

---

## Importante: a password NÃO chega

Desde **agosto de 2021** o GitHub deixou de aceitar a password da conta para
operações de `git` (push/pull por HTTPS). O servidor responde:

```
remote: Password authentication is not supported for Git operations.
```

A password (`examesdois`) serve **só** para entrar no site github.com.
Para enviar código precisas de **uma destas** duas coisas:

1. **GitHub CLI (`gh`)** — fazes login pelo browser. (mais fácil)
2. **Personal Access Token (PAT)** — um "token" que substitui a password.

---

## Opção A — GitHub CLI (recomendado)

### 1. Instalar o gh

Windows (PowerShell):

```powershell
winget install --id GitHub.cli
```

Fecha e reabre o terminal a seguir.

### 2. Login (abre o browser)

```powershell
gh auth login
```

Escolhe:
- `GitHub.com`
- `HTTPS`
- `Login with a web browser`

Copia o código que aparece, cola no browser, autoriza.

### 3. Criar repo + enviar tudo

```powershell
cd "D:\XAMPP\htdocs\Github-Manuelfariasousa-DMFS"
git init
git add .
git commit -m "Primeiro commit"
gh repo create Github-Manuelfariasousa-DMFS --public --source=. --push
```

Pronto. O código fica em:
`https://github.com/manuelfariasousa-DMFS/Github-Manuelfariasousa-DMFS`

---

## Opção B — Personal Access Token (PAT)

### 1. Criar o token

1. Entra em github.com com a conta **manuelfariasousa-DMFS**.
2. Canto superior direito → **Settings**.
3. Em baixo à esquerda → **Developer settings**.
4. **Personal access tokens** → **Tokens (classic)**.
5. **Generate new token (classic)**.
6. Nome qualquer, validade à escolha.
7. Marca a caixa **`repo`** (dá acesso aos repositórios).
8. **Generate token** → copia o token (começa por `ghp_...`).
   ⚠️ Só aparece uma vez. Guarda já.

### 2. Criar o repo no site

1. Botão **+** (cima à direita) → **New repository**.
2. Nome: `Github-Manuelfariasousa-DMFS`.
3. Public. **Não** marques README/gitignore. → **Create repository**.

### 3. Enviar o código

```powershell
cd "D:\XAMPP\htdocs\Github-Manuelfariasousa-DMFS"
git init
git add .
git commit -m "Primeiro commit"
git branch -M main
git remote add origin https://github.com/manuelfariasousa-DMFS/Github-Manuelfariasousa-DMFS.git
git push -u origin main
```

Quando pedir credenciais:
- **Username**: `manuelfariasousa-DMFS`
- **Password**: **cola o token `ghp_...`** (NÃO a password `examesdois`)

---

## Resolver problemas

| Erro | Causa | Solução |
|------|-------|---------|
| `Password authentication is not supported` | usaste a password | usa token ou `gh` |
| `repository not found` | repo não existe | cria primeiro (passo B2) ou usa `gh repo create` |
| `remote origin already exists` | já adicionaste o remote | `git remote remove origin` e repete |
| `gh: command not found` | gh não instalado | Opção A passo 1 |

---

## Notas

- Pasta atual tem: `sugestoes.php` + esta pasta `TUTORIALS`.
- O `sugestoes.php` envia sugestões via formsubmit.co para um email.
- Depois do primeiro push, para enviar alterações futuras:

```powershell
git add .
git commit -m "descrição da mudança"
git push
```
