# AWS Snow Family

## O que é?

Conjunto de dispositivos físicos usados para transferir grandes volumes de dados para a AWS e executar aplicações localmente, especialmente em locais com internet limitada ou inexistente.

## Serviços

### AWS Snowcone

Dispositivo compacto, ideal para **pequenas transferências de dados** e ambientes remotos com pouco espaço.

### AWS Snowball Edge

Voltado para transferência de **grandes volumes** de dados e para **computação local**, permitindo executar serviços como EC2 e Lambda sem depender de conexão constante com a internet.

### AWS Snowmobile (descontinuado)

Contêiner transportado por caminhão, desenvolvido para migrar até **100 PB** de dados de uma vez só. **Não está mais disponível** — tema de reconhecimento para a prova, não de uso.

## Comparações

| Serviço | Volume de dados | Uso principal |
|---|---|---|
| Snowcone | Pequeno | Transferência simples, pouco espaço físico |
| Snowball Edge | Grande | Transferência + computação local (EC2, Lambda) |
| Snowmobile | Até 100 PB | Descontinuado |

## ⚠️ Pegadinhas

- Snowmobile está descontinuado — se a prova perguntar "qual usar hoje", nunca é essa a resposta.
- Snowcone ≠ Snowball Edge: Snowcone é para transferências pequenas/ambientes compactos; Snowball Edge é para grandes volumes e roda cargas de trabalho localmente.

## 🧠 Para lembrar

- Snowcone = "pequeno e portátil"
- Snowball Edge = "grande e processa localmente"
- Snowmobile = "caminhão gigante, mas não existe mais"
