# Infraestrutura Global da AWS (Aula 03)

## Região (Region)

Localização geográfica onde a AWS possui um **cluster de data centers**. Cada Região é **completamente independente** das demais (própria energia, sistema, isolamento).

- Cada Região contém múltiplas Availability Zones.
- AWS possui dezenas de Regiões distribuídas pelos continentes.

## Availability Zone (AZ)

Um ou mais data centers físicos dentro de uma Região, com energia, refrigeração e rede **independentes**.

- ⚠️ **Toda Região tem no mínimo 3 AZs** (não 2 — pegadinha comum).
- Conectadas entre si por fibra óptica de altíssima velocidade e baixa latência.
- Fisicamente separadas para que um desastre não afete todas ao mesmo tempo.

### 🧠 Exemplo de Alta Disponibilidade
Uma aplicação web roda em instâncias EC2 distribuídas em 2+ AZs dentro da mesma Região. Se uma AZ cair, a aplicação continua funcionando na outra.

## Por que a Infraestrutura Global importa? (escolha de Região)

- **Performance**: escolher a região certa reduz a latência para os usuários.
- **Custo**: preços variam entre Regiões (até ~30% de diferença em alguns serviços).
- **Conformidade**: regulamentações como a LGPD exigem que dados fiquem em regiões específicas.

## Edge Locations

Pontos de presença da AWS espalhados pelo mundo, mais próximos dos usuários finais, usados para entregar conteúdo com menor latência.

- Usadas principalmente pelo **Amazon CloudFront** (CDN da AWS).
- **Diferença-chave**: Regiões têm serviços completos; Edge Locations focam em **cache e entrega de conteúdo**.

## AWS Local Zones x AWS Outposts

| | Local Zones | Outposts |
|---|---|---|
| O que é | Extensão de uma Região, mais perto de grandes centros populacionais | Rack físico da AWS instalado dentro do data center do cliente |
| Objetivo | Baixíssima latência para aplicações críticas | Rodar AWS on-premises, gerenciado remotamente pela AWS |
| Exemplo | Los Angeles, Denver, Miami | Hospitais, fábricas, bases militares |

## 🧠 Para lembrar

- Região = "país" (independente).
- AZ = "cidade" dentro do país (isolada, mas conectada).
- Edge Location = "posto avançado" pertinho do usuário, só para entrega rápida de conteúdo.
