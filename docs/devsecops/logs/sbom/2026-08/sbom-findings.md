# SBOM Findings and Validation Log

## SBOM-TRIVY-001 - CycloneDX SBOM Baseline

### Summary

Foi gerada uma SBOM em formato CycloneDX para a imagem Docker `e-signature-app`, utilizando Trivy no workflow de segurança.

A SBOM documenta os componentes presentes na imagem, incluindo pacotes do sistema operacional, dependências Maven da aplicação Java e componentes Go presentes na imagem base upstream.

Este registro documenta a baseline inicial de software supply chain do projeto.

### Tooling

```text
Method: SBOM Generation
Tool: Trivy
Workflow: .github/workflows/security-trivy.yml
Target: e-signature-app
Format: CycloneDX
Spec version: 1.7
Report: docs/devsecops/reports/sbom/2026-08/sbom.cdx.json
Trivy version: 0.74.0
```

### Evidence

ID do registro:

```text
SBOM-TRIVY-001
```

Arquivo de evidência:

```text
docs/devsecops/reports/sbom/2026-08/sbom.cdx.json
```

Dados técnicos do SBOM:

```text
Format: CycloneDX
SpecVersion: 1.7
SerialNumber: urn:uuid:e8fe8f29-800b-46b0-9ec7-cb1b80bdf095
Timestamp: 2026-08-20T23:27:42+00:00
Target: e-signature-app
ComponentCount: 227
VulnerabilityCount: 0
```

Componentes por tipo:

```text
operating-system: 1
application: 1
library: 225
```

Componentes por ecossistema:

```text
deb: 140
maven: 72
golang: 13
ubuntu: 1
gobinary: 1
```

### Affected Components

Componentes mapeados:

```text
Imagem Docker e-signature-app
Sistema operacional base Ubuntu
Dependências Maven da aplicação Java
Binário Go usr/bin/pebble presente na imagem base
Pacotes DEB da imagem base
```

Componente principal da aplicação:

```text
pkg:maven/AppAssinatura/app-assinatura@0.0.1-SNAPSHOT
```

### Risk

A ausência de SBOM reduz a rastreabilidade de componentes, versões e ecossistemas presentes em uma imagem de container.

Impactos mitigados com a geração da SBOM:

```text
Falta de inventário de componentes
Dificuldade para responder a novas CVEs
Dificuldade para auditar dependências transitivas
Baixa visibilidade de componentes da imagem base
Baixa maturidade de software supply chain
```

Risco residual:

```text
A SBOM registra os componentes, mas não corrige vulnerabilidades por si só.
Ela deve ser usada junto com Trivy image scan, Dependabot e atualização da
imagem base.
```

### Root Cause

Antes desta etapa, o projeto possuía scans de vulnerabilidade, mas ainda não registrava um inventário formal dos componentes da imagem em formato padronizado.

A causa raiz era a ausência de uma etapa de SBOM generation no pipeline DevSecOps.

### Remediation Plan

Log ID:

```text
log-01
```

Ação aplicada:

```text
Adicionar geração de SBOM CycloneDX ao workflow Security - Trivy.
Publicar o arquivo sbom.cdx.json como artifact do pipeline.
Salvar a evidência em docs/devsecops/reports/sbom/2026-08/.
Documentar a baseline em docs/devsecops/logs/sbom/2026-08/sbom-findings.md.
```

Objetivo:

```text
Permitir rastreabilidade de componentes, auditoria de dependências e análise
futura de supply chain da imagem Docker.
```

### Validation

Validações realizadas:

```text
Workflow Security - Trivy executado com geração de SBOM
Artifact trivy-reports baixado do GitHub Actions
Arquivo sbom.cdx.json validado como CycloneDX 1.7
Componentes da imagem listados no SBOM
Dependências Maven da aplicação identificadas no SBOM
Pacotes DEB da imagem base identificados no SBOM
Componentes Go da imagem base identificados no SBOM
```

Resultado validado:

```text
SBOM gerado com sucesso
227 componentes identificados
0 vulnerabilidades registradas no campo vulnerabilities do SBOM
```

Critério de fechamento:

```text
O pipeline deve continuar gerando sbom.cdx.json a cada execução do workflow
Security - Trivy.
```

### Status

```text
Generated - Baseline documented
```
