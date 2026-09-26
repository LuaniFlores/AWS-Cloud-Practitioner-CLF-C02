# Modelos de Preço — EC2

## O que são?

Diferentes formas de pagar pelo uso de instâncias EC2, cada uma com um trade-off entre **preço**, **flexibilidade** e **risco de interrupção**.

## Modelos

### On-Demand (mais caro)

Você sobe a instância, ela gera a conta e você paga no final do mês. Sem compromisso, sem desconto — é o modelo mais flexível e também o mais caro por unidade de tempo.

### Reserved Instances

Compromisso com um **tipo específico de instância e região**, por **1 ou 3 anos**, em troca de desconto significativo em relação ao On-Demand. É rígido: o desconto vale só pra aquela combinação reservada.

### Savings Plans

Modelo de preços flexível que oferece preços reduzidos mediante um compromisso de **gasto por hora** (ex: $10/hora) por um período. Diferente do Reserved Instances, o compromisso não é preso a um tipo de instância específico — tem flexibilidade entre famílias, tamanhos e até serviços (Lambda, Fargate).

### Instâncias Spot

Você utiliza recursos ociosos da nuvem com até 90% de desconto. Contudo, a AWS pode encerrar sua instância a qualquer momento, se precisar desses recursos de volta. Ideal para workloads tolerantes a interrupção.

## Comparações

| Modelo | Compromisso | Desconto | Risco de interrupção |
|---|---|---|---|
| On-Demand | Nenhum | Nenhum (mais caro) | Nenhum |
| Reserved Instances | 1–3 anos, tipo/região fixos | Alto | Nenhum |
| Savings Plans | 1–3 anos, gasto por hora (flexível) | Alto | Nenhum |
| Spot | Nenhum | Até 90% | Alto (AWS pode retomar) |

## ⚠️ Pegadinhas

- **Reserved Instances x Savings Plans**: os dois exigem compromisso de longo prazo com desconto parecido, mas Reserved é **rígido** (instância + região fixas) e Savings Plans é **flexível** (compromisso de gasto, não de recurso específico).
- Spot não é "mais barato e sem risco" — o desconto alto vem justamente do risco de interrupção.

## 🧠 Para lembrar

- On-Demand = "sem compromisso, pago o que der"
- Reserved = "casei com esse tipo de instância por 1–3 anos"
- Savings Plans = "prometo gastar X por hora, mas escolho onde"
- Spot = "pego a sobra da AWS, mas posso perder a qualquer momento"
