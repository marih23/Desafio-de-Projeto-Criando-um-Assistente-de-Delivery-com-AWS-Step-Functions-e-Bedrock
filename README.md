# Descrição
Criar um Assistente de Delivery utilizando AWS Step Functions e Amazon Bedrock. O projeto consiste em orquestrar diferentes serviços AWS para automatizar e gerenciar um fluxo de pedidos de delivery, desde a recepção do pedido até a entrega final.
Este desafio foi acompanhado a parte teórica e não foi desenvolvida a parte prática devido a fatores financeiros.

## Resumo

# AWS Step Functions

Serviço da Amazon Web Services (AWS) que permite orquestrar fluxos de trabalho compostos por múltiplos serviços AWS de forma sequencial ou paralela, de maneira simples e com monitoramento integrado. Ele ajuda a criar fluxos de trabalho altamente escaláveis e flexíveis para aplicações distribuídas. A principal função do Step Functions é orquestrar e automatizar processos, como chamadas a API's, funções Lambda, interações com bancos de dados, entre outros serviços AWS.

# Funcionamento

- Estados e Máquinas de Estados: O Step Functions utiliza um modelo baseado em estados. Cada etapa do fluxo de trabalho é representada por um estado. Esses estados podem ser de diferentes tipos: de execução de tarefas (funções Lambda), de escolha (condições), de paralelização de tarefas, entre outros.
- Definição de Fluxo: O fluxo de trabalho é definido em um Documento de Definição de Estado (State Machine) usando JSON ou YAML, o qual descreve os diferentes estados, transições entre eles e os dados a serem processados em cada etapa.
- Monitoramento e Erros: oferece um painel visual para acompanhar a execução de cada passo, assim como as transições entre estados. Ele também possui mecanismos para lidar com falhas e exceções no processo.

# Amazon Bedrock

O Amazon Bedrock é um serviço de inteligência artificial da AWS que facilita a criação e implementação de aplicações baseadas em modelos de linguagem generativa (como o ChatGPT, por exemplo). Ele fornece acesso a diversos modelos poderosos de IA para criação de chatbots, assistentes virtuais e outros tipos de interação com linguagem natural, sem precisar se preocupar com a infraestrutura de treinamento ou escalabilidade.
O Bedrock é otimizado para ser fácil de usar e oferece acesso a modelos de IA de grandes empresas como Anthropic, Stability AI, AI21 Labs e Amazon Titan, o que torna possível construir soluções personalizadas de IA.

# Funcionamento

- Modelos de IA sob demanda: O Amazon Bedrock oferece modelos prontos para uso que podem ser aplicados para tarefas como processamento de linguagem natural, geração de texto, análise de sentimentos e outras tarefas de IA.
- Customização de Modelos: Você pode personalizar os modelos pré-treinados para se adaptar a necessidades específicas da sua aplicação. Por exemplo, se o seu assistente de delivery precisa de uma personalidade ou forma de conversar única, você pode treinar um modelo baseado em um dos pré-existentes, mas com um toque específico.
- Integração com outros serviços AWS: Como o Amazon Bedrock é integrado com o resto da AWS, você pode facilmente usá-lo em conjunto com outros serviços da AWS, como Lambda ou Step Functions para adicionar inteligência à sua aplicação.

# Etapas do Fluxo de Trabalho do Delivery com Step Functions

1. Recepção do Pedido (início do processo):

   - O fluxo de trabalho começa assim que um pedido de delivery é recebido. Este pedido pode ser feito por meio de uma API ou uma interface de usuário (UI), que dispara um evento. O Step Functions pode ser configurado para acionar uma função Lambda que registra o pedido em uma base de dados ou sistema de gerenciamento de pedidos.

2. Validação do Pedido:

   - Em seguida, o pedido é validado. Isso pode envolver a verificação de dados como o endereço de entrega, disponibilidade de produtos, etc. O Step Functions pode chamar outra função Lambda ou integrar com um serviço de verificação de pagamentos.

3. Alocação do Motorista:

   - O sistema pode chamar um serviço para alocar um motorista para o pedido, seja por meio de uma API de rastreamento de motoristas ou através de outro processo interno. O Step Functions orquestraria essa tarefa, chamando APIs de terceiros ou funções internas para realizar esse trabalho.

4. Interação com o Cliente (Assistente de Delivery com Amazon Bedrock):

   - Aqui entra o Amazon Bedrock. Você pode criar um assistente de delivery inteligente que se comunica com o cliente, atualizando-o sobre o status do pedido (ex: "Seu pedido está a caminho!") ou respondendo dúvidas como "Qual o tempo estimado de entrega?". O Bedrock pode gerar essas respostas de forma natural, utilizando um modelo de linguagem avançado. Esse assistente poderia ser acessado via chat (pode ser via WhatsApp, por exemplo) ou até mesmo por comandos de voz em um dispositivo inteligente.

5. Rastreamento do Pedido:

   - A próxima etapa seria o rastreamento da entrega. O Step Functions pode orquestrar essa tarefa com integração de dados de localização do motorista e do cliente. Se o pedido está em andamento, o Step Functions pode consultar uma API de rastreamento e atualizar o status. O assistente de delivery também pode interagir com o cliente para informar o tempo estimado de chegada, por exemplo.

6. Finalização e Feedback:

   - Após a entrega, você pode criar uma etapa para solicitar o feedback do cliente. O assistente pode pedir para o cliente avaliar a entrega ou informar sobre algum problema. O Step Functions orquestraria a coleta desse feedback, enquanto o Bedrock poderia responder de forma personalizada, dependendo das respostas do cliente (por exemplo, se o feedback for negativo, poderia gerar uma resposta de desculpas).

# Resumo do Uso das Ferramentas:

- AWS Step Functions: Usado para orquestrar todo o fluxo de trabalho, conectando diferentes serviços e processos como o recebimento do pedido, alocação do motorista, validações de pagamento, rastreamento de status e coleta de feedback.
- Amazon Bedrock: Usado para criar um assistente inteligente que interage com o cliente, respondendo perguntas sobre o status do pedido, fornecendo informações e até pedindo feedback. Ele pode ser integrado ao Step Functions, sendo acionado sempre que for necessário realizar uma interação com o cliente.

Essa combinação de ferramentas permite a construção de um sistema de delivery eficiente, automatizado e inteligente, com um fluxo bem coordenado e interações de alta qualidade com o usuário.
