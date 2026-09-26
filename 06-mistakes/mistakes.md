# Role vs. Access Key fixa em código

**Situação:** EC2 precisa acessar o S3. Marquei "criar IAM user + access key no código".
**Correto:** Anexar uma **IAM Role** à instância.

**Por quê:** Access key fixa em código é risco de segurança (pode vazar, precisa rotação manual).
Role gera credenciais **temporárias** e é gerenciada automaticamente pela AWS.

**Classificação:** Caso de uso (não reconheci quando usar Role).

## 🧠 Como lembrar

> Serviço AWS falando com serviço AWS → **Role**.
> Pessoa logando no console/CLI → **User**.

---



# Deny implícito no IAM

**Situação:** Usuário sem grupo e sem política anexada. Achei que a AWS geraria uma política padrão.
**Correto:** Acesso **negado a tudo** por padrão.

**Por quê:** O IAM segue a regra do **deny implícito** — nada é permitido a menos que uma política diga explicitamente que sim.

**Classificação:** Conteúdo desconhecido (conceito novo).

## 🧠 Como lembrar

> No IAM, o padrão é "não" até que uma política diga "sim".



# Shared Responsibility Model — Quem faz o patch do SO?

## ❌ O erro

Pergunta: Quem é responsável por aplicar patches no sistema operacional de uma instância EC2?

Respondi: **A AWS**, pois ela gerencia toda a infraestrutura de qualquer serviço.

Correto: **O cliente**, pois EC2 é uma infraestrutura não gerenciada (IaaS) e o cliente controla o SO.

## Por que errei

Generalizei "AWS protege a infraestrutura global" como se isso cobrisse **tudo** dentro de qualquer serviço — inclusive o sistema operacional guest da instância. Mas infraestrutura global (hardware, rede, data center) é diferente do que roda **dentro** da instância.

## Conceito correto

O nível de responsabilidade **depende do quão gerenciado é o serviço**:

- **EC2 (IaaS, não gerenciado)** → cliente cuida do SO, patches, dados.
- **RDS / Lambda (gerenciado)** → AWS cuida do SO e do motor/runtime; cliente cuida principalmente de dados e configuração de acesso.

## 🧠 Como não errar de novo

Antes de responder "quem é responsável", perguntar: **"Esse serviço é gerenciado ou não gerenciado?"**
- Não gerenciado (EC2) → responsabilidades técnicas (SO, patch) = cliente.
- Gerenciado (RDS, Lambda, DynamoDB) → AWS assume SO/motor; cliente assume dados e acesso.

## Classificação

**Tipo de erro:** Conceito não compreendido (distinção entre nível de gerenciamento do serviço e onde a responsabilidade é traçada).



# Tipos de Instância EC2 — Confusão de gargalo

## ❌ Os erros

**Pergunta 1:** Qual tipo de instância é mais adequado para um servidor de jogos dedicado com alto uso de CPU?
Respondi: **Storage Optimized**
Correto: **Compute Optimized**

**Pergunta 2:** Qual tipo de instância é melhor para treinar modelos que dependem de GPU para cálculos de números flutuantes e renderização gráfica pesada?
Respondi: **Storage Optimized**
Correto: **Accelerated Computing**

## Por que errei

Associei "alta performance" / "processamento pesado" genericamente a Storage Optimized, sem identificar qual recurso era o gargalo real do cenário (CPU, GPU ou disco).

## Conceito correto

Cada tipo de instância resolve um gargalo diferente:

| Gargalo | Tipo de instância |
|---|---|
| CPU | Compute Optimized |
| Memória (RAM) | Memory Optimized |
| Disco (IOPS/velocidade) | Storage Optimized |
| GPU / gráficos | Accelerated Computing |
| Simulação extrema / ML pesado | HPC Optimized |
| Sem gargalo específico | General Purpose |

**Storage Optimized é sobre velocidade de leitura/gravação em disco — não tem nada a ver com CPU ou GPU.**

## 🧠 Como não errar de novo

Antes de responder, identificar a palavra-chave do cenário:
- "CPU intensivo", "processamento em lote", "jogos" → Compute Optimized
- "GPU", "gráficos", "números flutuantes" → Accelerated Computing
- "IOPS", "leitura/gravação em disco", "data warehousing" → Storage Optimized
- "banco de dados na memória" → Memory Optimized

## Classificação

**Tipo de erro:** Confusão entre serviços (tipos de instância com propósitos de "alta performance" parecidos, mas gargalos diferentes).
