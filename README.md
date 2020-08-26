## How to create a React and React Native project
🔠 [Português](README.pt-br.md)

This tutorial doesn't have a detailed introduction to React! The purpose of this article is to just unify the commands needed to create a project, very simplified and fast.

### Table of Contents
1. [Web (front-end)](#web)
2. [Server (back-end)](#server)
3. [Mobile using React Native](#mobile)
4. [How to run](#run)
5. [Contribution or Issues](#contribution)

First, you need to install these things:
- Node.js
- NPM
- Yarn
- Expo

## Web (front-end) <a name="web"></a>
To create the web app with react.js, you first need to install the create-react-app. Use this following command to do so:
```
npm install -g create-react-app
```

Access where you want to create your react app and use the command (the project-name without the `<>`):
```
create-react-app <project-name>
```

My favorite code editor is Visual Studio Code, so enter the web folder and use the command `code .` to open.
![image-20200826135405201](img/img-1.png)

The project structure should be like this:
![image-20200826130558117](img/img-2.png)

Delete these files:
- App.css
- App.test.js
- index.css
- logo.svg

The file servicerWorker.js is to work with PWA.

## Server (back-end) <a name="server"></a>

In the project folder open a terminal and execute the command:
```mkdir server```

Get into the folder `server` using the command `cd server`.

Execute the command:
```yarn init -y```

Open the folder on Visual studio Code using `code .`.

Add the typescript with the following command:

```yarn add typescript -D```
and
```yarn tsc --init```

In the `tsconfig.json `file, change the `"target": "es5"` to `"target": "es2017"`. You need to do that because until 2017 is the functionalities that the node.js understand. 

Execute this command to execute the server and see if there is some change inthe script. 
```yarn add ts-node-dev -D```


## Mobile using React Native <a name="mobile"></a>
Command to create the project:
`expo init mobile` ou `expo init mobile --template "blank"`


## 🦾 Contribution or 🐞 Issues <a name="contribution"></a>
I wrote this little tutorial for the adventurous beginners on this study journey to React. This is for everybody so, if you have some improvements or suggestion, feel free to open a issue or contact me! I will happily review your pull request. 🥰


## 📃 License
Written with 💙 by [Luiza R. Marinho](https://github.com/luizous).