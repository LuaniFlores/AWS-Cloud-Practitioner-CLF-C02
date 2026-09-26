# EC2 — Elastic Compute Cloud

## O que é?

Aluguel de servidores virtuais (**instâncias**), com diferentes opções de processadores, armazenamento, redes, sistemas operacionais e modelos de compra.

## Para que serve?

## Casos de uso comuns

- Hospedagem de website (webserver)
- Servidor de banco de dados
- Servidor de teste
- IA / Machine Learning
- Jogos online

## Conceitos importantes

- **Elasticidade**: ajusta o recurso conforme a demanda ("preciso de mais memória agora").
- **Escalabilidade**: capacidade de crescer, de forma **vertical** (aumentar o tamanho da instância) ou **horizontal** (adicionar mais instâncias).

## Tipos de instância EC2

Configurações específicas de servidores virtuais, projetadas com diferentes combinações de recursos. **A pegadinha da prova é identificar o gargalo do cenário** (CPU, memória, disco ou gráfico) e escolher o tipo certo.

| Gargalo do cenário | Tipo de instância | Casos de uso |
|---|---|---|
| Sem gargalo específico | **General Purpose** (uso geral) | Servidores web, repositórios de código, bancos de dados de pequeno/médio porte |
| CPU | **Compute Optimized** | Processamento em lote, transcodificação de mídia, servidores de jogos dedicados |
| Memória (RAM) | **Memory Optimized** | Bancos de dados, análise de dados, apps corporativos com grandes datasets em memória |
| GPU / gráficos | **Accelerated Computing** | GPUs para números flutuantes, processamento gráfico, correspondência de padrões |
| Disco (IOPS, leitura/gravação) | **Storage Optimized** | Bancos de dados de alto rendimento, processamento de dados, streaming |
| Simulação extrema / ML pesado | **HPC Optimized** | Simulações grandes e complexas, workloads de aprendizado profundo |

## Nomenclatura de instância

Formato: `<família><geração>.<tamanho>`

Exemplo: **t3.micro**
- `t` = família (otimizada para uso geral)
- `3` = geração (quanto mais recente, maior o número)
- `micro` = tamanho (define CPU e memória)

## AMI — Amazon Machine Image

### O que é?

Um molde pré-configurado que contém tudo que é necessário para iniciar um sistema operacional (Linux, Ubuntu, macOS, Windows).

### Para que serve?

Serve como base para criar instâncias EC2.

## ⚠️ Pegadinhas

- Não confundir o **gargalo do cenário** com o tipo de instância — "alta performance" sozinho não diz nada; a palavra-chave (CPU, GPU, memória, disco) é que define o tipo certo.
- **Storage Optimized** é sobre velocidade de disco (IOPS), **não** sobre poder de processamento — fácil de confundir com Compute ou Accelerated quando o cenário parece "pesado".

## 🧠 Para lembrar

- Compute = CPU | Memory = RAM | Storage = Disco | Accelerated = GPU | HPC = Simulação extrema | General = "não sei, uso geral"
