# Amazon S3 — Simple Storage Service

## O que é?

Serviço de armazenamento de **objetos** que oferece escalabilidade, disponibilidade de dados, segurança e performance líderes do setor.

## Estrutura do S3

- **Bucket**: pasta raiz onde ficam os arquivos.
- **Objetos**: são os arquivos.
- **Key**: caminho do arquivo + nome do objeto (identificador único dentro do bucket).
- **Region**: o local onde a bucket foi hospedada fisicamente.

## Durabilidade

**99.999999999%** (11 noves) — igual em **todas** as classes de armazenamento. O que muda entre as classes é a **disponibilidade**, não a durabilidade.

## Versionamento

Bucket Versioning = Enable → permite manter várias versões do mesmo objeto.

**Delete em bucket versionado**: não apaga de verdade — adiciona um **Delete Marker** que esconde o objeto. Removendo o Delete Marker, o objeto volta a aparecer.

---

## Classes de Armazenamento

| Classe | Quando usar | Tempo de recuperação |
|---|---|---|
| **S3 Standard** | Alta durabilidade, disponibilidade e baixa latência. Arquivos usados com frequência (ex: imagens de produto em e-commerce) | Imediato |
| **S3 Intelligent-Tiering** | Quando você não sabe prever a frequência de acesso aos dados — move automaticamente entre níveis com base no uso | Imediato |
| **S3 Standard-IA** | Dados importantes, mas acessados raramente (ex: backups semanais). Menor custo de armazenamento, cobra por acesso | Imediato |
| **S3 One Zone-IA** | Igual ao Standard-IA, mas em apenas 1 AZ. Ideal para dados que podem ser recriados se perdidos | Imediato |
| **S3 Glacier Instant Retrieval** | Arquivos antigos que podem precisar de consulta instantânea (ex: relatórios de vendas antigos) | Milissegundos |
| **S3 Glacier Flexible Retrieval** | Arquivos quase nunca acessados, mas que precisam ser mantidos (ex: arquivos legais) | Minutos a horas |
| **S3 Glacier Deep Archive** | Classe mais barata — arquivamento de longo prazo (ex: 10 anos, auditorias anuais) | Até 12 horas |

### ⚠️ Pegadinha: Standard-IA x One Zone-IA

A diferença não é o preço (ambos têm lógica parecida) — é a **resiliência**: One Zone-IA fica em **1 única AZ**, Standard-IA replica em **múltiplas AZs**.

---

## Replication

- **CRR** (Cross-Region Replication): replica objetos entre regiões diferentes.
- **SRR** (Same-Region Replication): replica objetos dentro da mesma região.

Objetivo: reduzir latência de acesso para usuários em locais diferentes (ex: bucket nos EUA replicado para o Reino Unido).

---

## S3 Encryption

**Todos os objetos são encriptados.**

### Tipos

| Momento | O que significa |
|---|---|
| **Em repouso** | Quando o objeto está parado na bucket |
| **Em trânsito** | Quando o objeto está em upload/download/read/write (via **HTTPS**) |

### Criptografia em repouso (SSE)

| Tipo | Quem gerencia a chave |
|---|---|
| **SSE-S3** | AWS gerencia totalmente a chave |
| **SSE-KMS** | Chave gerenciada pelo serviço AWS KMS — cliente tem controle de política, rotação e auditoria (CloudTrail) |
| **SSE-C** | **Cliente** fornece e gerencia a própria chave — a AWS nunca a armazena |

## ⚠️ Pegadinha

Não confundir SSE-KMS com SSE-C: em ambos a AWS "processa" a criptografia, mas só em **SSE-C** o cliente é o único responsável pela chave, sem a AWS guardá-la.

---

## Storage Gateway

Serviço de armazenamento em nuvem híbrida que conecta a infraestrutura de TI local ao armazenamento da AWS.

---

## Políticas do Amazon S3

São regras escritas em formato **JSON** que definem o controle de acesso e a segurança de buckets e objetos.

### Tipos principais

| Tipo | Para que serve |
|---|---|
| **Bucket Policies** | Definem permissões de acesso ao bucket: permitem ou negam ações a usuários, outras contas AWS ou acesso público |
| **Lifecycle Policies** | Automatizam a transição de arquivos entre classes de armazenamento e a exclusão de dados após períodos definidos |
| **Políticas de Controle de Acesso da AWS Organizations** | Gerenciam centralmente permissões e configurações de segurança de várias contas AWS |

## 🧠 Para lembrar

- Durabilidade é sempre 11 noves; o que muda entre classes é disponibilidade e tempo de acesso.
- Glacier: Instant (ms) → Flexible (minutos/horas) → Deep Archive (até 12h) — quanto mais lento, mais barato.
- SSE-S3 = AWS cuida de tudo | SSE-KMS = AWS cuida, mas você audita | SSE-C = você cuida de tudo.
- Delete com versionamento = "esconde", não apaga.
