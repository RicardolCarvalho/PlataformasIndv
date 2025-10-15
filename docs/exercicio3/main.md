
Now, the user wants to create an API that allows the user to convert between currencies. The API should use a third-party API to get the exchange rates. Note, this microservice ==HAVE TO== be code in Python.

``` mermaid
flowchart LR
    subgraph api [Trusted Layer]
        direction TB
        gateway --> account
        gateway --> auth
        account --> db@{ shape: cyl, label: "Database" }
        auth --> account
        gateway e1@==> exchange:::red
        gateway --> product
        gateway --> order
        product --> db
        order --> db
        order --> product
    end
    exchange e3@==> 3partyapi:::green@{label: "3rd-party API"}
    internet e2@==>|request| gateway
    e1@{ animate: true }
    e2@{ animate: true }
    e3@{ animate: true }
    classDef red fill:#fcc
    classDef green fill:#cfc
    click product "#product-api" "Product API"
```

# Repositórios
- [Exchange](https://github.com/RicardolCarvalho/exchange)
```bash
exchange/
├── main.py
├── requirements.txt
├── Dockerfile
├── .gitignore
```

!!! info "GET /exchange/{from}/{to}"

    Get the current of a coin from one currency to another. E.g. `GET /coin/USD/EUR`.

    === "Response"

        ``` { .json .copy .select linenums='1' }
        {
            "sell": 0.82,
            "buy": 0.80,
            "date": "2021-09-01 14:23:42",
            "id-account": "0195ae95-5be7-7dd3-b35d-7a7d87c404fb"
        }
        ```
        ```bash
        Response code: 200 (ok)
        ```
    === "Postman BRL"
        ![](./img/USD_BRL.png){ width=100% }
    === "Postman EUR"
        ![](./img/USD_EUR.png){ width=100% }

> This MkDocs was created by [Ricardo Luz Carvalho](https://github.com/RicardolCarvalho)