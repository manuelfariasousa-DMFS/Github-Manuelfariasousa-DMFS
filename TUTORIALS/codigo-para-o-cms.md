# Código para incorporar no CMS da escola

Link do formulário (a caixa de sugestões já publicada):

```
https://manuelfariasousa-dmfs.github.io/Github-Manuelfariasousa-DMFS/sugestoes.html
```

Escolhe **uma** das opções abaixo conforme o que o CMS permite.
A maioria dos CMS (WordPress, Moodle, etc.) tem um modo **"HTML"** ou
**"</> Código"** no editor — cola aí o snippet.

---

## Opção 1 — Botão (recomendado)

Abre o formulário numa aba nova. Mais simples e seguro.

```html
<p style="text-align:center;">
  <a href="https://manuelfariasousa-dmfs.github.io/Github-Manuelfariasousa-DMFS/sugestoes.html"
     target="_blank" rel="noopener"
     style="display:inline-block;background:#2563eb;color:#fff;
            padding:12px 24px;border-radius:8px;text-decoration:none;
            font-family:sans-serif;font-size:16px;">
    📝 Deixar uma sugestão
  </a>
</p>
```

---

## Opção 2 — Link de texto simples

Para meter no meio de uma frase.

```html
<a href="https://manuelfariasousa-dmfs.github.io/Github-Manuelfariasousa-DMFS/sugestoes.html" target="_blank" rel="noopener">Clica aqui para deixar uma sugestão</a>
```

---

## Opção 3 — Formulário embebido (iframe)

Mostra a caixa de sugestões **dentro** da página do CMS, sem sair.

```html
<iframe
  src="https://manuelfariasousa-dmfs.github.io/Github-Manuelfariasousa-DMFS/sugestoes.html"
  title="Caixa de Sugestões"
  style="width:100%;max-width:650px;height:500px;border:0;margin:auto;display:block;"
  loading="lazy">
</iframe>
```

> ⚠️ Alguns CMS bloqueiam `<iframe>` por segurança. Se aparecer em branco,
> usa a Opção 1 (botão).

---

## Opção 4 — Reencaminhamento automático (redirect)

A página do CMS salta **sozinha** para o formulário ao abrir.
Usa só se quiseres uma página dedicada que não mostra mais nada.

```html
<meta http-equiv="refresh"
      content="0; url=https://manuelfariasousa-dmfs.github.io/Github-Manuelfariasousa-DMFS/sugestoes.html">
<p>A reencaminhar para a caixa de sugestões…
   <a href="https://manuelfariasousa-dmfs.github.io/Github-Manuelfariasousa-DMFS/sugestoes.html">Clica aqui se não fores reencaminhado.</a>
</p>
```

---

## Qual escolher?

| Quero… | Opção |
|--------|-------|
| Um botão bonito | **1** |
| Só um link no texto | **2** |
| O formulário dentro da página | **3** |
| Saltar automaticamente para o formulário | **4** |

---

## Notas

- Em **WordPress**: usa o bloco **"HTML personalizado"** e cola o snippet.
- Em **Moodle**: no editor de texto, clica no botão **`</>`** e cola lá.
- Se o CMS "limpar" o código ao gravar, é porque filtra HTML — nesse caso
  usa a **Opção 2** (link simples), que quase nunca é bloqueada.
- Primeira sugestão: o serviço formsubmit pede **confirmação por email**
  (a `diretor.dmfs@gmail.com`). Confirma uma vez e fica a funcionar.
