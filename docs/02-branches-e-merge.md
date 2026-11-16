# Branches e merge

Uma branch é uma linha de desenvolvimento independente. Permite criar e testar mudanças sem mexer na `main`.

## Trabalhando com branches

```bash
git branch                    # lista as branches locais
git branch -a                 # lista locais e remotas
git switch -c feature/nome    # cria a branch e já troca para ela
git switch main               # volta para a main
```

## Unindo branches (merge)

```bash
git switch main
git merge feature/nome
```

Há dois resultados possíveis:

- **Fast-forward:** a `main` não andou desde que a branch foi criada, então o Git só move o ponteiro e nenhum commit de merge é criado.
- **Merge commit:** as duas linhas avançaram e o Git cria um commit que une as duas. Para forçar esse commit mesmo quando seria fast-forward, use `git merge --no-ff feature/nome`.

## Conflitos

Quando duas branches alteram a mesma linha do mesmo arquivo, o Git não decide sozinho e avisa `CONFLICT (content)`. O arquivo fica com marcações:

```text
<<<<<<< HEAD
conteúdo da branch atual
=======
conteúdo da branch que está sendo unida
>>>>>>> feature/nome
```

Para resolver:

1. Abra o arquivo e escolha o que manter, ou combine os dois trechos.
2. Apague as três linhas de marcação (`<<<<<<<`, `=======`, `>>>>>>>`).
3. Conclua o merge:

```bash
git add arquivo.txt
git commit -m "merge: resolve conflito em arquivo.txt"
```

Para desistir no meio do processo: `git merge --abort`.

## Rebase

O `rebase` reaplica os commits da sua branch sobre outra base, deixando o histórico linear:

```bash
git switch feature/nome
git rebase main
```

O `rebase -i` permite renomear, reordenar ou juntar commits:

```bash
git rebase -i HEAD~3
```

Regra de ouro: não faça rebase de commits que outras pessoas já baixaram, porque ele reescreve o histórico.

## Apagar branches

```bash
git branch -d feature/nome            # apaga a local (só se já foi integrada)
git branch -D feature/nome            # apaga a local mesmo sem integração
git push origin --delete feature/nome # apaga a remota
```

## Visualizar o resultado

```bash
git log --graph --oneline --all --decorate
```
