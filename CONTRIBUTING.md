# Guia de Contribuição

Este guia define como a equipe Nata Dev contribui com o Livro de Receitas.

## Regra de governança

**Todo PR deve ter no mínimo 3 aprovações antes do merge na main.**

A `main` é protegida: não são aceitos commits diretos. Toda mudança entra por Pull Request.

## Issues

- Toda receita começa com uma Issue.
- Título: `[Receita] Nome da Receita - Categoria` (exemplo: `[Receita] Pudim de Leite - Sobremesas`).
- A Issue deve ser atribuída (Assignees) ao autor da receita.
- Descrição: o que será adicionado, com critérios de aceitação em checklist.

## Branches

Toda contribuição usa uma Feature Branch criada a partir da `main` atualizada.

Padrão: `feature/<categoria>-<nome-da-receita>`

Exemplo: `feature/sobremesas-pudim-de-leite`

```bash
git switch main
git pull
git switch -c feature/sobremesas-pudim-de-leite
```

## Commits

Usamos Conventional Commits, em português e no imperativo.

| Prefixo | Uso | Exemplo |
| :--- | :--- | :--- |
| `feat:` | Receita nova | `feat: adicionar receita de pudim de leite` |
| `docs:` | Documentação e menu | `docs: atualizar menu com link para pudim de leite` |
| `fix:` | Correção de erro | `fix: corrigir link quebrado no menu` |

Para cada receita, faça um commit com o arquivo da receita e outro com a atualização do `menu.md`.

## Padrão das receitas

Cada receita fica em `<categoria>/<nome-da-receita>.md`, com este formato:

```markdown
# Nome da Receita

## Ingredientes
- item

## Modo de Preparo
1. passo

---

[Voltar à Categoria](.) | [Voltar ao Menu Principal](../menu.md)
```

Depois de adicionar a receita, inclua o link dela na seção "Receitas" do `menu.md`.

## Pull Requests

1. Suba a branch: `git push -u origin feature/<categoria>-<nome-da-receita>`.
2. Abra o PR para a `main`.
3. Título no padrão dos commits (exemplo: `feat: adicionar receita de pudim de leite`).
4. Descrição clara da receita adicionada.
5. Inclua `Closes #N` para fechar a Issue automaticamente.
6. Peça a revisão (Reviewers) aos colegas da equipe.

## Code Review

- No mínimo 3 integrantes diferentes revisam o PR na aba **Files changed**.
- Conferir a sintaxe Markdown e testar todos os links.
- Aprovar formalmente com **Approve**. O autor não aprova o próprio PR.
- Se houver pedido de ajustes, o autor faz novos commits na mesma branch e usa **Re-request review**.

## Conflitos no menu.md

Se outro colega atualizar o `menu.md` antes de você:

1. `git switch <sua-branch>`
2. `git pull origin main`
3. Resolva o conflito mantendo as linhas dos dois lados.
4. Faça o commit de ajuste e `git push`.

## Merge e limpeza

Com as 3 aprovações, faça o merge na `main` e exclua a branch remota (**Delete branch**). Depois, na máquina: `git switch main`, `git pull` e `git branch -d <branch>`.