# IAM, AWS Organizations e Account Reports

## IAM — Identity and Access Management

### O que é?

Serviço de gestão de identidades e permissões na AWS.

### Estrutura

**AWS Account root user** → identidade inicial da conta, com acesso total e irrestrito. Não deve ser usada no dia a dia.

A partir dela se criam:
- **Users**: identidades fixas, com credenciais de longo prazo (senha, access keys). Ex: Marcos, Alice, João, Helena.
- **Groups**: agrupam usuários com as mesmas permissões, facilitando a gestão de políticas. Ex: grupo Admin, grupo Developer (EC2, Lambda).
- **Roles**: assumidas temporariamente por uma entidade confiável (usuário, serviço ou conta externa). Fornecem credenciais **temporárias**, rotacionadas automaticamente — sem senha ou access key fixa.

### Quando usar Role em vez de User?

Exemplo clássico: uma instância **EC2** que precisa acessar o **S3**. Em vez de colocar as credenciais de um IAM User dentro da instância (risco de exposição), anexa-se uma **Role** à instância. Isso evita access keys fixas "hardcoded" na máquina.

## IAM Identity Center

### O que é?

Serviço de **SSO (Single Sign-On)** que centraliza o acesso da conta AWS a várias aplicações.

### Para que serve?

Em vez de ter vários usuários e senhas diferentes para cada aplicação, você associa a conta AWS a várias aplicações de uma vez.

## AWS Organizations

### O que é?

Serviço que permite gerenciar **várias contas AWS de forma centralizada**. Usado por empresas com múltiplas contas.

### O que faz

- Consolida a cobrança de várias contas em uma única fatura.
- Aplica políticas e controles de segurança.
- Organiza contas em **Unidades Organizacionais (OUs)**.
- Usa **Service Control Policies (SCPs)** para limitar ações e serviços.

### Conceito importante: SCP x IAM Policy

- **SCP** define o **teto máximo** de permissões que qualquer identidade da conta pode ter. **Nunca concede permissão por si só**, apenas restringe.
- O acesso efetivo de um usuário é sempre a **interseção** entre a SCP da conta e as IAM Policies do usuário.

## AWS Account Reports

| Relatório | Foco | Abrangência |
|---|---|---|
| **Credential Report (CR)** | Status das **credenciais**: uso de MFA, data do último acesso, idade de senha e access keys | Todos os IAM Users da conta |
| **Access Advisor (AA)** | Quais **serviços/permissões** o usuário ou role tem acesso, e **quando cada um foi usado pela última vez** | Um usuário ou role específico |

**Access Advisor na prática**: usado para aplicar o **princípio do menor privilégio** — identificar permissões concedidas mas nunca usadas, e removê-las.

## ⚠️ Pegadinhas

- OUs e SCPs **restringem/organizam**, nunca concedem acesso automático a ninguém.
- Confundir Credential Report com Access Advisor: CR = credenciais (de todos); AA = permissões e uso (de um específico).
- Achar que Role é exclusiva de serviços AWS — usuários e contas externas também podem assumir roles (acesso cross-account).

## 🧠 Para lembrar

- Credential Report → "Quem tem senha fraca ou sem MFA?"
- Access Advisor → "O que esse usuário realmente usa?"
- SCP → "O teto da casa" (nunca aumenta o espaço, só limita).
