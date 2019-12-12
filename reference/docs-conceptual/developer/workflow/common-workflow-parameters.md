---
title: Vanliga arbets flödes parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356660"
---
# <a name="common-workflow-parameters"></a>Vanliga arbetsflödesparametrar

En arbets flödes aktivitet som genereras från en Windows PowerShell-cmdlet definierar ett antal parametrar som är gemensamma för alla aktiviteter. En delmängd av dessa parametrar kan anges vid redigerings tiden så att arbets flödes författarna kan anpassa aktiviteter. En annan delmängd av dessa parametrar kan anges av användaren när aktiviteten anropas.

De gemensamma arbets flödes parametrarna grupperas i flera kategorier enligt följande.

## <a name="connectivity-parameters"></a>Anslutnings parametrar

|Namn|Typ|Beskrivning|Kan anges av slutanvändaren vid körning?|Kan anges av arbets flödets författare vid redigerings tiden?|Kan anges av arbets flödets författare vid instansiering?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|En lista med dator namn som jobben ska startas för.|Ja|Ja|Ja|
|PSCredential|[System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Autentiseringsuppgifter för autentisering som ska användas för att logga in på de datorer som anges av parametern PSComputerName. Den här parametern är endast giltig om PSComputerName har angetts.|Ja|Ja|Ja|
|PSPort|UInt32|Den port som ska användas för att köra arbets flödet.|Ja|Ja|Ja|
|PSUseSSL|Boolesk|Använd Secure Sockets Layer (SSL)-protokollet för att upprätta en säker anslutning till fjärrdatorn för att köra arbets flödet.|Ja|Ja|Ja|
|PSConfigurationName|Sträng|Den sessionsinformation som används för att köra arbets flödet.|Ja|Ja|Ja|
|PSApplicationName|Sträng|Program namns delen av anslutnings-URI: n för arbets flödes körningen. Använd bara den här parametern när du inte använder parametern ConnectionURI.|Ja|Ja|Ja|
|PSThrottleLimit|UInt32|Det maximala antalet samtidiga anslutningar som kan upprättas för att köra arbets flödet.|Ja|TBD|Ja|
|PSConnectionURI|String[]|En matris med fullständigt kvalificerade URI: er som anger slut punkterna för de interaktiva sessioner som används för att köra arbets flödet.|Ja|Ja|Ja|
|PSAllowRedirection|Boolesk|Anger om du vill tillåta omdirigering av anslutningen till en alternativ URI för att köra arbets flödet.|Ja|Ja|Ja|
|PSSessionOption|[System. Management. Automation. Remoting. Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Avancerade alternativ för den session som används för att köra arbets flödet.|Ja|Ja|Ja|
|PSAuthentication|[System. Management. Automation. körnings utrymmen. Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Ett värde av uppräkningen [system. Management. Automation. körnings utrymmen. Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) som anger den autentiseringsmekanism som används för att autentisera användarens autentiseringsuppgifter.|Ja|Ja|Ja|
|PSCertificateThumbprint|Sträng|Det digitala certifikatet för offentlig nyckel (X509) för ett användar konto som har behörighet att köra arbets flödet.|Ja|Ja|Ja|

### <a name="behavior-parameters"></a>Beteende parametrar