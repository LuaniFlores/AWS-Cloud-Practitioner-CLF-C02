# Erros — Aula 02

## 1. Role vs. Access Key fixa em código

**Situação:** EC2 precisa acessar o S3. Marquei "criar IAM user + access key no código".
**Correto:** Anexar uma **IAM Role** à instância.

**Por quê:** Access key fixa em código é risco de segurança (pode vazar, precisa rotação manual).
Role gera credenciais **temporárias** e é gerenciada automaticamente pela AWS.

**Classificação:** Caso de uso (não reconheci quando usar Role).

## 🧠 Como lembrar

> Serviço AWS falando com serviço AWS → **Role**.
> Pessoa logando no console/CLI → **User**.

---

## 2. Deny implícito no IAM

**Situação:** Usuário sem grupo e sem política anexada. Achei que a AWS geraria uma política padrão.
**Correto:** Acesso **negado a tudo** por padrão.

**Por quê:** O IAM segue a regra do **deny implícito** — nada é permitido a menos que uma política diga explicitamente que sim.

**Classificação:** Conteúdo desconhecido (conceito novo).

## 🧠 Como lembrar

> No IAM, o padrão é "não" até que uma política diga "sim".
