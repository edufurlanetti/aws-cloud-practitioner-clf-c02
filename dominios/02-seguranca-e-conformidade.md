# Domínio 2 — Segurança e conformidade (30%)

[← Conceitos de nuvem](01-conceitos-de-nuvem.md) · [Voltar](../README.md) · [Próximo: Tecnologia →](03-tecnologia-e-servicos.md)

## 2.1 Modelo de responsabilidade compartilhada

> **AWS**: segurança **DA** nuvem. **Cliente**: segurança **NA** nuvem.

| AWS é responsável por | O cliente é responsável por |
|---|---|
| Data centers e segurança física | Dados e sua classificação |
| Hardware, rede física e virtualização | Contas, usuários e permissões (IAM) |
| Infraestrutura global (Regiões, AZs, *edge*) | Configuração de *security groups* e NACLs |
| Software dos serviços gerenciados | Criptografia (decidir usar e gerenciar chaves) |
| | SO convidado e *patches*, **no caso do EC2** |

**Responsabilidades compartilhadas**: gestão de *patches*, gestão de configuração, conscientização e treinamento. Cada parte cuida da sua camada.

### A responsabilidade muda conforme o serviço

| Serviço | Quem aplica *patch* no SO? | O que sobra para o cliente |
|---|---|---|
| **Amazon EC2** (IaaS) | **Cliente** | SO, aplicação, *firewall* da instância, dados |
| **Amazon RDS** (gerenciado) | **AWS** | Usuários do banco, rede (*security groups*), dados, decidir criptografar |
| **AWS Lambda** (*serverless*) | **AWS** | Código da função, permissões (IAM) e dados |

Quanto mais gerenciado o serviço, menos responsabilidade fica com o cliente.

## 2.2 Segurança, governança e conformidade

### Conformidade

- **AWS Artifact**: portal **gratuito** para baixar relatórios de conformidade da AWS (ISO, SOC, PCI) e aceitar acordos, como o BAA da HIPAA.
- Os requisitos variam por **país** (ex.: LGPD no Brasil, GDPR na Europa) e por **setor** (saúde, financeiro). O cliente escolhe a Região, e com isso decide onde ficam os dados (soberania de dados).

### Criptografia

- **Em trânsito**: TLS/HTTPS. O **AWS Certificate Manager (ACM)** emite certificados.
- **Em repouso**: discos, bancos e objetos. O **AWS KMS** gerencia chaves; o **AWS CloudHSM** oferece um *hardware* dedicado de chaves.

### Logs e governança — não confunda

| Serviço | Responde à pergunta |
|---|---|
| **AWS CloudTrail** | **Quem** fez **o quê** e **quando**? (auditoria de chamadas de API) |
| **Amazon CloudWatch** | **Como está** o desempenho? Métricas, logs, alarmes e painéis |
| **AWS Config** | **Como estava configurado** o recurso e se está **em conformidade** com as regras |
| **AWS Audit Manager** | Coleta evidências para auditorias |
| **Relatórios de acesso** (IAM *credential report*, *access advisor*) | Quem tem credenciais e quais permissões não são usadas |

## 2.3 Gerenciamento de acesso

### AWS IAM

- **Usuário**: pessoa ou aplicação com credenciais de longo prazo.
- **Grupo**: conjunto de usuários que recebem as mesmas permissões. Grupos não contêm outros grupos.
- **Função (*role*)**: credenciais **temporárias** assumidas por serviços (ex.: EC2 acessando o S3), por outras contas ou por identidades federadas.
- **Política**: documento JSON com as permissões.
  - **Gerenciada pela AWS**: pronta, mantida pela AWS.
  - **Gerenciada pelo cliente**: reutilizável, criada por você.
  - ***Inline***: embutida em uma única identidade.
- **Princípio do menor privilégio**: conceder somente o necessário.

### Usuário *root*

- É criado junto com a conta e tem **acesso total**.
- **Proteja-o**: ative **MFA**, não crie *access keys* para ele, use-o apenas para tarefas exclusivas e crie um usuário administrativo para o dia a dia.
- **Tarefas que só o *root* pode fazer** (exemplos): alterar o e-mail, o nome e a senha da conta; **fechar a conta**; restaurar as permissões de um administrador IAM que perdeu o acesso; ativar o **MFA Delete** em um bucket S3; registrar-se como vendedor no *Reserved Instance Marketplace*.

### Autenticação e credenciais

- **MFA**: segundo fator (aplicativo, chave física).
- **AWS IAM Identity Center** (sucessor do AWS SSO): login único para várias contas da AWS Organizations e aplicações. É o recomendado para pessoas.
- **Federação**: usar identidades externas (Active Directory, Google, provedores SAML/OIDC) sem criar usuários IAM.
- **Funções entre contas** (*cross-account roles*): acessar outra conta sem compartilhar senhas.
- **Políticas de senha**: complexidade, expiração e reutilização.
- **Guardar segredos**: **AWS Secrets Manager** (rotação automática de senhas de banco) e **AWS Systems Manager Parameter Store** (parâmetros e segredos simples).

## 2.4 Serviços de segurança

| Serviço | Função |
|---|---|
| **AWS Shield** | Proteção contra **DDoS**. *Standard* é gratuito e automático; *Advanced* é pago e inclui equipe de resposta |
| **AWS WAF** | *Firewall* de **aplicação web** (camada 7): bloqueia SQL *injection*, XSS e IPs específicos |
| **AWS Firewall Manager** | Gerencia regras de WAF, Shield e *security groups* em **várias contas** |
| **Amazon GuardDuty** | **Detecção de ameaças** com *machine learning* a partir de logs (CloudTrail, VPC Flow Logs, DNS) |
| **Amazon Inspector** | **Varredura de vulnerabilidades** em EC2, imagens de contêiner e Lambda |
| **AWS Security Hub** | **Painel central** que consolida achados de segurança e verifica boas práticas |
| **Amazon Macie** | Descobre **dados sensíveis** (dados pessoais, cartões) no S3 |
| **Amazon Detective** | Investiga a causa raiz de incidentes |
| **AWS Trusted Advisor** | Recomendações, inclusive de segurança (ex.: *buckets* públicos, MFA no *root*) |
| **Security groups** | *Firewall* da **instância**; *stateful*, só regras de permitir |
| **Network ACLs** | *Firewall* da **sub-rede**; *stateless*, regras de permitir e de negar |

Para encontrar informações de segurança: **AWS Security Center**, **AWS Security Blog**, **AWS Knowledge Center** e documentação. Produtos de segurança de terceiros estão no **AWS Marketplace**.

## Para fixar

1. Quem aplica *patches* no SO de uma instância EC2? → **O cliente.**
2. Serviço para auditar quem excluiu um *bucket* S3 → **AWS CloudTrail.**
3. Baixar o relatório SOC 2 da AWS → **AWS Artifact.**
4. Detectar chamadas de API suspeitas e mineração de criptomoeda → **Amazon GuardDuty.**
5. Dar a uma instância EC2 acesso ao S3 sem guardar chaves → **IAM *role*.**
