
# Instruções para Inserir um Usuário no OJS e Atribuir ao Grupo de Administradores

## Passo 1: Inserir um Novo Usuário

Para inserir um novo usuário no Open Journal Systems (OJS), execute o seguinte comando SQL:

```sql
INSERT INTO `users` (`username`, `password`, `email`)
VALUES ('example', MD5(CONCAT('example', 'PasswordExample')), 'example@email');
```

Substitua `'example'`, `'PasswordExample'` e `'example@email'` pelos valores apropriados para o novo usuário.

## Passo 2: Identificar o user_id do Usuário

Para identificar o `user_id` do usuário que acabou de ser criado, execute a seguinte consulta:

```sql
SELECT user_id FROM users WHERE username = 'example';
```

Substitua `'example'` pelo nome de usuário inserido no Passo 1.

## Passo 3: Verificar o ID do Grupo de Usuários dos Administradores

Para verificar qual é o ID do grupo de usuários do seu grupo de administradores, execute a seguinte consulta:

```sql
SELECT user_group_id FROM user_groups WHERE context_id=0 AND role_id=1;
```

Esta consulta retorna o `user_group_id` do grupo de administradores.

## Passo 4: Adicionar o Usuário ao Grupo de Administradores

Para adicionar o novo usuário ao grupo de administradores, utilize o `user_id` obtido no Passo 2 e o `user_group_id` obtido no Passo 3 e execute o seguinte comando SQL:

```sql
INSERT INTO user_user_groups (user_id, user_group_id)
VALUES (<new_admin_user_id>, <admin_user_group_id>);
```

Substitua `<new_admin_user_id>` pelo `user_id` do novo usuário e `<admin_user_group_id>` pelo `user_group_id` do grupo de administradores.

---

**Nota:** Certifique-se de que os valores dos parâmetros sejam corretos e correspondam aos dados do seu sistema OJS.
