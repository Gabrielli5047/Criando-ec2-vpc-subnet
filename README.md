Atualizacao: Enviei o link na semana errada, nome do repositorio esta com o tema do exercicio da semana 1, porem, logo abaixo será a explicacao da semana 2.


1- Crie um serviço de mensagens em fila usando a Amazon SQS.
  1.1-Podemos criar filas tanto pela aws quando e pelo terminal aws cli:
  pela aws
  1 - ENTRA EM SQS - CREATE FILA
  2 - STANDARD - PARA MANDAR FORA ORDEM (FIFO - MANDA NA ORDEM)
  3-  NOME DA FILA - FILA-GABRIELLI
  4- configuration - deixar como ta la - create que
  5-  clicamos na fila e - send messeger
  6- escreve uma msg e - send messeger
  7- refresh aparece messages available  1
  8- instalar - install aws cli Mac
  9 - inicializar no terminal - aws configure
  10- vamos gerar um user para gerar key e password
  11- vamos em iam - users - add users - escreve um nome -  asco key - next - create group - da o nome busca por sqs e marca os 3 - create group - next tags - next review - create group 
  12- ai foi gerado o acess ket e password
  13- adiciona a acc key no terminal que ta com o AWS Asco key id … 
  A senha que ta do lado
  Região - us-east-1
  Format - json
  
  1.2- Criando uma fila nova pelo terminal : 
    aws sqs create-queue --queue-name MyQueueGabrieli
  15- gerou :
    {
      "QueueUrl": "https://sqs.us-east-1.amazonaws.com/755977887883/MyQueueGabrieli"
  }
  16- fui em sqs para verificar se criou minha fica myqyeyegabrielli - via linha de comando
  17- listar lista de sqs - AWS sqs list-queues
  18- mandar msg do meu terminal pra amazon - aws sqs send-message --message-body="testando 4” --queue-url="https://sqs.us-east-1.amazonaws.com/755977887883/MyQueueGabrieli"
  19- gerou:
    {
      "MD5OfMessageBody": "caa9c8f8620cbb30679026bb6427e11f",
      "MessageId": "3cee14dc-8d77-498b-be9f-8addccec392c"
  }
  20- para receber as msg:
    aws sqs receive-message --queue-url="https://sqs.us-east-1.amazonaws.com/755977887883/MyQueueGabrieli"
  21- para esperar msg - 
    aws sqs receive-message --queue-url="https://sqs.us-east-1.amazonaws.com/755977887883/MyQueueGabrieli" --wait-time-seconds=20
  22- deletar msg pelo terminal - 
    aws sqs delete-message --queue-url="https://sqs.us-east-1.amazonaws.com/755977887883/MyQueueGabrieli" --receipt-handle=“valor que vem do  "ReceiptHandle"
  23- para deletar a fila toda - aws sqs delete-queue --queue-url=“url da fila”
  
    1.3- Utilizando como base o repositorio do Professor, para utilizar o sqs com java:
    
    


2- Compare e descreva as diferenças e o objetivo entre a Amazon SQS e a Amazon SNS.

SNS - é um servico de notificacoes, por exemplo, se algo esta errado, atravez da notificacao conseguimos configurar, tem um baixo custo, gerenciavel pela aws, facil usabilidade, e tem varios endpoints como: email, sms, http, https, sqs, lambda (toma alguma acao) e etc...
SQS - é um servico de fila de mensagens gerenciado, tem tambem um baixo custo, é tambem gerenciavel pela aws, tem a dlq  - fila secundaria para nao perder nenhuma transacao. 

Uma das diferencas é que o sns é global e o sqs é regional. O servico de fila é interessante para armazenar todos os processamentos e executar conforme temos recurso. o servico de fila nao chama o backend diretamente, armazena na fila e pode chamar ou pode ser chamado para executar uma acao. Podemos criar configuracaos de acordo com a fila, gerando novos servidores, que vao ate o servico de fila e gerenciando.
    front - sqs - back
                - back
                - back ...
          
          
          
          
     
