# Simulado — 30 questões no estilo do CLF-C02

[← Voltar](../README.md) · [Gabarito comentado →](gabarito.md)

**Tempo sugerido:** 40 minutos. Anote as respostas e confira no [gabarito](gabarito.md) só no final.
A distribuição segue o peso dos domínios: 7 questões do domínio 1, 9 do domínio 2, 10 do domínio 3 e 4 do domínio 4.

---

**1.** Uma loja virtual recebe dez vezes mais acessos na Black Friday e quer que os servidores aumentem e diminuam automaticamente. Qual benefício da nuvem descreve essa necessidade?

- A) Alta disponibilidade
- B) Elasticidade
- C) Economia de escala
- D) Alcance global

**2.** Qual pilar do AWS Well-Architected Framework trata de minimizar o impacto ambiental das cargas de trabalho?

- A) Eficiência de performance
- B) Otimização de custos
- C) Sustentabilidade
- D) Excelência operacional

**3.** Uma empresa vai mover um servidor de aplicação para o Amazon EC2 sem nenhuma alteração. Qual estratégia de migração é essa?

- A) Refactor
- B) Replatform
- C) Rehost
- D) Repurchase

**4.** Qual afirmação descreve uma vantagem econômica da nuvem AWS?

- A) Exige grande investimento inicial em *hardware*
- B) Troca custos fixos de capital por custos variáveis
- C) Elimina toda a necessidade de gerenciar custos
- D) Garante preço fixo para sempre

**5.** Uma empresa quer usar as licenças de banco de dados que já possui, cobradas por núcleo físico. Que conceito de licenciamento é esse?

- A) Licença inclusa
- B) BYOL (*Bring Your Own License*)
- C) *Rightsizing*
- D) *Pay-as-you-go*

**6.** Quais são **duas** perspectivas do AWS Cloud Adoption Framework (AWS CAF)? *(Escolha duas.)*

- A) Pessoas (*People*)
- B) Marketing
- C) Plataforma (*Platform*)
- D) Vendas
- E) Jurídica

**7.** Um time quer reduzir o desperdício ajustando instâncias superdimensionadas ao uso real. Como se chama essa prática?

- A) *Lift and shift*
- B) Escalabilidade vertical
- C) *Rightsizing*
- D) Desacoplamento

**8.** No modelo de responsabilidade compartilhada, qual tarefa é do **cliente** ao usar o Amazon EC2?

- A) Manter a segurança física dos *data centers*
- B) Aplicar *patches* no sistema operacional convidado
- C) Substituir discos defeituosos dos servidores
- D) Manter a camada de virtualização

**9.** Ao usar o Amazon RDS, quem é responsável por aplicar *patches* no sistema operacional do servidor de banco de dados?

- A) O cliente
- B) A AWS
- C) Um parceiro da APN
- D) Ninguém: o RDS não usa sistema operacional

**10.** Um auditor precisa descobrir qual usuário excluiu uma tabela do DynamoDB na semana passada. Qual serviço fornece essa informação?

- A) Amazon CloudWatch
- B) AWS Config
- C) AWS CloudTrail
- D) Amazon Inspector

**11.** Onde um cliente obtém os relatórios de conformidade da AWS, como ISO 27001 e SOC 2?

- A) AWS Artifact
- B) AWS Trusted Advisor
- C) AWS Security Hub
- D) AWS Organizations

**12.** Qual é a forma recomendada de permitir que uma aplicação em uma instância EC2 leia arquivos de um *bucket* S3?

- A) Gravar a *access key* de um usuário IAM no código
- B) Usar as credenciais do usuário *root*
- C) Associar uma IAM *role* à instância
- D) Tornar o *bucket* público

**13.** Qual serviço protege aplicações web contra ataques de SQL *injection* e *cross-site scripting*?

- A) AWS Shield
- B) AWS WAF
- C) Amazon GuardDuty
- D) Amazon Macie

**14.** Quais são **duas** boas práticas para proteger o usuário *root*? *(Escolha duas.)*

- A) Ativar MFA
- B) Compartilhar a senha com a equipe de TI
- C) Criar *access keys* para automações
- D) Usar o *root* somente para tarefas que exigem esse usuário
- E) Usá-lo no dia a dia para evitar problemas de permissão

**15.** Uma empresa quer descobrir automaticamente se há números de cartão de crédito e dados pessoais armazenados em seus *buckets* S3. Qual serviço deve usar?

- A) Amazon Macie
- B) Amazon Inspector
- C) AWS Shield
- D) AWS Config

**16.** Qual serviço oferece um único login para que os funcionários acessem várias contas da AWS Organizations?

- A) AWS Secrets Manager
- B) AWS IAM Identity Center
- C) Amazon Cognito
- D) AWS Directory Service

**17.** Uma aplicação deve continuar disponível mesmo se um *data center* inteiro da AWS falhar. Qual é a abordagem correta?

- A) Usar uma instância maior
- B) Implantar em várias Zonas de Disponibilidade
- C) Usar uma *edge location*
- D) Ativar o AWS Shield

**18.** Uma equipe quer executar código toda vez que uma imagem for enviada ao S3, sem gerenciar servidores e pagando só pelo tempo de execução. Qual serviço atende?

- A) Amazon EC2
- B) AWS Lambda
- C) Amazon Lightsail
- D) AWS Batch

**19.** Qual banco de dados é um NoSQL chave-valor totalmente gerenciado, com latência de milissegundos em qualquer escala?

- A) Amazon RDS
- B) Amazon Redshift
- C) Amazon DynamoDB
- D) Amazon Aurora

**20.** Uma fábrica precisa de uma conexão privada e dedicada, que não passe pela internet, entre o seu *data center* e a AWS. Qual serviço deve usar?

- A) AWS Site-to-Site VPN
- B) Amazon CloudFront
- C) AWS Direct Connect
- D) Amazon Route 53

**21.** Dados de auditoria precisam ser mantidos por 10 anos, raramente serão acessados e podem levar horas para ser recuperados. Qual opção tem o **menor custo**?

- A) S3 Standard
- B) S3 Standard-IA
- C) S3 Glacier Deep Archive
- D) Amazon EBS

**22.** Várias instâncias EC2 Linux precisam acessar o mesmo sistema de arquivos ao mesmo tempo. Qual serviço usar?

- A) Amazon EBS
- B) Amazon EFS
- C) *Instance store*
- D) Amazon S3 Glacier

**23.** Uma equipe precisa recriar o mesmo ambiente (VPC, instâncias e banco) várias vezes, de forma padronizada e versionada. Qual é a melhor abordagem?

- A) Criar tudo manualmente pelo Console
- B) Usar AWS CloudFormation
- C) Abrir um chamado no AWS Support
- D) Usar o AWS Trusted Advisor

**24.** Qual serviço permite consultar com SQL arquivos CSV armazenados no Amazon S3, sem carregar os dados em um banco?

- A) Amazon Athena
- B) Amazon Kinesis
- C) AWS Glue
- D) Amazon QuickSight

**25.** Um sistema de pedidos deve guardar as mensagens até que o serviço de processamento as consuma, desacoplando os componentes. Qual serviço é o mais adequado?

- A) Amazon SNS
- B) Amazon SQS
- C) Amazon SES
- D) Amazon Connect

**26.** Uma empresa precisa de um *chatbot* de atendimento por texto e voz. Qual serviço da AWS foi feito para isso?

- A) Amazon Lex
- B) Amazon Polly
- C) Amazon Rekognition
- D) Amazon Textract

**27.** Um trabalho de renderização em lote pode ser interrompido e reiniciado sem prejuízo. Qual opção de compra do EC2 tem o **menor custo**?

- A) Sob demanda
- B) Instâncias reservadas
- C) Instâncias spot
- D) *Dedicated Hosts*

**28.** O gerente financeiro quer receber um e-mail quando o gasto mensal previsto ultrapassar US$ 1.000. Qual ferramenta deve usar?

- A) AWS Cost Explorer
- B) AWS Pricing Calculator
- C) AWS Budgets
- D) AWS Cost and Usage Report

**29.** Qual recurso do AWS Organizations permite receber uma única fatura para todas as contas e somar o uso para obter descontos por volume?

- A) *Service Control Policies*
- B) Faturamento consolidado
- C) *Cost allocation tags*
- D) AWS Control Tower

**30.** Qual serviço mostra eventos e manutenções programadas da AWS que afetam especificamente os recursos da sua conta?

- A) AWS Trusted Advisor
- B) AWS Health Dashboard
- C) Amazon CloudWatch
- D) AWS Config

---

[Ver gabarito comentado →](gabarito.md)
