## Monitoramento

O monitoramento de caixa preta faz a testagem do comportamento externo do sistema, assim como o usuário vê. É um método baseado em amostragem, em que se monitora o mesmo sistema que é responsável pelas solicitações dos clientes. Esse monitoramento representa problemas ativos, não previstos, é feito de forma programável e contém um mecanismo de validação. Cada vez que uma sondagem é feita, são armazenados os resultados (aprovado ou com falhas) em relatórios e alertas. Assim, é possível que se faça o diagnóstico de um problema.  
O monitoramento caixa branca é capaz de inspecionar todos os processos internos do sistema, como logs (processos de registros de eventos) ou _endpoints_ _HTTP_ (ponto de extremidade conectado diretamente à rede principal), com instrumentação. Esse monitoramento, portanto, permite a detecção de problemas iminentes, falhas mascaradas por novas tentativas, e assim por diante.

As ***métricas de monitoramento*** variam de acordo com a necessidade particular de cada organização. No geral, mede-se:  
- **Latência**: tempo de execução, espera e resposta de atendimento de uma solicitação.  
- **Tráfego**: medida da carga de trabalho, da demanda que se exige do sistema. Qual é a média de solicitações, tempo e demanda da CPU.  
- **Erros**: mensura as taxas de solicitações com falhas, sejam parciais ou completas.  
- **Saturação**: controle dos recursos que precisam ser mais restritos (controle de memória ou restrição de E/S, por exemplo), medição de carga de trabalho em níveis mais altos (o sistema suporta um tráfego maior?) ou, ainda, identificar a capacidade de armazenamento de um disco.   
- **Disponibilidade de servidores:** quantificar quantos servidores estão ativos ou inativos em uma rede.  
- **Métricas de segurança**: definição dos computadores que estão com softwares antivírus instalados, _patches_ de segurança ativos, checar as intrusões, autenticações e autorizações, entre outras.

Geralmente, ==quando se constrói um sistema de monitoramento do zero, atribui-se a média de latência e o uso médio da CPU, da memória, da capacidade do banco de dados, etc==. São fatores que devem ser prioridades no planejamento das métricas. Com o emprego das métricas, será possível uma otimização que possibilitará que se faça um monitoramento contínuo em vários aspectos. É preciso que sejam feitas configurações, para que o monitoramento seja eficiente. Essas configurações incluem:  
- Fazer alterações no monitoramento da configuração (quantas solicitações de _pull request_ ou alterações por semana são feitas no repositório que contém a configuração de monitoramento?).  
- Ter controle dos falsos positivos (alertas que foram dados, mas que não ajudaram a prever falhas e precisam ser excluídos) e dos falsos negativos (falhas que aconteceram, mas que não foram alertadas).  
- Criar, confirmar e silenciar alertas.  
- Configurar a usabilidade dos alertas, _runbooks_ e painéis, para que seja compreensível por todos da equipe (GOOGLE CLOUD, 2021).

### Ferramentas de configurações para monitoramentos de SO e servidores  

Existem várias ferramentas de monitoramento no mercado. Essas ferramentas são responsáveis por analisar a funcionalidade de um sistema, gerar relatórios, apresentar alertas, ou seja, identificar problemas. Algumas têm, também, o caráter de monitoramento técnico, que se preocupa com a integridade do hardware ou dos sistemas. Algumas das ferramentas mais populares são: Remote network monitoring MIB (Rmon), OpenNMS, Cacti, Nagios, Tripwire e Zabbix.
Com a cultura DevOps, a utilização de uma ferramenta como o Zabbix e outras aqui citadas pode parecer desnecessária, no entanto o Zabbix traz, em sua proposta, uma ferramenta centralizada. Ao invés de trabalhar com várias ferramentas, o ideal é integrar todas elas e fazer com que todos os alertas sejam disparados por uma única.

>Na prática, os produtos são capazes de simplificar o monitoramento de eventos, mandando alertas somente do que realmente importa; detectam e respondem anomalias e atividades suspeitas; têm um pacote de segurança para ameaças internas; auditoria de usuários; autenticação; detecção de DoS; detecção de violação e de intrusão; filtram os dados relevantes; apresentam uma visibilidade completa dos ativos da rede; gerenciam as alterações e os _logs_ de eventos; detectam os desvios na linha de base segura; entre outras vantagens

### Monitoramento com foco nas práticas contemporâneas

- Prometheus: é uma ferramenta de monitoramento que, como as demais, agrega métricas, avalia expressões, mostra os resultados e gerencia alertas. Sua vantagem sobre as outras é que se trata de um sistema adaptável tanto para monitoração de arquiteturas centralizadas como para arquiteturas orientadas a serviços altamente dinâmicos.   
- Graphite: monitora tanto infraestruturas simples como em nuvens, assim como o desempenho de sites, aplicativos, serviços de negócios e servidores em rede. Com seu uso, tornou-se fácil armazenar, recuperar, compartilhar e visualizar dados de séries temporais.  
	- Comparado ao Prometheus, o Graphite é uma ferramenta com tarefas mais simples. Não coleta dados, seu modelo de dados é menos detalhado, os dados armazenados não podem ser configurados com o tempo que persistirão no disco e não suporta gerenciamento de alertas (BERMAN, 2020).  
- InfluxDB: executa análises para obter detecções e resoluções mais rápidas; configura alertas ou detecções de anomalias; faz ingestão de métricas, eventos e logs em um banco de dados de série temporal de alto desempenho; projetado para lidar com grandes volumes e várias fontes de dados.  
- Elastic Stack: o acrônico ELK surgiu como um projeto OpenSource que reunia três ferramentas: Elasticksearch, Logstash e Kibana. Com o aumento desses projetos, uma nova ferramenta foi inserida, a Beats, o que fez com que surgisse a ferramenta Elastic Stack e os projetos ficassem independentes. Assim, o Elastic Stack se tornou uma solução de monitoramento de aplicação, infraestrutura, análise de logs e segurança integrada, avançada e cheia de possiblidades   
- Logstash: é um pipeline que, de forma dinâmica, faz ingestão, transformação e envio de dados.   
- Kibana: é um visualizador de dados do Elasticksearch e do Elastic Stack. Com ele, você pode criar visualizações interativas, simples e intuitivas e criar dashboards com gráficos, mapas e filtros.  
- Fluentd: é um coletor de dados, também de código aberto, que possibilita a unificação da coleta e do consumo dos dados, melhorando o uso e a compreensão desses dados.   
- Grafana: é uma das ferramentas mais simples para observar métricas (Prometheus e Grafite), _logs_ e _traces_. Com o uso de agentes e integrações, ele monitora o sistema, define regras para alertas e notificações, agenda silêncios, entre outras funções.  
- FogMon: é uma ferramenta leve para monitoramento distribuído. Criada para ser executada em infraestruturas heterogêneas entre _cloud_ e _edge_, no entanto Correia (2019), em estudo de caso, constatou que as soluções que tiram proveito apenas da _cloud_ dispõem de recursos ilimitados, contudo apresentam resultados de latência elevada e congestão na rede. E as soluções orientadas apenas para a perspectiva da _edge_ podem não satisfazer os requisitos da aplicação, dada a instabilidade que apresentam em termos de recursos e falhas. A _FogMon_ foi escrita em C++ e tem uma arquitetura de duas camadas _peer-to-peer_. Opera com dois agentes de software: _followers_ ou _leaders_. Os _leaders_ monitoram os nós e agregam periodicamente os dados que os _followers_ recolhem.   
- _FMonE_: criada com foco em infraestruturas fog, ou seja, o processamento acontece no hub de dados ou em um roteador ou gateway, reduzindo a quantidade de dados enviados para a nuvem. Essa ferramenta contempla as principais características de sistemas com essa infraestrutura, que são: heterogeneidade, mobilidade, conectividade e distribuição geográfica, apresentando requisitos fundamentais, como: não necessidade de instalações, agregação e filtragem de métricas, _back-end_ flexível, elasticidade, resiliência, atenção nas localizações, monitoração de _plugins_, agnóstico no hardware e sistema operativo (CORREIA, 2019).  

E não esgotamos aqui as ferramentas de monitoramento, podemos citar Data Dog, New Relic, Elastic APM, Dinatrace, Graylog, Sentry, Alertmanager, Pagerduty e muitas outras amplamente trabalhadas no mundo DevOps. Existem ferramentas para cada realidade de monitoramento e de infraestrutura.  

As métricas e ferramentas de monitoração diferirão de acordo com a necessidade de cada empresa (cliente), mas, com a dinâmica e a importância dos computadores nos negócios de qualquer empresa, é imprescindível que se utilize da monitoração, seja para controle de infraestrutura, de aplicações ou até de negócios. Com o monitoramento, os mecanismos de notificações e os alertas, é possível perceber tudo o que está acontecendo na rede. Assim, é plausível projetar sistemas que fiquem disponíveis 24 horas, tomar decisões quando houver necessidade de aumento de escala, fazer backups seguros, monitorar unidades remotas e ambientes de virtualização, garantir a segurança dos seus ativos, usar dashboards para visualizar dados de forma mais eficiente e se adequar de forma flexível às mudanças, sempre presentes, nos processos tecnológicos.  

## Integração Contínua (CI)

>A integração contínua é uma prática de desenvolvimento de software em que os membros de uma equipe integram seu trabalho com frequência, geralmente cada pessoa se integra pelo menos diariamente - levando a várias integrações por dia. Cada integração é verificada por um build automatizado (incluindo teste) para detectar erros de integração o mais rápido possível.
>(FOWLER, 2006, [s. p.])

Para que exista integração contínua, não é obrigatório o uso de ferramentas, porém essas integrações entre os vários desenvolvedores podem gerar conflitos no código e, para evitar isso, utilizam-se amplamente as ***ferramentas de controle de versões*** (**SCM**), como CVS, SVN e Git – o mais utilizado hoje em dia.  
Para resumir em uma frase simples, a integração contínua é a etapa em que várias pessoas diferentes geram códigos, os quais, depois, são mesclados em um código único, gerando, assim. a possibilidade de um trabalho descentralizado e focado entre vários colaboradores.

## Entrega Contínua e Implantação Contínua (C/D)

No caso do termo C/D, ele assume duas abordagens: 
- _Continuos Delivery_, ou entrega contínua, seria quando o código está integrado o suficiente, maduro e testado, e é liberada uma versão (_release_) segura para implantação do software para a produção, mas necessita de uma aprovação para que isso ocorra;
-  *Continuos Deployment*, ou implantação contínua, seria a automação de todo o processo de entrega desse software em produção, sem interação ou aprovação.

>Cuidado, pois existe muita confusão com os termos _Continuos Delivery_ (Entrega Contínua) e _Continuos Deployment_ (Implantação Contínua). Se você configurou sua pipeline para usar o código integrado nos estágios anteriores, testou e criou uma versão pronta para a produção, mas não aplica em produção de maneira automatizada, ou necessita de alguma aprovação para fazê-lo, você não tem _Continuos Deployment_ configurado na sua pipeline.

## SCM Git

Ver pasta Git

### Hospedagem centralizada de código-fonte

- **GitHub**: é um repositório e, ao mesmo tempo, uma rede social, o qual permite que qualquer pessoa possa enviar seu código para ele usando o Git, e ficará disponível para toda a comunidade. O GitHub foi concebido seguindo os princípios do Open Source, ou código aberto, que, basicamente, enfatiza a colaboração da comunidade e a liberdade de compartilhar o código com todos. Porém, muitas vezes, você não pode compartilhar o código da sua aplicação assim e precisa de um repositório privado, para isso, o GitHub tem um serviço pago, que permite que você crie seus códigos e controle o acesso a eles.
- **BitBucket**: permite que você crie até cinco repositórios privados por projeto na conta gratuita.
- **GitLab**: Com sua versão “Community”, permite que você instale localmente um servidor de SCM e de CI, sendo uma grande opção para quem deseja ter uma ferramenta de CI completa e repositórios privados.

# Hospedar uma API usando docker

## Containers 

O contêiner é, de maneira simplificada, uma forma de isolarmos o hardware no qual rodaremos nossa aplicação, tornando o software e seu ambiente o mais abstraído possível. Para isso, o contêiner usa de isolamento de recursos do sistema operacional (SO) e do hardware (GARCIA; PEREIRA, 2019), fazendo com que o hardware em si seja apenas um transportador de uma aplicação, não influindo nela.

>Um container Linux é um conjunto de processos isolados do SO que executam um ou mais serviços exclusivos em diversos ambientes diferentes (GARCIA; PEREIRA, 2019).

## Passo a passo para hospedar uma API usando Docker

1. **Instalar o Docker**
    - Baixe e instale o Docker em sua máquina.
    - Certifique-se de que o Docker está funcionando corretamente executando `docker --version` no terminal.

2. **Criar ou obter o código da API**
    - Certifique-se de que sua API esteja funcionando localmente.
    - Exemplo: um servidor Node.js com Express.

3. **Criar um arquivo `Dockerfile` no diretório do projeto**  
    Este arquivo define como a API será empacotada em um contêiner. Exemplo para Node.js:
    
    ```dockerfile
    # Use uma imagem base do Node.js
    FROM node:16
    
    # Defina o diretório de trabalho dentro do contêiner
    WORKDIR /app
    
    # Copie os arquivos necessários
    COPY package*.json ./
    RUN npm install
    
    # Copie o restante do código
    COPY . .
    
    # Exponha a porta usada pela API
    EXPOSE 3000
    
    # Comando para iniciar a API
    CMD ["npm", "start"]
    ```

4. **Criar o arquivo `.dockerignore` (opcional)**  
    Exclua arquivos desnecessários no contêiner para torná-lo mais leve. Exemplo:
    
    ```
    node_modules
    .env
    .git
    ```
    
5. **Construir a imagem Docker**  
    No terminal, execute:
    
    ```bash
    docker build -t minha-api .
    ```
    
    - `-t minha-api`: Nome da imagem.
    - O ponto (`.`) indica o diretório atual.

6. **Executar o contêiner Docker**  
    Inicie o contêiner com a API:
    
    ```bash
    docker run -d -p 3000:3000 minha-api
    ```
    
    - `-d`: Executa em modo "detached" (segundo plano).
    - `-p 3000:3000`: Mapeia a porta local (3000) para a porta do contêiner.
  
7. **Testar a API hospedada**
    - Acesse a API pelo navegador ou com ferramentas como Postman em:
        
    ```
    http://localhost:3000
    ```

8. **Publicar a imagem (opcional)**
    - Caso queira disponibilizar sua API, publique no **Docker Hub**:
        ```bash
        docker login
        docker tag minha-api meu-usuario/minha-api
        docker push meu-usuario/minha-api
        ```
        
    - Assim, qualquer pessoa pode rodar sua API com `docker pull`.
  
9. **Opcional: Usar `docker-compose` para ambientes complexos**  
    Crie um arquivo `docker-compose.yml` para gerenciar dependências (banco de dados, por exemplo).

10. **Hospedar em um servidor remoto (opcional)**
    - Use plataformas como AWS, DigitalOcean ou Heroku.
    - Configure o Docker no servidor remoto e execute os comandos acima para hospedar a API online.

## Ambiente de homologação

A homologação é uma forma de se garantir que a versão que será enviada para a produção é exatamente o que foi desenvolvido e que nada está falhando. Além de validar se todas as funcionalidades desenvolvidas funcionam corretamente (SALVADOR, 2015).

Nesse passo, podemos criar um item a mais na nossa pipeline, que enviará aquela versão ao ambiente de homologação e executará sua aplicação para rodar uma bateria de testes, validando se o que foi desenvolvido não “quebrou” a aplicação e é exatamente o que se pretendia fazer.  
Claro que, como estamos falando de construção de infraestrutura como código, precisamos codificá-la e criar uma infraestrutura semelhante à de produção, para simularmos que a nossa aplicação está funcionando corretamente.

Logo, criamos uma integração com o repositório centralizado da nossa aplicação, construímos um CI que realiza uma configuração na aplicação, para que ela possa ser disponibilizada em produção, e criamos um ambiente de testes simulando exatamente o de produção.  
Poderíamos incluir um ambiente de testes automatizados, scanners de vulnerabilidade e o _deployment_ da aplicação em produção, formando, assim, o CD (_Continuos Deployment_), e teríamos um ambiente de CI/CD completo, porém o que fizemos mostra como podemos integrar o código da nossa infraestrutura ágil, usando o Terraform com o código da aplicação em si, cumprindo um ambiente de DevOps mínimo.  
Como mencionado, não existe uma fórmula para a criação das ferramentas utilizadas, isso deve ser decidido em reunião das partes envolvidas, levando os conceitos de integração e colaboração pregados pelo DevOps como premissas, pois ninguém melhor para dizer qual tecnologia usar do que todos os envolvidos, desde a área de desenvolvimento até a de operações, resolvendo o que é melhor para o uso dentro dos requisitos exigidos.

### Passos na implantação do DevOps:

- **Criação dos ambientes**: não podemos esperar semanas ou meses para termos ambientes criados tanto para testes quanto para a produção, precisamos agilizar esse processo o máximo possível.  
- **Instalação do código**: da mesma forma que o item anterior, para termos agilidade na instalação da aplicação ( _deployment_ ), não podemos depender de centenas de ações manuais e correções de configuração para só então termos a aplicação utilizável e testável em produção. Precisamos tornar a instalação o menos dependente possível do software e com menos manipulações de configuração do ambiente de testes para o de produção. Dessa forma, temos que ter um entregável ( _package_ ) da aplicação, já pronta em homologação, para ser utilizável em produção.
- **Testes na aplicação**: claro que nenhum dos itens citados funcionará como o esperado se, antes de aplicarmos em produção, não testarmos para garantir que o código que está sendo instalado em produção é confiável e não permitirá que problemas graves sejam entregues ao cliente final, gerando prejuízos financeiros e de imagem à empresa. Para que isso também não seja um impedimento das entregas, todo o processo deve ser automatizado.  
- **Arquitetura da aplicação**: não podemos esquecer que construir aplicações que possibilitem atualizações frequentes não podem ser construídos como serviços únicos, não permitindo que sejam feitas adequações em sua arquitetura, por serem grandes monolitos, em que qualquer leve alteração pode causar uma falha sistêmica. Por isso, a adoção de microsserviços no DevOps é praticamente unânime atualmente.

## Técnicas para implantação em produção

**_Roll Deployments_**: essas implantações são as mais simples de se usar, pois, basicamente, apenas se preocupam com o _downtime_ da aplicação. Nelas, a nova versão da aplicação é implantada, mas a antiga ainda convive no ambiente e vai sendo “rolada” para fora do ambiente à medida que as cópias da nova versão são implementadas com sucesso. Importante dizer que isso é feito de maneira automática. 

Os sistemas e as ferramentas, quando configurados para isso, conseguem avaliar se a versão nova é estável e trocará automaticamente a versão antiga pela nova, até que todas as cópias da aplicação sejam da nova versão. Isso faz com que os usuários não percebam a mudança, pois, mesmo que eles acessem a aplicação durante a rolagem, ainda receberão a resposta de uma aplicação, seja da cópia antiga ou da nova.

**_Blue-green Deployments_**: esse tipo de implantação já se preocupa em avaliar a resposta da aplicação durante um tempo para verificar se a nova versão se mantém estável e pode substituir por completo a antiga. Para isso, implanta-se a versão nova, e ela convive com a antiga o tempo todo. Diferente da técnica de “roll”, ela não retira as versões antigas, mantém as duas e usa um balanceador de carga (_Load Balancer_), que direcionará alguns usuários para o deploy antigo “azul” e outros para o “verde”, até que a equipe avalie se mantém a nova ou a antiga.

**_Canary Deployments_**: a implantação canário é a mais avançada de todas, pois ela é uma melhoria da _Blue-green_, permitindo um controle de quantos usuários utilizarão a versão nova e quantos utilizarão a antiga. Por exemplo, 30% receberão a cópia nova da aplicação, e 70%, a cópia da antiga. Ao avaliar se a resposta é positiva para uma parcela dos usuários, pode-se estender a versão nova para o restante. Ainda dentro dessa abordagem, em um controle maior, pode-se liberar uma versão da aplicação baseada no próprio usuário, como liberar 25% para mulheres entre 20 e 30 anos, por exemplo. Isso permite um controle da implantação a nível de experiência do usuário. Também, por ser a mais avançada, tem um nível de complexidade de configuração das ferramentas mais alto.

# _Rollback_ e _Rollforward_

_Rollback_ é um nome em inglês que significa retorno ao estado anterior da aplicação, e _rollforward_ seria aplicar uma correção, mas não retomar à versão anterior, apenas criar a correção da falha e aplicar outra versão já com a correção.

---

# Monitoramento de Serviços

Existem diversos tipos de monitoramento, para diversos tipos de abordagens e ambientes, por isso, precisamos verificar quais são ideais para cada tipo de infraestrutura e arquitetura de sistemas utilizada.  
Importante, também, escolher o que monitorar, já que existem diversos itens que podem ser utilizados como métricas. Devemos saber quais utilizar, tendo em mente como fazer uma separação inteligente, que traga assertividade ao monitoramento.  
E aliado a todo esse sistema devemos pensar em criar alertas, que nos avisarão em caso de falhas, e definir as políticas deles, para que possamos atingir os objetivos de sermos avisados somente se um item crítico ao funcionamento das aplicações estiver com problema e evitar o envio excessivo de alertas, com coisas banais misturadas a informações críticas, causando um efeito indesejado de recebermos alertas demais e não conseguirmos diferenciar o que é crítico do que não é.

## Métricas

O surgimento do DevOps está intrinsicamente ligado ao advento da computação em nuvem (_cloud computing_), porém não é exclusivo dela. Uma empresa pode muito bem possuir sua infraestrutura interna, conhecida como _on-premises_, e ainda utilizar a cultura DevOps. Atualmente, muitas empresas adotaram o modelo híbrido, em que parte da infra está no _on-premises_ e parte está no _cloud computing_.  
Todas essas abordagens têm suas diferenças, vejamos algumas. Quando monitoramos infra _on-premises_, nos preocupamos muito com a parte física de cada equipamento e servidor. Portanto, devemos nos preocupar com itens, como:

- **Uso de CPU e memória**: não devemos deixar que os aplicativos esgotem todo o recurso computacional dos servidores antes de tomarmos uma ação.   
- **Espaço disponível em disco**: temos que saber preventivamente se um disco está ficando cheio, pois isso pode causar a parada de todo o ambiente.  
- **Disponibilidade de componentes de rede**: _switches_ e _firewalls_ podem falhar e, se isso acontecer, temos que ter uma forma de contornar o problema rapidamente. Porém, isso só será possível se tivermos um monitoramento nesses equipamentos para saber quando eles vierem a falhar.

Um outro conceito que alterou também a maneira como o monitoramento é feito é a arquitetura de microsserviço. Antigamente, os sistemas eram construídos de maneira única, provendo todos em um único serviço no final. Agora, o conceito mais utilizado é o de separar a aplicação em pequenos serviços, como na Figura 2.33, cada um com uma função, e eles se falarão internamente para prover a resposta ao usuário

![[Pasted image 20241128112709.png#center|600]]

### Monitorando *logs*

Todo e qualquer sistema gera informações sobre seu funcionamento, que são utilizadas pelos times de operações como uma poderosa ferramenta. São os chamados _logs_, os quais fornecem pistas sobre um possível problema com algum sistema inoperante. Para isso, os sistemas de logs, geralmente, fornecem uma saída padrão, em arquivo de texto, com tudo que o sistema fez ao iniciar, seja de sucesso ou erro. Esse arquivo é consultado como uma forma de encontrar pistas sobre os problemas.

Um bom sistema de monitoramento inclui gerenciar esses logs em um local único para centralizar a análise, fazer correlações de problemas com outros sistemas e possibilitar encontrar falhas relacionadas.

### Monitorando aplicações

as aplicações, hoje, rodam, basicamente, com arquitetura de microsserviços, que faz com o que a monitoração tradicional seja alterada para uma que consiga analisar traços e relacionamentos internos que uma aplicação faz.  
Por isso, surgiram ferramentas chamadas de _Application Performance Monitoring_ (**APM**), ou Monitoramento de Performance de Aplicação. Elas fornecem uma gama de visualizações e interações entre as aplicações internas, capazes de monitorar quanto tempo uma determinada ação dentro de sistema está levando, quais classes e itens são chamados internamente, etc. As ferramentas de APM são o que há de mais avançado dentro do conceito de monitoramento.

### Alertas  

Fechando todo o ciclo de monitoração, temos o sistema de alertas, que serve, basicamente, para informar quando um item do monitoramento estiver com problemas e fora dos parâmetros considerados normais. Devemos configurar os limites previamente para que o sistema saiba quando é considerado um problema ou não.

>==Importante==: métricas são os itens usados para criar as regras de alerta, como a quantidade de uso de CPU de um servidor, mas o limite (*threshold*) é o analista que configura caso a caso. Portanto, podemos ter diferentes métricas em casos de alertas diferentes.

### Observabilidade vs Monitoramento

Diante desse cenário de microsserviços, surge um debate sobre o monitoramento já não ser mais suficiente para atingir o objetivo de prever falhas. Surge, então, o termo “observabilidade”, que propõe usar os monitoramentos para identificar e depurar, dentro dos microsserviços, as possíveis falhas e problemas.
O sistema de monitoramento deve responder a duas perguntas:   
1.  O que está quebrado?   
2.  Por quê?

Ao combinar itens, como inspeção de sistemas com depuração de aplicação, infraestrutura, exceções e travamentos e inspeção de tráfegos, temos uma visão holística do todo.A observabilidade em si não significa um monitoramento melhorado, mas uma combinação de elementos monitorados que, juntos, podem trazer uma visão mais completa do todo, um complementa o outro. Ela é uma capacidade de entender os estados internos dos sistemas, ou seja, você usa as saídas do monitoramento e consegue extrair deles as informações que ajudam a melhorar os sistemas como um todo e, para isso, você precisa conhecer muito bem o que deveria ser a resposta aceitável e o que não está bem e pode ser melhorado.   
Podemos dizer que a observabilidade é como unificar as visões, tanto das aplicações e do negócio quanto da infraestrutura e das operações (Figura 2.39), como na ideia de unificação do time de Dev e Operações pregada pelo DevOps.

### Malha de serviços

Ele ajuda muito a monitorar e encontrar defeitos não tão aparentes como em outros sistemas de monitoramento. Para sermos completos com o termo, o _Service Mesh_ em si não é apenas para monitoramento, ele é usado como uma forma de **controle granular** dos microsserviços, como fazer _deployment_ canário e _blue/green_.

---

# Containers

Muitos confundem os containers com máquinas virtuais, no entanto, eles não funcionam tal qual a virtualização que conhecemos. Uma das diferenças é que o container compartilha o mesmo Kernel do Sistema Operacional. Em um sistema como o Linux, por exemplo, a modularidade característica de seu Kernel permite provisionamentos de sistemas mais enxutos e com economia de recursos.  

Ou seja, “***containers têm recursos isolados de CPU, memória e rede enquanto compartilham o kernel do sistema operacional. Eles hospedam código-fonte, ferramentas de sistema e bibliotecas***. Diferem-se de formas específicas das máquinas virtuais (VMs), mas podemos pensar neles como iterações leves de VMs”

Outra diferença é a forma como ele pode ser **provisionado**. Em uma máquina virtual você pode criar um ambiente que pode se valer de várias ferramentas (PHP, MSQL, Apache, dentre outros), tudo rodando no mesmo SO; já os containers *assumem apenas uma função*, isolando os processos de cada ferramenta. A vantagem é que facilita bastante a escalabilidade, consequentemente, a performance e flexibilidade dos processos.

>Quando estamos utilizando máquinas virtuais, nós emulamos um novo sistema operacional e todo o seu hardware utilizando mais recursos da máquina host, o que não ocorre quando utilizamos containers, pois os recursos são compartilhados. O ganho óbvio disso é a capacidade de rodar mais containers em um único host, se comparado com a quantidade que se conseguiria com máquinas virtuais.    
  (VITALINO; CASTRO, 2016, p. 13)

### Container vs Docker

São conceitos diferentes, o container é um ambiente isolado, o Docker é uma plataforma de implementação de containers que usa um esquema de camadas, montadas a partir das técnicas de Copy-On-Write, que é um procedimento que permite compartilhar dados entre camadas, mas só é possível alocar um novo recurso a partir do momento em que esteja modificado. Na prática, funciona assim: a cópia de um arquivo é mandada para uma camada superior, são visualizadas somente as informações modificadas dessa camada, no entanto, o arquivo original permanece em uma camada inferior e pode ser visualizado, caso se exclua a camada sobreposta.

### Kubernetes (K8S)

É um sistema open source de orquestração de containers que automatiza deploy, facilita o escalonamento e gerencia aplicações. Dentre as suas muitas características destaca-se a capacidade de trabalhar com atualizações diversas nas aplicações. Ele permite que se altere novos releases da aplicação com muito mais frequência e de forma automática. Com o Kubernetes é possível agendar a implantação de uma versão nova e, se ocorrer problema, reverter tudo de forma automática, sem comprometer a disponibilidade da aplicação.   
No Kubernetes, vários containers rodam em uma única aplicação, balanceando de acordo com as requisições. Na prática, uma aplicação pode aumentar rapidamente e exponencialmente a sua capacidade.

Com o Kubernetes é possível que se faça implantações e atualizações de forma rápida e a todo instante. Passar de um container para vários rapidamente, o que chamamos de *escalonamento dinâmico*. Também conta com uma busca de dispositivos e serviços de forma automática (*Service Discovery*), faz o *balanceamento de carga* e, se associado a uma malha de serviço no cluster, como o *Istio*, pode interromper a comunicação entre front-end e back-end se uma falha for detectada no back-end (*circuit breaker*), dentre outros serviços.

Dentre os principais **benefícios** em usar o kubernetes destacam-se: a automatização de implantações e atualizações de aplicações; a facilidade para escalonar aplicativos em containers; a capacidade de operar containers em diferentes hosts; a otimização do uso do hardware, reduzindo custos e o suporte de carga para diversas aplicações.

#### Docker Swarm  

O orquestrador já vem instalado com o Docker e permite a construção de clusters de containers de forma nativa, usando balanceamento de carga (*loadbalancer*) e *failover*. Você cria clusters facilmente indicando os hosts que serão supervisionados; quando criar um novo container, por conta do balanceamento de carga, ele direcionará ao host que possuir a menor carga. “A estrutura se resume em um manager e diversos _workers_. O _manager_ orquestra os containeres e distribui em hosts workers, os workers hospedam o container” (VITALINO; CASTRO, 2016).  
Docker Swarm é, portanto, outra forma de orquestrar seus containers através da criação de um cluster com alta disponibilidade, balanceamento de carga e comunicação criptografada, tudo isso nativo, sem esforço e dificuldade.

#### Docker EE (Enterprise Edition)  

Embora o Docker Swarm seja também um orquestrador, o Docker EE atenderá melhor a demanda do mundo corporativo com mais eficiência e velocidade. Isso acontece por conta da solução *Docker Universal Control Plane* (**UCP**), que auxilia no gerenciamento de inúmeros clusters e aplicativos por meio de uma interface simples. Dentre as tarefas do Docker EE estão: analisar as imagens nos repositórios para verificar se estão livres de vulnerabilidades, conectar os containers a volumes, administrar a maneira com os containers se comunicam entre si e externamente, controlar a autenticidade dos usuários, fazer registros das imagens, etc. (FREITAS, 2021).
### OpenShift  

É uma plataforma de gerenciamento e orquestração de containers que faz monitoramento, automação, gera relatórios e integração com outras ferramentas. Foi desenvolvida pela Red Hat, uma empresa especialista nesse mercado, que oferece também a versão Enterprise do produto, o *Red Hat OpenShift Container Platform*, que tem as mesmas funções, mas para grande escala e maior segurança. Dentre as suas características estão: desenvolvimento, hospedagem, escalonamento e entrega de aplicações ágeis na nuvem, redução de burocracia, criação de ambientes de testes, elevação do poder de processamento dos servidores da empresa, melhor aproveitamento dos recursos computacionais, redução de custos, flexibilidade aos sistemas, etc. (EVEO, 2017). 

### Replicação e padronização de containers Dockers

Containers Dockers permitem a padronização e facilitam a replicação de suas imagens. Uma vez que essas imagens são construídas por meio de arquivos de definição, já se tem um determinado padrão. Assim, facilita o escalonamento da estrutura, utilizando replicações dessa imagem.

Passos para criar um arquivo Dockerfile para o Apache:

```dockerfile title:"Criando um Dockerfile"
#mkdir /root/dockerfile

#cd /root/docekerfile
#mkdir apache
#cd apache

#vim Dockerfile
FROM debian
RUN apt-get update && apt-get install -y apache2 && apt-get clean
ENV APACHE_LOCK_DIR=“/var/lock”
ENV APACHE_PID_FILE=“/var/run/apache2.pid”
ENV APACHE_RUN_USER=“www-data”
ENV APACHE_RUN_GROUP=“www-data”
ENV APACHE_LOG_DIR=“/var/log/apache2”
LABEL description=“Webserver”
VOLUME /var/www/html/
EXPOSE 80
```

#### Significado das linhas de comandos:

**FROM**: Indica a imagem que serviu de base. Caso o propósito fosse servir uma aplicação Java, por exemplo, poderíamos criar uma imagem para que, quando fôssemos rodar o container, seria a própria aplicação JAVA. Nesse caso, o mínimo que precisaríamos ter era um sistema operacional com um JDK instalado. No FROM podemos pesquisar uma imagem que tenha as configurações que precisamos.

**RUN**: é a lista dos comandos que devem ser executados na criação da imagem (a criação de uma camada nova no container).
- `apt-get update`: fará com que ele pegue os pacotes mais recentes do repositório.  
- `&& apt-get install -y`: o parâmetro -y fará com que, no momento da construção da imagem, tudo aconteça de forma automática, sem a necessidade de nenhuma confirmação sua. No caso, o “y” é o yes, já informando que a instalação pode ser feita sem precisar confirmar.  
- `&& apt-get clean`: Ele vai limpar tudo o que foi utilizado para a instalação.

**ENV**: É a definição das variáveis do ambiente. As variáveis que usamos são variáveis do Apache, usadas para que funcione perfeitamente dentro do container, ou seja, essas variáveis diferem em cada tipo de aplicação usada.  

**LABEL**: Adiciona uma metadata à imagem, como descrição, versão, etc.  

**VOLUME**: Define um volume a ser montado no container. No nosso exemplo, é o local dos arquivos do nosso site; no Debian, os arquivos ficam nesse diretório informado acima.   

**EXPOSE**: é a porta onde o container se comunica; 80 é a porta do webservice.

Depois de criado o arquivo, basta construir a imagem, certifique-se de que você está no mesmo diretório onde foi criada a imagem e digite o comando:  

```script
#docker build -t teste:1.0.
```

O parâmetro -t serve para definir o nome da versão do container que estamos criando. O nome pode ser qualquer um.  
Para executar o container utilizando a imagem, digite:  

```
#docker container run -ti teste/:1.0
```

Caso você queira usar uma imagem armazenada no repositório Docker Hub, o comando é:

```
docker pull (nome da imagem)
```

Se fizermos um teste com uma imagem: “Hello World”, digitaríamos assim:

```
docker pull hello-world
```

Para abrir a imagem, o comando é:

```
docker run hello-world
```

---

# Monitoramento de Containers

A partir do momento em que aumenta a quantidade de containers implantados, aumenta também a dificuldade em os monitorar. Quando levamos essa problemática para as nuvens, nuvens híbridas, por exemplo, nas quais os containers aparecem tanto em nuvens públicas como privadas, o monitoramento fica ainda mais comprometido. Mas o fato é que o monitoramento de containers não deve ser menosprezado, é imprescindível que se crie formas de analisar, localizar erros e tomar decisões a partir de eventos gerados pelos containers.

Plataformas como o Docker, por exemplo, que operam por meio de camadas, permitem com facilidade na movimentação e dimensionamento dos containers, o que é ótimo para os desenvolvedores, mas um problema para gerenciar o que está acontecendo.

O monitoramento de containers, portanto, consiste em: 
- Identificar em quais hosts os containers estão executando; 
- Isolar containers que apresentam problemas para corrigi-los; 
- Detalhar e controlar o consumo de memória do servidor; 
- Quantificar o número total de containers e os que estão ativos; 
- Investigar os detalhes de cada container a fim de analisar o seu desempenho; 
- Acompanhar, distribuir ou restringir a quantidade usada de CPU; 
- Apurar problemas de comunicação e troca de recursos, analisando o tráfego de rede; 
- Rastrear métricas de desempenho; 
- Identificar problemas no desempenho, implementar soluções e fazer análises periódicas de desempenho que possam ajudar a prever tendências.

## Ambiente e Infraestrutura de Containers

A transformação digital pressionou as empresas a encararem mudanças em sua infraestrutura. Passou-se a tratar a **infraestrutura como código**, o que possibilitou a redução de gastos e velocidade na entrega dos produtos. *Um ambiente gerido de forma correta possibilita a testagem de softwares com mais facilidade e, assim, implantações estáveis e que podem ser reaproveitadas*.

No hardware as infraestruturas modernas passaram a virtualizar as máquinas físicas, tendo reduções consideráveis com gastos na compra de equipamentos. Com a infraestrutura de nuvem pública, passou-se a terceirizar a manutenção e o provisionamento de servidores e redes, um ganho de tempo incomparável a o que se tinha antes, quando era necessário aguardar semanas para um novo servidor ser provisionado para continuar um projeto.

No software, evidencia-se uma transição de construções monolíticas para o desmembramento em camadas, o que impulsionou arquiteturas orientadas por serviços (SOAs, *Service Oriented Architectures*), tipo de design que permite que seus componentes sejam reutilizáveis através de uma interface de compartilhamento em rede; as SOAs, por sua vez, evoluíram para serviços Web, arquiteturas orientadas por eventos e para os microsserviços, que dominam as estratégias de implementação para aplicações no mercado de desenvolvimento de software atualmente (MAZMANOV, 2020).

## Métricas e verificações de integridade

Os endpoints de métricas dos containers não são estáticos.  O uso de um serviço Kubernetes não forneceria endpoints eficientes, pois são necessárias estatísticas mais concentradas em containers separados, em vez de agrupados.

Outro problema de monitoramento de containers são as verificações de integridade. Os endpoints de integridade implantados de maneira tradicional costumam ter endereços de rede **estáticos**, quando os containers são programados para execuções **dinâmicas** nos nós.
Uma solução poderia ser o Kubernetes, que monitora todos os containers no cluster e responde as verificações de integridade implantadas, excluindo e reiniciando os pods.

> Exemplificando: “A instrumentação da verificação de integridade proporciona diversos níveis de eficácia. Por exemplo, uma aplicação pode expor um controlador isolado que retorna um código de resposta HTTP 200 ao ser chamado. Essa verificação de integridade é útil em muitos casos, mas é capaz de detectar apenas determinados tipos de problemas. Se a conexão de uma aplicação com o banco de dados não for íntegra, uma verificação superficial no endpoint provavelmente não detectará esse problema” (GORDON, 2018, p. 3).

---

# Inf. Ág em Cloud e Escalonamento automático

Cloud Computing não substitui o DevOps. Embora tenham características similares, o DevOps está mais ligado a pessoas e processos, e a Cloud aos recursos disponíveis para facilitar as práticas.

Tem como principal característica evitar a dependência de um único recurso de hardware (que pode ficar obsoleto), facilitando a prospecção de recursos computacionais que podem ser acessados de forma online através da Internet.

A Computação em Nuvens surge a partir dos estudos sobre virtualização de servidores, softwares orientados a serviços e gestões de grandes instalações, como Data Centers. Esse modelo eficaz utiliza-se de softwares, acessos, armazenamentos e processos de dados em meio a diferentes dispositivos e tecnologias Web (RODRIGUES; GALDINO; NETO, 2019).

A Computação em Nuvens traz diversos benefícios para as empresas, dentre eles, destacamos: a redução de custos, maior produtividade, competitividade, mobilidade, disponibilidade e escalabilidade. Essas, por sua vez, são também características das infraestruturas ágeis.
Os serviços de computação na nuvem são divididos em três classes, que levam em consideração o nível de abstração do recurso provido e o modelo de serviço do provedor:
- **Infraestrutura como um serviço** - IasS: é um modelo no qual as partes referentes aos servidores, processamentos e memórias são oferecidas por um provedor que possibilita ao cliente um mecanismo de virtualização que tem controle sobre máquinas virtuais, armazenamento, aplicações instaladas e um controle limitado dos recursos de rede. Assim, o usuário não precisa adquirir hardware e softwares básicos, ele passa a usar uma infraestrutura virtualizada para desenvolver suas aplicações pagando como se fosse um serviço.
- **Plataforma como Serviço** (PaaS): É uma plataforma que possibilita o uso de ferramentas de desenvolvimento de softwares oferecidos por um provedor de serviços. Utilizando a Internet como meio de acesso, os desenvolvedores criam aplicações e armazenam dados de forma compartilhada através de uma plataforma.
- **Software como Serviço** (SaaS): é a classe mais comum. Nesse modelo o usuário usa todas as funcionalidades de um sistema de forma remota, sem a necessidade de instalação, ambiente para execução, manutenção e upgrades. A aplicação completa é ofertada e acessível ao cliente por um determinado preço.

Além das classes, é importante enfatizar que as nuvens podem ser classificadas em: 
- **Privadas**, quando opera para uma única instituição; 
- **Comunitária**, ou seja, pode ser dividida entre várias organizações; 
- **Pública**, quando é de responsabilidade de uma organização que vende os serviços, mas é disponível para o público; 
- **Híbrida**, quando usa mais de um tipo de nuvem.

## Infraestrutura baseada em Plataforma como Serviço (PaaS)

A economia com as abstrações de SO, o uso middleware (softwares que fornecem serviços e recursos comuns em aplicações) e Data Centers trazem agilidade e possibilitam uma modernização nos trabalhos desenvolvidos.

Além da estrutura de desenvolvimento na qual o desenvolvedor pode compilar, desenvolver e personalizar aplicações baseadas nas nuvens, a outra vantagem é poder usar os recursos das nuvens como escalabilidade, disponibilidade, redução de codificação, dentre outros. Outro uso muito comum de PaaS é a análise ou business intelligence, ou seja, algumas plataformas permitem análise e mineração de dados.

Dentre as **vantagens** do PaaS, temos a redução do tempo de codificação, já que existem componentes pré-codificados que podem ser inseridos no projeto; facilita o desenvolvimento em diferentes plataformas; permite ao usuário o uso de ferramentas sofisticadas; facilita o trabalho remoto, já que tudo é feito na Internet, e gerencia o ciclo de vida do aplicativo, dando suporte a todas as fases do desenvolvimento.

### Elasticidade e escalabilidade

Trata-se da capacidade de um sistema expandir e contrair a sua infraestrutura de acordo com uma demanda específica. Recursos de memória, armazenamento e processamento são alterados para mais ou para menos, conforme a necessidade do sistema. Essa característica propicia a ilusão de que os recursos computacionais são infinitos, os usuários têm a expectativa de que a nuvem seja capaz de fornecer rapidamente recursos em qualquer quantidade e a qualquer momento. É esperado que os recursos adicionais possam ser providos, possivelmente de forma automática, quando ocorre o aumento da demanda e retidos, no caso da diminuição desta demanda (BUYYA; GOSCINSKI; BROBERG, 2011).

>Elasticidade é um termo que muitos acreditam ser sinônimo de escalabilidade, mas não é. A diferença, como os nomes sugerem, é que, enquanto a *escalabilidade* em nuvem refere-se à facilidade de crescimento dos recursos disponibilizados, a *elasticidade* é uma forma de ajustar os recursos de acordo com a demanda.

Utilização ***On-demand*** diz respeito à instalação de novas instâncias em um curto período de tempo que será cobrado por hora do cliente. Para economizar recursos, a ativação e desligamento de máquinas é feito de forma otimizada, e o cliente paga de acordo com o tempo em que uma máquina estiver operando. Esse monitoramento pode ser feito através de relatórios.

Há dois tipos de escalonamentos automáticos: **vertical** e **horizontal**. O horizontal adiciona ou remove instâncias de recursos computacionais associados à aplicação, ou seja, adiciona ou remove computadores para uma aplicação de software distribuída; e o vertical aumenta ou diminui características dos recursos computacionais, como tempo, núcleo de CPU, memória Ram ou largura de banda da rede.

O aumento e a diminuição de recursos podem resultar em problemas de ***over-provisioning*** (sobreprovisionamento) quando um sistema provê mais recursos do que o necessário ou ***under-provisioning*** (subprovisionamento), quando um sistema provê menos recursos que o necessário. Um sistema elástico será mais eficiente quando apresentar menos possibilidades que elevem a under ou over-provisioning.

#### Toda a ação é automática, porém algumas de modo *reativo* e outras de modo *proativo*:

No modo **reativo**, como o nome sugere, as ações acontecem de acordo com reações a limiares ou regras estabelecidas, que podem ser a carga de trabalho ou a utilização de recursos, adaptando-se às mudanças necessárias.
Os limiares do modo reativo também diferem, em **estáticos** ou **dinâmicos**, sendo o primeiro mais usado. O modo estático compara as métricas e aciona o autoscaling quando o limiar é atingido. Por exemplo, se o consumo de uma CPU atingir 80% durante cinco minutos, aumente os recursos. O dinâmico opera de acordo com a demanda.

O modo **proativo** necessita adotar técnicas de *predição* que antecipem demandas futuras e sirvam para o acionamento do *autoscaling* com base nessas informações. Uma abordagem usada é a de análise de séries temporais para identificar padrões de repetição, que estima recursos necessários para lidar com a carga de trabalho antes que a demanda aconteça.
 A abordagem proativa conta com a ajuda de técnicas, como: 
 
- **média móvel** (analisa os dados obtendo a média dos últimos períodos e projetando o último valor médio no futuro)
- **auto-regressão** (classificação que prevê um número ao invés de uma categoria) 
-  **aprendizagem de máquina** (na qual o sistema analisa uma série de dados e deduz o conhecimento que será usado posteriormente).

---

# ==TERMINAR DE LER==

## Testes:

- **Unitários** Esse teste é o mais básico que se pode criar em uma aplicação, e diz respeito principalmente à funcionalidade que se está desenvolvendo. Pode ser um método ou até uma classe toda, o importante aqui é passar valores diferentes para essa unidade e testar se o retorno é o esperado.
- **Integração** Nos testes de integração, o foco é nas relações das classes em si, as que já existem no sistema e as que estão entrando (PRESSMAN; MAXIM, 2016). Por exemplo, se você está desenvolvendo uma nova funcionalidade que envia e-mail aos clientes, se determinado evento ocorrer, todas as classes envolvidas no seu código devem ser testadas, como cadastro do cliente, recuperação desses dados em um banco de dados, o evento que dispara os e-mails, etc.
- **Funcionais** Nesses testes o foco é verificar como o sistema se comporta quando dados inesperados forem passados a ele (PRESSMAN; MAXIM, 2016), por exemplo, quando uma função que faz multiplicação receber o valor “zero”, que é impossível de se calcular, ou quando um campo de e-mail receber um endereço inválido.
- **Desempenhos** Chamado também de teste de stress e carga, serve para testar cargas altíssimas no sistema e observar seu comportamento. Geralmente, é feito em sistemas web, para verificar até onde o sistema consegue receber e tratar requisições de maneira correta até que falhe.
- **Fim a Fim** São também conhecidos como testes de sistema, ou end-to-end, que servem para testar o sistema como um todo (PRESSMAN; MAXIM, 2016). Esse teste é muito custoso em tempo, e geralmente é feito em mudanças críticas que alteram a versão da aplicação e que mudam o funcionamento do sistema como um todo.

## Test Driven Development - TDD

Podemos dizer que o TDD foi a primeira técnica de desenvolvimento focada exclusivamente em testes, mas a ideia central aqui não é criar testes e, sim, como o próprio nome diz, orientar todo o desenvolvimento de softwares por testes (ANICHE, 2014).

como podemos escrever testes antes de termos um código? Parece complicado, mas, na verdade, é bem simples, focando os esforços nos requisitos, ou seja, no que o sistema tem que fazer, antes de desenvolver o código propriamente dito.  

Os passos do TDD são:  

- Crie um teste que valide o requisito;  
- Crie o código que passe no teste;  
- Refatore o código, atualizando-o.

## BDD – Desenvolvimento Orientado a Comportamento 

O BDD é uma evolução do TDD, levando em conta uma série de problemas enfrentados pelos desenvolvedores, proposto primeiramente por North (2006). O autor relata os problemas reais enfrentados ao tentar usar a técnica do TDD.

Foi proposta uma forma de descrever as funcionalidades da seguinte forma:
- **Funcionalidade** Descrever o que a funcionalidade deve fazer
- **Como** Quem executa essa funcionalidade
- **Eu quero** O que e essa pessoa espera da funcionalidade
- **De modo que** a descrição do resultado que se espera alcançar com a funcionalidade

## DevSecOps
![[Pasted image 20241129210215.png]]

### Análise de Composição de Software (SCA)   

Todo software desenvolvido, atualmente, utiliza bibliotecas que não são por padrão criadas pelo desenvolvedor. Usar itens que já foram criados auxilia na produtividade, já que não é necessário ficar quebrando a cabeça para inventar aquilo que já existe. Sabendo disso, entendemos também que essas bibliotecas importadas para o código podem conter vulnerabilidades.

Whitesource | FOSSA | Sonatype | BackDuck
### Varredura de segurança de banco de dados   

Essas ferramentas fazem uma varredura em banco de dados para verificar falhas que podem afetar a sua segurança, como versões desatualizadas, patches não aplicados, senhas fracas, erros de configuração, problemas com ACL (listas de controle de acesso), e muito mais. Podemos citar:  

- Scuba;
- MSSQL DataMask;  
- BSQL Hacker;  
- Oracle auditing tools.

