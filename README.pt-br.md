## Como criar um projeto React, React Native e Node.js
[![EN](https://img.shields.io/badge/English-gray)](README.md)

Este tutorial não é uma introdução detalhada sobre React, React Native e Node.js. O propósito é de juntar em um só lugar o passo-a-passo e os comandos necessários para criar um projeto, rápido e simplificado.

Sugiro ler as documentações de qualquer tecnologia que for utilizar. No começo pode parecer complicado, mas é só com a documentação que você realmente se aprodunda sobre o assunto.

#### Links que pode te ajudar a começar com o React e Node.js:
* [Cursos do Rocketseat](https://app.rocketseat.com.br/dashboard);
* [Documentação do React](https://reactjs.org/docs/getting-started.html).


### Conteúdo
1. [Web (front-end)](#web)
2. [Server (back-end)](#server)
3. [Mobile usando React Native](#mobile)
4. [Contribuição e Problemas](#contribution)
5. [License](#license)

### O que precisa para começar:
Primeiro, você precisa instalar essas ferramentas:
* [Node.js](https://nodejs.org/en/): instale o "Recommended for most users";
* [NPM](https://www.npmjs.com/get-npm): após instalar o Node.js, utilize um terminal de comando para instalar o NPM utilizando `npm install npm@latest -g`;
* [Yarn](https://yarnpkg.com/getting-started): com o NPM instalado, utilize o comando `npm install -g yarn`;
* [Expo](https://expo.io/learn): o expo é para fazer apenas a parte mobile. Utilize o comando `npm install expo-cli --global`.


## Web (front-end) <a name="web"></a>
Para criar o web app você precisa primeiro instalar o create-react-app. Use o seguinte comando no seu terminal de preferência:
```
npm install -g create-react-app
```

Acesse a pasta onde você deseja criar seu projeto e execute o seguinte comando (o nome do projeto é sem o `<>`):
```
create-react-app <nome-projeto>
```

Meu editor de código favorito é o Visual Studio Code, então para abrir de maneira rápida a pasta que eu quero acessar, eu entro nesta pasta pelo terminal e uso o comando `code .` para abrir.

![Exemplo de como abrir a pasta pelo terminal de comando](img/img-2.png)

A estrutura do projeto ficará assim:

![Exemplo de estrutura do projeto](img/img-1.png)

Geralmente, deleto alguns arquivos que não irei utilizar:
* `App.css`
* `App.test.js`
* `index.css`
* `logo.svg`

O arquivo `servicerWorker.js` é para trabalhar com projetos em PWA.


## Server (back-end) <a name="server"></a>
Entre na pasta em que deseja criar o server e execute o seguinte comando:

```
mkdir server
```

Entre na pasta `server` usando o comando `cd server` e execute o comando:

```
yarn init -y
```

Agora você pode abrir a pasta. Se estiver utilizando o Visual Studio Code, use o comando `code .` para abrir.

Para concluir a configuração do projeto, você precisa instalar o Typescript. Use o seguinte comando:

```
yarn add typescript -D
```

e 

```
yarn tsc --init
```

No arquivo `tsconfig.json`, mude o `"target": "es5"` para `"target": "es2017"`. Você precisa fazer isso porque é até a versão de 2017 que tem as funcionalidades que o Node.js reconhece. 

Use o seguinte [comando](https://www.npmjs.com/package/ts-node-dev) para executar o servidor e observar se tem alguma alteração no script. Isto automatiza o processo para conseguir fazer com que o Node entenda o Typescript:

```
yarn add ts-node-dev -D
```

O `-D` significa que será usado apenas em ambiente de desenvolvimento e não em produção.

Cole o seguinte json no arquivo packge.json:
```json
"scripts": {
    "start": "ts-node-dev --transpile-only --ignore-watch node_modules --respawn src/server.ts",
    "knex:migrate": "knex --knexfile knexfile.ts migrate:latest",
    "knex:migrate:rollback": "knex --knexfile knexfile.ts migrate:rollback"
  },
```

* `--transpile-only`: converte o typescript para javascript. Isso acelera o processo de execução da aplicação; 
* `--ignore-watch`: faz com que esse tipo de conversão não ocorra dentro da pasta `node_modules`;
* `--respawn`: a aplicação recarrega toda vez que tiver alguma alteração e o código for salvo.

Agora, iremos intalar o [Express](https://expressjs.com/), que é um micro framework que traz alguma funcinalidades prontas pro Node.js:
```
yarn add express
```

O Express irá pedir pra você instalar o @types/express pra que seja possível interpretar o Typescript:

```
yarn add @types/express -D
```

### Criando os arquivos necessários para um back-end
Crie uma pasta `src`, onde irá ficar todo o código da aplicação. 
Dentro de `src`, crie as seguintes pastas e arquivos: 
* Pasta `controllers`;
* Pasta `database`;
* Arquivo `routes.js`.

Em `routes.js` é onde ficará as rotas da API. Terá esse formato:
```
import express from 'express';

import UserController from './controllers/UserController';

const routes = express.Router();

const userController = new UserController();
routes.post('/create', userController.create);

export default routes;
```

Na pasta `controllers` crie um arquivo com o nome da sua controller. Aqui vou colocar de `UserController.ts`. A controller ficará com esse formato:
```
import { Request, Response } from 'express';

import db from '../database/connection';

export default class UserController {
    async create(request: Request, response: Response) {
    }
}
```

O arquivo `server.js` deverá ficar assim:
```
import express from 'express';
import routes from './routes';

const app = express();

app.use(express.json());
app.use(routes);

app.listen(3333);
```

### Configurando o banco de dados
Executar comando `yarn add knex sqlite3`.
O `knex` é um query builder. Ele basicamente permite que voce esreva as querys para o SQL em JavaScript.

Crie uma pasta chamada `database` e, dentro dela, crie outra pasta chamada `migrations` e um arquivo chamado `connection.ts`.
O `connection.ts` ficará assim:
```
import knex from 'knex';
import path from 'path';

const db = knex({
    client: 'sqlite3',
    connection: {
        filename: path.resolve(__dirname, 'database.sqlite')
    },
    useNullAsDefault: true
});

export default db;
```

A pasta migration é onde ficará os arquivos de criação das tabelas do banco. Como exemplo, crie um arquivo chamado `00_create_users.ts` e terá essa estrutura:
```
import Knex from 'knex';

// Knex Documentation: http://knexjs.org/

export async function up(knex: Knex) {
    return knex.schema.createTable('users', table => {
        table.string('id').notNullable;
        table.integer('name').notNullable();
    });
};

export async function down(knex: Knex) {
    return knex.schema.dropTable('users');
};
```

Execute também o `yarn add cors` para permitir que aplicaçoes em endereços diferentes acesse a api.
Depois, utilize o `yarn add axios` para facilitar o consumo de apis externas.


## 📱 Mobile using React Native <a name="mobile"></a>
[Parte mobile incompleto]
Utilize um dos seguintes comandos para criar o projeto mobile:

```
expo init mobile
```

ou 

```
expo init mobile --template "blank"
```


## 🦾 Contribution or 🐞 Issues <a name="contribution"></a>
Escrevi este pequeno tutorial para ajudar na jornada dos aventureiros de React e Node.js iniciantes. Se você tem alguma sugestão ou melhoria, sinta-se livre para abrir uma Issue ou entrar em contato comigo! Vou ficar muito feliz em receber seu pull request. 🥰


## 📃 License <a name="license"></a>
Escrito com 💙 por [Luiza R. Marinho](https://github.com/luizous).

Este tutorial está sob licença [MIT](LICENSE).
