# Security Group, Firewall e Stateful

## Firewall (conceito geral)

Barreira que controla o tráfego de rede que entra e sai de um recurso, permitindo ou bloqueando conexões com base em regras (IP de origem, porta, protocolo).

## Security Group

### O que é?

Firewall virtual da AWS, aplicado no nível da **instância** (via ENI — Elastic Network Interface), não da sub-rede.

### Comportamento padrão

- Bloqueia **todo** tráfego de entrada.
- Libera **todo** tráfego de saída.
- Você só adiciona **regras de permissão** (não existe regra de "negar" em Security Group).

## Stateful

### O que significa?

Security Group **lembra da conexão**. Se uma conexão de entrada é permitida, a resposta de saída dessa mesma conexão é **automaticamente permitida**, mesmo sem regra de saída criada.

### Exemplo prático

- Instância A inicia um REQUEST para a instância B.
- SG de B precisa de uma regra de entrada permitindo o IP de A.
- O REPLY de B de volta para A é liberado automaticamente — sem regra de saída no SG de B nem regra de entrada extra no SG de A.

### Ponto de atenção

Statefulness vale **por conexão iniciada**, não é uma via de mão dupla liberada entre A e B. Se B quiser iniciar sua própria conexão nova com A (não uma resposta), o SG de A precisa da própria regra de entrada explícita.

## Comparações

| | Security Group | NACL |
|---|---|---|
| Nível | Instância | Sub-rede |
| Regras | Só "permitir" | Permitir e negar |
| Stateful? | Sim | Não (stateless) |

## ⚠️ Pegadinhas

- Stateful não significa "libera tudo entre A e B" — só libera a **resposta** da conexão que a própria instância iniciou ou aceitou.
- Não confundir Security Group (instância, stateful) com NACL (sub-rede, stateless) — tema que será aprofundado no módulo de Rede.

## 🧠 Para lembrar

- Security Group = "deny by default, allow explicitamente".
- Stateful = "eu lembro que eu perguntei, então aceito a resposta sem pedir de novo".
