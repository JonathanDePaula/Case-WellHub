# Case-WellHub
Trabalho de estudo WellHub -  Problema fictício.
# Estudo de arquitetura

# **Contextualização do Problema**

O Wellhub tornou-se um benefício indispensável para o bem-estar e a qualidade de vida dos colaboradores das empresas clientes. Em 2024, a plataforma atingiu 500 milhões de check-ins diários, refletindo um crescimento de 130% no faturamento em 2023. Uma pesquisa recente revelou que 93% dos usuários consideram o bem-estar proporcionado pela plataforma tão importante quanto o salário, o que evidencia o impacto direto do Wellhub na vida dos colaboradores (fonte: Panorama do Bem Estar Corporativo 2024).

Entretanto, ao mudar de emprego, muitos colaboradores enfrentam períodos de carência que suspendem temporariamente seus benefícios, incluindo aqueles oferecidos pelo Wellhub. Esse período de carência pode prejudicar a experiência do usuário e, consequentemente, reduzir a percepção de valor do Wellhub, o que pode levar à busca por alternativas no mercado. A eliminação deste período de carência é vista como uma estratégia crucial para melhorar a satisfação do usuário, assegurar uma retenção de clientes mais eficaz e garantir a continuidade da receita, reforçando a liderança do Wellhub no mercado por meio de um serviço superior e confiável.

## Motivadores

O principal motivador para este projeto é otimizar a experiência do usuário, assegurando que os benefícios oferecidos pelo Wellhub sejam contínuos e sem interrupções, mesmo durante a transição de emprego dos colaboradores. A percepção de valor pelo usuário final é um dos principais impulsionadores de crescimento para o Wellhub. Portanto, eliminar o período de carência não só aprimora a proposta de valor da plataforma, como também consolida o Wellhub como líder de mercado, proporcionando um serviço superior em relação aos concorrentes.

## Objetivos do Projeto

**Aprimorar a Experiência do Usuário:** Garantir que colaboradores que mudam de emprego dentro da rede de empresas clientes do Wellhub não enfrentem interrupções nos seus benefícios, proporcionando uma transição suave e sem atritos.

**Aumentar a Retenção e Fidelização de Clientes:** Reduzir a insatisfação dos usuários, o que contribui diretamente para aumentar a retenção de clientes e, consequentemente, a receita recorrente.

**Crescimento de Receita:** A redução do período de carência aumentará os dias ativos de cada usuário, resultando em um incremento direto na receita. Um grupo de controle de 100.000 usuários, por exemplo, mostrou que a eliminação de 5 dias de carência por ano resultaria em um ganho adicional de R$ 4.300.000,00 por ano.

**Eficiência Operacional:** A automação dos processos de transição de emprego entre empresas reduzirá o trabalho manual e minimizará erros, resultando em economia de custos operacionais e maior eficiência.

**Diferenciação Competitiva:** Posicionar o Wellhub como um serviço superior no mercado, atraindo novos clientes corporativos e aumentando a penetração de mercado.

# **Visão de Arquitetura**

Dadas as premissas, objetivos, justificativas, ganhos e complexidades do problema, a visão de arquitetura da solução foi desenvolvida em cinco níveis distintos:

## **Nível 1: Visão Geral do Processo**

A solução foi mapeada utilizando a técnica de Domain Storytelling para entender como a continuidade dos benefícios durante a transição de emprego pode ser garantida.

**Narrativa do Domínio:**

O Wellhub é uma plataforma que oferece benefícios de bem-estar aos colaboradores de empresas clientes. Quando um funcionário aceita uma nova posição em outra empresa dentro da rede de clientes do Wellhub, a continuidade dos benefícios torna-se crucial para manter a satisfação do usuário. A nova arquitetura visa eliminar qualquer interrupção desses benefícios, removendo o período de carência durante a transição.

**Principais Etapas do Processo:**

1. **Início da Transição de Emprego:**
    - **Usuário:** O colaborador aceita uma nova posição em outra empresa dentro da rede do Wellhub.
    - **Sistema de Gestão de Benefícios:** Identifica a mudança de emprego e inicia o processo de transição de benefícios.
2. **Verificação de Elegibilidade:**
    - **Sistema de Gestão de Benefícios:** Verificar a elegibilidade do colaborador para manter os mesmos benefícios na nova empresa.
    - **Caso de Inelegibilidade:** Se o colaborador não for elegível para um benefício específico, o sistema notifica o colaborador e sugere alternativas.
3. **Transferência de Benefícios:**
    - **Sistema de Gestão de Benefícios:** Automatiza a transferência dos benefícios para a nova empresa sem interrupção.
    - **Cenário Alternativo:** Em caso de falha na comunicação com o sistema da nova empresa, o sistema realiza novas tentativas e alerta o suporte técnico para intervenção manual.
4. **Monitoramento e Notificação:**
    - **Sistema de Monitoramento:** Acompanha a transição para assegurar a ativação de todos os benefícios na nova empresa.
    - **Caso de Degradação:** Se houver atrasos ou falhas na ativação dos benefícios, o sistema alerta a equipe de suporte para resolução imediata.
5. **Confirmação e Uso:**
    - **Usuário:** Recebe uma notificação confirmando a transferência bem-sucedida e a continuidade dos benefícios.
    - **Sistema de Benefícios:** Registra a confirmação e inicia o monitoramento contínuo do uso dos benefícios.

https://paladino-6d6.notion.site/Estudo-de-arquitetura-1028b2719c0c807f8bc4c6daf4aa47dc

**Figura 1:** Diagrama geral do processo

https://paladino-6d6.notion.site/Estudo-de-arquitetura-1028b2719c0c807f8bc4c6daf4aa47dc

---

## 

## **Nível 2: Visão de Alto Nível da Solução**

A arquitetura proposta para o Wellhub aborda a continuidade dos benefícios durante a transição de emprego com uma abordagem holística e bem estruturada. A solução foi desenhada para ser resiliente, escalável e segura, utilizando uma arquitetura multicloud que combina os serviços da AWS e GCP.

**Componentes Principais:**

- **Portal do Usuário:** Principal ponto de contato entre o colaborador e seus benefícios, garantindo acesso ininterrupto mesmo durante a transição de emprego.
- **Camada de Autenticação e Autorização:** Utiliza Single Sign-On (SSO) para assegurar uma experiência segura e consistente, centralizada em serviços como AWS Cognito e Google Identity Platform, orquestrados pelo Maverics da Strata.
- **Sistema de Gestão de Benefícios:** O núcleo operacional que gerencia e rastreia os benefícios dos colaboradores. Aqui, a lógica de eliminação do período de carência é implementada, assegurando a continuidade dos serviços.
- **Camada de Integração API:** Facilita a interoperabilidade entre o Wellhub e sistemas externos, permitindo que a solução seja flexível e se integre facilmente com os sistemas das empresas clientes.
- **Sistemas das Empresas Clientes:** Integração com sistemas de ERP/HR e autenticação de identidade (SSO), garantindo uma transição suave e contínua dos benefícios dos colaboradores.
- **Provedores Externos e Serviços de Pagamento:** Gerenciam e processam adequadamente todos os aspectos dos benefícios sem interrupções.
- **Serviço de Monitoramento e Observabilidade:** Implementado com Prometheus e Grafana Cloud, assegura alta disponibilidade do sistema e rápida resolução de problemas.

https://paladino-6d6.notion.site/Estudo-de-arquitetura-1028b2719c0c807f8bc4c6daf4aa47dc

**Figura 2:** Diagrama em alto nível do processo

https://paladino-6d6.notion.site/Estudo-de-arquitetura-1028b2719c0c807f8bc4c6daf4aa47dc

---

## **Nível 3: Visão dos Componentes de Aplicação**

A solução de arquitetura proposta detalha a estrutura técnica e os componentes de aplicação que suportam a continuidade dos benefícios no Wellhub. Cada componente desempenha um papel crucial na entrega de uma solução escalável, segura e eficiente.

**1. Microfrontend:**

- **Arquitetura:** O ponto de entrada para os colaboradores é um microfrontend modular e responsivo, servido através de uma arquitetura de computação de borda (edge computing) utilizando os serviços da Azion.
- **Armazenamento:** Arquivos estáticos são armazenados em sistemas distribuídos em múltiplas clouds (AWS S3 e Google Cloud Storage), garantindo alta disponibilidade e baixa latência.
- **Segurança:** Protegido por um Web Application Firewall (WAF) da Imperva, que defende contra ataques como SQL Injection, Cross-Site Scripting (XSS), e DDoS.

**2. Autenticação e Autorização:**

- **SSO e IDPs:** Integração com SSO para autenticação centralizada, utilizando AWS Cognito e Google Identity Platform, orquestrados pelo Maverics da Strata.
- **Segurança:** Garante que todos os colaboradores acessem o sistema com uma única credencial, simplificando a gestão de identidades e melhorando a segurança.

**3. Gerenciamento de Segredos:**

- **Secret Manager:** Uso de AWS Secret Manager e GCP Secret Manager para armazenamento seguro de credenciais, chaves de API e outros segredos, com criptografia automática e controle de acesso granular.

**4. Kubernetes e Orquestração de Aplicações:**

- **Clusters Kubernetes:** Infraestrutura baseada em Kubernetes (EKS na AWS e GKE na GCP) para escalabilidade horizontal e portabilidade.
- **Estrutura dos Nós:** Três tipos de nós (Aplicações, Componentes, Dados) para gerenciar APIs, integração de sistemas e armazenamento de dados com alta resiliência.

**5. Redes e Comunicação:**

- **VPCs e Subnets:** Uso de VPCs (AWS e GCP) com subnets públicas e privadas para segmentação segura do tráfego.
- **Gateways:** NAT Gateway e Internet Gateway para comunicação segura e eficiente entre os componentes do sistema.

**6. Monitoramento e Observabilidade:**

- **Prometheus e Grafana Cloud:** Coleta e visualização de métricas em tempo real, permitindo monitoramento proativo e solução rápida de problemas.

**7. Deploy e CI/CD:**

- **Pipelines Automatizados:** Uso de GitHub Actions e Terraform para provisionamento de infraestrutura, e ArgoCD para deploy contínuo de aplicações.

**8. Segurança:**

- **WAF da Imperva:** Filtragem de tráfego malicioso, garantindo a integridade e disponibilidade das aplicações.

https://paladino-6d6.notion.site/Estudo-de-arquitetura-1028b2719c0c807f8bc4c6daf4aa47dc

**Figura 3:** Visão dos componentes de aplicação

https://paladino-6d6.notion.site/Estudo-de-arquitetura-1028b2719c0c807f8bc4c6daf4aa47dc

---

## 

## **Nível 4: Visão de Arquitetura de Cloud/Infraestrutura**

A solução foi projetada para operar em um ambiente multicloud, combinando os recursos da AWS e do Google Cloud Platform para garantir alta disponibilidade, resiliência e escalabilidade.

**Camadas da Arquitetura:**

- **Camada de Frontend:** Composta por buckets S3 (AWS) e Google Cloud Storage (GCP), conectados ao Internet Gateway e entregues via rede de borda da Azion.
- **Camada de Segurança:** Protegida pelo WAF da Imperva, filtrando o tráfego antes que ele alcance os serviços de backend.
- **VPCs:** Cada cloud tem sua própria VPC, com subnets públicas e privadas, NAT Gateways e Internet Gateways, dividindo os clusters de Kubernetes entre nós de Aplicações, Componentes e Dados.
- **Orquestração e Deploy:** Gestão de infraestrutura e ciclo de vida de aplicações com Terraform e ArgoCD, garantindo consistência e automação.
- **Monitoramento e Observabilidade:** Monitoramento centralizado com Prometheus e visualização de métricas no Grafana Cloud.
- **Camada de Identidade:** Integração de múltiplos IDPs com AWS Cognito e Google Identity Platform via Maverics para SSO consistente.

**Fluxo de Dados e Backup:**

- **Microfrontend:** Servido a partir de buckets S3 (AWS) e Google Cloud Storage (GCP) através da rede de borda da Azion.
- **API de Dados:** Processamento e cache em MongoDB e Redis, com mensagens gerenciadas por Kafka.
- **Backup:** Backups regulares gerenciados pelo Velero, armazenados em buckets dedicados.

https://paladino-6d6.notion.site/Estudo-de-arquitetura-1028b2719c0c807f8bc4c6daf4aa47dc

**Figura 4:** Visão da infraestrutura da solução
https://paladino-6d6.notion.site/Estudo-de-arquitetura-1028b2719c0c807f8bc4c6daf4aa47dc
---

## 

## **Nível 5: Visão de Evolução da Plataforma**

A evolução da plataforma considera tanto os pontos de ganho quanto os pontos de falha e melhoria, além de possíveis gargalos e aprofundamentos necessários para garantir a longevidade e a eficiência da solução.

**Pontos de Ganho:**

1. **Escalabilidade Multicloud:** A configuração atual oferece flexibilidade e resiliência, permitindo balanceamento de carga e otimização de custos entre AWS e GCP.
2. **Resiliência e Alta Disponibilidade:** Kubernetes em múltiplas clouds e segregação de nós garantem a resiliência da solução.
3. **Segurança Centralizada:** WAF e orquestração de identidades fortalecem a segurança em um ambiente multicloud.
4. **Automação de Deploy:** CI/CD com Terraform e ArgoCD assegura atualizações rápidas e seguras.
5. **Monitoramento e Observabilidade:** Prometheus e Grafana Cloud fornecem uma base sólida para a visibilidade do sistema.

**Pontos de Falha:**

1. **Dependência de Serviços Gerenciados:** Interrupções nos serviços gerenciados podem afetar a disponibilidade e desempenho do sistema.
2. **Complexidade da Orquestração Multicloud:** A gestão de identidades e redes pode se tornar complexa e suscetível a erros.
3. **Backup e Recuperação Distribuídos:** A gestão de backups entre clouds pode ser um ponto crítico se não for monitorada e testada rigorosamente.

**Pontos de Melhoria:**

1. **Otimização de Custos:** Avaliar o uso de instâncias spot, ajustes de escalabilidade e negociação de contratos para reduzir custos operacionais.
2. **Integração de Ferramentas de Observabilidade:** Expansão do monitoramento com ferramentas como Loki para logs centralizados e Jaeger para rastreamento distribuído.
3. **Gestão de Configurações e Segredos:** Implementar práticas mais frequentes de rotação de segredos e gestão de configurações com ferramentas como HashiCorp Vault.
4. **Expansão da Computação de Borda:** Considerar a integração com mais provedores de computação de borda para melhorar a entrega de conteúdo globalmente.

**Pontos de Atenção:**

1. **Governança Multicloud:** Implementar governança eficaz para manter consistência em políticas de segurança, conformidade e gestão de custos.
2. **Evolução das Ferramentas de Cloud:** Manter-se atualizado com novos serviços e soluções para manter a competitividade.
3. **Segurança no Tráfego Interno:** Garantir a criptografia ponta a ponta e monitoramento rigoroso do tráfego interno entre os componentes.

**Possíveis Gargalos:**

1. **Escalabilidade de Kafka:** Monitorar e ajustar o throughput do cluster Kafka para evitar atrasos na entrega de mensagens.
2. **Latência em Ambientes Multicloud:** Monitorar e otimizar a latência entre serviços distribuídos nas clouds, usando interconexões diretas se necessário.
3. **Limitações de Banda de Rede:** Garantir que a capacidade de rede esteja dimensionada para o crescimento futuro, especialmente para operações de backup e replicação de dados.

**Pontos que Merecem Aprofundamento:**

1. **Estratégia de Disaster Recovery (DR):** Desenvolver uma estratégia detalhada de DR, incluindo testes regulares e automação de processos de recuperação.
2. **Adoção de Novas Tecnologias:** Avaliar continuamente novas tecnologias e padrões que possam melhorar a eficiência e reduzir custos.
3. **Integração com IA e Machine Learning:** Considerar o uso de IA/ML para análise preditiva, otimização de recursos e segurança.

**Expansão Global e Localização:**

Suportar melhor a localização de serviços e garantir conformidade com regulamentos locais de proteção de dados.
