---
title: Gemensamma arbetsflödesparametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: 2aca4483e500432ef9f52804e85678d2268aa4cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846909"
---
# <a name="common-workflow-parameters"></a>Vanliga arbetsflödesparametrar

En arbetsflödesaktivitet som genereras från en Windows PowerShell-cmdlet definierar ett antal parametrar att gemensamma för alla aktiviteter. Du kan ange en delmängd av dessa parametrar när du redigerar så att arbetsflödesskapare kan anpassa aktiviteter. En annan del av dessa parametrar kan anges av användaren när du anropar aktiviteten.

De gemensamma arbetsflödesparametrarna för är grupperade i flera kategorier på följande sätt.

## <a name="connectivity-parameters"></a>Parametrar för anslutning

|Namn|Typ|Beskrivning|Kan anges av slutanvändaren vid körning?|Du kan ange installationskommandot arbetsflöde vid redigeringen?|Du kan ange installationskommandot arbetsflöde vid instansiering?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|En lista med datornamn som du vill starta jobb.|Ja|Ja|Ja|
|PSCredential|[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)|Autentisering-autentiseringsuppgift som ska användas för inloggning till de datorer som anges av parametern PSComputerName. Den här parametern är bara giltiga om PSComputerName har angetts.|Ja|Ja|Ja|
|PSPort|UInt32|Porten som ska användas för att köra arbetsflödet.|Ja|Ja|Ja|
|PSUseSSL|Boolesk|Använda Secure Sockets Layer (SSL)-protokollet för att upprätta en säker anslutning till fjärrdatorn att köra arbetsflödet.|Ja|Ja|Ja|
|PSConfigurationName|Sträng|Sessionskonfigurationen som används för att köra arbetsflödet.|Ja|Ja|Ja|
|PSApplicationName|Sträng|Programmet klientnamnsdelen av URI-anslutning för arbetsflödeskörning. Använd den här parametern endast när du inte använder parametern ConnectionURI.|Ja|Ja|Ja|
|PSThrottleLimit|UInt32|Det maximala antalet samtidiga anslutningar som kan fastställas för att köra arbetsflödet.|Ja|TBD|Ja|
|PSConnectionURI|String[]|En matris med fullständigt kvalificerade URI: er som anger slutpunkterna för de interaktiva sessioner som används för att köra arbetsflödet.|Ja|Ja|Ja|
|PSAllowRedirection|Boolesk|Anger om du vill tillåta omdirigering för den här anslutningen till en annan URI: N för att köra arbetsflödet.|Ja|Ja|Ja|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Avancerade alternativ för den session som används för att köra arbetsflödet.|Ja|Ja|Ja|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Värdet på [System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) uppräkning som anger den autentiseringsmetod som används för att autentisera användarens autentiseringsuppgifter.|Ja|Ja|Ja|
|PSCertificateThumbprint|Sträng|Det digitala offentliga nyckelcertifikatet (X509) för ett användarkonto som har behörighet att köra arbetsflödet.|Ja|Ja|Ja|

### <a name="behavior-parameters"></a>Beteendeparametrar