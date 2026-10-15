# Domínio 4 — Faturamento, preços e suporte (12%)

[← Tecnologia](03-tecnologia-e-servicos.md) · [Voltar](../README.md)

## 4.1 Modelos de preço

### Opções de compra de computação (EC2)

| Opção | Como funciona | Use quando... | Economia (aprox.) |
|---|---|---|---|
| **Sob demanda** (*On-Demand*) | Paga por segundo ou hora, sem compromisso | Cargas curtas, imprevisíveis ou em teste | — |
| **Savings Plans** | Compromisso de **gasto por hora** (US$/h) por 1 ou 3 anos; *Compute Savings Plans* valem para EC2, Fargate e Lambda | Uso constante, com flexibilidade de família e Região | até 72% |
| **Instâncias reservadas** (RI) | Compromisso de 1 ou 3 anos com uma configuração | Cargas estáveis e previsíveis (ex.: banco 24x7) | até 72% |
| **Instâncias spot** | Capacidade ociosa da AWS; **podem ser interrompidas** com aviso de 2 minutos | Cargas tolerantes a falhas e flexíveis (*batch*, renderização, CI) | até 90% |
| ***Dedicated Hosts*** | Servidor físico inteiro dedicado a você | **Licenças por soquete ou núcleo (BYOL)** e exigências de conformidade | — |
| ***Dedicated Instances*** | Instâncias em *hardware* não compartilhado com outros clientes | Isolamento físico, sem controle do *host* | — |
| **Reservas de capacidade** (*Capacity Reservations*) | Garante capacidade em uma AZ específica, sem compromisso de prazo | Eventos críticos em que não pode faltar capacidade | — |

**Flexibilidade das RIs**: as *Standard RIs* dão maior desconto, mas permitem pouca mudança; as *Convertible RIs* permitem trocar de família, SO e *tenancy*, com desconto menor. RIs regionais aplicam o desconto a qualquer AZ da Região e a tamanhos diferentes da mesma família (Linux).

**RIs no AWS Organizations**: com o **faturamento consolidado**, o desconto de uma RI comprada em uma conta pode ser **compartilhado** com as outras contas da organização (o compartilhamento pode ser desativado).

### Transferência de dados

- **Entrada** de dados na AWS (*inbound*): geralmente **gratuita**.
- **Saída** para a internet (*outbound*): **cobrada**.
- **Entre Regiões**: cobrada.
- **Entre AZs** da mesma Região: normalmente cobrada (valor menor); **dentro da mesma AZ** por IP privado: geralmente gratuita.

### Armazenamento

Cobra-se por **GB armazenado por mês**, por **requisições** e por **recuperação** (classes IA e Glacier). Classes mais baratas para guardar costumam ser mais caras para recuperar.

## 4.2 Ferramentas de faturamento e custos

| Ferramenta | Para que serve |
|---|---|
| **AWS Pricing Calculator** | **Estimar** o custo **antes** de implantar |
| **AWS Budgets** | Definir **orçamentos** e receber **alertas** (de custo, de uso ou de cobertura de RI e Savings Plans); pode disparar ações |
| **AWS Cost Explorer** | **Visualizar e analisar** gastos passados, com previsão de até 12 meses |
| **AWS Cost and Usage Report (CUR)** | Relatório **mais detalhado** de custos, entregue no S3 |
| **AWS Organizations** | Gerenciar várias contas: **faturamento consolidado** (uma fatura e descontos por volume somados) e políticas SCP |
| ***Cost allocation tags*** | Etiquetas para separar custos por projeto, centro de custo ou cliente. Há as **geradas pela AWS** e as **definidas pelo usuário**; ambas precisam ser **ativadas** no console de faturamento para aparecer nos relatórios |
| **AWS Compute Optimizer** | Recomenda *rightsizing* com base no uso |

## 4.3 Suporte e recursos técnicos

### Planos do AWS Support

No fim de 2025 a AWS reformulou os planos, acrescentando recursos de IA e novos níveis.

| Plano | Para quem | Destaques | Resposta a caso crítico |
|---|---|---|---|
| **Basic** | Todas as contas, **gratuito** | Atendimento de conta e faturamento, documentação, re:Post, verificações básicas do Trusted Advisor, AWS Health Dashboard | — |
| **Business Support+** | Cargas em produção | Recomendações com IA e acesso a especialistas da AWS | 30 minutos |
| **Enterprise Support** | Cargas críticas | **TAM designado** (*Technical Account Manager*), monitoramento contínuo e resposta a incidentes de segurança | 15 minutos |
| **Unified Operations Support** | Missão crítica em grande escala | Equipe dedicada (TAM, engenheiro de domínio, especialista em faturamento), monitoramento 24x7 | 5 minutos |

Os planos anteriores (**Developer**, **Business** clássico e **Enterprise On-Ramp**) continuam valendo até **1º de janeiro de 2027** para quem já os contratou. Questões antigas de simulado ainda podem citá-los; o principal é saber que **o TAM está nos planos Enterprise** e que o **Basic é gratuito**.

### Outros recursos

| Recurso | Função |
|---|---|
| **AWS Trusted Advisor** | Verificações automáticas em seis categorias: **otimização de custos**, **performance**, **segurança**, **tolerância a falhas**, **cotas de serviço** e **excelência operacional** |
| **AWS Health Dashboard** | Eventos da AWS que **afetam as suas contas** (manutenções, incidentes) e o status geral dos serviços. A **AWS Health API** dá acesso programático |
| **AWS re:Post** | Comunidade de perguntas e respostas, com especialistas |
| **AWS Knowledge Center** | Respostas às dúvidas mais comuns |
| **AWS Prescriptive Guidance** | Guias e padrões de implementação |
| **Documentação, *whitepapers* e blogs** | Material técnico oficial |
| **AWS Trust & Safety** | Equipe para **denunciar abusos** cometidos com recursos da AWS (*spam*, ataques, conteúdo ilegal) |
| **AWS Professional Services** e **arquitetos de soluções** | Consultoria técnica da própria AWS |
| **AWS Partner Network (APN)** | Parceiros: **ISVs** (fornecedores de software) e **integradores de sistemas**. Benefícios para parceiros: treinamento e certificação, eventos e descontos por volume |
| **AWS Marketplace** | Catálogo de software de terceiros, com faturamento pela conta AWS, gestão de custos, governança e controle de licenças |

## Para fixar

1. Estimar o custo de uma arquitetura antes de criá-la → **AWS Pricing Calculator**.
2. Receber um alerta quando o gasto mensal passar de US$ 500 → **AWS Budgets**.
3. Processamento em lote que pode ser interrompido, ao menor custo → **instâncias spot**.
4. Licença de software cobrada por núcleo físico → ***Dedicated Hosts***.
5. Ver se há manutenção programada da AWS que afeta minhas instâncias → **AWS Health Dashboard**.
