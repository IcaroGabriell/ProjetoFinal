# Comandos básicos

O ciclo de trabalho do dia a dia no Git: criar ou clonar um repositório, ver o que mudou, registrar e consultar o histórico.

## Configuração inicial

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@exemplo.com"
git config --list
```

Esses dados aparecem em todos os commits. A configuração é feita uma única vez por computador.

## Criar ou clonar

```bash
git init                                  # transforma a pasta atual em repositório
git clone git@github.com:usuario/repo.git # baixa um repositório existente
```

Se o caminho de destino tiver espaços, use aspas:

```bash
git clone git@github.com:usuario/repo.git "C:\minha pasta\repo"
```

Não clone um repositório dentro de outro repositório Git.

## Ver o que mudou

```bash
git status            # estado dos arquivos (modificados, em staging, novos)
git diff              # alterações ainda não adicionadas ao staging
git diff --staged     # alterações já adicionadas, prontas para commit
```

## Registrar alterações

```bash
git add arquivo.txt   # adiciona um arquivo ao staging
git add .             # adiciona todas as alterações
git commit -m "tipo: descrição"
```

O Git trabalha em duas etapas: o `add` escolhe o que entra no próximo commit e o `commit` grava o registro.

## Consultar o histórico

```bash
git log                       # histórico completo
git log --oneline             # uma linha por commit
git log --graph --oneline --all --decorate   # gráfico de todas as branches
```

## Desfazer

```bash
git restore arquivo.txt            # descarta alterações não commitadas
git restore --staged arquivo.txt   # tira um arquivo do staging
git commit --amend -m "nova mensagem"   # reescreve o último commit
```

O `--amend` muda o hash do commit. Se ele já foi enviado ao GitHub, o próximo push precisará de `--force-with-lease`.

## Ignorar arquivos

Arquivos listados no `.gitignore` não são rastreados. Serve para logs, arquivos temporários e pastas de editor.

## Mensagens de commit

O projeto segue o padrão **Conventional Commits**: `tipo(escopo): descrição no imperativo`.

| Tipo       | Uso                                            |
| ---------- | ---------------------------------------------- |
| `feat`     | nova funcionalidade ou conteúdo                |
| `fix`      | correção de erro                               |
| `docs`     | documentação                                   |
| `style`    | formatação e estilo, sem mudar a lógica        |
| `refactor` | mudança de estrutura sem alterar comportamento |
| `chore`    | manutenção e organização                       |
