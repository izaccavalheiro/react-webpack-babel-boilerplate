# Criando um projeto de SPA com React

A seguir temos um passo-a-passo sobre como iniciar um projeto de SPA com React utilizando apenas Webpack e Babel. Não iremos utilizar o Create React App.

> Nota: Antes de iniciar o tutorial é necessário instalar o Node.js https://nodejs.org/.

**1. Criar pacote NPM**

    npm init -y

Esse comando cria o pacote utilizando as informações padrões coletadas do diretório atual (nome e urls do repositório) sem fazer perguntas.

**2. Instalar as dependências de desenvolvimento**

    npm i webpack webpack-cli webpack-dev-server html-loader @babel/core @babel/preset-env @babel/preset-react @babel/runtime babel-loader html-webpack-plugin -D

**3. Instalar as dependências da aplicação**

    npm i react react-dom -S

**4. Criar arquivo de configuração do Webpack na raiz do projeto conforme abaixo.**

#### webpack.config.js

    const HtmlWebPackPlugin = require('html-webpack-plugin')

    module.exports = {
      module: {
        rules: [
          {
            test: /\.(js|jsx)$/,
            exclude: /node_modules/,
            use: {
              loader: 'babel-loader'
            }
          },
          {
            test: /\.html$/,
            use: [
              {
                loader: 'html-loader'
              }
            ]
          }
        ]
      },
      resolve: {
        extensions: ['*', '.js', '.jsx']
      },
      devServer: {
        contentBase: './dist'
      },
      plugins: [
        new HtmlWebPackPlugin({
          template: './index.html',
          filename: './index.html'
        })
      ]
    }

**5. Criar o arquivo de configuração do Babel na raiz do projeto conforme abaixo.**

#### .babelrc

    {
      "presets": ["@babel/preset-env", "@babel/preset-react"]
    }

**6. Criar uma pasta para o código-fonte da SPA**

    mkdir src

**7. Dentro da pasta src, criar o arquivo HTML que fará o carregamento da SPA, conforme abaixo.**

#### src/index.html

    <!DOCTYPE html>
      <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <title>Hello World!</title>
        <meta name="description" content="">
        <meta name="viewport" content="width=device-width, initial-scale=1">
      </head>
      <body>
        <div id="app"></div>
      </body>
    </html>

**8. Dentro da pasta src, criar o arquivo de entrada da SPA conforme abaixo.**

#### src/index.js

    import React from 'react'
    import ReactDOM from 'react-dom'
    
    import App from './App'
    
    ReactDOM.render(<App />, document.querySelector('#app'))

**9. Ainda dentro da pasta src, criar o arquivo do principal componente conforme abaixo.**

#### src/App.jsx

    import React from 'react'
    
    function App () {
      return (
        <div>Hello world!</div>
      )
    }
    
    export default App

**10. Inserir as seguintes linhas na chave "scripts" do arquivo package.json localizado na raiz do projeto.**

    "start": "webpack-dev-server --open --hot --mode development",
    "build": "webpack --mode production"

O seu arquivo deve ficar assim:

#### package.json

    {
      "name": "react-webpack-babal-boilerplate",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "start": "webpack-dev-server --open --hot --mode development",
        "build": "webpack --mode production"
      },
      "repository": {
        "type": "git",
        "url": "git+https://github.com/izaccavalheiro/react-webpack-babal-boilerplate.git"
      },
      "author": "",
      "license": "ISC",
      "bugs": {
        "url": "https://github.com/izaccavalheiro/react-webpack-babal-boilerplate/issues"
      },
      "homepage": "https://github.com/izaccavalheiro/react-webpack-babal-boilerplate#readme",
      "dependencies": {
        "react": "^16.8.6",
        "react-dom": "^16.8.6"
      },
      "devDependencies": {
        "@babel/core": "^7.4.3",
        "@babel/preset-env": "^7.4.3",
        "@babel/preset-react": "^7.0.0",
        "babel-loader": "^8.0.5",
        "babel-runtime": "^6.26.0",
        "html-loader": "^0.5.5",
        "html-webpack-plugin": "^3.2.0",
        "webpack": "^4.30.0",
        "webpack-cli": "^3.3.1",
        "webpack-dev-server": "^3.3.1"
      }
    }

**11. Executar a SPA em modo de desenvolvimento**

    npm start

## Conclusão

Este é um passo-a-passo simples para iniciar um projeto básico de uma Single Page Application em React com o mínimo necessário.

A SPA pode ser acessada a partir do endereço http://localhost:8080/, de acordo com a configuração padrão do Webpack.

## Código-fonte

[https://github.com/izaccavalheiro/react-webpack-babel-boilerplate](https://github.com/izaccavalheiro/react-webpack-babel-boilerplate)

## Informações adicionais

Node.js: Plataforma construída em cima do motor de Javascript do Google Chrome.

NPM: "Node.js Package Manager" Gerenciador de pacotes para Javascript.

React: Biblioteca declarativa para construção de interfaces (front-end).

React-DOM: Biblioteca auxiliar do React utilizada para acessar o DOM.

Webpack: Gerador/Empacotador de módulos Javascript.

webpack-cli: Linha de comando do Webpack.

webpack-dev-server: Servidor de teste para o desenvolvimento aplicações com Webpack.

@babel/core: Compilador de Javascript.

html-loader: Exportador de HTML como string.

html-webpack-plugin: Plugin do Webpack que simplifica a criação dos arquivos HTML que serão utilizados para servir a SPA. 

@babel/preset-env: Biblioteca auxiliar do Babel utilizada para permitir o uso das versões mais recentes do Javascript (ES 5, ES 6, ES 7 etc).

@babel/preset-react: Biblioteca auxiliar do Babel utilizada para permitir o uso com React.

babel-loader: Biblioteca auxiliar do Babel utilizada para permitir o uso com Webpack.

babel-runtime: Biblioteca auxiliar do Babel
