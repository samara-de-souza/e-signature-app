# e-signature-app

Aplicação Java com Spring Boot para administração de assinaturas, clientes, aplicativos e pagamentos, usada como projeto prático de Application Security (AppSec) e DevSecOps.

## Objetivo

O projeto nasceu como trabalho acadêmico de fundamentos de desenvolvimento de software. Hoje serve como portfólio para demonstrar práticas de segurança aplicadas a um projeto real: identificar vulnerabilidades, documentar evidências, corrigir e revalidar, com rastreabilidade por commits.

## O que foi feito

- API REST e interface web estática, ambas servidas pelo Spring Boot
- Arquitetura em camadas (controller, domain, repository, infrastructure)
- Domínio de assinaturas com Cliente, Aplicativo, Assinatura, Pagamento e Usuário
- Containerização com Docker
- Pipeline de CI com GitHub Actions para build, testes e verificações de segurança
- Análise de segurança com SCA, secret scanning, container scanning, SAST e DAST
- Documentação de findings e remediações separada do README, em `docs/appsec`

## Tecnologias e conceitos

Java 21, Spring Boot, Spring Data JPA, Spring Data REST, Spring Boot Actuator, H2, Maven, Docker, GitHub Actions, Trivy, GitHub CodeQL, OWASP ZAP, AppSec, DevSecOps.

## Resultados

- Aplicação funcional com build e testes automatizados
- Trilha AppSec iniciada, com análise de vulnerabilidades e registro de remediações
- Próximos passos: security gates, hardening de Docker, imagem no GitHub Container Registry, Dependabot, SBOM e deploy controlado
