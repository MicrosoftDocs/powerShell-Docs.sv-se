---
title: Översikt över Windows PowerShell-Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 81f6c8cd75ccea9e711cd8f6d6daa6cca5a499a0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356828"
---
# <a name="windows-powershell-provider-overview"></a>Översikt över Windows PowerShell-providers

Med en Windows PowerShell-Provider kan alla data lager visas som ett fil system som om det vore en monterad enhet. Den inbyggda Registry-providern gör det till exempel möjligt att navigera i registret, precis som du navigerar `c` hård disken på din dator. En provider kan även åsidosätta `Item`-cmdletar (till exempel `Get-Item`, `Set-Item`osv.), så att data i data lagret kan behandlas som filer och kataloger när du navigerar i ett fil system. Mer information om leverantörer och enheter och de inbyggda providers i Windows PowerShell finns [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Leverantörer och enheter

En provider definierar den logik som används för att komma åt, navigera i och redigera ett data lager, medan en enhet anger en viss start punkt för ett data lager (eller en del av ett data lager) som är av den typ som definieras av providern. Registry-providern kan till exempel använda Hive och nycklar i ett register, och HKLM-och HKCU-enheterna anger motsvarande registreringsdatafiler i registret. HKLM-och HKCU-enheterna använder båda register leverantören.

När du skriver en provider kan du ange standard enheter – enheter som skapas automatiskt när leverantören är tillgänglig. Du definierar också en metod för att skapa nya enheter som använder providern.

## <a name="type-of-providers"></a>Typ av leverantörer

Det finns flera typer av leverantörer, som var och en har olika funktions nivåer. En provider implementeras som en klass som härleds från en av de underordnade objekten i klassen [system. Management. Automation. SessionStateCategory](/dotnet/api/system.management.automation.sessionstatecategory?view=pscore-6.2.0) **CmdletProvider** . Information om olika typer av leverantörer finns i [typer](./provider-types.md)av leverantörer.

## <a name="provider-cmdlets"></a>Cmdlets för providers

Leverantörer kan implementera metoder som motsvarar cmdlets och skapa anpassade beteenden för dessa cmdletar när de används i en enhet för providern. Olika uppsättningar cmdlets är tillgängliga beroende på typ av Provider. En fullständig lista över de cmdletar som är tillgängliga för anpassning i providrar finns i [Provider-cmdletar](./provider-cmdlets.md).

## <a name="provider-paths"></a>Provider-sökvägar

Användare navigerar leverantörs enheter som fil system. Därför förväntas syntaxen för sökvägar som motsvarar de sökvägar som används i fil system navigering. När en användare kör en provider-cmdlet anger de en sökväg till det objekt som ska nås. Den angivna sökvägen kan tolkas på flera sätt. En provider bör ha stöd för en eller flera av följande Sök vägs typer.

### <a name="drive-qualified-paths"></a>Enhet – kvalificerade sökvägar

En enhets kvalificerad sökväg är en kombination av objekt namn, behållare och under behållare där objektet finns och Windows PowerShell-enheten som objektet har åtkomst till. (Enheter definieras av den provider som används för att få åtkomst till data lagret. Den här sökvägen börjar med enhets namnet följt av ett kolon (:). Exempel: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Kvalificerade sökvägar för Provider

Providern måste ha stöd för en provider-kvalificerad sökväg för att Windows PowerShell-motorn ska kunna initiera och avinitiera providern. Användaren kan till exempel initiera och avinitiera fil systemets Provider eftersom den definierar följande Provider-kvalificerade sökväg: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Provider – direkta sökvägar

Om du vill tillåta fjärråtkomst till Windows PowerShell-providern ska den stödja en provider-direkt sökväg för att skicka direkt till Windows PowerShell-providern för den aktuella platsen. Till exempel kan registrets Windows PowerShell-Provider använda `\\server\regkeypath` som en provider-direkt sökväg.

### <a name="provider-internal-paths"></a>Provider – interna sökvägar

Om du vill tillåta Provider-cmdleten att komma åt data med icke-Windows PowerShell-API: er (Application Programming Interfaces) ska din Windows PowerShell-Provider stödja en provider-intern sökväg. Den här sökvägen anges efter "::" i providerns kvalificerade sökväg. Den provider-interna sökvägen för Windows PowerShell-providern för fil systemet `\\uncshare\abc\bar`till exempel.

## <a name="overriding-cmdlet-parameters"></a>Åsidosätter cmdlet-parametrar

Beteendet för vissa providerspecifika cmdletar kan åsidosättas av en provider. En lista över parametrar som kan åsidosättas och hur du åsidosätter dem i din leverantörs klass finns i [providerns cmdlet-parametrar](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>Dynamiska parametrar

Leverantörer kan definiera dynamiska parametrar som läggs till i en providers-cmdlet när användaren anger ett visst värde för en av de statiska parametrarna för cmdleten. En provider gör detta genom att implementera en eller flera dynamiska parameter metoder. En lista över cmdlet-parametrar som kan användas för att lägga till en dynamisk parameter och de metoder som används för att implementera dem finns i [dynamiska parametrar för provider-cmdlet](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Leverantörs funktioner

I uppräkningen [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) definieras ett antal funktioner som providers kan stödja. Detta inkluderar möjligheten att använda jokertecken, filtrera objekt och stöd transaktioner. Om du vill ange funktioner för en provider lägger du till en lista med värden för attributet [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) , kombinerat med en logisk `OR`-åtgärd, som egenskapen [system. Management. Automation. Provider. Cmdletproviderattribute. ProviderCapabilities *](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) (den andra parametern för attributet) för attributet [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) för din leverantörs klass. Följande attribut anger till exempel att providern stöder funktionerna [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **ShouldProcess** och [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **transaktioner** .

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Hjälp om Provider-cmdlet

När du skriver en provider kan du implementera din egen hjälp för de Provider-cmdletar som du stöder. Detta omfattar ett enda hjälp avsnitt för varje provider-cmdlet eller flera versioner av ett hjälp avsnitt för fall där providerns cmdlet fungerar på olika sätt baserat på användningen av dynamiska parametrar. Om du vill ha stöd för providerns cmdlet-/regionsspecifika hjälp måste leverantören implementera gränssnittet [system. Management. Automation. Provider. Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) .

Windows PowerShell-motorn anropar metoden [system. Management. Automation. Provider. Icmdletprovidersupportshelp. Gethelpmaml *](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) för att visa hjälp avsnittet för dina Provider-cmdletar. Motorn tillhandahåller namnet på den cmdlet som användaren angav när du körde `Get-Help`-cmdlet och den aktuella sökvägen till användaren. Den aktuella sökvägen krävs om providern implementerar olika versioner av samma provider-cmdlet för olika enheter. Metoden måste returnera en sträng som innehåller XML-koden för cmdlet-hjälpen.

Innehållet för hjälp filen skrivs med PSMAML XML. Detta är samma XML-schema som används för att skriva Hjälp innehåll för fristående cmdlets. Lägg till innehållet för din anpassade cmdlet-hjälp till hjälp filen för din Provider under `CmdletHelpPaths`-elementet. I följande exempel visas `command`-elementet för en enda Provider-cmdlet, och det visar hur du anger namnet på den provider-cmdlet som din Provider. har stöd för

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

[Funktioner i Windows PowerShell-Provider](./provider-types.md)

[Provider-cmdletar](./provider-cmdlets.md)

[Skriva en Windows PowerShell-Provider](./writing-a-windows-powershell-provider.md)