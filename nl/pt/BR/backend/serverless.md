---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}
{:tip: .tip}

# Desenvolvimento do Serverless
{: #serverless}

O que é serverless? O padrão de desenvolvimento sem servidor refere-se ao desenvolvimento de aplicativo em que a lógica do lado do servidor é executada em contêineres stateless. Os contêineres são acionados por evento, efêmeros (duráveis para uma única execução) e são totalmente gerenciados por um terceiro. Esse paradigma, também conhecido como Functions as a Service (FaaS), é onde o desenvolvedor fornece uma função stateless que pode ser acionada e executada sem criar ou gerenciar explicitamente um servidor.

Ao abstrair a infraestrutura e as estruturas necessárias para o desenvolvimento do lado do servidor, a arquitetura sem servidor permite que os desenvolvedores se concentrem na gravação do código que executa reativamente para mudar dados.

A oferta FaaS da IBM, [{{site.data.keyword.openwhisk}}](https://console.bluemix.net/openwhisk/), se empenha para fornecer uma experiência de desenvolvimento simples e do lado do servidor sem precisar de nenhum conhecimento especializado do lado do servidor. Ao usar a tecnologia sem servidor, é possível desenvolver rapidamente as soluções de back-end extensíveis para atender praticamente qualquer demanda de carga de trabalho sem a necessidade de criar recursos antecipadamente. Para aplicativos que têm padrões de carregamento imprevisíveis ou tempo de inatividade do servidor alto, o {{site.data.keyword.openwhisk_short}} pode ser uma excelente solução de nuvem com desempenho aprimorado e seu sistema "pague pelo que você usa" ajuda a reduzir os custos.

## Alterações Arquiteturais
{: #comparison}

Para ajudá-lo a entender os benefícios arquiteturais de se alternar para o FaaS, as arquiteturas tradicionais e do FaaS são comparadas usando um aplicativo iOS simples que é vinculado a um banco de dados.

Em uma arquitetura mais tradicional, o aplicativo iOS transfere as tarefas de uso intensivo de rede ou processa os dados remotamente em um servidor centralizado, pelo qual ele mesmo é conectado por suas próprias opções de serviços ou de armazenamento. O trabalho pesado é colocado em um servidor singular que processa muitas tarefas intensivas para minimizar o estresse no cliente e fornecer sincronização em toda a sua base do usuário.

Uma arquitetura sem servidor pode alterar essa estrutura para parecer mais com a imagem a seguir.

![](./images/Architecture.png)  Figura 1. Arquitetura sem

Em vez de manipular todo o processamento e a lógica de autenticação dentro de um único servidor, uma arquitetura sem servidor usa as funções que encapsulam muito da lógica do lado do servidor e transfere alguma lógica para o cliente (e os serviços externos).

Olhando para o esquemático, é possível ver os seguintes pontos:

1. O cliente autentica-se em um Provedor de identidade, como o ID do app.
2. Chamadas para a API de backend do FaaS, incluindo o token de acesso.
3. O backend é implementado com o  {{site.data.keyword.openwhisk_short}}. As ações sem servidor são expostas como ações da web e esperam que os tokens sejam enviados no cabeçalho da solicitação para verificação (assinatura e data de validação) para fornecer acesso à API real.
4. Quando o cliente envia dados, o feedback é armazenado em um {{site.data.keyword.cloudant_short_notm}}.
5. O texto de feedback é processado com o  {{site.data.keyword.toneanalyzershort}}.
6. Com base no resultado da análise, uma notificação é enviada de volta para o cliente pelo {{site.data.keyword.mobilepushshort}}.
7. O cliente recebe a notificação.

Em um modelo puramente sem servidor, o cliente geralmente assume responsabilidades extras devido à incapacidade de armazenar o estado do usuário. A autorização é manipulada pelo cliente e pelo serviço do provedor de identidade do {{site.data.keyword.appid_short_notm}}.

Embora as arquiteturas sem servidor nem sempre sejam ideais, elas podem fornecer benefícios profundos sob a equipe e as condições de uso corretas. Verifique alguns exemplos específicos para conhecer alguns dos [casos de uso](#use_cases) mais comuns.

## Benefícios do Server
{: #benefits}

### Custo Reduzido

A terceirização do tempo e do custo monetário associada à administração do sistema, reduz o custo geral associado aos servidores de backend tradicionais. Além disso, o {{site.data.keyword.openwhisk_short}} é diferente das tecnologias de computação tradicionais porque você paga apenas pelo tempo que seu código leva para satisfazer as solicitações, arredondado para os 100 ms mais próximos. Economias de custo consideráveis são possíveis quando você compara com outras tecnologias, como VMs e contêineres, que provavelmente não são 100% usados e consomem a memória no sistema do seu provedor em nuvem.

### Alta disponibilidade e escalabilidade

As arquiteturas sem servidor fornecem inerentemente escalabilidade instantânea com disponibilidade quase constante.

### Aceleração e desenvolvimento simplificado

Eliminando a necessidade de administração do sistema e fornecendo interfaces simples para implementação, o paradigma sem servidor acelera o desenvolvimento de aplicativo. Os desenvolvedores podem construir apps rapidamente com sequências de ações que são executadas em resposta a um mundo orientado a eventos.

## Casos de uso de exemplo
{: #use_cases}

### Backend Móvel
![](./images/cloud-functions-rest-api-trigger.png)

Os desenvolvedores de dispositivos móveis podem acessar facilmente a lógica do lado do servidor e terceirizar as tarefas computacionalmente intensivas para uma plataforma em nuvem. É possível implementar funções em linguagens como Swift e consumir facilmente funções do lado do servidor usando o iOS SDK sem a necessidade de experiência do lado do servidor.

### Processamento de Dados

![](./images/cloud-functions-cloudant-trigger.png)

É possível executar código sempre que os dados são atualizados em seu armazenamento de dados por meio de acionadores integrados. Também é possível automatizar processos facilmente, como normalização de áudio, rotação de imagem, aumento da nitidez, redução de ruído, geração de miniatura ou transcodificação de vídeo por meio de um modelo de programação funcional do lado do servidor.

### Processamento de Dados Cognitivo

É possível analisar dados assim que eles se tornam disponíveis. Sua função pode tirar proveito de poderosos serviços cognitivos, como o IBM Watson, para detectar objetos ou pessoas em imagens ou vídeos.

### Tarefas Planejadas

Execute suas funções periodicamente e defina planejamentos que seguem uma sintaxe semelhante à cron para especificar quando as ações devem ser executadas.

## Referência da API
{: #openwhisk_start_api notoc}

<!-- * [REST API Documentation](./openwhisk_reference.html#openwhisk_ref_restapi)-->
* [API REST](https://console.{DomainName}/apidocs/98)

## Links Relacionados
{: #general notoc}

* [Descubra o {{site.data.keyword.openwhisk_short}}](http://www.ibm.com/cloud-computing/bluemix/openwhisk/)
<!-- redirects to link above * [{{site.data.keyword.openwhisk_short}} on IBM developerWorks](https://developer.ibm.com/openwhisk/)-->
* [ website do projeto Apache OpenWhisk ](http://openwhisk.org)
* [ Mais sobre Serverless ](https://martinfowler.com/articles/serverless.html)
