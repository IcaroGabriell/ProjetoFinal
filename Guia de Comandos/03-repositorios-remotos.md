# Repositórios remotos e colaboração

O GitHub guarda uma cópia do repositório na nuvem. O Git conversa com ela por meio de um **remoto**, normalmente chamado `origin`.

## Conectando ao GitHub

```bash
git remote add origin git@github.com:usuario/repo.git
git remote -v                       # confere os remotos
git remote set-url origin <nova-url> # troca a URL
git push -u origin main             # primeiro envio, associando a branch
```

Depois do `-u`, basta usar `git push` e `git pull`.

Autenticação por SSH: gere uma chave com `ssh-keygen -t ed25519 -C "seu-email@exemplo.com"`, cadastre a chave pública em **Settings → SSH and GPG keys** e teste com `ssh -T git@github.com`.

## Fetch, pull e push

| Comando     | O que faz                                                          |
| ----------- | ------------------------------------------------------------------ |
| `git fetch` | baixa as novidades do remoto sem alterar seus arquivos             |
| `git pull`  | `fetch` seguido de `merge`: baixa e já integra                     |
| `git push`  | envia seus commits ao remoto                                       |

O `fetch` atualiza branches como `origin/main`, que mostram onde o remoto estava na última consulta. Para ver o que falta antes de integrar:

```bash
git fetch origin
git log main..origin/main --oneline
```

## Erros comuns

- **`push` rejeitado com `fetch first`:** o remoto tem commits que você não tem, geralmente um README criado junto com o repositório. Resolva com `git pull origin main --allow-unrelated-histories` e envie de novo.
- **`'remote' não é reconhecido`:** faltou o `git` no começo do comando.
- **`Permission denied (publickey)`:** a chave SSH não está cadastrada no GitHub.
- **`Too many arguments` no `git clone`:** caminho com espaços sem aspas.

## Pull Requests

Um Pull Request (PR) pede a integração de uma branch à `main` com revisão e histórico de discussão.

```bash
git switch -c feature/nome
# ... commits ...
git push -u origin feature/nome
```

No GitHub, clique em **Compare & pull request**, descreva a mudança e faça o merge pelo botão **Merge pull request**. Depois, atualize a cópia local:

```bash
git switch main
git pull
```

## Issues

Issues registram tarefas, bugs e ideias. Para fechar uma Issue automaticamente quando o PR for integrado, use `Closes #N` na descrição do PR ou na mensagem do commit:

```bash
git commit -m "docs: adiciona guia de remotos" -m "Closes #1"
```

## GitHub Pages

O Pages publica arquivos estáticos (HTML, CSS e JavaScript) direto de um repositório. Em **Settings → Pages**, escolha **Deploy from a branch**, **main** e **/ (root)**. O `index.html` precisa estar na raiz do projeto.
