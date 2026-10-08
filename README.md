# **(Atividade 1) Lab Project - Treinando uma IA de Aprendizagem - Explore o Poder do NotebookLM#**<br>
**TEMA/OBJETIVO:**<br>
Criar um núcleo de referência sobre nichos específicos de arquitetura de software: Event Driven Architecture, Microservices, Messaging e afins.<br><br>
**FONTES - VIDEOS:**<br>
- https://www.youtube.com/watch?v=1O2LkhlKO5Q<br>
- https://www.youtube.com/watch?v=hrvx8Nv9eQA<br>
- https://www.youtube.com/watch?v=C842vFY5kRo<br>
- https://www.youtube.com/watch?v=7YmLbhiK-PM<br>
- https://www.youtube.com/watch?v=lEcULR30-GM<br>
- https://www.youtube.com/watch?v=yxeMFqIAOwg<br>
- https://www.youtube.com/watch?v=DOaDpHh1FsQ<br>
- https://www.youtube.com/watch?v=vRyKe6Ya0dI<br><br>

**FONTES - PDF:**<br>
- Building Microservices - Designing Fine-Grained Systems - Sam Newman<br>
- Clean Architecture - Robert C. Martin<br>
- Designing Event-Driven Systems - Ben Stopford<br>
- Designing Data-Intensive Applications - Martin Kleppmann<br>
- Production-Ready Microservices - Susan J. Fowler<br><br>

**DIRETRIZ DE COMPORTAMENTO:**<br>
Se comporte como um experiente professor de arquitetura e engenharia de software.<br><br>

**PERGUNTAS REALIZADAS:**<br><br>

1) qual seria o roadmap pra aprender microserviços?*

Aprender microsserviços não é apenas aprender novas ferramentas ou frameworks, mas sim dominar a **gestão de complexidade em sistemas distribuídos, a definição de fronteiras de domínio e a prontidão operacional**[1][2][3].

Abaixo está o **roadmap pedagógico estruturado em 5 fases**, elaborado a partir das principais referências da área:

### **Fase 1: Fundamentos Arquiteturais e Decisão de Modelo**

Antes de construir sistemas distribuídos, é essencial entender o ponto de partida e os reais motivos para adotar essa arquitetura:

* **O Monolito como Ponto de Partida Sensato**: O monolito (especialmente o **Monolito Modular**) deve ser a escolha padrão sensata para a maioria das aplicações e organizações em estágio inicial[4][5][6]. Ele evita a complexidade desnecessária de rede e implantação[7][8].
* **Identificação de Problemas Reais**: A migração deve ser motivada por gargalos claros de escalabilidade, contenção de entrega (*delivery contention*) entre equipes organizacionais ou necessidade de autonomia técnica[9][10][11][12].
* **A Metáfora do Botão (** **Dial** **) e Trade-offs**: Adotar microsserviços não é um "interruptor", mas um "botão" que se gira gradualmente[13][14]. Quanto mais serviços são criados, maior a flexibilidade, mas também maiores os pontos de dor e as formas imprevisíveis de falha de um sistema distribuído[1][13][15].

### **Fase 2: Modelagem de Domínio e Decomposição**

A maior dificuldade em microsserviços não é o código, mas a definição das **fronteiras (** **boundaries** **)** corretas[13][16]:

* **Princípios Modulares Clássicos**: Dominar o **Ocultamento de Informação (** **Information Hiding** **)** — esconder detalhes internos atrás de contratos externos estáveis[17][18] — além de garantir **Alta Coesão** e **Baixo Acoplamento**[19][20].
* **Domain-Driven Design (DDD) e Contextos Delimitados (** **Bounded Contexts** **)**: Usar o DDD para mapear os *seams* (costuras) do negócio e definir os *Bounded Contexts*[21][22][23]. As fronteiras dos microsserviços devem refletir os domínios de negócio, e nunca divisões estritamente técnicas (como criar um serviço exclusivo para banco de dados)[24][25].
* **Decomposição Incremental**: Aprender a estratégia de "descascar" o monolito aos poucos (padrão *Strangler Fig*) em vez de tentar uma reescrita do zero (*big-bang rewrite*)[26][27][28][29].

### **Fase 3: Estilos de Comunicação e Padrões de Integração**

Compreender como os serviços trocam dados sem criar dependências frágeis:

* **Síncrono vs. Assíncrono**:
  * *Síncrono (HTTP/REST, gRPC)*: Fácil de implementar, mas introduz **acoplamento temporal** (ambos os serviços precisam estar online ao mesmo tempo) e cascata de latência[30][31][32][33].
  * *Assíncrono (Messaging / Message Brokers)*: Utiliza um *broker* intermediário (como RabbitMQ ou Apache Kafka) para desacoplar remetente e destinatário, garantindo entrega confiável e tolerância a picos de tráfego[34][35][36][37][38].
* **Arquitetura Orientada a Eventos (EDA)**: Diferenciar **Comandos** (solicitações de ação futura) de **Eventos** (fatos imutáveis passados)[34][39], explorando padrões como *Publish-Subscribe* e *Event-Carried State Transfer*[40][41][42].
* **Gestão de Transações Distribuídas**: Substituir transações ACID distribuídas pelo padrão **Saga** (gerenciando fluxos via **Coreografia** ou **Orquestração** com ações de compensação em caso de falha)[43][44][45][46].

### **Fase 4: Infraestrutura, Implantação e Plataforma**

Entender a camada de plataforma que sustenta o ecossistema de microsserviços[47][48]:

* **Conteinerização**: Uso de **Docker** para isolar dependências e empacotar aplicações de forma padronizada[49][50].
* **Orquestração e Escala**: Evolução para **Kubernetes** e plataformas *serverless*/FaaS conforme a escala e a complexidade do ecossistema aumentam[43][51][52].
* **Roteamento e Descoberta (** **Service Discovery &amp; API Gateways** **)**: Implementação de *Service Registries* (como Consul ou ZooKeeper) e *Service Meshes* para gerenciar roteamento, resolução de IPs e balanceamento de carga de instâncias saudáveis[53][54][55].
* **Pipelines de CI/CD e Implantação Segura**: Automação do ciclo de compilação, testes e deploys[56][57], utilizando estratégias como ambiente de *Staging*, lançamentos canário (*Canary Releases*) e *Blue-Green Deployments* para evitar paradas em produção[58][59][60].

### **Fase 5: Testes, Observabilidade e Prontidão para Produção (** **Production Readiness** **)**

Garantir que os serviços funcionem de forma confiável em um ambiente real e instável[11][61]:

* **Evolução da Pirâmide de Testes**: Reduzir a dependência de testes *End-to-End* (caros e lentos em sistemas distribuídos)[62][63] e focar em **Testes de Unidade**, **Testes de Serviço** e **Consumer-Driven Contracts (CDC)** com ferramentas como Pact[64][65], além de testes em produção[66].
* **Pilares de Observabilidade**: Implementar agregação centralizada de **Logs**, **Métricas** e **Rastreamento Distribuído (** **Distributed Tracing** **)** com OpenTelemetry para acompanhar uma requisição através das fronteiras dos serviços[64][67][68][69][70].
* **Padrões de Resiliência e Estabilidade**: Aplicar *Circuit Breakers*, *Timeouts*, *Bulkheads*, *Retries*, Idempotência e *Defensive Caching* para evitar que a falha de um serviço derrube todo o sistema[71][72][73][74][75].
* **Auditorias de Production Readiness**: Estabelecer padrões operacionais claros, documentação técnica, *runbooks* para sobreaviso (*on-call*) e monitoramento baseado em SLOs/SLAs[3][56][76][77].

🎯 *Se você quiser focar na prática de alguma destas fases, podemos detalhar como implementar a* **decomposição de um monolito usando DDD** *, ou estruturar um projeto prático de* **mensageria assíncrona com RabbitMQ** *.*

---


Foram mais de 70 citações das fontes utilizadas. Seguem 3 prints para evidenciar:
- ![Pergunta 1 - Imagem 1](./imagens/imagem01.jpg)
- ![Pergunta 1 - Imagem 2](./imagens/imagem02.jpg)
- ![Pergunta 1 - Imagem 3](./imagens/imagem03.jpg)




