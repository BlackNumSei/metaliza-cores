# Metaliza · Cadastro de Cores

Sistema simples para cadastrar as fórmulas de cores das peças cromadas, no lugar do caderno.

Site: https://blacknumsei.github.io/metaliza-cores/

## O que faz

- **Login:** um acesso único da empresa (e-mail + senha). A senha pode ser trocada em **Ajustes**.
- **Cores:** cadastrar, buscar, editar, duplicar, excluir e imprimir fórmulas por referência.
- **Recalcular:** informe quanto vai usar de um ingrediente (ex.: 5 L de verniz) e o sistema recalcula o restante.
- **Ingredientes:** vernizes, bases, pigmentos, solventes etc. Tudo pode ser adicionado, editado ou removido.
- **Ajustes:** categorias e unidades (g, kg, ml, L, gotas…) totalmente editáveis, a troca de senha e a cópia de segurança.

## Onde ficam os dados

No Supabase, projeto **metaliza-cores** (região São Paulo). As tabelas são `categorias`, `unidades`, `ingredientes` e `cores` (os ingredientes de cada fórmula ficam na coluna `itens`).

## Segurança

- A chave que aparece no `index.html` é a chave **pública** do Supabase, feita para ficar no site.
- Todas as tabelas têm RLS: só quem estiver logado **e** tiver o e-mail na lista `privado.acesso` consegue ler ou alterar os dados.
- O cadastro de novos usuários deve ficar **desligado** no Supabase (Authentication → Sign In / Providers → "Allow new users to sign up").

Para liberar outro e-mail (no SQL Editor do Supabase):

```sql
insert into privado.acesso (email) values ('outro@email.com');
```
