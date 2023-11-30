- Join: É uma cláusula que permite agrupar registros de duas ou mais tabelas em uma única consulta.

### Inner Join

- Se quiser fazer um inner join, basta escrever join que funciona da mesma maneira
- Sempre que utilizar `join`, deve ser passada uma condição instruída por `on`:
```sql
select * from empresas join filiais on empresa.id = filiais.empresa_id
```

- Também posso atribuir apelidos para minhas tabelas, para facilitar o código:
```sql
select * from empresas emp join filiais fil on emp.id = fil.empresa_id
```

### Left Join

```sql
select * from empresas emp left join filiais fil on emp.id = fil.empresa_id;
```

- Ele traz os registros independente da quantidade de registros que estão relacionados com a tabela da direita

### Right Join

```sql
select * from empresas emp right join filiais fil on emp.id = fil.empresa_id;
```
 
 - Ele traz os registros independente da quantidade de registros que estão relacionados com a tabela da esquerda

### Full Join

- Traz todas das duas tabelas relacionadas
