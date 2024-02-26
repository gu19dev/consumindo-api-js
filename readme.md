# Consumindo a API ViaCEP com Node.js

Este projeto tem como objetivo exemplificar o consumo da API "ViaCEP" utilizando JavaScript.

Um **webservice** é um serviço disponibilizado na web que permite a comunicação e interação entre sistemas diferentes através de uma interface padrão, geralmente utilizando protocolos como HTTP. Essa abordagem facilita a integração de sistemas distintos, permitindo que eles troquem informações de forma eficiente e padronizada.

A API "ViaCEP" requer um CEP no formato de {8} números para realizar consultas. Este projeto demonstra como realizar consultas à API "ViaCEP" utilizando Node.js, fornecendo uma base para a integração de serviços de CEP em aplicações web e sistemas diversos.
Você pode acessar o site da ViaCEP [aqui](https://viacep.com.br/).

## Sobre o código

Para realizar as requisições, foi optado por utilizar os módulos nativos do Node.js, 'https' e 'readline'. Esses módulos fornecem funcionalidades essenciais para lidar com requisições HTTP e para interagir com a entrada do usuário no terminal, respectivamente.

O código se encontra no arquivo `read-multiples-cep.http`. Basicamente, é um script JavaScript que, primeiramente, recebe através de um "input" um CEP no formato de 8 números, verifica se estes números estão validados (estão corretos) e, se estiverem, retorna um JSON com os dados da API.

##

### Explicando o código

#### Parte 1: Leitura do Input do Usuário

```javascript
const reader = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
});
```

O módulo `readline` é uma biblioteca do Node.js que permite a leitura de entrada de texto do usuário a partir do terminal de forma assíncrona. Ele fornece uma interface de leitura que facilita a interação do usuário com o programa, especialmente quando se trata de entrada de dados interativa.

Quando você cria uma interface de leitura usando o método `createInterface` do módulo `readline`, você precisa especificar de onde será a entrada (`input`) e para onde será a saída (`output`). No caso específico do exemplo que você forneceu:

- `input: process.stdin`: Isso indica que a entrada de dados será obtida a partir do fluxo padrão de entrada (`stdin`), que geralmente é o teclado quando o programa é executado no terminal. Ou seja, o programa estará esperando que o usuário digite algo no terminal para interagir com ele.

- `output: process.stdout`: Isso indica que a saída de dados será enviada para o fluxo padrão de saída (`stdout`), que também é o terminal. Qualquer saída do programa, como mensagens ou prompts, será exibida no terminal para o usuário ver.

Essa configuração é necessária para que o módulo `readline` saiba de onde obter a entrada do usuário e para onde enviar qualquer saída. Dessa forma, ele pode esperar que o usuário forneça entrada de texto e exibir mensagens de maneira adequada no terminal, facilitando a interação do usuário com o programa.

Esta parte do código cria uma interface de leitura (`readline`) que permite ler a entrada do usuário a partir do terminal. Isso é necessário para que o usuário possa fornecer o CEP desejado.

#### Parte 2: Requisição à API ViaCEP

Nesse trecho de código, estamos declarando uma constante chamada `options` que é um objeto contendo várias propriedades. Essas propriedades são utilizadas para configurar a requisição HTTP que será feita para a API ViaCEP.

```javascript
const options = {
  hostname: "viacep.com.br",
  path: `/ws/${cep}/json/`,
  method: "GET",
};

const req = https.request(options, (res) => {
  let data = "";

  res.on("data", (chunk) => {
    data += chunk;
  });

  res.on("end", () => {
    // Exibir os dados do endereço
    console.log(JSON.parse(data));
  });
});
```

- `hostname`: Esta propriedade especifica o nome do host para onde a requisição será feita. No caso, estamos configurando-a para `'viacep.com.br'`, que é o host da API ViaCEP.

- `path`: Aqui, definimos o caminho da URL para onde a requisição será feita. Estamos utilizando **template literals** para incluir dinamicamente o valor da variável `cep` no caminho da URL. Isso nos permite fazer a consulta do CEP desejado. O formato da URL segue as especificações da API ViaCEP, onde `/ws/` é o endpoint padrão para consulta de CEPs, seguido pelo CEP desejado e o formato de retorno (JSON, neste caso).

  - **Template literals**: As template literals são uma funcionalidade do JavaScript que permite a inclusão de expressões JavaScript dentro de strings delimitadas por crases (\`\`). Isso nos permite inserir dinamicamente o valor da variável `cep` dentro da string do caminho da URL.

- `method`: Esta propriedade especifica o método HTTP que será utilizado na requisição. No caso, estamos configurando-a para `'GET'`, indicando que faremos uma requisição do tipo GET, que é usada para obter dados do servidor.

Essas opções são passadas como argumentos para o método `https.request()`, que realiza a requisição HTTP para a API ViaCEP. Elas permitem configurar a requisição de acordo com as necessidades específicas do nosso programa, como o host a ser acessado, o caminho da URL e o método HTTP a ser utilizado.
Em seguida, faz uma requisição GET para a API utilizando o módulo `https`. Quando os dados da resposta são recebidos, eles são armazenados em uma variável `data` e, quando a resposta é concluída, os dados são exibidos no console.

#### Parte 3: Chamada da Função `getCep`

```javascript
getCep();
```

Esta parte do código chama a função `getCep` pela primeira vez para iniciar o processo de solicitação do CEP ao usuário.

### Adquirindo o Código

Você pode adquirir o código deste projeto de diferentes maneiras:

#### Baixando o repositório em zip

### ou

#### Clonando o Repositório via Linha de Comando

Para clonar o repositório e ter uma cópia do código em sua máquina local, siga estas etapas:

1. Certifique-se de ter o Git instalado em sua máquina.
2. Abra seu terminal ou o Git Bash.
3. Altere o diretório de trabalho atual para o local em que deseja ter o diretório clonado.
4. Copie a URL do repositório.
5. Digite o seguinte comando no terminal, substituindo `<URL-do-repositório>` pela URL que você copiou:

```
git clone https://github.com/gu19dev/consumindo-api-js
```

6. Navegue até o diretório clonado:

```
cd consumindo-api-js
```

7. Execute `npm install` para instalar as dependências, se necessário.

8. E por fim, execute o script Node.js com o seguinte comando:

```
node read-multiples-cep.http
```

Obrigado!
