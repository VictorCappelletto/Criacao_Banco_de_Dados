#<h1 align="center"> Criação_Banco_de_Dados </h1>
![Logo_BD](https://user-images.githubusercontent.com/104593037/168647107-ca47fb4b-e0f5-4667-8eec-4e13c6537db0.png)

<p align="center">
<img src="http://img.shields.io/static/v1?label=STATUS&message=%20CONCLUIDO&color=GREEN&style=for-the-badge"/>
</p>

Projeto para criação do Banco de Dados, desde a etapa de elaboração da regra de negocio obtido através de entrevistas com os gestores das areas até a elaboração do modelo físico do BD

## Índice 

* [Descrição do Projeto](#descrição-do-projeto)
* [Regras_do_Negocio](#regras-do-negocio)
* [Modelo Logico](#modelo-logico)
* [Comandos DDL de Criação das Estraturas](#comandos-dll-de-criacao-das-estruturas)
* [Comandos DDL SEQUENCE e DROP](#comandos-dll-sequence-e-drop)
* [Tecnologias utilizadas](#tecnologias-utilizadas)
* [Pessoas Desenvolvedoras do Projeto](#pessoas-desenvolvedoras)
* [Conclusão](#conclusão)

<h4 align="center"> 
    :white_check_mark:  Projeto Concluído  :white_check_mark:
</h4>

## 🗒️DESCRIÇÃO DO PROJETO

Projeto para criação do Banco de Dados, desde a etapa de elaboração da regra de negocio obtido através de entrevistas com os gestores das areas até a elaboração do modelo físico do Banco de Dados. As entregas desse projeto serão:

- Arquivo *.PDF, contendo o modelo lógico de dados e que represente todas as regras de negócios descritas.
- Arquivo *.PDF, contendo o modelo físico (relacional) de dados e que represente todas as regras de negócios descritas.
- Arquivo *.SQL, contendo os comandos DDL de criação das estruturas de armazenamento.
- Comandos CREATE SEQUENCE e DROP SEQUENCE de seu projeto.



## 🖋️REGRAS DO NEGOCIO 

- Um produto pode ter nenhum ou vários vídeos associados, e cada vídeo somente pode exibido caso seu status esteja em “A” (ativo).
- O código de identificação do produto deve ser um número sequencial para ser utilizado como SEQUENCE e crescente de acordo com novos produtos que forem sendo cadastrados.
- A descrição normal do produto, sua descrição completa, e o preço unitário são obrigatórios. Já o código de barras padrão EAN13 ou correspondentes deve ser opcional.
- Uma categoria de produtos pode estar associada a nenhum ou a vários produtos, e um produto somente pode estar associado a uma categoria.
- O código da categoria deve ser um número sequencial para ser utilizado como SEQUENCE e crescente de acordo com novas categorias que forem cadastradas.
- A descrição da categoria, o status e a data de início devem ter conteúdos obrigatoriamente. Já a data de término deve ser opcional, determinando que a categoria está com status “A” (ativo) e operante.
- Existe a necessidade de se armazenar a data, hora, minutos e segundos da visualização do vídeo. Sendo assim, um vídeo pode ter nenhuma ou várias visualizações e uma visualização pertence a um único vídeo. Vídeos que estão inativos  não podem ser  visualizados.
- Se o usuário estiver conectado (logado como cliente) é necessário armazenar essa informação. Caso seja um usuário anônimo (não tem login na plataforma), não é necessário armazenar informação.
- A data e hora de visualização é informação obrigatória, bem como o código do produto visualizado.
- Cada vídeo deve ser classificado em categoria. A seguir temos alguns exemplos dessas categorias: instalação do produto, uso no cotidiano, comercial com personalidade, entre outros. Existem centenas de categorias, sendo assim, sugerimos fortemente uma entidade aqui.
- Somente o usuário logado (cliente) pode abrir nenhum ou vários chamados de dúvidas e sugestões, e cada chamado desses deve ser associado a um único cliente.
- Os chamados de dúvidas e sugestões deve conter uma chave única e que possa ser utilizada como SEQUENCE.
- Os chamados de dúvidas e sugestões deve conter uma data e hora de abertura do chamado e é uma informação obrigatória. Já a data e hora de atendimento do chamado deve ser opcional, ou seja, preenchida somente quando um funcionário da Melhores Compras atender.
- Todo chamado tem que ter o código do funcionário associado em algum momento, pois é a partir dele que sabemos quem está realizando o atendimento. Nesse nosso projeto, vamos assumir que o chamado deve ser associado somente a um funcionário e um funcionário pode atender nenhum ou vários chamados.
- Todo chamado tem um status que permite saber em qual situação ele se encontra. Os principais status são: “A” (aberto) e o primeiro status criado no início, “E” (em atendimento), “C” (cancelado)”, “F” (fechado com sucesso), “X” (fechado com insatisfação do cliente), conforme for evoluindo o atendimento. Sendo assim, esse status é informação obrigatória.
- Todo chamado deve o tempo total de atendimento, computado desde a abertura até à conclusão dele. A unidade de medida é horas, ou seja, em quantas horas o chamado foi concluído desde a sua abertura.
- Todo chamado dever ter um índice de satisfação, computado como um valor simples de 1 a 10, em que 1 refere-se ao cliente menos satisfeito e 10 ao cliente mais satisfeito. Esse índice de satisfação é opcional e informado pelo cliente ao final do atendimento.
- Todo chamado deve ser classificado em  dois tipos:"Tipo 1: Sugestão e  Tipo 2: Reclamação e é informação obrigatória."
- Todo chamado deve ser associado a um produto. Então, um produto pode possuir nenhum ou vários chamados e um chamado pertence a um único produto.
- Todo chamado deve ter um texto contendo no mínimo 10.000 caracteres e seu conteúdo é obrigatório. Nessa estrutura de armazenamento, essas preciosas informações que o cliente descrever serão analisadas posteriormente pelo funcionário.
- Todo chamado deve conter um texto de no mínimo 20.0000 caracteres e seu conteúdo dever ser opcional. Nessa estrutura de armazenamento, as informações de retorno do chamado serão informados pelo funcionário que atendeu ao chamado.
- As principais informações do funcionário que atendeu são: código do funcionário (PK), nome do funcionário, data de nascimento, telefone com DDD, e-mail, cargo e nome do departamento que trabalha. Todas essas informações são obrigatórias.
- As principais informações do cliente, que está logado e solicita abertura de chamado, são: código do cliente (PK), nome do cliente, data de nascimento, gênero de nascimento, telefone com DDD e e-mail. Todas essas informações são obrigatórias.
- Regra de negócio a ser definida pelo grupo. Crie uma regra de negócio adicional e única de seu grupo que necessite criar uma nova entidade (tabela no modelo físico), bem como no mínimo três atributos (sem contar a chave PK).

## :paperclip: MODELO LÓGICO
O modelo logico foi elaborado com o sofware #OracleDataModeler adotando os criterios de modelagem:
- MER: Modelo Entidade e Relacionamento
- Cardinalidade entre Entidades (Forte e Fraca)
- CONSTRANT: PRIMARY KEY (PK), FOREIGN KEY (FK), UNIQUE (UN) e CHECK (CK)
- Tipos de dados (NVARCHAR, DATE, NUMERIC, etc)

Com as analises entre as entidades e seus relacionamentos foi elaborado o seguinte modelo:

[Modelo_Logica_Atividade1.pdf](https://github.com/VictorCappelletto/victorcappelletto/files/8702572/Modelo_Logica_Atividade1.pdf)

<p align="center">  
  
![Imagem_Mod_Logic](https://user-images.githubusercontent.com/104593037/168660819-4ba2773a-6f60-42fa-af93-a5fd77845c40.png)  
  
</p>

## :floppy_disk: Comandos DDL de Criação das Estraturas
O modelo fisico foi elaborado com o sofware #OracleDeveloper utilizando linguagem SQL, no arquivo possui os seguintes comandos:

- Criação de Tabela (CREATE TABLE)
- Alteração de Tabela (ALTER TABLE)
- Adição de Constraint (ADD CONSTRAINT)
- Remoção de Tabela (DROP TABLE)
- Criação de Sequencia (SEQUENCE)

[Comando DDL.zip](https://github.com/VictorCappelletto/victorcappelletto/files/8702695/Comando.DDL.zip)

<p align="center">
  
![img_sql_bd](https://user-images.githubusercontent.com/104593037/168663555-4b261369-c80d-4bda-b652-7fc03937378f.png)
  
</p>

## :page_facing_up: Comandos DDL DROP e SEQUENCE

:closed_book: DROP 

O comando DROP tem como função excluir do banco de dados diversas funções, ou seja, para remover uma tabela em um banco de dados é necessario utilizar esse comando. Segue abaixo o modelo de utilização do comando DROP para remoção de uma tabela gerada no projeto:

`DROP TABLE T_SGV_CATEGORIA CASCADE CONSTRAINTS;`

é adicionado o complemento CASCADE CONSTRAINTS para excluir todas as constraints que estejam vinculadas a tabela removida


:notebook: SEQUENCE 

Uma sequência é um item de banco de dados, cuja função é gerar uma série de números inteiros. A sequência é normalmente utilizada para preencher uma coluna chave primária numérica, com valores numéricos inteiros.Com o uso da sequência,os números são gerados de forma automática pelo SQGB  (Sistema  Gerenciador  de  Banco  de  Dados).

📚MODELO DE CODIGO GERAL SQL PARA CRIAÇÃO DE UMA SEQUENCIA:

```CREATE SEQUENCE nome_sequencia
START WITH num_inicio
INCREMENT BY  num_incremento
{ MAXVALUE  num_maximo | NOMAXVALUE }
{ MINVALUE  num_minimo | NOMINVALUE }
{ CYCLE | NOCYCLE}
{ CACHE   num_cache | NOCACHE }
{ ORDER | NOORDER }
```

- nom_sequencia:nome da sequência.
- num_inicio:número inteiro usado para iniciar a sequência. O número inicial padrão é 1.
- num_incremento:número inteiro para incrementar a sequência. O número de incremento padrão é 1.
- num_maximo:Número  inteiro  máximo  da  sequência.  Deve  ser  maior  ou igual ao númeroinicial. Deve ser maior que o númeromínimo.
- NOMAXVALUE: Especifica  que  o  máximo  é  1027 para  uma  sequência crescente ou -1 para uma sequência decrescente. A opção NOMAXVALUE é padrão.
- num_minimo: Número  inteiro  mínimo  da  sequência.  Deve  ser  menor  ou igualao númeroinicial  da  sequência.  Deve  ser  menor  que    o númeromáximo da sequência.
- NOMINVALUE:Especifica que o mínimo é 1 para uma sequência crescente ou 10-26 para uma sequência decrescente. NOMINVALUE é o padrão
- CYCLE:Significa que a sequência gera números inteiros mesmo depois de atingir  seu  valor  máximo  ou  mínimo.  Quando  uma  sequência  crescente atinge seu valor máximo, o próximo valor gerado é o mínimo. Quando uma sequência decrescente atinge seu valor mínimo, o próximo valor gerado é o máximo.
- NOCYCLE: Significa que a sequência não pode gerar mais número inteiro algum após atingir seu valor máximo ou mínimo. NOCYCLE é o padrão.
- num_cache: é o número de valores inteiros a manter na memória. O número de valores inteiros padrão colocados na cache é 20. O número mínimo de valores inteiros que podem ser colocados no cache é 2. O número máximo  de valores inteiros que podem ser colocados no cache é determinado pela fórmula CEIL ( num_maximo –num_minimo) / ABS ( num_incremento ).
- NOCACHE: Significa semcache. Isso impede o banco de dados de alocar valores previamente para a sequência,  o que evita lacunas numéricas na sequência,  mas  reduz  o  desempenho.  As  lacunas  ocorrem  porque  os valores  alocados  no  cache  são  perdidos  quando  um  banco  de  dados  é fechado.Se for omitida CACHE/NOCACHE, o banco de dados colocará 20 números de sequência na CACHE, por padrão.
- ORDER:  Garante  que  os  números  inteiros  sejam  gerados  na  ordem  da solicitação.
- NOORDER: Não garante que os números inteiros sejam gerados na ordem de solicitação. NOORDER é o padrão.

✔️EXEMPLO DE CODIGO SQL PARA CRIAÇÃO E REMOÇÃO DE UMA SEQUENCIA NO PROJETO:

```CREATE SEQUENCE SQ_SGV_CATEGORIA
INCREMENT BY 1
START WITH 1
MAXVALUE 99999
NOCACHE
NOCYCLE;

SELECT SEQUENCE_NAME,
       INCREMENT_BY,
       MAX_VALUE,
       LAST_NUMBER
FROM   USER_SEQUENCES
WHERE  SEQUENCE_NAME='SQ_SGV_CATEGORIA
```

EXEMPLO DE CODIGO SQL PARA REMOÇÃO DE SEQUENCE TABELA T_SGV_CATEGORIA 

`DROP SEQUENCE SQ_SGV_CATEGORIA`

EXEMPLO DE CODIGO SQL PARA ADICIONAR VALOR UTILIZANDO .NEXTVAL 🔖

```
INSERT INTO T_SGV_CATEGORIA (cd_categ, nm_categ, ds_categ, dt_term_categ, dt_inicio_categ, cd_sta_categ, cd_prod)
        VALUES(SQ_SGV_CATEGORIA.nextval, /*VALORES DA CATEGORIA*/)
```

## :computer: Tecnologias utilizadas
        
 - `SQL`
 - `Oracle Developer`
 - `Oracle DataModeler`

## :space_invader: Pessoas Desenvolvedoras do Projeto

 | [<img src="https://avatars.githubusercontent.com/u/104593037?s=400&u=7d1315697c09704b873c4e2048aa5a276ad4e68a&v=4" width=115><br><sub>Victor Cappelletto</sub>](https://github.com/VictorCappelletto) | 
 | :---: | 

## :pushpin: Conclusão

Com essas etapas é possivel visualizar os processos para a elaboração do modelo lógico de um banco de dados que é gerado através da regra de negocio junto com a codificação que gera o modelo fisico do banco de dados. Quando o modelo fisico é gerado, torna possivel a locação dos dados, ou seja, realizar o input dos dados.

Espero ter contribuido!! =D
