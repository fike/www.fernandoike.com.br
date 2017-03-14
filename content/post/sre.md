+++
draft = true
date = "2017-02-24T12:01:08-03:00"
title = "Site Realibility Engineer - SRE"
description = "O que é SRE"
categories = ["devops", "sre", "portugues"]
tags = ["devops", "sre", "blameles", "postmortem"]

+++
Se ainda não viu uma vaga de trabalho ou mesmo só a sigla SRE, então se prepare porque a tendência é tornar-se bem popular. O acrônimo SRE é usado para descrever tanto Site Reliability Engineering ("Disciplina/Cultura") como Site Reliability Engineer (descrição de função/vaga de trabalho). O termo foi criado em 2003 por Ben Treynor, atual VP de Engenharia do Google e ele relata sobre a criação da equipe no livro Site Reliability Engineering. (tradução livre)

> SRE é o que acontece quando você pergunta para um engenheiro de software para projetar uma equipe de operações. Quando entrei no Google em 2003 e recebi a tarefa de gerenciar uma "Equipe de Produção" de sete engenheiros, durante a minha vida fui engenheiro de software até aquele ponto. Então, projetei e gerenciei o grupo da maneira que eu gostaria que ele funcionasse, se eu trabalhasse como um SRE. Desde então, esse grupo amadureceu para se tornar a equipe atual de SRE do Google que permanece fiel a suas origens como previsto por engenheiro de software ao longo da vida

Treynor define um pouco melhor ao final do capítulo introdutório do mesmo livro. (tradução livre)

>*Site Reliability Engineer representa uma ruptura significativa das melhores prática da indústria existente para gerenciar serviços grande e complicados. Motivado originalmente pela familiaridade - "como um engenheiro de software, isso é como gostaria de investir meu tempo para realizar um conjunto de tarefas repetitivas" - tornou-se muito mais: um conjunto de princípios, práticas, incentivos e um campo de atuação dentro de disciplina maior que é a engenharia de software*.

Recomendo fortemente ler o livro do Google sobre SRE, ele mostra várias e excelente boas práticas para área de operações de TI de uma organização. Há algumas ressalvas como a abordagem sysadmin para gerenciamento de serviço como ultrapassada. Na verdade, Treynor descreve como funciona a TI no modelo tradicional com equipes de desenvolvimento e operações trabalhando como silos, áreas de baixa interação, iteração e muitos conflitos entre elas. Em quase uma década após DevOps ser cunhado (2008), sysadmins tiveram uma mudança significativa como função e também em importância ao lidar com automação da infraestrutura e serviços na nuvem (cloud).   

Quando Guto Carvalho e outros conversamos sobre a definição de [Infraestrutura Ágil](http://infraagil.io/), ali tentava delimitar um conjunto de princípio, práticas e disciplinas para área de operações de uma organização. De fato isso foi definido e pode ser lido [aqui](http://infraagil.io/), contudo ao aprofundar um pouco meu estudo sobre DevOps e SRE, acredito que SRE faz mais sentido para ser aplicado nas organizações (empresas, repartições públicas, etc.). Afinal, são mais de uma década de experiência em manter sistemas gigantes, escaláveis e resilientes (Google).

## DevOps ou SRE

A similaridade entre SRE e Infra(estrutura) Ágil fica evidente quando Treynor tenta definir SRE do pontos de vista de "DevOps". (tradução livre)

>*O termo "DevOps" emergiu na indústria no fim de 2008 e como este texto foi escrito (início de 2016) está num estado de fluxo. Seus princípios principais - envolvimento das funções de TI em cada fase da definição e desenvolvimento de um sistema, forte dependência da automação versus esforço humano, a aplicação das práticas de engenharia e ferramentas para tarefas operacionais - são consistentes com muitas práticas e princípios de SRE. Poderia ver o DevOps como uma generalização de vários princípios fundamentais para uma ampla e vasta gama de organizações, estruturas de gestão e pessoal. Poderia, de forma equivalente, ver o SRE como uma implementação do DevOps com algumas extensões peculiares.*

O que é SRE faz?

Basicamente um time SRE é responsável pela **disponibilidade**, **latência**, **desempenho**, **eficiência**, **gerenciamento de mudança**, **monitoramento**, **resposta a emergência** e **plano de capacidade** (capacity planning) dos serviços que eles são responsáveis (SRE não cuida da manutenção de impressoras...). Isso não quer dizer que eles são responsáveis somente pelo ambiente de produção, eles interagem com outros times baseado em regras de engajamento e princípios para manter o foco no trabalho de engenharia e não no trabalho operacional.

Ao ver os princípios que definem a disciplina SRE, verá que ele também aborda o **C.A.M.S.** (**Culture**, **Automation**, **Measurement**, **Sharing**) ou **The Tree Ways** (**Systems Thinking**, **Amplify Feedbacks**, **Culture Of Continual Experimentation and Learning**). Claro que a comparação direta entre SRE e DevOps não mostrará a relação de forma tão evidente, contudo, de fato estão lá. DevOps permite ser definido de maneiras diferentes e geralmente com definições abertas, por exemplo: Minha definição é "*DevOps significa uma cultura que permitir as organizações alterar seus processos, transformando-se de organizações de baixa performance em alta.*". O Gartner [define](http://www.gartner.com/it-glossary/devops/) como - "*DevOps representa uma mudança na cultura da TI, focando na entrega rápida dos serviços de TI através da adoção do Agile, práticas Lean no contexto de um abordagem orientada à sistema. DevOps enfatiza pessoas (e cultura), procura melhorar a colaboração entre equipes de desenvolvimento e operações. As implementações DevOps utilizam tecnologia - especialmente ferramentas de automação que podem alavancar uma infraestrutura cada vez mais dinâmica e programável a partir de uma perspectiva de um ciclo de vida.*" . Já com SRE, seja como disciplina ou como uma função de trabalho numa organização a definição é mais restrita.

## As Equipes

As equipes SRE são composta por uma mescla que tem mais conhecimento em software e pessoas com maior conhecimento em sistemas. A composição das equipes feita com pessoas de conhecimentos diferentes permite que haja um fluxo de comunicação e troca de conhecimento entre os membros, acelerando o aprendizado rápido e intenso. Na TI tradicional não é raro encontrar a função do Arquiteto de Software ou Arquiteto de rede, etc. Nas equipes de SRE não existe a função do Arquiteto, no artigo "[Hiring Site Reliability Engineers](https://www.usenix.org/publications/login/june15/hiring-site-reliability-engineers)" na [The Usenix Magazine](https://www.usenix.org/publications/login) é explicado porque não tem "**arquitetos**" - "**Nós especificamente não olhamos para *"arquitetos"* - porque é uma função que simplesmente não existe no Google: todos da nossa engenharia projetam como também desenvolvem.**"

O tempo das equipes é divido entre atividades de rotina de operação de TI (exemplo: tickets, indisponibilidade de serviços, suporte, plantão, etc.) e atividades relacionadas as habilidades deles de código para projetos como automação, projetos de infraestrutura, etc. Eles dividem o tempo pela metade, ou seja, 50% para atividades tradicionais de suporte e o restante aos projetos do trabalho que podem ser de simples automação como desenvolver serviços para serem usados na própria área ou mesmo interação com as equipes de desenvolvimento para. Uma fração do tempo (5%) também é direcionada para interações com as equipes de desenvolvimento, este tempo com os desenvolvedores ajudam a evitar indisponibilidade de um futuro serviço já que permite compartilhar boas práticas de aplicadas em outros projetos.

Há também uma liberdade do profissional SRE possa decidir mudar de equipe por uma razão qualquer. O impacto é relativamente pequeno porque todas equipes usam os mesmos processos e princípios. Portanto, mesmo que não tenho o conhecimento de um framework usado de um outro time, isso não é um impedimento para mudança de equipe já que ele pode aprender rapidamente. Outro ponto bem interessante é que no processo de recrutamento de novos SRE, não é requisito saber as linguagens e frameworks usados pelo Google, o mais importante é que o candidato saber programar (**Coders**).

Reuniões semanais de 30 à 60 minutos

Shadow on-call

Além das equipes SREs, outra equipe importante, além das equipes de desenvolvimento de produtos, é a Launch Coordination Engineering. Eles são "consultores internos",  

Além das equipes SREs, há um outro tipo de equipe no Google que vale destacar, é o Launch Coordination Engineering. Eles são equipes de consultoria interna de profissionais SRE com experiência em lançamento de produtos/serviços, orientando "*... os desenvolvedores para a construção de produtos rápidos e confiáveis que atendam aos padrões do Google em confiabilidade, escalabilidade e robustez*" **(Cap. 27 - Reliable Product Launches at Scale - SRE Book)**

##  Os princípios básicos

Os princípios básico de SRE são:

- Garantia um foco duradouro na Engenharia
- Perseguindo a maior velocidade de mudança sem violar um serviço SLO
- Monitoramento
- Resposta a emergências
- Gerenciamento de mudança
- Previsão de demanda e Capacity Planning
- Provisionamento
- Eficiência e Performance

Abaixo alguns princípios que vale destacar.

### Garantia um foco duradouro na Engenharia

Como mencionado no início do texto, os SRE trabalham 50% em atividades típicas de área de operações de TI de um organização. Quando este percentual eleva-se, as atividades excedentes são encaminhadas para os times de desenvolvimento de produto ou por um tempo determinado é alocado SREs de outras equipes para ajudar.

### Perseguindo a maior velocidade de mudança sem violar um serviço SLO

Sabe o que é **S**ervice **L**evel **O**bjective? No ITIL V3 ele mudou para **S**ervice **L**evel **T**arget, importante não confundir com **S**ervice **L**evel **A**greement. Exemplos bem simplistas de SLO e SLA: Servidores Web devem ter disponibilidade acima de 96% (SLO) medido pelo monitoramento pela monitoramento da Foobar Galaxy Company (a mesma empresa responsável pelos servidores web), a Overdrive IaaS tem SLA de 99% de disponibilidade da sua infraestrutura em contrato com a Foobar. Entendeu? SLO é uma medido internamente pela Foobar e SLA é sempre um "acordo" entre partes, na nuvem (cloud) é acordo de disponibilidade ou performance oferecido pelos fornecedores como IaaS, SaaS, PaaS, etc.

Como definir o SLO de um serviço ou aplicação?

Talvez seja um dos pontos de maior conflito entre áreas de TI e/ou mesmo outras áreas de uma organização. A área de operações pode definir que o SLO é de 97% de disponibilidade mas desenvolvimento ou a gerencia querer 100%. Muitas vezes já tive que explicar o quanto é inatingível 100% de disponibilidade, uma das respostas que mais ouvi era - "Ah, então o mais próximo de 100%, ok?". Muitas vezes saia frustrado das reuniões por não ter conseguindo explicar o quanto era difícil acrescentar noves para chegar mais próximo ao 100%. Gerentes e desenvolvedores só entendiam quando mostrava financeiramente o custo para aumentar a disponibilidade e perguntava de onde iria mover recurso financeiro para alocar para aquilo. Depois disso, SLO e SLA eram definidos com alguma razoabilidade a partir de então.

O Google via SRE tem uma abordagem melhor, eles a chamam de **Error Budget**. Ele é definido pelo inverso do SLO, exemplo: o SLO é de 99%, então o Error Budget é de 1%, portanto, 1% de indisponibilidade é a meta que as equipes responsáveis por serviço tem. Ele pode ser maior, por exemplo, no lançamento de um serviço e posteriormente ajustar para um percentual menor.  

### Monitoramento

Provavelmente, muitos dos que estão lendo devem fazer de forma similar aos SRE no Google. Eles usam métodos para monitorar seus serviços, poderia ser um outro texto só sobre o assunto mas está pensando em iniciar ou revisar o monitoramento do seu ambiente, vale usar o que eles chamam de "Os quatros sinais de ouro" (The Four Golden Signals): **latência**, **tráfego**, **erros** e **saturação**.

O monitoramento gera três tipos de saída: alertas, tickets e logs. Eles enfatizam que as saídas devem ter informações úteis e simplificar o possível sem que seja simplista. Por exemplo: configurar somente "pings" para avaliar a disponibilidade de um serviço. Além de recomendarem o monitoramento ser time-series como [Prometheus](https://prometheus.io)

Alguns anos atrás numa empresa que trabalhei, tínhamos um sistema de monitoramento que "não monitorava" segundo alguns dos meus colegas. Ninguém confiava nele para receber alertas de saturação de discos, rede ou memória, por exemplo. As pessoas preferiam entrar nos servidores e olharem por si, portanto, a confiabilidade do monitoramento era zero. Alguns diziam que o problema era ferramenta, era melhor trocar por outra. Outros diziam que não ninguém ali entendia de monitoramento e por isso que não funcionava.

Para "resolver", contratamos uma pessoa que já tinha implantado com sucesso a mesma ferramenta em outro lugar. Contratado, ele reimplementou o monitoramento e ninguém falava mais nisso, tudo certo? Após algumas semanas, perguntei por que o monitoramento estava com tantos alertas em vermelho. A resposta foi que os estavam usando o template padrão do agente de monitoramento e também não gerava ticket para eles olharem. Decidimos mudar a abordagem, inicialmente monitorávamos somente o básico de cada servidor (CPU, memória e disco), caso um algum indicador passasse do limite era aberto um ticket para Operações. Posteriormente foi incorporando outras métricas, ainda não chegava aos Quatros Sinais de Ouro mas o dashboard do sistema de monitoramento só tinha alertas (vermelho) quando realmente tinha alguma problema.

As informações do monitoramento só são úteis se as pessoas ou robôs souberem o que fazer fazer com elas.

### Resposta a emergências

Na maioria dos lugares que trabalhei na área de Operações de TI, o mais importante era sempre o MTTF (Mean Time to Failure), mas e não só eles (Google) consideram tão importante ou mais o MTTR (Mean Time to Repair).

Faz sentido, não? Uma vez o presidente da empresa que eu trabalhava se o site da empresa iria cair, disse que provavelmente sim. Ele me olhou indignado e na sequencia respondi: "*Sistemas são como carros, sempre tem alguma manutenção para fazer e nem sempre você consegue prever o que irá quebrar no carro.*". Bom, passado alguns meses estávamos conversando (Diretor de TI e eu) sobre uma RFP para contratação de um serviço especializado para a área de Operações e queria entender sobre MTBF (Mean Time Between Failures), MTTF e MTTR. Expliquei para ele o significado deles e ele perguntou porque tinha colocado o MTTR tão baixo para um serviço especializado que estava contratando. A resposta foi - "O indicador mais importante é o MTTR, porque o serviço pode ficar um ano sem qualquer tipo de incidente mas se houver uma indisponibilidade, qual será o tempo necessário para voltarmos ele?".

O Google identificou que o MTTR teve melhora de desempenho de até 3 vezes ao usarem um playbook (em alguns lugares também chamado de runbook). Ele é muito usado em outras indústrias e áreas do governo que precisam responder por incidente como desastres, ameaças a segurança, etc. No ITIL verá como **Emergency Change**. O playbook deve ser claro sobre como tratar um mais incidentes de emergência como: procedimentos a serem executados, fluxo do processo ou escalonamento. Na empresa de telecom que trabalhei há muitos anos atrás tinha um playbook para incidentes emergenciais, num plantão de um colega teve um sistema importante (billing) que caiu, ele ficou apavorado e me ligou para saber o que fazer. Perguntei se ele tinha olhado o playbook porque lá tinha o contato da equipe de produto responsável por aquele sistema que poderia ajudar. Ele não tinha visto, ele e a maioria das pessoas da equipe que eu trabalhava. A principal razão é que era porque o documento era enorme e difícil entender, além de ser um arquivo do Word, isso acrescentava um outro fator que era a versão que uma equipe usava nem sempre era a mais atual.

Por fim, eles praticam a "**Wheel of Misfortune**" (A roda do azar?). São simulações de incidentes que já ocorreram no Google em que semanalmente um membro da equipe de SRE é escolhido para fazer a simulação. Este tipo de exercício é excelente para acelerar o aprendizado e também prepara o SRE para situações de plantão, além de possibilitar que haja outras formas de resolver os incidentes.

### Gerenciamento de Mudança

Este é um número interessante, 70% dos problemas de indisponibilidade estão relacionados ao mudanças em sistemas em produção. Eles recomendam:

- Implementar lançamentos (rollouts) progressivos
- Detecção rápida e precisa dos problemas
- Rollback com segurança quando os problemas surgirem

## Outros destaques





Blameless
Postmortem
Testes (unitários, sistêmicos, performance, falhas, etc)
PRR Model (Production Readiness Review)
The SRE Engagement Model
