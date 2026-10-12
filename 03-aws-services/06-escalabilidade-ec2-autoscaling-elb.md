# Escalabilidade EC2 — Auto Scaling e Load Balancing

## Escalabilidade

| Tipo | O que é | Termo técnico |
|---|---|---|
| **Vertical** | Trocar o tipo/tamanho da instância (ex: t2.micro 1GB → t2.2xlarge 32GB), aumentando recursos de uma única instância | **Scale Up / Scale Down** |
| **Horizontal** | Adicionar ou remover instâncias (Auto Scaling + ELB) | **Scale Out / Scale In** |

## Elasticidade

Elástico: se adapta automaticamente às mudanças de carga (load), via Auto Scaling.

## Disponibilidade

Auto Scaling melhora a disponibilidade de duas formas:
1. **Distribuição em múltiplas AZs**: se uma AZ cair, as instâncias nas outras AZs continuam funcionando ("se um cair, tem o outro").
2. **Self-healing**: monitora a saúde das instâncias (health checks) e **substitui automaticamente** qualquer uma que falhe, independente de AZ.

## Auto Scaling

### O que é?

Sistema que aumenta (**scale out**) ou diminui (**scale in**) automaticamente os recursos (instâncias) da aplicação, conforme a demanda.

### Exemplo prático

- **Dia normal**: 2 servidores são suficientes.
- **Black Friday**: muito acesso → Auto Scaling adiciona mais servidores (scale out).
- **Madrugada**: pouco acesso → Auto Scaling remove servidores desnecessários (scale in).

## Balanceamento de Carga (ELB)

Auto Scaling pode ser usado junto com **Elastic Load Balancing (ELB)** para distribuir o tráfego entre várias instâncias EC2, melhorando disponibilidade e tolerância a falhas.

### Tipos de Load Balancer

| Tipo | Tráfego | Foco |
|---|---|---|
| **ALB** — Application Load Balancer | HTTP e HTTPS | Inteligência de roteamento, sistemas web |
| **NLB** — Network Load Balancer | TCP, UDP e TLS | Velocidade extrema, alta performance de rede |
| **CLB** — Classic Load Balancer | HTTP, HTTPS, TCP e SSL | Geração **legada** — AWS recomenda ALB/NLB para novas aplicações |

## ⚠️ Pegadinhas

- Não confundir **Scale Up/Down** (vertical) com **Scale Out/In** (horizontal) — a prova testa a terminologia exata.
- Disponibilidade via Auto Scaling não é só "mais de uma AZ" — inclui também o **self-healing** (substituição automática de instâncias não saudáveis).
- CLB ainda existe mas é tema de **reconhecimento**, não de uso recomendado — ALB e NLB são a escolha atual.

## 🧠 Para lembrar

- Vertical = "Up/Down" (uma instância maior ou menor)
- Horizontal = "Out/In" (mais ou menos instâncias)
- ALB = Web (camada de aplicação) | NLB = Velocidade (camada de rede) | CLB = Legado
