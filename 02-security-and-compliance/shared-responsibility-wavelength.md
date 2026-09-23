# Shared Responsibility Model e AWS Wavelength

## Modelo de Responsabilidade Compartilhada

### O que é?

Divide as obrigações de segurança entre a **AWS** e o **Cliente**.

- **AWS — Security OF the cloud**: protege a infraestrutura global (hardware, software, redes e instalações físicas que executam os serviços).
- **Cliente — Security IN the cloud**: protege seus próprios dados, configurações, sistema operacional, credenciais e código de aplicativos.

### Conceito importante: a linha muda conforme o nível de gerenciamento do serviço

Quanto **menos gerenciado** o serviço, **mais responsabilidade fica com o cliente**. Quanto **mais gerenciado**, **mais responsabilidade migra pra AWS**.

| Camada | EC2 (IaaS — não gerenciado) | RDS / Lambda (gerenciado) |
|---|---|---|
| Patch do SO | Cliente | AWS |
| Patch do motor/runtime | — | AWS |
| Dados | Cliente | Cliente |
| Configuração de acesso (IAM, credenciais) | Cliente | Cliente |
| Segurança física do data center | AWS | AWS |
| Infraestrutura de rede global | AWS | AWS |

**Sempre da AWS, em qualquer serviço**: segurança física dos data centers, infraestrutura de rede global, durabilidade do hardware.

**Sempre do Cliente, em qualquer serviço**: gestão de credenciais e chaves de acesso IAM, classificação e proteção dos próprios dados.

## AWS Wavelength

### O que é?

Serviço que embute infraestrutura de computação/armazenamento da AWS **na borda das redes de telecom 5G**.

### Para que serve?

Permite que desenvolvedores criem aplicações com **latência de um dígito (milissegundos)** para dispositivos móveis e usuários finais.

### Comparações

| Serviço | Foco |
|---|---|
| **Wavelength** | Latência ultrabaixa em redes móveis 5G |
| **CloudFront** | CDN — cache/distribuição de conteúdo estático globalmente |
| **Direct Connect** | Conexão de rede dedicada e privada entre o data center do cliente e a AWS |

## ⚠️ Pegadinhas

- "AWS protege a infraestrutura global" ≠ "AWS protege tudo dentro de qualquer serviço". O sistema operacional guest de uma instância EC2 **não** é infraestrutura global — é responsabilidade do cliente.
- Wavelength, CloudFront e Direct Connect são frequentemente confundidos por serem "sobre rede/latência", mas resolvem problemas diferentes.
- OUs e SCPs (Organizations) não têm relação com Shared Responsibility — não confundir os dois temas de segurança.

## 🧠 Para lembrar

- **"OF the cloud" = AWS** (a nuvem em si). **"IN the cloud" = Cliente** (o que você coloca dentro dela).
- Regra de ouro: **quanto mais gerenciado o serviço, menos trabalho de segurança pro cliente**.
- Wavelength = "AWS dentro da torre de celular".
