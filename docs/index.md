# Template de Entrega


???+ info inline end "Edição"

    2025.5


## Alunos

1. Ricardo Luz Carvalho
2. João Gabriel Faus Faraco
3. Vitor Trufino Raia

## Entregas Individuais - Ricardo Luz Carvalho

- [x] Roteiro 1 - Data 24/09/2025
- [x] Roteiro 2 - Data 07/10/2025
- [x] Roteiro 3 - Data 15/10/2025
- [x] Roteiro 4 - Data 17/10/2025
- [x] Roteiro 5 - Data 24/10/2025

## Entregas em Grupo

- [x] Projeto - Data 06/11/2025

## Diagrama

``` mermaid
flowchart LR
    subgraph api [Subnet API]
        direction TB
        gateway --> account
        gateway --> auth:::red
        gateway --> product
        gateway --> order
        gateway --> exchange
        auth --> account
        order --> product
        account --> db@{ shape: cyl, label: "Database" }
        product --> db
        order --> db
    end
    exchange e3@==> 3partyapi:::green@{label: "3rd-party API"}
    internet e2@==> |request| gateway:::orange
    e2@{ animate: true }
    e3@{ animate: true }
    classDef green fill:#cfc
    classDef orange fill:#FCBE3E
```

## Referências

[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/reference/){:target='_blank'}