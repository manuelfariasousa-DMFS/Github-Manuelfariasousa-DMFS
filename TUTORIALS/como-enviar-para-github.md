# Tutorial — GitHub + Formulário online

Projeto: `Github-Manuelfariasousa-DMFS`
Conta GitHub: **manuelfariasousa-DMFS**
Repo: https://github.com/manuelfariasousa-DMFS/Github-Manuelfariasousa-DMFS

> ✅ **Já está tudo a funcionar.** Repo criado, autenticado, e o formulário
> publicado online. Para o dia-a-dia só precisas da secção
> [Alterações futuras](#alteracoes-futuras).

---

## Link do formulário (para o CMS da escola)

```
https://manuelfariasousa-dmfs.github.io/Github-Manuelfariasousa-DMFS/sugestoes.html
```

É este o link a meter no CMS para reencaminhar para a caixa de sugestões.

⚠️ **NÃO uses** o link `github.com/.../blob/...` nem o `raw.githubusercontent...`:
o primeiro mostra só o código-fonte, o segundo serve como texto. Nenhum
**mostra o formulário**. Só o link `github.io` acima é que renderiza a página.

### Primeira sugestão = confirmar email (uma vez)

O envio usa o serviço **formsubmit.co**, que manda as sugestões para
`diretor.dmfs@gmail.com`. Na **primeira** submissão, o formsubmit envia
um email de confirmação a esse endereço. Abre-o e clica em confirmar **uma
vez**. A partir daí todas as sugestões chegam automaticamente.

---

## Alteracoes futuras

Editaste o formulário ou outro ficheiro? Envia assim:

```powershell
cd "D:\XAMPP\htdocs\Github-Manuelfariasousa-DMFS"
git add .
git commit -m "descrição da mudança"
git push
```

O site online (GitHub Pages) reconstrói sozinho **~1 minuto** depois do push.

> 💡 Se mudares o `sugestoes.html`, é esse o ficheiro que o site mostra.
> O `sugestoes.php` é só uma cópia (não é usado pelo site online).

---

## Porque a password NÃO chega

Desde **agosto de 2021** o GitHub não aceita a password da conta para o `git`
(push/pull HTTPS). O servidor responde:

```
remote: Password authentication is not supported for Git operations.
```

A password serve **só** para entrar no site github.com. Para o `git` enviar
código, autentica-se via **GitHub CLI (`gh`)** — foi o método usado aqui —
ou via **token (PAT)**.

---

## Como tudo foi montado (referência)

Só precisas disto se mudares de PC, perderes o login, ou criares projeto novo.

### 1. Instalar o gh (uma vez por PC)

```powershell
winget install --id GitHub.cli
```

Fecha e reabre o terminal.

### 2. Login na conta DMFS (browser)

```powershell
gh auth login --hostname github.com --git-protocol https --web
```

- Mostra código `XXXX-XXXX`.
- Abre https://github.com/login/device, cola o código, autoriza.
- O browser tem de estar logado na conta **manuelfariasousa-DMFS**.

Confirmar:

```powershell
gh auth status
```

Deve dizer `Logged in ... account manuelfariasousa-DMFS`.

### 3. Criar repo + primeiro envio

```powershell
cd "D:\XAMPP\htdocs\Github-Manuelfariasousa-DMFS"
git init -b main
git add .
git commit -m "Primeiro commit"
gh repo create Github-Manuelfariasousa-DMFS --public --source=. --remote=origin --push
```

### 4. Publicar online (GitHub Pages)

```powershell
gh api -X POST repos/manuelfariasousa-DMFS/Github-Manuelfariasousa-DMFS/pages -f "source[branch]=main" -f "source[path]=/"
```

> No Git Bash mete `MSYS_NO_PATHCONV=1` antes do `gh api` (senão reescreve o URL).

Espera ~1 min e abre o link `github.io` da secção do topo.

---

## Alternativa — Token (PAT), sem gh

1. github.com (conta DMFS) → **Settings** → **Developer settings**
   → **Personal access tokens** → **Tokens (classic)**.
2. **Generate new token (classic)**, scope **`repo`**, gera, copia (`ghp_...`).
3. No `git push`, quando pedir:
   - Username: `manuelfariasousa-DMFS`
   - Password: cola o **token** (NÃO a password da conta)

---

## Resolver problemas

| Sintoma | Causa | Solução |
|---------|-------|---------|
| Link dá **404** | Pages não ativo / ficheiro errado | passo 4; usa link `.html` |
| Vejo código em vez do formulário | usaste link `blob` ou `raw` | usa link `github.io/.../sugestoes.html` |
| `Password authentication is not supported` | usaste password | usa `gh` ou token |
| `repository not found` | conta errada | `gh auth status` |
| `gh: command not found` | gh não instalado | passo 1 |
| Sugestões não chegam ao email | falta confirmar formsubmit | confirma o email da 1ª submissão |
| Mudança não aparece no site | Pages ainda a reconstruir | espera ~1 min e recarrega |

---

## Conteúdo do projeto

- `sugestoes.html` — formulário online (é este que o site mostra).
- `sugestoes.php` — cópia local (XAMPP); não usado pelo site online.
- `TUTORIALS/` — este guia.
