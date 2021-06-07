<h1 align="center">
  Redis I: Armazenando chaves e valores
</h1>

<p align="center">Exercícios do curso de Redis I.</a>
</p>

<p align="center">
  
  <img alt="GitHub language count" src="https://img.shields.io/github/languages/count/dpalmas/redis1?color=0000FF">

  <img alt="License" src="https://img.shields.io/github/license/dpalmas/redis1?color=0000FF&logo=MIT">
  
  <a href="https://github.com/dpalmas/redis1/commits/master">
    <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/dpalmas/redis1?color=0000FF">
  </a>
</p>

### Os problemas que o redis resolve
**1° O que é Redis? :pencil:**

Redis é um sistema que possibilita armazenar um conjunto de chave e valores e através desses retornar um único valor de 
modo que a busca seja extremamente rápida, sem a necessidade de utilizar um banco de dados com sql e fazer pesquisas complexas.

### Atualizando os valores
**2° Atualize o valor da chave "total_de_respostas" para 1446015. Depois recupere o valor para confirmar que houve a atualização. Forneça os comandos necessários. :pencil:**

```
SET "total_de_respostas" 1446015
GET "total_de_respostas"
```

### Removendo valores
**3° Defina uma chave chamada "ultimo_usuario_que_se_logou" junto com o valor "guilherme silveira" para a chave. Remova o conjunto de chave e valor utilizando o comando DEL. Verifique se chave e valor foram realmente removidos utilizando o comando GET que deve devolver (nil). :pencil:**

```
SET "ultimo_usuario_que_se_logou" "guilherme silveira"
GET "ultimo_usuario_que_se_logou"
DEL "ultimo_usuario_que_se_logou"
GET "ultimo_usuario_que_se_logou"
```
### Importância de definir um padrão no nome das chaves
**4° Qual a importância de definir um padrão para o nome das nossas chaves? :pencil:**

A importância de definir um padrão no nomes das nossas chaves é a facilitação no momento em que estivermos fazendo buscas.

### Padrão
**5° Qual das alternativas a seguir não é boa para uma escolha de padrão de chaves. :pencil:**

- [ ] id_do_usuario:categoria_em_portugues

- [ ] id_do_usuario:categoria_em_ingles

- [ ] data_em_formato_dd_mm_yyyy

- [ ] categoria_em_portugues:id_do_usuario

:white_check_mark: categoria_em_qualquer_lingua:id_do_usuario

### Os coringas
**6° No seu ponto de vista, qual a grande vantagem de usar caracteres coringa (?) e os colchetes ao buscar chaves?. :pencil:**

Uma das grandes vantagens é entender quais tipos de valores foram armazenados em nosso banco de dados Redis. 

### Utilizando o Redis para armazenar a sessão de um usuário
**7° No seu ponto de vista, qual a grande vantagem de usar caracteres coringa (?) e os colchetes ao buscar chaves?. :pencil:**

A primeira vantagem é que as informações não precisam ser compartilhadas entre os próprios servidores, mas sim no banco de dados, evitando a replicação da informação nos servidores web.

### GET e SET
**8° Qual o problema de executar um GET e depois um SET para aumentar ou diminuir em 1 o valor de uma chave? :pencil:**

Por padrão o banco Redis não envolve duas chamadas em um conceito de transição, e cada uma delas é executada de maneira atômica por si só, mas não em conjunto. Por exemplo um GET que retorna 40, e um SET que vai alterar o valor para 500, podem ter sido feitos 100, 1000, 10000 atualizações neste valor.

### Utilização do comando SETBIT
**9° Para que serve o comando SETBIT e onde voce usaria ele no mundo real? :pencil:**

O comando SETBIT permite que seja representada uma sequência de valores binários, ou bitmaps. Um bitmap funciona como um array que armazena zeros e uns associados a um offset.
