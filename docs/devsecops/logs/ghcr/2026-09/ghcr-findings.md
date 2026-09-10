# GHCR Publication Log

## GHCR-001 - Docker Image Published to GitHub Container Registry

### Summary

A imagem Docker do projeto `e-signature-app` foi publicada com sucesso no GitHub Container Registry como parte da fase DevSecOps do projeto.

A publicação validou o uso de um registry centralizado, tag imutável baseada no commit SHA e rastreabilidade entre código, workflow de CI/CD e imagem containerizada.

### Tooling

```text
Method: Container Registry Publication
Tool: GitHub Container Registry
Platform: GitHub Actions
Workflow: Publish GHCR Image
Workflow file: .github/workflows/publish-ghcr.yml
Registry: ghcr.io
Authentication: GITHUB_TOKEN
Permission scope: packages: write
```

### Evidence

ID do registro:

```text
GHCR-001
```

Imagem publicada com tag imutável baseada no commit SHA:

```text
ghcr.io/samara-de-souza/e-signature-app:328cb6b94dd71a2ac80ed4a52759febce78f1640
```

Imagem publicada com tag `latest`:

```text
ghcr.io/samara-de-souza/e-signature-app:latest
```

Digest registrado pelo workflow:

```text
sha256:6ee40ce8b47b8d0957b2c3c68f6cfe9f3010decae7f1fc1f0e4744d9aba562b1
```

Media type:

```text
application/vnd.docker.distribution.manifest.v2+json
```

Validação visual no GitHub Packages:

```text
Package: e-signature-app
Visibility: Public
Latest tag: latest
Recent tagged image version: 328cb6b94dd71a2ac80ed4a52759febce78f1640
Workflow status: Success
```

### Affected Components

Componentes envolvidos:

```text
.github/workflows/publish-ghcr.yml
dockerfile
GitHub Container Registry package: e-signature-app
GitHub Actions workflow: Publish GHCR Image
```

### Risk

Antes da publicação no GHCR, a imagem Docker existia apenas como build local ou como artefato temporário dos workflows.

Isso reduzia a rastreabilidade da imagem que poderia ser usada em deploys e dificultava a promoção de uma imagem aprovada para ambientes posteriores, como staging na AWS.

### Root Cause

O projeto ainda não possuía um registry central para armazenar imagens Docker versionadas.

Sem essa etapa, o deploy cloud dependeria de builds locais ou imagens sem rastreabilidade direta por commit SHA e digest.

### Remediation Plan

Log ID:

```text
log-01
```

Ação aplicada:

```text
Criar workflow dedicado para publicação no GHCR.
Autenticar no registry usando GITHUB_TOKEN.
Conceder ao workflow somente as permissões necessárias para leitura do repositório e escrita em packages.
Publicar a imagem com tag baseada no commit SHA.
Publicar a tag latest somente a partir da branch main.
Registrar o digest da imagem publicada.
Validar a existência da imagem no GitHub Packages.
```

### Validation

Validações realizadas:

```text
Workflow Publish GHCR Image executado com sucesso.
Imagem publicada no GitHub Container Registry.
Tag baseada no commit SHA disponível.
Tag latest disponível.
Digest da imagem registrado.
Package e-signature-app visível no GitHub Packages.
```

Resultado:

```text
Imagem Docker publicada, versionada e rastreável por commit SHA e digest.
Imagem pronta para ser usada na próxima fase de deploy AWS com Terraform.
```

### Status

```text
Fixed - Docker image published and traceable by commit SHA and digest
```
