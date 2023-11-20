- Criando banco de dados:
```sql
create database aula_modelagem;
```

- *Sistema de Livrarias*
- Criando tabela de editoras
```sql
create table editoras (
	id serial primary key,
	nome text not null,
	cnpj text unique,
	data_cadastro timestamp default now()
);
```

- serial (Auto incremento),
- primary key (Chave primaria)
- text (campo de texto variavel)
- not null (Não pode ser vazio)
- unique (Campo único, que não pode ter dois donos)
- timestap (Data e hora)
- default now(): Data atual do sistema como padrão
<br>
- Inserindo registro em editoras:
```sql
insert into editoras (nome, cnpj) values ('Editora Teste', '00112233445521');
```

### Relacionamento entre tabelas

- Criando a tabela de livros

```sql
create table livros (
	isbn integer primary key,
	editora_id integer,
	foreign key (editora_id) references editoras(id),
	titulo text not null,
	data_publicacao date not null
);
```

- foreign key: Identifica a chave primaria de outra tabela, para agir como relacionamento, nesse caso, o campo id. 

```sql
insert into livros 
(isbn, editora_id, titulo, data_publicacao) values 
(12345, 1, 'Backend com Node', '2015-12-01');
```

- Criando tabela endereços
```sql
create table enderecos(
  id serial primary key,
  editora_id integer references editoras(id),
  cep text not null,
  rua text,
  bairro text,
  cidade text,
  estado char(2),
  pais text
  );
```
- Inserindo valores obrigatórios

```sql
insert into enderecos
(editora_id, cep)
values
(1, '41000-000');
```

### Muitos Relacionamentos

```sql
create table categorias (
	id serial primary key,
  nome text not null
);

create table livro_categoria (
	livro_isbn integer references livros(isbn),
  categoria_id integer references categorias(id)
);
```

- Criando categorias:
```sql
insert into categorias (nome) values ('Tecnologia'), ('Programação'), ('Node');
```

- Criando novo livro:
```sql
insert into livros (isbn, editora_id, titulo, data_publicacao)
values
(121234, 1, 'Node', '2022-12-03');
```

- Criando as relações:
```sql
insert into livro_categoria (livro_isbn, categoria_id)
values
(12345, 1),
(12345, 2),
(12345, 3),
(121234, 2);
```