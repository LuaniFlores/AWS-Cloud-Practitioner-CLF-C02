# Conceitos de Nuvem (Aula 00 e 01)

## O que é Computação em Nuvem?

Fornecimento de recursos de TI (servidores, armazenamento, banco de dados, rede) **sob demanda**, pela internet, com **pagamento conforme o uso**.

## Modelos de Serviço (quem cuida do quê)

| Modelo | O que você recebe | O que você gerencia | Exemplo AWS | Analogia |
|---|---|---|---|---|
| **IaaS** | Infraestrutura básica (servidor, storage, rede) | SO, aplicações, dados | Amazon EC2 | Alugar um terreno vazio e construir do seu jeito |
| **PaaS** | Plataforma pronta para rodar sua aplicação | Só seu código e seus dados | AWS Elastic Beanstalk | Alugar uma casa pronta, você só decora e mora |
| **SaaS** | Software pronto para uso | Praticamente nada (config de usuário) | Gmail, Netflix, Spotify | Ficar em um hotel, tudo já está pronto |

> ⚠️ Pegadinha: PaaS **não é responsabilidade técnica zero** — você ainda responde pelo seu código/dados. Vai diminuindo o controle (IaaS → PaaS → SaaS) e diminuindo a responsabilidade técnica, mas nunca chega a zero.

## Modelos de Implantação

- **Nuvem Pública**: recursos compartilhados entre clientes, gerenciados por um provedor (ex: AWS).
- **Nuvem Privada**: infraestrutura dedicada a uma única organização.
- **Nuvem Híbrida**: combinação dos dois, conforme a carga de trabalho.

## Economia da Nuvem

- **CapEx** (modelo tradicional): investimento grande e antecipado em hardware próprio.
- **OpEx** (modelo cloud): gasto operacional, conforme o uso, sem grande investimento inicial.
- A nuvem **transforma CapEx em OpEx** → um dos maiores benefícios financeiros.

## Elasticidade

Capacidade de **aumentar ou diminuir recursos automaticamente**, conforme a demanda (ex: Auto Scaling).

## 🧠 Para lembrar

- IaaS → EC2 → "monto tudo"
- PaaS → Elastic Beanstalk → "só o código"
- SaaS → app pronto → "só uso"
