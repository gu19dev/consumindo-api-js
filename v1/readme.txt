# Consumindo API com JavaScript


### 
Este código é um script simples desenvolvido em Node.js que realiza
consultas à API "ViaCEP" para obter informações sobre um determinado
CEP. A API "ViaCEP" é um webservice gratuito que fornece dados de
endereçamento postal do Brasil.

#
O funcionamento do script é o seguinte:

Utiliza os módulos nativos do Node.js [readline e https], para interagir
com o usuário através do terminal e fazer requisições HTTP para a API
"ViaCEP".

Primeiro, solicita ao usuário que insira o CEP desejado através do
terminal.

Em seguida, constrói a URL de consulta à API "ViaCEP" com base no CEP
fornecido pelo usuário. O formato da URL segue as especificações da API,
onde /ws/ é o endpoint padrão para consulta de CEPs, seguido pelo CEP
desejado e o formato de retorno (JSON, neste caso).

Realiza uma requisição HTTP GET para a URL construída, utilizando o
módulo https.

Quando a resposta da API é recebida, os dados são armazenados em uma
variável e, após o término da resposta, esses dados são exibidos no
console do Node.js.

Portanto, este código é útil para consultar informações de CEP através
da API "ViaCEP" diretamente no terminal usando Node.js. Os dados são
retornados no formato JSON para fácil manipulação e exibição no ambiente
do Node.js.
