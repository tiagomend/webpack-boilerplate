# Boilerplate do Webpack

Este é um boilerplate básico para configurar o Webpack em seu projeto.

## Instalação de Pacotes

Para começar, você precisará iniciar o `npm` com o seguinte comando:

```bash
npm init -y
```

Depois você precisará instalar os seguintes pacotes:

```bash
npm i --save-dev @babel/preset-env @babel/core @babel/cli babel-loader webpack webpack-cli

npm i regenerator-runtime core-js
```

Certifique-se de instalar os pacotes `@babel/preset-env`, `@babel/core`, `@babel/cli`, `babel-loader`, `webpack` e `webpack-cli` como dependências de desenvolvimento (`dev`). Os pacotes `regenerator-runtime` e `core-js` são necessários como dependências de produção (`prod`).

## Configuração do Arquivo `webpack.config.js`

Você precisará configurar o arquivo `webpack.config.js` com as seguintes opções:

```javascript
module.exports = {
  mode: 'development',
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'public', 'static'),
    filename: 'index.bundle.js'
  },
  module: {
    rules: [{
      exclude: /node_modules/,
      test: /\.js$/,
      use: {
        loader: 'babel-loader',
        options: {
          presets: ['@babel/env']
        }
      }
    }]
  },
  devtool: 'source-map',
}
```

Certifique-se de ajustar o caminho do arquivo de entrada (`entry`) e o nome do arquivo de saída (`filename`) conforme necessário para o seu projeto.

Esta configuração inclui a regra para o uso do Babel Loader para transpilar arquivos JavaScript, excluindo a pasta `node_modules`. O `devtool` é configurado para gerar mapas de origem para facilitar a depuração.

## Configuração do `package.json`

Adicione o seguinte script ao seu arquivo `package.json` para executar o Webpack em modo de observação:

```json
{
  "scripts": {
    "dev": "webpack -w"
  }
}
```

Este script executará o Webpack em modo de observação (`-w`), que automaticamente reconstruirá o bundle sempre que os arquivos de origem forem modificados.

Com esta configuração básica, você pode começar a usar o Webpack em seu projeto.