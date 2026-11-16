# Guia de Git e GitHub pela linha de comando

Projeto integrador final do curso de Git e GitHub do CEFET-MG. Reúne um guia de comandos organizado por tema, construído usando o mesmo fluxo de trabalho que descreve: branches, Pull Requests, Issues e commits semânticos.

**Site publicado:** https://icarogabriell.github.io/ProjetoFinal

## Objetivo

Consolidar o aprendizado do curso em um material de consulta e demonstrar, no próprio histórico do repositório, o uso de um fluxo de trabalho colaborativo com Git e GitHub.

## Conteúdo

| Documento | Assunto |
| --------- | ------- |
| [Comandos básicos](docs/01-comandos-basicos.md) | configuração, ciclo de commits, histórico, desfazer alterações |
| [Branches e merge](docs/02-branches-e-merge.md) | branches, merge, conflitos, rebase |
| [Repositórios remotos](docs/03-repositorios-remotos.md) | remotos, fetch/pull/push, Pull Requests, Issues, GitHub Pages |
| [Reflexão](reflexao.md) | análise crítica do aprendizado no curso |

## Estrutura do repositório

```text
.
├── README.md
├── reflexao.md
├── index.html          # página do site publicado
├── css/
│   └── style.css
├── docs/
│   ├── 01-comandos-basicos.md
│   ├── 02-branches-e-merge.md
│   └── 03-repositorios-remotos.md
└── .gitignore
```

## Fluxo de trabalho

- O conteúdo principal entra na `main` por Pull Request, depois de revisado na própria branch.
- Cada frente de trabalho tem uma branch própria: `feature/guia-comandos`, `feature/site-pages` e `feature/reflexao`.
- Cada branch está ligada a uma Issue e a fecha com `Closes #N`.
- Os commits seguem o [Conventional Commits](https://www.conventionalcommits.org/pt-br/): `tipo(escopo): descrição no imperativo`.

Para ver o histórico completo:

```bash
git log --graph --oneline --all --decorate
```

## Como visualizar localmente

```bash
git clone git@github.com:IcaroGabriell/ProjetoFinal.git
cd ProjetoFinal
```

Depois, abra o `index.html` no navegador.

## Autor

**Ícaro Gabriel**, estudante de Engenharia da Computação na UEMG Divinópolis.
GitHub: [@IcaroGabriell](https://github.com/IcaroGabriell)