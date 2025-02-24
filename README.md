# Projeto Segurança AWS

Este projeto demonstra uma arquitetura robusta e segura na AWS, combinando diversos serviços para garantir alta disponibilidade, escalabilidade e proteção contra ameaças. A estrutura segue as melhores práticas de segurança, com segmentação de rede, monitoramento contínuo e gerenciamento de identidades.

## Estrutura da Arquitetura

- **AWS Cloud (Região us-west-2):** Infraestrutura principal onde os recursos são provisionados.
- **VPC "Nova Tech":** Ambiente isolado que agrega todos os recursos da aplicação.
- **Múltiplas Zonas de Disponibilidade:** Distribuição em AZs (A, B e C) para assegurar resiliência e alta disponibilidade.
- **Sub-redes Públicas e Privadas:** Cada zona possui sub-redes públicas para acesso externo (por exemplo, via Internet Gateway e CloudFront) e sub-redes privadas para recursos internos (como bancos de dados e servidores de aplicação).

## Serviços Utilizados e Suas Funções

- **Amazon EC2:** Hospeda as instâncias dos servidores que executam a aplicação.
- **Amazon Aurora (Primary & Replication):** Banco de dados relacional com alta performance e replicação para garantir disponibilidade e integridade dos dados.
- **Amazon Cognito (SSO):** Gerencia a autenticação de usuários externos, permitindo Single Sign-On.
- **Amazon Route 53 & AWS WAF:** Gerenciam o DNS e aplicam regras de segurança para mitigar ataques web.
- **Amazon CloudFront:** Distribui o conteúdo globalmente com baixa latência.
- **Internet Gateway & NAT Gateway:** Permitem a comunicação segura entre a VPC e a internet, mantendo a separação entre recursos públicos e privados.
- **Bastion Host:** Facilita o acesso administrativo seguro aos recursos localizados nas sub-redes privadas.
- **AWS SNS:** Serviço de notificações para alertas e comunicação entre os componentes.
- **AWS CloudTrail & CloudWatch:** Monitoram e registram atividades na conta AWS, possibilitando auditoria e resposta rápida a incidentes.
- **AWS Config & AWS Systems Manager:** Auxiliam no gerenciamento e conformidade dos recursos.
- **IAM & AWS Secrets Manager:** Gerenciam identidades, permissões e segredos de acesso de forma segura.
- **CloudWatch Logs:** Centralizam os logs das aplicações para análise e troubleshooting.
- **Amazon SES:** Gerencia o envio de emails para notificações e comunicação.
- **Amazon S3:** Armazena dados, backups e logs de forma durável e escalável.
- **Amazon GuardDuty:** Detecta atividades suspeitas e potenciais ameaças na infraestrutura.

## Interação Entre os Serviços

A arquitetura foi desenhada para que cada serviço cumpra uma função específica, garantindo uma integração coesa:

- **Rede e Segurança:** A VPC com sub-redes segmentadas, juntamente com Security Groups, NAT Gateways e o WAF, assegura que o tráfego seja controlado e protegido.
- **Acesso e Autenticação:** Enquanto o Cognito facilita o acesso de usuários externos, o Bastion Host permite que administradores acessem de forma segura os recursos privados.
- **Computação e Armazenamento:** Instâncias EC2 processam as requisições da aplicação e se conectam ao banco de dados Aurora para armazenamento crítico. O S3 fornece suporte para backup e armazenamento de logs.
- **Monitoramento e Gerenciamento:** CloudTrail, CloudWatch, Config e Systems Manager trabalham juntos para oferecer visibilidade completa da infraestrutura e rápida resposta a incidentes.
- **Comunicação e Notificação:** SNS e SES garantem que os administradores e usuários sejam notificados de eventos importantes.

## Nível de Segurança

O design da aplicação apresenta um alto nível de segurança, composto por diversas camadas:

- **Segurança de Rede:** Segmentação por VPC e sub-redes, uso de Security Groups, NAT Gateways e regras rigorosas no Internet Gateway.
- **Proteção Contra Ameaças:** AWS WAF e GuardDuty monitoram e mitigam tentativas de ataques, enquanto Flow Logs auxiliam na análise de tráfego.
- **Gerenciamento de Identidades e Acessos:** IAM, Cognito e Secrets Manager garantem que apenas usuários autorizados tenham acesso aos recursos.
- **Monitoramento Contínuo:** CloudTrail e CloudWatch permitem a detecção imediata de atividades anômalas e a execução de ações corretivas.

## Considerações Finais

Este projeto evidencia uma infraestrutura AWS cuidadosamente planejada, que integra serviços de computação, banco de dados, segurança e monitoramento para oferecer uma aplicação resiliente e segura. A combinação de práticas de isolamento, autenticação rigorosa, monitoramento constante e resposta a incidentes torna este ambiente altamente robusto contra ameaças e falhas.
