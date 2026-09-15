# IAM Básico e Formas de Acesso à AWS (Aula 02)

## Conta Root x Usuário IAM

- **Conta Root**: acesso total (cobrança, segurança, exclusão da conta). Só usar para tarefas administrativas raras.
  - ✅ Habilitar **MFA** na root.
  - ✅ Nunca gerar/usar access key da root — se existir, desabilitar.
- **Usuário IAM**: criado para uso diário, seguindo o **princípio do menor privilégio** (acesso mínimo necessário).

## Formas de Acessar a AWS

| Forma | O que é | Quando usar |
|---|---|---|
| **Console** | Interface visual no navegador | Uso manual, exploração, config pontual |
| **CLI** | Comandos de texto no terminal | Automação, tarefas repetitivas, scripts |
| **SDK** | Bibliotecas dentro do seu código (Python, JS, Java, .NET, Go...) | Aplicações que precisam falar com a AWS programaticamente |

Estrutura de um comando CLI:
```
aws <serviço> <ação> [parâmetro]
aws s3 ls
```

## IAM — Identity and Access Management

Controla **quem pode fazer o quê** dentro da conta AWS.

- **Usuário**: identidade individual (pessoa ou aplicação).
- **Grupo**: conjunto de usuários com as mesmas permissões.
- **Política**: documento que define o que é permitido fazer.
- **Role (função)**: identidade **sem credenciais fixas**, assumida temporariamente (por um serviço AWS, outra conta ou usuário federado). Gera credenciais **temporárias**.

### User x Role (não confundir!)

| | IAM User | IAM Role |
|---|---|---|
| Credencial | Permanente (senha / access key) | Temporária (assumida via STS) |
| Pertence a | Uma pessoa/app fixa | Ninguém fixo — é "vestida" quando necessário |
| Uso típico | Pessoa que loga no console/CLI | Serviço AWS (ex: EC2) acessando outro serviço (ex: S3) |

> ⚠️ Pegadinha clássica: "Uma instância EC2 precisa acessar o S3, qual é a prática recomendada?" → **Role**, nunca colocar access key fixa dentro do código/instância.

### Como as peças se conectam

- Um usuário pertence a um ou mais grupos.
- Um grupo recebe políticas, que se aplicam a todos os seus usuários.
- Boa prática: atribuir política via **grupo**, não diretamente no usuário (tecnicamente possível, mas não recomendado).

## 🧠 Para lembrar

- Root = chave mestra → guardar trancada (MFA, sem access key).
- User = crachá permanente da pessoa.
- Role = crachá de visitante temporário que qualquer um (ou serviço) pode "vestir" na hora.
