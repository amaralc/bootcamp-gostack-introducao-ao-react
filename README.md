# bootcamp-gostack-introducao-ao-react 

## Configurando a estrutura

  * (terminal) Add dependencies: 
    * `yarn init -y`;
    * `yarn add @babel/core @babel/preset-env @babel/preset-react webpack webpack-cli -D`;
    * `yarn add react react-dom`;
    * `yarn add babel-loader -D`;
    * `yarn add webpack-dev-server -D`;

  * Create **babel.config.js**:

    ```js
    module.exports = {
      presets: [
        "@babel/preset-env", 
        "@babel/preset-react"
      ]
    }
    ```

  * Create **webpack.config.js**:

    ```js
    const path = require('path');

    module.exports = {
      entry: path.resolve(__dirname,'src','index.js'),
      output: {
        path: path.resolve(__dirname, 'public'),
        filename: 'bundle.js'
      },
      devServer: {
        contentBase: path.resolve(__dirname, 'public'),
      },
      module: {
        rules: [
          {
            test: /\.js$/,
            exclude: /node_modules/,
            use: {
              loader: 'babel-loader'
            }
          }
        ]
      }
    }
    ```

  * Cria atributo `scripts` no package.json:

    ```js
    "scripts": {
      "build": "webpack --mode production",
      "dev": "webpack-dev-server --mode development"
    },
    ```

  * Cria arquivo **src/index.js**:

    ```js
    const soma = (a, b) => a + b;

    alert(soma(1,3));
    ```

  * (terminal) Cria bundle e pasta public: `yarn build`;

  * Cria **public/index.html**:

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>ReactJS</title>
    </head>
    <body>
      <h1>Hello World!</h1>
      <script src="./bundle.js"></script>
    </body>
    </html>
    ```

  * (terminal) Roda servidor de desenvolvimento: `yarn dev`;

