# Gabarito comentado

[← Voltar ao simulado](simulado.md)

| Questão | Resposta | Domínio |
|---|---|---|
| 1 | B | 1 |
| 2 | C | 1 |
| 3 | C | 1 |
| 4 | B | 1 |
| 5 | B | 1 |
| 6 | A, C | 1 |
| 7 | C | 1 |
| 8 | B | 2 |
| 9 | B | 2 |
| 10 | C | 2 |
| 11 | A | 2 |
| 12 | C | 2 |
| 13 | B | 2 |
| 14 | A, D | 2 |
| 15 | A | 2 |
| 16 | B | 2 |
| 17 | B | 3 |
| 18 | B | 3 |
| 19 | C | 3 |
| 20 | C | 3 |
| 21 | C | 3 |
| 22 | B | 3 |
| 23 | B | 3 |
| 24 | A | 3 |
| 25 | B | 3 |
| 26 | A | 3 |
| 27 | C | 4 |
| 28 | C | 4 |
| 29 | B | 4 |
| 30 | B | 4 |

**Resultado:** 24 acertos ou mais (80%) indicam que você está pronto para agendar a prova.

---

## Comentários

**1 — B.** Elasticidade é ajustar os recursos **automaticamente** à demanda, para cima e para baixo. Alta disponibilidade trata de continuar funcionando diante de falhas.

**2 — C.** O pilar de sustentabilidade foi o sexto a entrar no Well-Architected e trata do impacto ambiental, por exemplo maximizando a utilização dos recursos.

**3 — C.** *Rehost* (*lift and shift*) é mover sem alterações. *Replatform* faz pequenos ajustes; *Refactor* reescreve a aplicação.

**4 — B.** Na nuvem não há investimento inicial em servidores: paga-se pelo uso (OpEx). A gestão de custos continua sendo necessária, daí a alternativa C estar errada.

**5 — B.** BYOL é usar licenças já adquiridas. Licenças por núcleo ou soquete físico costumam exigir *Dedicated Hosts*.

**6 — A e C.** As seis perspectivas do CAF são *Business*, *People*, *Governance*, *Platform*, *Security* e *Operations*.

**7 — C.** *Rightsizing* é adequar o tamanho do recurso ao uso real, e é a primeira medida de otimização de custos.

**8 — B.** No EC2 (IaaS), o SO convidado é do cliente. Segurança física, *hardware* e virtualização são da AWS.

**9 — B.** No RDS, a AWS gerencia o SO e o motor do banco. O cliente cuida de usuários, rede, dados e da decisão de criptografar.

**10 — C.** O CloudTrail registra as chamadas de API: quem fez, o quê, quando e de onde. O CloudWatch trata de métricas e logs de desempenho; o Config, do histórico de configuração.

**11 — A.** O AWS Artifact é o portal gratuito de relatórios de conformidade e acordos.

**12 — C.** Uma *role* fornece credenciais temporárias e rotacionadas automaticamente. Chaves no código e uso do *root* são más práticas graves.

**13 — B.** O AWS WAF atua na camada 7 (HTTP). O Shield protege contra DDoS; o GuardDuty detecta ameaças; o Macie encontra dados sensíveis.

**14 — A e D.** Ative o MFA, não crie *access keys* para o *root* e use-o só quando necessário, mantendo um usuário administrativo para o dia a dia.

**15 — A.** O Amazon Macie usa *machine learning* para descobrir dados sensíveis no S3. O Inspector procura vulnerabilidades em instâncias e contêineres.

**16 — B.** O IAM Identity Center oferece login único para várias contas e aplicações. O Cognito serve para usuários **das suas aplicações**, não para funcionários acessando a AWS.

**17 — B.** As AZs são isoladas entre si e não compartilham pontos únicos de falha. Para se proteger de um desastre que afete uma Região inteira, seriam necessárias várias Regiões.

**18 — B.** O Lambda é *serverless*, acionado por eventos (como um *upload* no S3) e cobrado por requisição e duração.

**19 — C.** O DynamoDB é o NoSQL chave-valor gerenciado. RDS e Aurora são relacionais; Redshift é *data warehouse*.

**20 — C.** O Direct Connect é um link físico dedicado. A VPN também conecta, mas passa pela internet.

**21 — C.** O Glacier Deep Archive é a classe mais barata, feita para retenção longa com recuperação em horas.

**22 — B.** O EFS é um sistema de arquivos compartilhado (NFS). Um volume EBS, em geral, fica ligado a uma única instância.

**23 — B.** Infraestrutura como código (CloudFormation) torna o ambiente repetível, versionado e padronizado.

**24 — A.** O Athena executa SQL diretamente sobre o S3, sem servidor. O Glue faz ETL e catálogo; o QuickSight faz painéis; o Kinesis trata de *streaming*.

**25 — B.** O SQS é uma fila: guarda as mensagens até o consumidor processá-las. O SNS entrega na hora a vários assinantes (*pub/sub*).

**26 — A.** O Lex cria *chatbots* conversacionais. O Polly converte texto em fala; o Rekognition analisa imagens; o Textract extrai texto de documentos.

**27 — C.** As instâncias spot custam até 90% menos e são ideais para cargas tolerantes a interrupção.

**28 — C.** O AWS Budgets envia alertas por limite de custo real ou **previsto**. O Cost Explorer serve para analisar; o Pricing Calculator, para estimar antes de criar.

**29 — B.** O faturamento consolidado gera uma única fatura e soma o uso das contas para alcançar faixas de desconto. As SCPs controlam permissões máximas.

**30 — B.** O AWS Health Dashboard mostra os eventos da AWS que afetam a **sua** conta. O Trusted Advisor faz recomendações de boas práticas.
