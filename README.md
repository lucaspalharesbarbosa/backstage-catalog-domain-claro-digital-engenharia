# Catálogo Backstage — domínio Claro Digital Engenharia

Repositório de **entidades do Software Catalog** do [Backstage](https://backstage.io/) para o domínio **Claro Digital Engenharia**: sistemas, componentes e APIs relacionados a esteiras CI/CD, pipelines de imagem e orquestração Camunda/Zeebe.

## Estrutura


| Pasta         | Conteúdo                                                |
| ------------- | ------------------------------------------------------- |
| `domains/`    | Domínio de negócio / engenharia                         |
| `systems/`    | Sistemas (agrupamento lógico)                           |
| `components/` | Componentes de software                                 |
| `apis/`       | Definições de API (OpenAPI, gRPC, etc.)                 |
| `locations/`  | Referências de URL no GitHub para registrar no catálogo |


## Entidades incluídas

- **Domain:** `claro-digital-engenharia`
- **Systems:** `esteiras-cicd-claro`, `camunda-zeebe-8`
- **Component:** `golden-image-pipeline-ti`
- **APIs:** `camunda-tasklist-or-operate`, `camunda-zeebe-grpc`

As entidades YAML seguem o formato oficial: [Software Catalog — Descriptor format](https://backstage.io/docs/features/software-catalog/descriptor-format).

## Como registrar no Backstage

O arquivo `[locations/github-locations.yaml](locations/github-locations.yaml)` é uma entidade `**kind: Location`**: o catálogo ingere esse descritor e, em seguida, expande cada URL listada em `spec.targets` (outras entidades do catálogo).

1. No `app-config.yaml`, em `catalog.locations`, aponte **uma única** entrada `type: url` para o YAML da Location no GitHub (o mesmo repositório, branch `main`, caminho `locations/github-locations.yaml`), **ou** registre esse arquivo a partir de um catálogo pai que já importe este repositório.
2. Garanta que o processador de URL do catálogo esteja habilitado e que a instância consiga acessar `github.com` (rede / allowlists).
3. Os `spec.owner` referenciam grupos (`group:default/...`). Ajuste ou cadastre esses grupos no seu catálogo para bater com a sua organização.

## Contribuindo

Altere ou adicione YAMLs nas pastas acima, mantenha relações (`spec.domain`, `spec.system`, etc.) consistentes e atualize `locations/github-locations.yaml` se criar novos arquivos de entidade servidos por URL.

