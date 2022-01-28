# CRIAÇÃO DE UM CHAT COM NEXTJS - ESTILO DISCORD
> Aula ministrado pelo devSoutinho, para a imersão Alura de 01/2022.
>
> Será criado um sistema de chat, similar ao discord, com NextJS
>
- iniciar `yarn`
```
yarn init -y
```
- instalar o next
```
yarn add next react react-dom
```
Agora foi adicionado as dependências, no `package.json`
```json
  "dependencies": {
    "next": "^12.0.9",
    "react-dom": "^17.0.2"
  }
```
- Adicionar os `scripts` no `package.json`
```json
"scripts": {
  "dev": "next dev",
  "build": "next build",
  "start": "next start",
  "lint": "next lint"
}
``` 
Resultando no `package.json` assim:
```json
{
  "name": "imersao_alura",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
  "dependencies": {
    "next": "^12.0.9",
    "react-dom": "^17.0.2"
  },
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  }
}
```
- Agora, criar um pasta chamada `pages`, dentro dela criar um arquivo js chamado `index.js` com o conteudo seguinte.

`.pages/index.js`
```js
function HomePage() {
  return <div>Bem Vindo ao Next.js!</div>
}

export default HomePage
```
Iniciar o projeto com `yarn dev` no terminal
```
yarn dev
```
Entrando pelo navegador em `localhost:3000` deverá aparecer:
```
Bem Vindo ao Next.js!
```
Dentro do arquivo `index.js`, temos:
1. *Componente React*
```js
function HomePage() { 
    ...
}
```

2. *JSX - Javascript XML*

```js
return ( 
    ...
)
```

>Todo o conteúdo escrito em *html* entre os *parênteses* será compilado pelo **Babel** e retornará para a página *index.html*, que está sendo executada na *porta 3000* do *localhost*

3. *Execução*
```js
export default HomePage
```

## Exemplo de uma função com conteúdo ##
No exemplo seguinte, pode se perceber uma função com um conteúdo `function Title()`, sendo chamada dentro da função principal `function HomePage()`

```js
function Title() {
    return (
        <h1>Boas vindas de volta!!!</h1>
    );
}

function HomePage() {
    return (
        <div>
            <Title/>
            <h2>Discord - Alura Matrix</h2>
        </div>
    )
  }
  
  export default HomePage
```

## Exemplo de uma função com argumento ##
Através de `props` é possível passar argumentos para dentro da função, e assim alterar o seu conteúdo
```js
function Title(props) {
    console.log(props);
    console.log(props.children)
    return (
        <h1>Boas vindas de volta!!!</h1>
    );
}

// Componente React
function HomePage() {
    // JSX
    return (
        <div>
            <Title>Conteúdo passado por "props", funcionando como "children"</Title>
            <h2>
                Discord - Alura Matrix
            </h2>
        </div>
    )
  }
  
  export default HomePage
```

Entrando no console log do navegador, encontraremos:
```js
Object
    Objectchildren: "Conteúdo passado por \"props\", funcionando como \"children\""
    [[Prototype]]: Object

Conteúdo passado por "props", funcionando como "children"
```

Então, assim é possível passar esse argumento `props.children`, dentro do `<h1>` da função, com as ***chaves*** `<h1>{props.children}</h1>`
```js
function Title(props) {
    return (
        <h1>{props.children}</h1>
    );
}
function HomePage() {
    return (
        <div>
            <Title>Conteúdo passado por "props", funcionando como "children"</Title>
            <h2>
                Discord - Alura Matrix
            </h2>
        </div>
    )
  }
  
  export default HomePage
```


## GlobalStyle ##
Por padrão, mas não por obrigação, é criado um componente com o nome `GlobalStyle`, que fica responsável por guardar todos os *estilos CSS* 

`index.js`
```js
function GlobalStyle () {
    return (
        <style global jsx>{`         
            * {                
                margin: 0;
                padding: 0;
                box-sizing: border-box;
                
                background: grey;
            }

        `}</style>
    );
};

function Title(props) {
    return (
        <h1>{props.children}</h1>
    );
};

// Componente React
function HomePage() {
    // JSX
    return (
        <div>
            <GlobalStyle />
            <Title>Conteúdo passado por "props", funcionando como "children"</Title>
            <h2>
                Discord - Alura Matrix
            </h2>
        </div>
    );
  };
  
  export default HomePage;
```


## Styled JSX ##
```js
<style jsx>{`
      p {
        color: red;
      }
    `}</style>
```

## config.json ##
Arquivo json com configurações do tema.
Criar na raiz `config.json` com o seguinte conteúdo:
```json
{
  "name": "Aluracord - Matrix (peas)",
  "theme": {
    "colors": {
      "primary": {
        "100": "#C1EAC5",
        "200": "#A3D9A5",
        "300": "#7BC47F",
        "400": "#57AE5B",
        "500": "#3F9142",
        "600": "#2F8132",
        "700": "#207227",
        "800": "#0E5814",
        "900": "#05400A",
        "050": "#E3F9E5"
      },
      "neutrals": {
        "100": "#E4E7EB",
        "200": "#CBD2D9",
        "300": "#9AA5B1",
        "400": "#52667A",
        "500": "#313D49",
        "600": "#29333D",
        "700": "#212931",
        "800": "#181F25",
        "900": "#101418",
        "999": "#080A0C",
        "000": "#FFFFFF",
        "050": "#F5F7FA"
      }
    }
  },
  "stickers": [
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_1.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_2.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_3.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_4.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_5.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_6.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_7.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_8.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_9.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_10.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_11.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_12.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_13.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_14.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_15.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_16.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_17.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_18.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_19.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_20.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_21.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_22.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_23.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_24.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_25.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_26.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_27.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_28.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_29.png",
    "https://www.alura.com.br/imersao-react-4/assets/figurinhas/Figurinha_30.png",
    "http://2.bp.blogspot.com/-d21tffsTIQo/U_H9QjC69gI/AAAAAAAAKqM/wnvOyUr6a_I/s1600/Pikachu%2B2.gif",
    "https://media1.giphy.com/media/BdghqxNFV4efm/200.gif",
    "https://c.tenor.com/TKpmh4WFEsAAAAAC/alura-gaveta-filmes.gif",
    "https://i.pinimg.com/originals/0b/1c/23/0b1c2307c83e1ebdeed72e41b9a058ad.gif",
    "https://c.tenor.com/VylWt5lyjBoAAAAC/omg-yes.gif",
    "https://i.pinimg.com/originals/96/34/c5/9634c520c9a3cd4e7f23190bb2c96500.gif"
  ]
}
```
- Importar para dentro do `index.js`
```
import appConfig from '../config.json';
```

## SkyNexUI ##
```
yarn add @skynexui/components
```

`index.js`
```
import { Box, Button, Text, TextField, Image } from '@skynexui/components';
```

## Github ##

## Publicar na Vercel ##

## Obter o usuário dinamicamente ##
Neste código, temos um campo `TextField` que funciona como um input, mas de forma já estilizada.
Comentando o `TextField` e criando um `input`, a funcionalidade é a mesma:
```html
<input
  type="text"
  value="arqpatrick"
/>
{/* <TextField
  fullWidth
  textFieldColors={{
    neutral: {
      textColor: appConfig.theme.colors.neutrals[200],
      mainColor: appConfig.theme.colors.neutrals[900],
      mainColorHighlight: appConfig.theme.colors.primary[500],
      backgroundColor: appConfig.theme.colors.neutrals[800],
    },
  }}
/> */}
```
> Há um problema nesse código! A utilização de um `value` *fixo*, como `value="arqpatrick"` faz com que *quebre* o **React!!!**
>
### **ESTADO - STATE** ###
A grande *jogada* do React é a utilização de `components` e `state`. Quando colocamos um valor *fixo*, o React percebe que um `input`, pode receber uma **mudança** de **estado**.
É como se a cada mudança *(digitação, menu, ação, etc)* de estado, o React *"Tirasse uma foto"* daquele estado.
> Então, precisamos *"avisar"* para o React, que esse Estado do `input` poderá sofrer alteração
>
- Como **avisar** o React?
- [x] Declarar/Utilizar uma variável para utilizar a sua **variação**

```js
const username = 'arqpatrick';

<input
  type="text"
  value={username}
/>
```
Declarar a variável entre chaves `{variavel}`

- [x] Criar um `onChange` para lidar com essa mudança dos dados digitados pelo usuário

```js
const username = 'arqpatrick';

<input
  type="text"
  value={username}
  onChange={ function handler() {
    console.log('usuário digitou');
  }}
/>
```
Agora o React já está *"vendo"* a digitação do usuário, mas ainda não *"sabe"* como usar essa informação
- [x] Criar um `event` (evento), para lidar com utilizar as mudanças

```js
const username = 'arqpatrick';

<input
  type="text"
  value={username}
  onChange={ function handler(event) {
    console.log('usuário digitou', event.target.value);
  }}
/>
```
O React já `enxerga` o que é digitado, mas não consegue mudar ainda, precisa *desbloquear* o navegador
- [x] Utilizar o `useState` do React
```js
const [username, setUsername] = React.useState('arqpatrick');

<input
  type="text"
  value={username}
  onChange={ function handler(event) {
    console.log('usuário digitou', event.
    target.value);
    // Onde está o valor?
    const valor = event.target.value;
    // Trocar o valor da variável
    setUsername(valor);
  }}
/>
```
Aqui o `setUsername` trabalha como uma **função**. Ele que avisa o React que uma alteração está acontecendo e por isso ele é o responsável por armazenar esse novo valor: `setUsername(valor)` recebe o valor adquirido pela `const valor` através do `event.target.value`, que é a entrada do teclado no `input` criado

Agora podemos inserir esse sistema do React dentro do tag `TextField` que estava comentada anteriormente
```js
<TextField
  fullWidth
  value={username}
  onChange={ function handler(event) {                  
    const valor = event.target.value;
    setUsername(valor);
  }}
  textFieldColors={{
    neutral: {
      textColor: appConfig.theme.colors.neutrals[200],
      mainColor: appConfig.theme.colors.neutrals[900],
      mainColorHighlight: appConfig.theme.colors.primary[500],
      backgroundColor: appConfig.theme.colors.neutrals[800],
    },
  }}
/>
```
## RECARREGAMENTO PARCIAL NO REACT ##
Por padrão, a tag `form` de formulário, sempre executa um *refresh* quando o botão `submit` é executado.

Nesse exemplo, a tag `Box` está sendo `as = form` um formulário `form`.

Mas o React trabalha com desempenho, e para melhorar o desempenho, é melhor que as as funções, objetos, etc, sejam atualizados apenas na parte onde é necessário, não na página inteira. Para tanto, devemos controlar essa ação, e no `form` podemos usar o `onSubmit`, que funciona similar ao `onChange` utilizado anteriormente


## CRIAR NOVA PÁGINA ##



## ROUTER ##
Utilizando o `router` do React, podemos fazer os links sem necessidade de recarregar a página inteira, melhorando a performance e a experiência do usuário
```js
import { useRouter } from 'next/router';

const roteamento = useRouter();

<input

onSubmit={ function (infosDoEvento) {
  infosDoEvento.preventDefault();
  roteamento.push('/chat');
}}

/>
```

## _app.js ##
No Next, criando uma página chamada `_app.js` dentro de `pages`, temos uma wrapper, que envolve todas as páginas automaticamente. Então tudo que estiver dentro dela será exibido em todas as páginas
`>pages/_app.js`
```js
export default function MyApp({ Component, pageProps }) {
    console.log('Roda em todas as páginas');
    return <Component {...pageProps} />
}
```
Então podemos colocar o recortar o `GlobalStyle` de dentro do `index.js` e colocá-lo dentro desse *wrapper*
```js
// GLOBALSTYLE CSS
function GlobalStyle() {
    return (
      <style global jsx>{`
        * {
          margin: 0;
          padding: 0;
          box-sizing: border-box;
          list-style: none;
        }
        body {
          font-family: 'Open Sans', sans-serif;
        }
        /* App fit Height */ 
        html, body, #__next {
          min-height: 100vh;
          display: flex;
          flex: 1;
        }
        #__next {
          flex: 1;
        }
        #__next > * {
          flex: 1;
        }
        /* ./App fit Height */ 
      `}</style>
    );
  }

export default function CustomApp({ Component, pageProps }) {
    return (
        <>
            <GlobalStyle />
            <Component {...pageProps} />
        </>
    )
}
```

## HOOKS ##

- useState
- useRouter

# LINKS #

### **NextJS** ###
https://nextjs.org/docs/getting-started
### **Styled JSX** ###
https://github.com/vercel/styled-jsx
### **Custom `App`** ###
https://nextjs.org/docs/advanced-features/custom-app