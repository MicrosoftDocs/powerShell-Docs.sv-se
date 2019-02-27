---
title: Windows PowerShell-providern översikt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 31ee7222c35e82ee58d6d56f710792dbc5cb24d7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848652"
---
# <a name="windows-powershell-provider-overview"></a>Översikt över Windows PowerShell-providers

En Windows PowerShell-providern kan ingen datalagring exponeras som ett filsystem som om det vore en monterad enhet. Till exempel inbyggda register-provider kan du navigera i registret som du vill navigera i `c` på datorns hårddisk. En provider kan också åsidosätta den `Item` cmdletar (till exempel `Get-Item`, `Set-Item`och så vidare) så att data i ditt datalager kan behandlas som filer och kataloger behandlas när du navigerar ett filsystem. Mer information om leverantörer och enheter och providrar för inbyggd i Windows PowerShell finns i [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).
En Windows PowerShell-providern kan ingen datalagring exponeras som ett filsystem som om det vore en monterad enhet. Till exempel inbyggda register-provider kan du navigera i registret som du vill navigera i `c` på datorns hårddisk. En provider kan också åsidosätta den `Item` cmdletar (till exempel `Get-Item`, `Set-Item`och så vidare) så att data i ditt datalager kan behandlas som filer och kataloger behandlas när du navigerar ett filsystem. Mer information om leverantörer och enheter och providrar för inbyggd i Windows PowerShell finns i [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Leverantörer och enheter

En leverantör definierar logiken som används för att komma åt, navigera och redigera ett datalager, medan en enhet som anger en specifik startpunkt till ett datalager (eller en del av ett datalager) som är av typen som definierats av providern. Till exempel en register-provider kan du komma åt registreringsdatafilerna och nycklar i ett register och HKLM och HKCU enheter ange motsvarande registreringsdatafilerna i registret. De HKLM och HKCU enheterna båda använda register-provider.

Du kan ange standard-enheter – enheter som skapas automatiskt när providern är tillgänglig när du skriver en provider. Du kan också definiera en metod för att skapa nya enheter som använder providern.

## <a name="type-of-providers"></a>Typ av Providers

Det finns flera typer av leverantörer, som har olika funktioner. En provider implementeras som en klass som härleds från en av de underordnade objekten för den [System.Management.Automation.Sessionstatecategory.Cmdletprovider](/dotnet/api/System.Management.Automation.SessionStateCategory.CmdletProvider) klass. Information om de olika typerna av leverantörer finns i [providertyper](./provider-types.md).

## <a name="provider-cmdlets"></a>Cmdlets för providers

Leverantörer kan implementera metoder för cmdlet: ar, skapa anpassade beteenden för cmdletar när den används i en enhet för providern. Olika uppsättningar av cmdlets som är tillgängliga beroende på vilken typ av provider. En fullständig lista över cmdletarna som är tillgängliga för anpassning i providers Se [cmdlets Provider](./provider-cmdlets.md).

## <a name="provider-paths"></a>Providern sökvägar

Användare navigera providern enheter, filsystem. De förväntar sig syntaxen för sökvägar som motsvarar de sökvägar som används i filen system navigeringen på grund av detta. När användaren kör en provider-cmdlet, anger de en sökväg till objektet som ska användas. Den sökväg som har angetts kan tolkas på flera olika sätt. En provider ska ha stöd för en eller flera av följande typer av sökvägen.

### <a name="drive-qualified-paths"></a>Enheten kvalificerade sökvägar

En enhet sökväg är en kombination av objektnamnet, behållaren och underbehållare där objektet finns och Windows PowerShell-enhet som objektet används. (Enheter definieras av den provider som används för att få åtkomst till datalagret. Den här sökvägen börjar med enhetsnamnet följt av ett kolon (:). Exempel: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Providern kvalificerade sökvägar

För att tillåta Windows PowerShell-motorn att initiera och uninitialize din provider måste providern stödja en provider-sökväg. Exempelvis kan användaren kan initiera och uninitialize filsystem-providern eftersom den definierar följande provider kvalificerade sökvägen: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Provider-direct sökvägar

För att tillåta fjärråtkomst till Windows PowerShell-providern, bör det stöder en provider-direct sökväg skickas direkt till Windows PowerShell-providern för den aktuella platsen. Windows PowerShell-providern registret kan till exempel använda `\\server\regkeypath` som en provider-direct-sökväg.

### <a name="provider-internal-paths"></a>Provider-interna sökvägar

Om du vill tillåta provider-cmdlet för att få åtkomst till data med hjälp av icke - Windows PowerShell programgränssnitt (API: er), Windows PowerShell-providern ska ha stöd en provider-internt sökväg. Den här sökvägen anges i ”::” i sökvägen med providern. Till exempel den provider-interna sökvägen för Windows PowerShell-providern filsystem är `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Åsidosätta cmdlet-parametrarna

Beteendet för vissa provider-specifik cmdlets kan åsidosättas av en leverantör. En lista över parametrar som kan åsidosättas och hur du kan åsidosätta dem i din providerklass finns i [Provider cmdlet-parametrarna](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>Dynamiska parametrar

Leverantörer kan definiera dynamiska parametrar som läggs till en provider-cmdlet när användaren anger ett visst värde för en statisk parametrarna för cmdleten. En provider gör detta genom att implementera en eller flera dynamiska parametern-metoder. En lista över cmdlet-parametrarna som kan användas för att lägga till dynamisk parameter, samt de metoder som används för att implementera dem, se [providern cmdlet dynamiska parametrar](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Provider-funktioner

Den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning definierar ett antal funktioner som har stöd för leverantörer. Dessa inkluderar möjligheten att använda jokertecken, filtrera objekt och stöd för transaktioner. Funktioner för en provider lägger du till en lista med värden för den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen, i kombination med en logisk `OR` åtgärd, som den [ System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) egenskapen (den andra parametern för attributet) för den [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut för providerklassen. Till exempel följande attribut anger att providern stöder den [System.Management.Automation.Provider.Providercapabilities.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.ShouldProcess) och [ System.Management.Automation.Provider.Providercapabilities.Transactions](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.Transactions) funktioner.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Cmdlet-hjälpavsnitten för provider

När du skriver en provider ska implementera du egna hjälp för provider-cmdletar som du stöder. Detta inkluderar ett enda hjälpavsnitt för varje provider-cmdlet eller flera versioner av ett hjälpavsnitt i de fall där cmdleten providern fungerar på olika sätt beroende på användningen av dynamiska parametrar. För att stödja providern cmdlet-specifik hjälp leverantören måste implementera de [System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) gränssnitt.

Windows PowerShell-motorn anrop den [System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) metod för att visa hjälpavsnitt för provider-cmdletar. Motorn innehåller namnet på den cmdlet som du angav när du kör den `Get-Help` cmdlet och den aktuella sökvägen för användaren. Den aktuella sökvägen krävs om din provider implementerar olika versioner av samma provider-cmdlet för olika enheter. Metoden måste returnera en sträng som innehåller XML-filen för cmdleten hjälp.

Innehållet för hjälpfilen skrivs med PSMAML XML. Det här är samma XML-schema som används för att skriva hjälpinnehållet för fristående cmdletar. Lägg till innehåll för din anpassade cmdlet hjälp att hjälpfilen för din leverantör under den `CmdletHelpPaths` element. I följande exempel visas den `command` element för en enskild provider-cmdlet och visar hur du anger namnet på den provider-cmdleten som din provider. har stöd för

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>Se även

[Providerfunktioner för Windows PowerShell](./provider-types.md)

[Cmdlets för provider](./provider-cmdlets.md)

[Skriva ett Windows PowerShell-providern](./writing-a-windows-powershell-provider.md)