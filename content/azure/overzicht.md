---
title: "Overzicht"
intro: "Microsoft Azure is het cloudplatform dat we gebruiken voor hosting, opslag en netwerken."
weight: 1
date: "2026-02-01"
tags: ["azure", "cloud", "basics"]
---

## Inloggen via CLI

```bash
# Inloggen
az login

# Beschikbare subscriptions bekijken
az account list --output table

# Actieve subscription instellen
az account set --subscription "jouw-subscription-naam"
```

## Resource Groups

Een Resource Group is een container voor gerelateerde Azure-resources. Alles in een project zit in dezelfde groep.

```bash
# Nieuwe resource group aanmaken
az group create \
  --name rg-mijn-project \
  --location westeurope

# Overzicht van alle groepen
az group list --output table
```

{{< callout title="Conventie" >}}
Gebruik een vaste naamgevingsconventie: `rg-{project}-{omgeving}`. Bijvoorbeeld: `rg-webapp-prod`.
{{< /callout >}}
