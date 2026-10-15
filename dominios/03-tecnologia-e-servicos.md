# Domínio 3 — Tecnologia e serviços de nuvem (34%)

[← Segurança](02-seguranca-e-conformidade.md) · [Voltar](../README.md) · [Próximo: Faturamento →](04-faturamento-precos-e-suporte.md)

Este é o domínio de **maior peso**. Para cada serviço, saiba **para que serve** e **quando escolhê-lo**.

## 3.1 Formas de implantar e operar

| Forma de acesso | Quando usar |
|---|---|
| **AWS Management Console** | Interface web; tarefas pontuais e aprendizado |
| **AWS CLI** | Linha de comando; *scripts* e automações simples |
| **SDKs** (Python, Java, .NET...) | Acessar a AWS de dentro de aplicações |
| **Infraestrutura como código (IaC)** | Ambientes **repetíveis** e versionados: **AWS CloudFormation** (YAML/JSON) e **AWS CDK** (em linguagens de programação) |

Operações pontuais cabem no Console. Processos que se repetem (criar o mesmo ambiente várias vezes) pedem IaC.

## 3.2 Infraestrutura global

```
Região (ex.: sa-east-1, São Paulo)
├── Zona de Disponibilidade A ── um ou mais data centers
├── Zona de Disponibilidade B ── energia, rede e refrigeração independentes
└── Zona de Disponibilidade C
Edge locations (pontos de presença) ── CloudFront, Route 53, Global Accelerator
```

- **Região**: área geográfica com várias AZs isoladas. Escolha pela **conformidade/soberania de dados**, **latência** para os usuários, **disponibilidade dos serviços** e **preço**.
- **Zona de Disponibilidade (AZ)**: um ou mais *data centers* sem pontos únicos de falha em comum com as outras AZs. **Alta disponibilidade = usar várias AZs.**
- ***Edge locations***: muito mais numerosas que as Regiões; armazenam conteúdo em cache perto do usuário (**Amazon CloudFront**).
- **Várias Regiões**: para recuperação de desastres, continuidade do negócio, baixa latência global e soberania de dados.
- **AWS Local Zones**, **AWS Wavelength** (5G) e **AWS Outposts** (AWS no seu *data center*) estendem a infraestrutura.

## 3.3 Computação

| Serviço | Use quando... |
|---|---|
| **Amazon EC2** | Precisa de controle total do servidor virtual |
| **Auto Scaling** | Precisa de **elasticidade**: adicionar e remover instâncias conforme a demanda |
| **Elastic Load Balancing** | Precisa distribuir tráfego entre instâncias e AZs (ALB para HTTP/HTTPS, NLB para TCP/UDP de alto desempenho) |
| **AWS Lambda** | Precisa executar código **sem servidor**, por evento; cobra por execução e duração (até 15 minutos por execução) |
| **Amazon ECS** | Precisa orquestrar contêineres com a ferramenta da AWS |
| **Amazon EKS** | Precisa de Kubernetes gerenciado |
| **AWS Fargate** | Precisa rodar contêineres **sem gerenciar servidores** (funciona com ECS e EKS) |
| **AWS Elastic Beanstalk** | Precisa publicar uma aplicação web só enviando o código (PaaS) |
| **Amazon Lightsail** | Precisa de VPS simples com preço fixo |

**Famílias de instâncias EC2**: uso geral (M, T), **otimizadas para computação** (C, para processamento intenso), **otimizadas para memória** (R, X, para bancos em memória), **computação acelerada** (P, G, com GPU, para ML) e **otimizadas para armazenamento** (I, D, com muito I/O local).

## 3.4 Bancos de dados

| Serviço | Tipo | Use quando... |
|---|---|---|
| **Amazon RDS** | Relacional gerenciado | Precisa de MySQL, PostgreSQL, MariaDB, Oracle, SQL Server ou Db2 sem administrar o servidor |
| **Amazon Aurora** | Relacional da AWS | Precisa de compatibilidade com MySQL/PostgreSQL e alto desempenho, com 6 cópias em 3 AZs |
| **Amazon DynamoDB** | NoSQL chave-valor | Precisa de milissegundos em qualquer escala, *serverless* |
| **Amazon ElastiCache** | Em memória (Redis/Valkey/Memcached) | Precisa de cache e de latência de microssegundos |
| **Amazon DocumentDB** | Documentos | Precisa de compatibilidade com MongoDB |
| **Amazon Neptune** | Grafos | Precisa de redes sociais, recomendação ou detecção de fraude |
| **Amazon Redshift** | *Data warehouse* | Precisa de análises (OLAP) sobre grandes volumes |

**Banco no EC2 × gerenciado**: no EC2, você instala, faz *backup*, aplica *patches* e configura alta disponibilidade. No RDS, a AWS cuida disso (*backups* automáticos, Multi-AZ, réplicas de leitura). Use EC2 só quando precisar de acesso ao SO ou de um motor/versão não suportado.

## 3.5 Redes

- **Amazon VPC**: rede privada isolada logicamente na AWS.
  - **Sub-rede pública**: tem rota para o **Internet Gateway**.
  - **Sub-rede privada**: sem acesso direto da internet; sai por meio de um **NAT Gateway**.
  - ***Security groups*** (instância, *stateful*) e **network ACLs** (sub-rede, *stateless*).
- **Amazon Route 53**: **DNS** gerenciado, registro de domínios e roteamento (latência, *failover*, geolocalização).
- **Amazon CloudFront**: **CDN**, que entrega conteúdo com baixa latência a partir das *edge locations*.
- **AWS Site-to-Site VPN**: conexão criptografada **pela internet** com o *data center*; rápida de configurar.
- **AWS Direct Connect**: conexão **dedicada e privada**, que não passa pela internet; latência consistente e alta banda.
- **AWS Global Accelerator**: melhora o desempenho global usando a rede da AWS.
- **AWS Transit Gateway**: conecta muitas VPCs e redes locais em um *hub* central.

## 3.6 Armazenamento

| Tipo | Serviço | Características |
|---|---|---|
| **Objetos** | **Amazon S3** | Arquivos acessados via HTTP, capacidade ilimitada, durabilidade de 99,999999999% (11 noves) |
| **Bloco** | **Amazon EBS** | "Disco" de **uma** instância EC2, persistente e vinculado a uma AZ |
| **Bloco** | ***Instance store*** | Disco físico do *host*, **temporário**: os dados se perdem ao parar a instância |
| **Arquivos** | **Amazon EFS** | Sistema de arquivos **compartilhado** (NFS) para muitas instâncias Linux |
| **Arquivos** | **Amazon FSx** | Para Windows File Server, Lustre (HPC), NetApp ONTAP e OpenZFS |
| **Híbrido** | **AWS Storage Gateway** | Liga o armazenamento local ao S3 com cache local |
| ***Backup*** | **AWS Backup** | Políticas centralizadas de *backup* para vários serviços |

### Classes do Amazon S3

| Classe | Use para |
|---|---|
| **S3 Standard** | Dados acessados com frequência |
| **S3 Intelligent-Tiering** | Padrão de acesso **desconhecido ou variável**: move os dados automaticamente |
| **S3 Standard-IA** | Acesso infrequente, mas que precisa ser rápido quando ocorre |
| **S3 One Zone-IA** | Acesso infrequente, dados recriáveis (uma única AZ, mais barato) |
| **S3 Glacier Instant Retrieval** | Arquivo acessado cerca de uma vez por trimestre, com recuperação em milissegundos |
| **S3 Glacier Flexible Retrieval** | Arquivo com recuperação em minutos ou horas |
| **S3 Glacier Deep Archive** | **Menor custo**; retenção de longo prazo, recuperação em até 12 horas ou mais |
| **S3 Express One Zone** | Desempenho altíssimo, latência de um dígito de milissegundo |

**Políticas de ciclo de vida** (*lifecycle*) movem objetos entre classes ou os excluem automaticamente. Exemplo: mover para o Glacier após 90 dias e excluir após 7 anos.

## 3.7 IA/ML e análise de dados

| Serviço | Função |
|---|---|
| **Amazon SageMaker AI** | Construir, treinar e implantar modelos de ML |
| **Amazon Bedrock** | Usar modelos de IA generativa (*foundation models*) por API |
| **Amazon Lex** | *Chatbots* de voz e texto |
| **Amazon Rekognition** | Análise de imagens e vídeos |
| **Amazon Comprehend** | Processamento de linguagem natural (sentimento, entidades) |
| **Amazon Polly** / **Amazon Transcribe** | Texto para fala / fala para texto |
| **Amazon Translate** / **Amazon Textract** | Tradução / extração de texto de documentos |
| **Amazon Athena** | Consultas **SQL diretamente sobre o S3**, *serverless* |
| **Amazon Kinesis** | Dados em **tempo real** (*streaming*) |
| **AWS Glue** | **ETL** e catálogo de dados |
| **Amazon QuickSight** | **Painéis** e BI |
| **Amazon EMR** | Big data com Spark e Hadoop |

## 3.8 Outras categorias

| Categoria | Serviços |
|---|---|
| **Integração de aplicações** | **Amazon SQS** (fila; desacopla componentes), **Amazon SNS** (*pub/sub* e notificações: e-mail, SMS, *push*), **Amazon EventBridge** (barramento de eventos e agendamentos) |
| **Aplicações de negócio** | **Amazon Connect** (*contact center*), **Amazon SES** (envio de e-mails em massa) |
| **Ferramentas de desenvolvimento** | **AWS CodeBuild** (compilar e testar), **AWS CodePipeline** (CI/CD), **AWS X-Ray** (rastrear requisições e depurar) |
| **Computação para o usuário final** | **Amazon WorkSpaces** (desktops virtuais), **Amazon AppStream 2.0** (aplicações transmitidas ao navegador), **Amazon WorkSpaces Secure Browser** |
| ***Frontend*, web e mobile** | **AWS Amplify** |
| **IoT** | **AWS IoT Core** (conectar e gerenciar dispositivos) |
| **Suporte ao cliente** | **AWS Support** (veja o domínio 4) |

## Para fixar

1. Aplicação precisa sobreviver à falha de um *data center* → implantar em **várias AZs**.
2. Executar código quando um arquivo chega ao S3, sem servidores → **AWS Lambda**.
3. Consultar com SQL arquivos CSV guardados no S3, sem carregar em banco → **Amazon Athena**.
4. Conexão privada e dedicada entre a fábrica e a AWS → **AWS Direct Connect**.
5. Desacoplar o pedido do processamento, guardando mensagens até serem consumidas → **Amazon SQS**.
