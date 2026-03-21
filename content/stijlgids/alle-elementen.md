---
title: "Alle elementen"
intro: "Een compleet overzicht van alle opmaakelementen die je kunt gebruiken in artikelen — van koppen en tabellen tot diagrammen en callouts."
weight: 1
date: "2026-03-01"
tags: ["docs", "stijlgids", "markdown"]
---

## Koppen

Kop 2 gebruik je voor hoofdsecties. Elke `h2` verschijnt automatisch in de inhoudsopgave rechts.

### Kop 3 — Subonderdelen

Kop 3 groepeert verwante onderwerpen binnen een sectie.

#### Kop 4 — Extra detail

Gebruik kop 4 spaarzaam, alleen voor extra detailniveau.

---

## Tekst & nadruk

Normale paragraaftekst heeft een regelafstand van 1,75. **Vetgedrukte tekst** gebruik je voor sleutelbegrippen en termen. *Cursieve tekst* voor benamingen, titels of lichte nadruk. `Inline code` voor variabelen, commando's en bestandsnamen.

Doorgestreepte tekst wordt zo geschreven: ~~verouderde waarde~~.

---

## Lijsten

**Ongesorteerd:**

- Azure Resource Groups
- Storage Accounts
- Virtual Networks
  - Subnets
  - Network Security Groups
  - Route Tables

**Gesorteerd:**

1. `terraform init` — haalt providers en modules op
2. `terraform plan` — toont wat er gaat veranderen
3. `terraform apply` — voert de wijzigingen door

---

## Citaten

> Infrastructure as Code betekent dat je infrastructuur net zo behandelt als applicatiecode: versiebeheer, peer reviews en geautomatiseerde deployment.
>
> — HashiCorp

---

## Tabellen

| Resource             | Type            | Locatie       | SKU           |
|----------------------|-----------------|---------------|---------------|
| rg-webapp-prod       | Resource Group  | West Europe   | —             |
| st-webapp-prod       | Storage Account | West Europe   | Standard_LRS  |
| vnet-webapp-prod     | Virtual Network | West Europe   | —             |
| nsg-webapp-prod      | NSG             | West Europe   | —             |

---

## Code blokken

```bash
# Resource group aanmaken
az group create \
  --name rg-webapp-prod \
  --location westeurope

# Overzicht bekijken
az group list --output table
```

```hcl
resource "azurerm_resource_group" "example" {
  name     = "rg-webapp-prod"
  location = "West Europe"

  tags = {
    environment = "production"
    project     = "webapp"
  }
}
```

```yaml
name: Deploy to Azure
on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Azure Login
        uses: azure/login@v1
        with:
          creds: ${{ secrets.AZURE_CREDENTIALS }}
```

```json
{
  "name": "webapp",
  "version": "1.0.0",
  "scripts": {
    "build": "tsc && vite build",
    "preview": "vite preview"
  }
}
```

---

## Callouts

{{< callout title="Tip" >}}
Gebruik een remote backend voor Terraform state zodat je veilig in een team kunt werken. Azure Blob Storage is de meest gebruikte optie.
{{< /callout >}}

{{< callout title="Let op" type="warning" >}}
Sla nooit secrets op in je Terraform-bestanden of git-repository. Gebruik Azure Key Vault of omgevingsvariabelen via een CI/CD-pipeline.
{{< /callout >}}

---

## Mermaid diagrammen

Diagrammen maak je met de `mermaid` shortcode. Flowcharts, sequence diagrams en meer worden ondersteund.

{{< mermaid >}}
flowchart TD
  code["📝 Code\n(.tf bestanden)"] --> init["terraform init"]
  init --> plan["terraform plan"]
  plan --> review{"Review\ngoedgekeurd?"}
  review -->|ja| apply["terraform apply"]
  review -->|nee| code
  apply --> state["State opgeslagen\n(Azure Blob)"]
  apply --> infra["☁️ Azure\nInfrastructuur"]
{{< /mermaid >}}

---

## Links

- Interne link: [Terraform overzicht](/terraform/overzicht/)
- Interne link: [State beheer](/terraform/state-beheer/)
- Externe link: [Azure documentatie](https://learn.microsoft.com/azure)
- Externe link: [Terraform registry](https://registry.terraform.io)
