# Comparativos — os serviços que mais confundem na prova

[← Voltar](../README.md)

## Monitoramento e auditoria

| Pergunta da questão | Resposta |
|---|---|
| "Quem fez a alteração?", "qual usuário chamou a API?" | **AWS CloudTrail** |
| "Uso de CPU", "alarme", "métricas", "logs da aplicação" | **Amazon CloudWatch** |
| "Histórico de configuração", "recurso fora do padrão" | **AWS Config** |
| "Recomendações de boas práticas, custo e segurança" | **AWS Trusted Advisor** |
| "Evento da AWS afetando minha conta" | **AWS Health Dashboard** |

## Segurança

| Pergunta | Resposta |
|---|---|
| Ataque **DDoS** | **AWS Shield** |
| Bloquear **SQL injection**, XSS ou IPs em aplicação web | **AWS WAF** |
| Detectar **ameaças** e comportamento malicioso | **Amazon GuardDuty** |
| **Vulnerabilidades** em instâncias e contêineres | **Amazon Inspector** |
| **Dados sensíveis** no S3 | **Amazon Macie** |
| Visão **consolidada** dos achados de segurança | **AWS Security Hub** |
| **Relatórios de conformidade** da AWS | **AWS Artifact** |
| Gerenciar **chaves de criptografia** | **AWS KMS** (compartilhado) ou **AWS CloudHSM** (*hardware* dedicado) |
| **Senhas de banco** com rotação automática | **AWS Secrets Manager** |

## Mensageria e integração

| Serviço | Modelo | Exemplo |
|---|---|---|
| **Amazon SQS** | **Fila**: um consumidor processa cada mensagem | Pedidos aguardando processamento |
| **Amazon SNS** | ***Pub/sub***: uma mensagem para **vários** assinantes | Alerta por e-mail e SMS ao mesmo tempo |
| **Amazon EventBridge** | **Barramento de eventos**, com regras e agendamentos | "Quando X acontecer em um serviço, acione Y" |

## Conectividade híbrida

| AWS Site-to-Site VPN | AWS Direct Connect |
|---|---|
| Pela **internet**, criptografada | Link **dedicado e privado** |
| Configuração em minutos, baixo custo | Instalação leva semanas, custo maior |
| Latência variável | Latência **consistente**, alta banda |

## Bancos de dados

| Necessidade | Serviço |
|---|---|
| SQL tradicional gerenciado | **Amazon RDS** |
| Relacional de alto desempenho compatível com MySQL/PostgreSQL | **Amazon Aurora** |
| NoSQL chave-valor, escala ilimitada, *serverless* | **Amazon DynamoDB** |
| Cache em memória | **Amazon ElastiCache** |
| *Data warehouse* e análises | **Amazon Redshift** |
| Grafos | **Amazon Neptune** |
| Compatível com MongoDB | **Amazon DocumentDB** |

## Armazenamento

| Necessidade | Serviço |
|---|---|
| Arquivos, imagens, *backups*, *site* estático | **Amazon S3** |
| Disco de **uma** instância EC2 | **Amazon EBS** |
| Pasta **compartilhada** entre várias instâncias Linux | **Amazon EFS** |
| Compartilhamento de arquivos Windows (SMB) | **Amazon FSx for Windows File Server** |
| Arquivamento de longo prazo, mais barato | **S3 Glacier Deep Archive** |
| Padrão de acesso desconhecido | **S3 Intelligent-Tiering** |

## Computação

| Necessidade | Serviço |
|---|---|
| Controle total do servidor | **Amazon EC2** |
| Código por evento, sem servidor | **AWS Lambda** |
| Contêineres sem gerenciar servidores | **AWS Fargate** |
| Kubernetes gerenciado | **Amazon EKS** |
| Subir uma aplicação web só com o código | **AWS Elastic Beanstalk** |

## Custos

| Pergunta | Resposta |
|---|---|
| Estimar **antes** de criar | **AWS Pricing Calculator** |
| **Alerta** de orçamento | **AWS Budgets** |
| **Analisar** gastos passados e tendências | **AWS Cost Explorer** |
| Relatório **mais detalhado** | **AWS Cost and Usage Report** |
| **Uma fatura** para várias contas | **AWS Organizations** (faturamento consolidado) |

## Palavras-chave que entregam a resposta

| Se a questão diz... | Pense em... |
|---|---|
| "menor esforço operacional", "gerenciado", "sem servidores" | Serviço gerenciado ou *serverless* (RDS, Lambda, Fargate, DynamoDB) |
| "pode ser interrompido", "mais barato" | Instâncias **spot** |
| "1 ou 3 anos", "carga estável" | **Savings Plans** ou **instâncias reservadas** |
| "sobreviver à falha de um *data center*" | **Várias AZs** |
| "desastre regional" | **Várias Regiões** |
| "usuários no mundo todo", "baixa latência para conteúdo" | **CloudFront** (*edge locations*) |
| "repetível", "versionado", "modelo" | **CloudFormation** (IaC) |
| "credenciais temporárias" | **IAM *role*** |
| "login único em várias contas" | **IAM Identity Center** |
