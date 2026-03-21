---
title: "State beheer"
intro: "Terraform slaat de huidige toestand van je infrastructuur op in een state file. Goed beheer hiervan is essentieel."
weight: 2
date: "2026-01-15"
tags: ["terraform", "state", "azure"]
---

## Hoe werkt state?

{{< mermaid >}}
flowchart LR
  dev["💻 Developer"] -->|terraform plan| plan["Plan\n(vergelijkt state)"]
  plan -->|terraform apply| azure["☁️ Azure\nInfrastructuur"]
  azure -->|resultaat| state["State file\n(Azure Blob)"]
  state -->|volgende run| plan
{{< /mermaid >}}

## Remote state in Azure

Sla je state op in Azure Blob Storage zodat het veilig en gedeeld is.

```hcl
terraform {
  backend "azurerm" {
    resource_group_name  = "rg-terraform-state"
    storage_account_name = "stterraformstate"
    container_name       = "tfstate"
    key                  = "prod.terraform.tfstate"
  }
}
```

{{< callout title="Let op" type="warning" >}}
Verwijder nooit handmatig je state file. Gebruik altijd `terraform state` commando's om wijzigingen door te voeren.
{{< /callout >}}

## Handige commando's

```bash
# Huidige state bekijken
terraform state list

# Resource uit state verwijderen (zonder te destroyen)
terraform state rm azurerm_resource_group.example

# State vernieuwen vanuit echte infrastructuur
terraform refresh
```
