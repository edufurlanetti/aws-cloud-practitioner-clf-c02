# Domínio 1 — Conceitos de nuvem (24%)

[← Voltar](../README.md) · [Próximo: Segurança →](02-seguranca-e-conformidade.md)

## 1.1 Benefícios da nuvem AWS

**Computação em nuvem** é a entrega de recursos de TI sob demanda, pela internet, com pagamento conforme o uso.

| Benefício | O que significa | Palavra-chave na questão |
|---|---|---|
| **Elasticidade** | Aumentar e reduzir recursos **automaticamente** conforme a demanda | "picos imprevisíveis", "automaticamente" |
| **Escalabilidade** | Capacidade de crescer para atender a mais carga | "crescimento" |
| **Alta disponibilidade** | O sistema continua funcionando mesmo com falhas, usando várias Zonas de Disponibilidade | "sem interrupção", "tolerância a falhas" |
| **Agilidade** | Criar recursos em minutos, experimentar e inovar rápido | "reduzir o tempo para", "experimentar" |
| **Alcance global** | Implantar em várias Regiões do mundo em minutos | "usuários em outros países", "baixa latência" |
| **Economia de escala** | A AWS compra em volume gigantesco e repassa preços menores | "preços menores com o tempo" |
| **Trocar CapEx por OpEx** | Em vez de comprar servidores (investimento), paga-se pelo uso (despesa variável) | "sem investimento inicial" |
| **Parar de adivinhar capacidade** | Sem superdimensionar nem faltar recurso | "capacidade ociosa" |

### Modelos de serviço

| Modelo | Você gerencia | Exemplo AWS |
|---|---|---|
| **IaaS** | SO, aplicação, dados | Amazon EC2 |
| **PaaS** | Aplicação e dados | AWS Elastic Beanstalk, Amazon RDS |
| **SaaS** | Só o uso | Amazon WorkSpaces, Amazon Connect |

### Modelos de implantação

- **Nuvem** (*cloud-native*): tudo na AWS.
- **Híbrido**: parte *on-premises* e parte na nuvem, conectadas (ex.: AWS Direct Connect, AWS Outposts).
- ***On-premises*** (nuvem privada): infraestrutura própria, com ferramentas de virtualização.

## 1.2 AWS Well-Architected Framework — os 6 pilares

| Pilar | Foco | Dica de memorização |
|---|---|---|
| **Excelência operacional** | Executar e monitorar sistemas, automatizar mudanças, aprender com falhas | operações como código |
| **Segurança** | Proteger dados, sistemas e ativos | menor privilégio, rastreabilidade |
| **Confiabilidade** | Recuperar-se de falhas e atender à demanda | Multi-AZ, recuperação automática |
| **Eficiência de performance** | Usar os recursos certos de forma eficiente | escolher o tipo certo de instância |
| **Otimização de custos** | Evitar gastos desnecessários | *rightsizing*, pagar só o que usa |
| **Sustentabilidade** | Minimizar o impacto ambiental | maximizar a utilização, reduzir desperdício |

> A ferramenta **AWS Well-Architected Tool** avalia uma carga de trabalho frente aos pilares.

## 1.3 Migração para a nuvem

### AWS Cloud Adoption Framework (AWS CAF) — 6 perspectivas

- **Negócios**: Business, People e Governance.
- **Técnicas**: Platform, Security e Operations.

Os **resultados de negócio** prometidos pelo CAF: menor risco de negócio, melhor desempenho em ESG (ambiental, social e de governança), aumento de receita e maior eficiência operacional.

### Os 7 Rs da migração

| Estratégia | O que é |
|---|---|
| **Retire** (aposentar) | Desligar o que não é mais necessário |
| **Retain** (reter) | Manter no local, por ora |
| **Rehost** (*lift and shift*) | Mover como está, por exemplo para EC2 |
| **Relocate** | Mover a plataforma inteira sem alterações (ex.: VMware Cloud on AWS) |
| **Replatform** (*lift, tinker and shift*) | Pequenos ajustes, como trocar o banco próprio pelo Amazon RDS |
| **Repurchase** | Trocar por um produto SaaS |
| **Refactor / Re-architect** | Reescrever para nuvem nativa (ex.: *serverless*) |

### Ferramentas de apoio à migração

- **AWS Database Migration Service (DMS)**: migra bancos com o mínimo de indisponibilidade, por replicação contínua.
- **AWS Schema Conversion Tool (SCT)**: converte esquemas entre motores diferentes (ex.: Oracle para Aurora PostgreSQL).
- **AWS Snow Family**: transferência física de grandes volumes de dados quando a rede é lenta ou cara.
- **AWS Migration Hub** e **AWS Application Migration Service**: acompanhar e executar migrações de servidores.

## 1.4 Economia da nuvem

- **Custos fixos × variáveis**: no *data center* próprio, os custos são fixos (servidores, energia, refrigeração, espaço, pessoal); na nuvem, viram custos variáveis.
- **Custos *on-premises* ocultos**: energia, refrigeração, segurança física, manutenção de hardware e substituição a cada ciclo.
- **Licenciamento**:
  - **BYOL** (*Bring Your Own License*): usa licenças que a empresa já possui, às vezes exigindo hosts dedicados.
  - **Licença inclusa**: o custo da licença vem embutido no preço do serviço.
- ***Rightsizing***: ajustar o tamanho do recurso ao uso real. É a primeira ação de otimização de custos.
- **Automação**: menos trabalho manual e menos erros; recursos criados e destruídos por código (ex.: AWS CloudFormation).

## Para fixar

1. Uma empresa quer pagar apenas pelo que usa, sem comprar servidores. Qual benefício? → **Trocar despesas de capital por despesas variáveis.**
2. Qual pilar do Well-Architected trata de se recuperar de falhas? → **Confiabilidade.**
3. Migrar um banco Oracle para o Amazon Aurora com a menor indisponibilidade possível → **AWS SCT** (esquema) + **AWS DMS** (dados).
