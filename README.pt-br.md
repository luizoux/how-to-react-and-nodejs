## Como criar um projeto React e React Native
🔠 [English](README.md)

Este tutorial não tem possui uma instrodução detalhada sobre React e React Native. O propósito é de incluir em um só lugar os passo-a-passo e comandos para criar um projeto, rápido e simplificado.

Sugiro ler as documentações de qualquer tecnologia que for utilizar. No começo pode parecer complicado, mas só com a documentação que realmente aprende sobre.

Links que pode te ajudar a começar com o React:
* [Start Cursos do Rocketseat](https://app.rocketseat.com.br/dashboard) e se atualizar sobre a stack lendo os artigos do [blog](https://blog.rocketseat.com.br/tag/reactjs/);
* [Documentação do React](https://reactjs.org/docs/getting-started.html).

### Conteúdo
1. [Web (front-end)](#web)
2. [Server (back-end)](#server)
3. [Mobile usando React Native](#mobile)
4. [Como rodar o projeto](#run)
5. [Contribuição e Bugs/Problemas](#contribution)

### O que precisa para começar:
Primeiro, você precisa instalar essas ferramentas:
* Node.js 
* NPM
* Yarn
* Expo


## Web (front-end) <a name="web"></a>
Para criar o web app você precisa primeiro instalar instalar o create-react-app. Use o seguinte comando no seu terminal de preferencia:
```
npm install -g create-react-app
```

Acesse a pasta onde você deseja criar seu projeto e execute o seguinte comando (o nome do projeto é sem o `<>`):
```
create-react-app <nome-projeto>
```

Meu editor de código favorito é o Visual Studio Code, então para abrir de maneira rápida a pasta que eu quero acessar, eu entro nela pelo terminal e uso o comando `code .` para abrir.
![image-20200826135405201](C:\Users\luiza\AppData\Roaming\Typora\typora-user-images\image-20200826135405201.png)

A estrutura do projeto ficará assim:
![image-20200826130558117](C:\Users\luiza\AppData\Roaming\Typora\typora-user-images\image-20200826130558117.png)

Geralmente, deleto alguns arquivos que não irei utilizar:
- App.css
- App.test.js
- index.css
- logo.svg

O arquivo `servicerWorker.js` é para trabalhar com projetos em PWA.


## Server (back-end) <a name="server"></a>
Entre na pasta em que deseja criar o server e execute o seguinte comando:
```mkdir server```

Entre na pasta `server` usando o comando `cd server` e ezecute o comando
```yarn init -y```

Agora você pode abrir a pasta usando comando se quiser `code .`.

Para concluir a configuração do projeto você precisa instalar o Typescript no projeto. Use o seguinte comando:
```yarn add typescript -D```
e 
```yarn tsc --init```

No arquivo `tsconfig.json`, mude o `"target": "es5"` para `"target": "es2017"`. Você precisa fazer isso porque é até a versão de 2017 que tem as funcionalidades que o Node.js reconhece. 

Use o seguinte [comando](https://www.npmjs.com/package/ts-node-dev) para executar o servidor e observar se tem alguma alteração no script. Isto automatiza o processo para conseguir fazer com que o Node entenda o Typescript
```yarn add ts-node-dev -D```
O `-D` significa que será usado apenas em dev e não em produção.

## Mobile using React Native <a name="mobile"></a>
Utilize um dos seguintes comandos para criar o projeto mobile:
```expo init mobile```
ou 
```expo init mobile --template "blank"```


## 🦾 Contribution or 🐞 Issues <a name="contribution"></a>
Escrevi este pequeno tutorial para ajudar na jornada dos aventureiros de React iniciantes. Se você tem alguma sugestão ou melhoria, senta-se livre para abrir uma Issue ou entrar em contato comigo! Vou ficar muito feliz em receber seu pull request. 🥰


## 📃 License
Escrito com 💙 por [Luiza R. Marinho](https://github.com/luizous).