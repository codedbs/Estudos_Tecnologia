# Modelagem de dados

- Como estruturar tabelas:
	- Definir as entidades do sistema
	- Criar um identificador único da entidade
	- Características da entidade
	- Se alguma característica for uma lista de dados, crie uma nova entidade.

### Tipos de dados numéricos

- Smallint: 2 Bytes, -32768 a +32767 de Alcance
- integer: 4 Bytes, Maior alcance em relação a Smallint (Mais utilizado)
- biginteger: 8 Bytes e maior alcance em geral.

### Tipos Numéricos
- Tipos númerico de precisão arbitrária:
<br>
- numeric
- decimal

Exemplo:
```sql
decimal(7, 4) -- 7 de tamanho e 4 de escala (Tamanho do numero ou numero de digitos, e quantidade de numeros após a virgula)
```

- real
- double precision

### Tipos Seriais

- smallserials: 2 bytes
- serial: 4 bytes
- bigserial: 8 bytes

- Não aceitam valores negativos ou zero
- Auto incremento
- Não nulo

### Tipos de dados para caracteres

- varchar(n): Comprimento variável com limite que eu defino
- char(n): Comprimento fixo, completando com espaços em branco o resto do campo que não for preenchido
- text: Comprimento variável sem limite

### Tipo Booleano

- boolean:
	- 1 byte
	- Possui tres valores: Verdadeiro, Falso ou Nulo
	- Verdadeiro: true, t, yes, on ou 1
	- Falso: false, f, no, off ou 0
	- Não há diferença entre maiúsculas ou minúsculas

### Tipos para Data e Hora

- timestamp: Data e hora sem fuso horário
- timestamptz: Data e Hora com fuso horário
- date: Data sem hora do dia
- time: Hora do dia sem data
- timetz: Hora do dia sem data + fuso

## Relacionamento entre tabelas

- 1 para muitos (1:N):
	- Uma linha de uma tabela se relaciona com zero ou mais linhas de outras tabelas. Geralmente indica pertencimento.
	- *Exemplos*:
	- Um país tem vários estados
	- Uma casa tem vários moradores
	- Um cliente fez várias compras

- Um para um (1:1)
	- Uma linha de uma tabela se relaciona com uma e apenas uma linha de outra tabelas e vice-versa.
	- *Exemplos:*
	- Uma pessoa tem um telefone para contato.
	- Uma empresa tem uma sede.

- Muitos para muitos (N:N)
	- Uma linha de uma tabela se relaciona com zero ou mais linhas de outras tabelas. Mas cada linha dessa outra tabela também se relaciona com zero ou mais da primeira tabela. Nesse relacionamento precisa existir uma tabela auxiliar para representar a relação.
	- *Exemplos*:
	- Produtos tem várias categorias
	- Pessoas são amigas de pessoas

- Auto relação
	- Uma tabela se relaciona com ela mesma
	- Funciona da mesma forma dos outros tipos de relacionamento
	- *Exemplo*
	- Um comentário tem comentários