# ON15-TET-S12-BD
Turma Online Todas em Tech - Back-end | Semana 12: Introdução ao Banco de Dados e Integração

##   🧑🏽‍💻 Apresentação

  Meu nome é Beatriz Ramerindo, sou Engenheira de Software, trabalho desenvolvimento back-end, nas stacks de Spring boot(Koltin) e Node com Express/NestJs (TypeScript/JavaScript). Sou carioca, mas estou atualmente resido em São Paulo, no meu tempo livre  amo assistir um pirata que estica e/ou jogar um lolzinho, no trabalho, gosto de codar ouvindo MPB e/ou fazer pair-programing. Sou apaixonada por compartilhar conhecimentos, principalmente me js, então se tiver uma curiosidade ou quiser tirar uma curiosidade, adoraria passar altas madrugadas conversando sobre.

###  👩🏽‍🏫 recadinho da professora 
    - Bebam água meninas
    - Qualquer pergunta é válida, principalmente aquela que a gente pensa que não faz sentido.
    - Pode deixar a camera aberta para a prof não se sentir sozinha
    
### 📑 Conteúdo da Aula

    - Introdução ao Banco de Dados(sql, nosql, mongo e orm)
    - Projeto sem mongo
    - Criar conta no MongoAtlas
    - Conhecendo o mongoCompass
    - Projeto com mongo
    - get com mongo
    - post com mongo
    - patch com mongo

## 📑 Arquitetura do Projeto
```
ReprogramaMusic  
├── api_com_mongo           
│    ├─ src                       
│    │  ├─ controllers            
│    │  │  └─ musicController.js  
│    │  ├─ database               
│    │  │  └─ moogoseConnect.js      
│    │  ├─ models                 
│    │  │  └─ musicModel.js      
│    │  ├─ routes                 
│    │  │  └─ musicRouter.js      
│    │  └─ app.js                 
│    ├─ package-lock.json         
│    ├─ package.json  
│    ├─ .gitignore            
│    └─ server.js
|
├── api_sem_mongo           
│    ├─ src                       
│    │  ├─ controllers            
│    │  │  └─ musicController.js      
│    │  ├─ models                 
│    │  │  └─ music.json      
│    │  ├─ routes                 
│    │  │  | index.js
│    |  |  └─musicRouter.js   
│    │  └─ app.js                 
│    ├─ package-lock.json         
│    ├─ package.json
│    ├─ .gitignore      
│    └─ server.js
|
└─README.md
```

## ⚙️ Dependencias do Projeto
    - Mongoose
    - Cors
    - Express
    - Nodemom

### 💻 Dependências de ambiente
- Node `~> 14`
- Mongodb > `~> 4`

## 🏦 História do banco de dados

A motivação de criar um sistema para armazenagem de dados surgiu devido ao alto custo de leitura/escrita de arquivos no HD. Os primeiros fundamentos de banco de dados relacionais surgiram entre as décadas de 1960 a 1970 pela IBM. Na  década de 80, a Oracle, com a permissão da IBM, foi a primeira empresa a desenvolver o banco utilizando o padrão SQL para consulta/escrita como é conhecido hoje. Após a explosão da web, também conhecida como web 2.0, foi necessário uma alternativa ao SQL(relacional), assim, a partir de 1998, foi criado o conceito de banco nosql( não relacional )

####  As diferenças De SQL(relacional) vs NOSQL(não relacional)

No resumo, um banco de dados SQL, é aquele que possui tabelas e que podem ter relação entre si. Para relacionar uma tabela com uma ou mais  é necessário uma chave, podendo ser primária ou estrangeira. Um banco NOSQL é aquele que possui uma estrutura de chave/valor, sem relação entre si.

#### Banco de dados Relacionais

No banco de dados relacional, os dados são armazenados em tabelas, onde cada linha representa um registro que é um dado salvo  e cada coluna representa um campo.
Como os dados são armazenados em uma tabela, é necessário um relacionamento para identificar quais campos pertencem a quais linhas. Essa referência é chamada de chave primária, também podemos usar outras chaves como a estrangeira.


Exemplo de consulta em SQL com MySQL:

```sql
    $ SELECT from musicas
    WHERE artista = "ludmila"
```

 - Os mais conhecidos do mercado atualmente são o MySQL, PostgreSQL e o Oracle.

#### Banco de dados Não Relacionais

No banco de dados não-relacional, os dados são estruturados com um par de chaves/valor. Caso seja necessário fazer uma relação, utilizamos  um id, que nesse caso é chamado de ObjectId, que é um identificador único para cada documento ( como se fosse um cpf). Uma vantagem do banco de dados NOSQL sobre o SQL, é que ele nos permite salvar qualquer tipo de dado e em qualquer ordem, isso é muito útil quando, por exemplo, precisamos salvar um array.


Exemplo de consulta em NOSQL com Mongo

```javascript
    $ db.musicas.find({ artista: "ludmila"})
```

- Os mais conhecidos do mercado atualmente são o MongoDB, Redis e o Firebase.

## 🏦 Introdução ao Mongo
Mongodb é um banco de dados NOSQL (não relacional) que surgiu em 2009 e foi desenvolvido em C + +. Ele utiliza BJSON que é bem similar com o JSON, sua linguagem de consulta/escrita é javascript, logo, por ser uma  linguagem comum ( eu amo o js ),  a sua curva de aprendizagem é pequena  para quem vem da web.

  alguns comandos com mongo

```javascript
     $ show databases;
     $ show collections;
     $ db.createCollection("alunas");
     $ db.nome_da_colecao.insert({nome: "beatriz", idade: "25"});
     $ db.nome_da_colecao.drop();
```

mais sobre: [mogodb comandos](https://www.tutorialspoint.com/mongodb/index.htm)

###  Database
Acho que já ouvimos a famosa expressão 'quebrei a base de prod' então, nossa database( base de dados ) é constituída por collections, que possui document,  geralmente num projeto, a gente possui diferentes tipos de base, para diferentes tipos de ambientes, como por exemplo: Produção, Homologação, Desenvolvimento, Testes, etc.

exemplo: criando um banco de dados

```javascript
    $ mongo
    $ use musicas;
    $ db.musicas.find();
```

### Collection e Document
Nossa `collection` é uma coleção(lista) de `document`, similar a  array, onde armazenamos, por exemplo, as nossas músicas. Nesse exemplo, uma playlist seria a `collection`, enquanto cada música seria um `document`, contendo as informações daquela música.

exmplo:

```json
[
    {   
        "_id": "ObjectId('5c8f8f8f8f8f8f8f8f8f8f8f')",
        "nome": "Duas doses de Saudade",
        "artista": "ludmila",
        "genero": "pop",
        "ano": "2016"
    },
    {   
        "_id": "ObjectId('4fsd44ffassasdasd234f56f')",
        "nome": "Amor de Que",
        "artista": "Pablo Vittar",
        "genero": "pop",
        "ano": "2016"
    }
]

```

## ⚙️ Introdução ao ORM
Um ORM é uma `técnica de desenvolvimento para nós devas`, conseguimos manipular de forma simples o nosso banco, sem ele precisamos de um especialista(DBA). Nos permite fazer como por exemplo `migrations` ( versionamento de base ) de forma simples.

### Introdução ao ORM Mongoose
O ORM Mongoose `não é o banco`, é uma ferramenta que como mencionado acima, facilita o nosso dia-a-dia enquanto devas, ele possui um conjunto recursos / funções que nos auxilia no desenvolvimento.

### `{}` Schema

Nosso mongoose utiliza a `Schema` para pôr ordem na ' bagunça ', afinal como podemos salvar qualquer coisa, de qualquer jeito, seria uma loucura não?  Para isso precisamos de um schema( espelho ) de como será salvo nosso `document`.


exemplo de schema:

```javascript
const mongoose = require('mongoose');
const MusicaSchema = monogoose.Schema({
    nome: String,
    artista: String,
    album: String,
    ano: Number,
    genero: String,
    duracao: Number,
    link: String,
    capa: String
});

```

### `[]` Model
Nossa `Model` ( modelo ) é a nossa representação da Collection ( coleção ), nele assim como no Array, possuímos `métodos` ( funções ) que nos permite realizar as operações do CRUD: 

| OPERAÇÃO| DESCRIÇÃO | HTTP |
| --- | --- | --- |
| C | criar/gerar | POST |
| R | ler/obter |  GET | 
| U | atualizar/substiuir | PUT/PATCH |
| D | remover/deletar | DELETE |


Exemplo de como criar uma model

```javascript
const MusicaModel = mongoose.model('musica', MusicaSchema);
```
Obs: Não é necessário salvar como músicas, pois o ORM cria no plural por nós, que massa né 💅

### ObjectId( )
O ObjectID é um identificador único para cada documento, ele é gerado automaticamente, podemos pensar nele como um CPF, único por dado, é por ele que consegue identificar um `Document` realizar as operações do CRUD.

```javascript
    const musicId = new moogose.Types.ObjectId();
```

## 🧑🏽‍💻 Classes | OOP (orientação a objetos) Conceitos básicos
Uma breve introdução sobre classes e objetos, para que possamos entender melhor o  nosso ORM.

###  uso da palavra reservada `new`
Quando possuímos uma classe, podemos utilizar a palavra reservada `new`  para instanciar um objeto, ou seja, construir um novo documento a partir da classe( nossa `Schema` ),  afinal, não queremos que a música da Anitta tenha altere as informações da música da Ludmila né? 🤔

```javascript
const musica = new MusicaModel({
    nome: 'Cat',
    artista: 'Gatinho',
    album: 'Cat Aleatorio',
    ano: '2019',
    genero: 'MPB',
    duracao: '3:00',
    link: 'https://www.youtube.com/watch?v=QH2-TGUlwu4',
    capa: 'https://i.ytimg.com/vi/QH2-TGUlwu4/maxresdefault.jpg'
});

```


### Métodos
Como mencionamos em aulas passadas, assim como o objeto, as classes possuiem métodos, que são funções que nos auxiliam a realizar **ações** como por exemplo: salvar um música, ou tocar uma música, no nosso dia-a-dia usamos o console`.log`, *.log("hello word")* é um método que nos permite imprimir no terminal uma mensagem de texto.

#### Métodos relação com a nossa API

| OPERAÇÃO | MONGODB | MOOGOSE | DESCRIÇÃO | HttpCode
| ---------- | -------------- | ---------------- | ----------------- | ---- |
| **C**REATE | **db**.insertOne() | new **MusicModel**() | cria um documento | 201 |
| **R**EAD | **db**.find() |  **MusicModel**.find() | ler um documento | 200 |
| **U**PDATE | **db**.updateOne() | **MusicModel**.updateOne() | atualiza um documento | 200 |
| **D**ELETE | **db**.deleteOne() | **MusicModel**.deleteOne() | deleta um documento | 200 ou 204


### Constructor
Nosso `constructor` é responsável por inicializar a nossa classe, ele recebe os parametros para criar construir a instancia da classe, como por exemplo, nossa música, é assim que nossa Schema gera a música no formato que o banco espera, no caso do mongo, um BJSON.

### Tipagem - Tipos primários
Na programação, existem tipos primários, que são responsáveis por definir o tipo de informação ( dado ) que estamos trabalhando, por exemplo um número de celular `Number`, ou um email que é texto `String`, ou até mesmo se é verdadeiro(true) ou falso(false) que é um `Boolean`, além disso, temos o `Date` que representa uma data. 

 - String -> representa *texto* -> `""`
 - Number -> representa *número*  `0`
 - Boolean -> representa `true` ou `false`
 - Date -> representa uma data, por exemplo, 1970-01-13 -> `Date`

```typescript
    class Musica {
        nome: String,
        artista: String,
        album: String,
        ano: Date,
        duracao: Number,
        curtidas: Number,
        comentarios: String,
        disponivel: Boolean,
    };
```

## 📖 Referências
- https://www.gartner.com/en/information-technology/glossary/object-data-model
- https://medium.com/tkssharma/node-js-with-mongoose-odm-9697c09665df
- https://developer.mozilla.org/pt-BR/docs/Learn/Server-side/Express_Nodejs/mongoose
- https://docs.mongodb.com/
- https://docs.mongodb.com/manual/crud/
- https://docs.atlas.mongodb.com/tutorial/create-new-cluster/
- https://studio3t.com/academy/topic/mongodb-vs-sql-concepts/
- https://dzone.com/articles/sql-vs-nosql
- https://mongoosejs.com/docs/index.html

### 🎥 Videos de apoio

- [Resumo Mongodb - Codigo Fonte TV](https://www.youtube.com/watch?v=4dTI1mVLX3I)
- [nodeJs Express Mongo - Api rest full Turitorial](https://www.youtube.com/watch?v=K5QaTfE5ylk)
- [O que é banco de dados? - Curso em Video](https://www.youtube.com/watch?v=Ofktsne-utM)

##  🎓 Combinado da semana
 - [PARA O LAR](./para_o_lar//instru%C3%A7%C3%B5es.md) < clique aqui

## 👋🏾 Minhas redes sociais
 - [LINKEDIN](https://www.linkedin.com/in/beatriz-ramerindo/)
 - [GITHUB](https://github.com/isjanebia)
 - [INSTAGRAN](https://www.instagram.com/isjanebea/)
 - [site] [beatriz.ramerindo.com.br](beatriz.ramerindo.com.br)
 - [email] bea@ramerindo.com.br