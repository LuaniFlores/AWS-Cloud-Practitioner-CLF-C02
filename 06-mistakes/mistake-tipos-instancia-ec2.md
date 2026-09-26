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
