# Armazenamento EC2 — EBS, EFS e FSx

## As 3 categorias de armazenamento da AWS

| Categoria | Serviço | Característica |
|---|---|---|
| **Bloco** | EBS | Vinculado a 1 instância, na mesma AZ |
| **Arquivo** | EFS (Linux/NFS) e FSx (Windows/SMB ou Lustre) | Compartilhável entre várias instâncias/AZs |
| **Objeto** | S3 | Visto em detalhe no próximo módulo |

---

## EBS — Elastic Block Store (Disco)

### O que é?

Serviço de armazenamento em bloco de alto desempenho oferecido pela AWS para uso com EC2.

### Conceito importante

**Não compartilha com múltiplas zonas e instâncias** — por padrão, um volume EBS está vinculado a uma única instância, na mesma Availability Zone.

### Principais características

1. Desempenho de armazenamento
2. Durabilidade
3. Tipos de volumes
4. Backup com Snapshot
5. Criptografia
6. Integração com AWS

### Snapshot

O EBS oferece a capacidade de criar cópias dos seus volumes, que são armazenadas no **Amazon S3** para durabilidade.

### Tipos de volume EBS

| Tipo | Nome | Uso |
|---|---|---|
| SSD | **gp3** (General Purpose) | Uso geral, padrão para a maioria dos casos |
| SSD | **io2** (Provisioned IOPS) | Bancos de dados críticos, IOPS alta e consistente |
| HDD | **st1** (Throughput Optimized) | Big data, processamento de logs (mais espaço, mais lento) |
| HDD | **sc1** (Cold HDD) | Dados acessados raramente, menor custo |

---

## EFS — Elastic File System

### O que é?

Serviço de armazenamento de arquivos totalmente gerenciado, projetado para ser altamente disponível, durável e seguro.

### Para que serve?

Facilita o compartilhamento de arquivos entre instâncias EC2 e outros serviços, **em diferentes AZs simultaneamente** (ex: Server1 em us-east-1a e Server2 em us-east-1c acessando o mesmo EFS via Mount Target).

### Conceito importante

Compatível principalmente com **Linux**, via protocolo **NFS** (Network File System).

---

## FSx

### O que é?

Serviço que torna mais fácil executar sistemas de arquivos totalmente gerenciados na AWS. Suporta sistemas de arquivos **Windows** e **Lustre**.

### FSx for Windows File Server

Serviço de armazenamento em nuvem totalmente compatível com Windows. Roda em Windows Server e oferece criptografia, deduplicação de dados e acesso via protocolo **SMB** (Server Message Block) — o equivalente Windows ao NFS do Linux.

### FSx for Lustre

Serviço totalmente gerenciado e otimizado para **computação de alta performance**. Facilita a execução do sistema de arquivos Lustre para acelerar cargas de trabalho intensivas: **Big Data, Machine Learning e processamento de mídia**.

## ⚠️ Pegadinhas

- EBS = bloco, preso a 1 instância/AZ. EFS/FSx = arquivo, compartilhável entre instâncias e AZs. Não confundir os dois modelos.
- EFS (Linux/NFS) x FSx for Windows (Windows/SMB): mesma ideia de "arquivo compartilhado", mas sistemas operacionais e protocolos diferentes.
- FSx for Lustre não é para compartilhamento comum de arquivos — é para computação de alta performance (HPC-like).

## 🧠 Para lembrar

- EBS = "HD particular de uma instância"
- EFS = "pasta compartilhada do Linux"
- FSx Windows = "pasta compartilhada do Windows"
- FSx Lustre = "turbo pra Big Data e ML"
