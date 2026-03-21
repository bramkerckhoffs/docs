---
title: "Overzicht"
intro: "Terraform is een open-source tool van HashiCorp waarmee je infrastructuur als code definieert en beheert."
weight: 1
date: "2026-01-10"
tags: ["terraform", "iac", "basics"]
---

## Wat is Terraform?

Met Terraform beschrijf je je infrastructuur in `.tf` bestanden. Terraform vergelijkt de gewenste toestand met de werkelijkheid en past alleen aan wat nodig is.

{{< callout title="Tip" >}}
Sla je Terraform state nooit lokaal op in een team. Gebruik een remote backend zoals Azure Blob Storage.
{{< /callout >}}

## Basisworkflow

Elke Terraform-run volgt drie stappen:

1. `terraform init` — haalt providers en modules op
2. `terraform plan` — toont wat er gaat veranderen
3. `terraform apply` — voert de wijzigingen door

## Minimale configuratie

```hcl
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "~> 3.0"
    }
  }
}

provider "azurerm" {
  features {}
}
```
