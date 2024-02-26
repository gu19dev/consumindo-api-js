# Consumindo a API ViaCEP com Node.js

A API "ViaCEP" é um webservice gratuito de alto desempenho para consulta de Código de Endereçamento Postal (CEP) do Brasil. Para acessar o webservice, um CEP no formato de 8 dígitos deve ser fornecido, exemplo: "01001000". Após o CEP, deve ser fornecido o tipo de retorno desejado, que deve ser "json" ou "xml".

## Sobre o código

O código se encontra no arquivo ead-multiples-cep.http. Basicamente, é um script JavaScript que, primeiramente, recebe através de um "input" um CEP no formato de 8 números, verifica se estes números estão validados (estão corretos) e, se estiverem, retorna um JSON com os dados da API.

### Explicando o código

O código é interpretado através do Node.js e utiliza os módulos nativos do ambiente como o eadline e https. O módulo eadline é semelhante ao input disponível nos navegadores, porém, para este módulo do Node.js, ele permite ler a entrada do usuário a partir do terminal.

A função getCep solicita ao usuário que digite um CEP. Quando o usuário digita o CEP e pressiona Enter, a função de callback é chamada com o CEP digitado pelo usuário.

Você está definindo as opções para a requisição HTTP. Você vai fazer uma requisição GET para a API ViaCEP, passando o CEP digitado pelo usuário na URL.

Você está fazendo a requisição HTTP e lidando com a resposta. Quando os dados chegam, você os adiciona à variável data. Quando todos os dados foram recebidos, você imprime os dados (que são um objeto JavaScript representando o endereço associado ao CEP) e chama a função getCep novamente para solicitar outro CEP ao usuário.

Finalmente, você chama a função getCep pela primeira vez para iniciar o processo.
