# Plano de estudos — 6 semanas

[← Voltar](README.md)

Cerca de **5 horas por semana**, por exemplo 45 minutos por dia nos dias úteis e uma revisão no fim de semana. Quem já trabalha com nuvem pode condensar o plano em 3 semanas.

| Semana | Conteúdo | Atividade prática (no [AWS Free Tier](https://aws.amazon.com/free/)) |
|---|---|---|
| **1** | [Domínio 1](dominios/01-conceitos-de-nuvem.md): benefícios da nuvem, modelos de serviço, Well-Architected, CAF, 7 Rs | Criar a conta, ativar **MFA no *root***, criar um usuário administrativo e configurar o **AWS Budgets** com alerta de US$ 1 |
| **2** | [Domínio 2](dominios/02-seguranca-e-conformidade.md): responsabilidade compartilhada, IAM, criptografia, serviços de segurança | Criar grupo e usuário IAM com política de menor privilégio; explorar o **AWS Artifact** e o **Trusted Advisor** |
| **3** | [Domínio 3](dominios/03-tecnologia-e-servicos.md), parte 1: infraestrutura global, computação, redes | Subir uma instância **EC2** (t2/t3.micro), acessar por SSH ou Instance Connect, ver o *security group* e depois **encerrar** |
| **4** | [Domínio 3](dominios/03-tecnologia-e-servicos.md), parte 2: armazenamento, bancos, IA/ML, análise e integração | Criar um *bucket* **S3**, publicar um *site* estático e criar uma regra de ciclo de vida; criar uma função **Lambda** "Olá, mundo" |
| **5** | [Domínio 4](dominios/04-faturamento-precos-e-suporte.md) e os [comparativos](resumos/comparativos.md) | Montar uma estimativa no **Pricing Calculator** e explorar o **Cost Explorer** |
| **6** | Revisão e simulados | Fazer o [simulado](simulado/simulado.md) e a prova prática oficial do Skill Builder; revisar os erros; **agendar a prova** quando acertar 80% ou mais |

## Dicas para o dia da prova

- Leia o **final da pergunta** primeiro: "qual é o **mais econômico**?", "qual tem **menor esforço operacional**?". O critério decide entre respostas que parecem certas.
- Elimine as alternativas absurdas; geralmente sobram duas.
- Nas questões de múltipla resposta, o enunciado informa **quantas** alternativas escolher.
- Marque as questões difíceis para revisão e **não deixe nenhuma em branco**.
- A prova pode ser feita **em português**, no centro de testes ou *online*. Quem não é falante nativo de inglês pode pedir **acomodação de +30 minutos** ao agendar a versão em inglês.

> **Cuidado com custos:** sempre exclua o que criar nas práticas (instâncias, IPs elásticos, NAT Gateways) e mantenha o alerta do AWS Budgets ativo.
