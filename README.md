# Desafio (South System) - Backend Votos

## Texto

No cooperativismo, cada associado possui um voto e as decisões são tomadas em assembleias, por votação. A partir disso, você precisa criar uma solução back-end para gerenciar essas sessões de votação. Essa solução deve ser executada na nuvem e promover as seguintes funcionalidades através de uma API REST:

    Cadastrar uma nova pauta;
    Abrir uma sessão de votação em uma pauta (a sessão de votação deve ficar aberta por um tempo determinado na chamada de abertura ou 1 minuto por default);
    Receber votos dos associados em pautas (os votos são apenas 'Sim'/'Não'. Cada associado é identificado por um id único e pode votar apenas uma vez por pauta);
    Contabilizar os votos e dar o resultado da votação na pauta.

Para fins de exercício, a segurança das interfaces pode ser abstraída e qualquer chamada para as interfaces pode ser considerada como autorizada. A escolha da linguagem, frameworks e bibliotecas é livre (desde que não infrinja direitos de uso).

É importante que as pautas e os votos sejam persistidos e que não sejam perdidos com o restart da aplicação.

## Ferramentas e detalhes

associado tem um voto
assembleia

- FUNCIONALIDADES

  - cadastrar pauta
  - abrir sessao de votacao na pauta (sessao tem tempo informado em sua abertura ou 1 min por default)
  - associado vota apenas 1 vez na pauta ("sim" ou 'nao') e tem um id unico
  - contabilizar os votos e dar resultado da votacao na pauta

- BONUS
  - integracao com sistemas externos:
    - associado pode votar se for feitta integracao com api
    - cpf invalido retorna 404
    - cpf valido retorna 'ABLE_TO_VOTE' ou 'UNABLE_TO_VOTE'
  - mensageria/fila: quando a sessao fechar, poste uma mensagem com o resultado da votacao
  - performance: testes de performance, como sua aplicacao se comporta. cenarios de centenas de milhares de votos.
  - versionamento da api: que estrategia usar?

associado, pauta, sessoes

eslint, prettier, commitzen, (analise de codigo),
0x, autocannon, clinicjs
c4 model, swagger, codigo (nao oq faz, mas porque faz, contexto daquela decisao), estrutura arquivos, fluxos, como executar, como fazer deploy,
over engineering, organizacao do codigo, manutenalibilidade, legibilidade,
tratamento de excecoes e erros
logs
mensagens e organizacao dos commits
breves explicacoes do porque das escolhas tomadas durante o desenvolvimento

integracoes: code climate, new relic, sonarqube, npm audit, snyk,

conhecimento de padroes: design patternns, psr, solid
desacoplar componentes: camadas, service, repository
estruturar pensamento antes de escrever

## Ações (atividades)

Descrição das atividades

- user cria pauta
- user lista pautas
- user cria sessao da pauta e informa seu prazo
- associado vota na sessao
  - envia voto (com cpf)
    - producer recebe a requisicao e cria uma mensagem fila
    - consumer pega a mensagem na fila e processa
      - verifica se a pauta ja fechou
      - verifica se cpf é valido em api externa
      - verifica se o cpf ja esta registrado nas votacoes da pauta
- user lista sessoes
- sessao tem seu prazo terminado
  - schedule

Tecnologias

- nestjs
  - sqs rabbitmq
  - localstack e terraform
  - schedule
