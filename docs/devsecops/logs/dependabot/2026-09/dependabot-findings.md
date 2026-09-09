# Dependabot Findings and Triage Log

## DEPENDABOT-TRIAGE-001 - Initial Dependency Update Triage

### Summary

Foi realizada a triagem inicial dos pull requests abertos automaticamente pelo Dependabot no projeto `e-signature-app`.

O objetivo foi validar o funcionamento do Dependabot na fase DevSecOps, revisar atualizações de dependências e aplicar somente mudanças compatíveis com a baseline atual do projeto.

As atualizações seguras e compatíveis foram mergeadas após aprovação dos checks obrigatórios. Atualizações com impacto de versão major ou mudança de runtime foram adiadas com justificativa técnica.

### Tooling

```text
Method: Dependency Update Automation
Tool: Dependabot
Platform: GitHub
Repository: samara-de-souza/e-signature-app
Configuration: .github/dependabot.yml
Ecosystems: maven, github-actions, docker
Branch protection: enabled for main
Required checks: CI, Trivy, CodeQL, OWASP ZAP
```

### Evidence

ID do registro:

```text
DEPENDABOT-TRIAGE-001
```

Configuração analisada:

```text
.github/dependabot.yml
```

Ecossistemas configurados:

```text
Maven
GitHub Actions
Docker
```

Atualizações aceitas:

```text
actions/checkout: 4 -> 7
actions/setup-java: 4 -> 5
actions/setup-java: 5 -> 6
actions/upload-artifact: 4 -> 7
org.apache.maven:apache-maven: 3.9.7 -> 3.9.16
org.apache.maven.wrapper:maven-wrapper: 3.3.2 -> 3.3.4
```

Atualizações adiadas:

```text
org.springframework.boot:spring-boot-starter-parent: 3.5.16 -> 4.1.1
eclipse-temurin: 21-jre -> 25-jre
```

### Affected Components

Componentes atualizados:

```text
GitHub Actions workflows
Maven Wrapper
Maven distribution used by the wrapper
```

Componentes avaliados e não atualizados:

```text
Spring Boot parent
Docker runtime base image
```

Arquivos relacionados:

```text
.github/dependabot.yml
.github/workflows/ci.yml
.github/workflows/codeql.yml
.github/workflows/security-trivy.yml
.github/workflows/security-zap.yml
.mvn/wrapper/maven-wrapper.properties
dockerfile
pom.xml
```

### Risk

Dependabot reduz o risco de dependências desatualizadas, mas seus pull requests não devem ser mergeados automaticamente sem triagem.

Riscos tratados:

```text
Uso de versões antigas de GitHub Actions
Uso de versão antiga do Maven Wrapper
Ausência de processo automatizado para identificar updates
Ausência de revisão explícita para mudanças de dependências
```

Riscos evitados:

```text
Merge cego de major upgrade do Spring Boot
Mudança do runtime Java 21 LTS para Java 25 sem avaliação dedicada
Quebra de compatibilidade por atualização de framework
Alteração de baseline tecnológica sem planejamento
```

### Root Cause

Antes da configuração do Dependabot, o projeto não possuía automação para abertura de pull requests de atualização em Maven, GitHub Actions e Docker.

Isso poderia fazer com que dependências, actions e imagens base ficassem desatualizadas sem visibilidade contínua.

### Remediation Plan

Log ID:

```text
log-01
```

Ação aplicada:

```text
Configurar Dependabot para Maven, GitHub Actions e Docker.
Revisar os pull requests abertos automaticamente.
Mergear atualizações compatíveis após checks obrigatórios.
Adiar atualizações incompatíveis ou de maior impacto com justificativa.
```

Política de triagem:

```text
Patch/minor updates com checks verdes podem ser mergeados após revisão.
Major upgrades exigem branch dedicada, análise de breaking changes e testes.
Mudanças de runtime fora da baseline LTS exigem decisão arquitetural separada.
```

Decisões aplicadas:

```text
Atualizações de GitHub Actions foram aceitas.
Atualizações de Maven Wrapper e Maven distribution foram aceitas.
Spring Boot 4.1.1 foi adiado por ser major upgrade.
Eclipse Temurin 25 foi adiado para manter Java 21 LTS como baseline.
```

### Validation

Validações realizadas:

```text
Pull requests do Dependabot revisados individualmente
Checks obrigatórios executados antes do merge
Branch protection aplicada na main
Atualizações compatíveis mergeadas via pull request
Pull requests incompatíveis fechados ou adiados com justificativa
Main atualizada após merges
```

Checks usados como gate:

```text
CI / Build and Test
Security - Trivy / Trivy Vulnerability Scan
Security - CodeQL / CodeQL SAST
Security - OWASP ZAP / OWASP ZAP Baseline
```

Resultado:

```text
Dependabot validado como controle DevSecOps para atualização contínua.
Atualizações seguras foram aplicadas.
Atualizações de maior risco foram triadas e não mergeadas automaticamente.
```

### Status

```text
Completed - Initial triage documented
```
