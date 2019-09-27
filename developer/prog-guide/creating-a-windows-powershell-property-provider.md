---
title: Skapa en Windows PowerShell-egenskaps leverantör | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: c36b93a5b4d3e7ef92d7f5b16381a8def2dd5466
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323106"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Skapa en Windows PowerShell-egenskapsprovider

I det här avsnittet beskrivs hur du skapar en provider som gör det möjligt för användaren att ändra egenskaperna för objekt i ett data lager. Därför kallas den här typen av Provider en Windows PowerShell-egenskaps leverantör. Registry-providern som tillhandahålls av Windows PowerShell hanterar till exempel register nyckel värden som egenskaper för register nyckel posten. Den här typen av Provider måste lägga till gränssnittet [system. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) i implementeringen av .net-klassen.

> [!NOTE]
> Windows PowerShell innehåller en mallfil som du kan använda för att utveckla en Windows PowerShell-Provider. TemplateProvider.cs-filen finns i Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Den nedladdade mallen är tillgänglig i  **\<PowerShell-exemplen >** Directory. Du bör göra en kopia av den här filen och använda kopian för att skapa en ny Windows PowerShell-Provider och ta bort alla funktioner som du inte behöver.
>
> Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Metoderna för egenskaps leverantören ska skriva alla objekt med metoden [system. Management. Automation. Provider. Cmdletprovider. Writepropertyobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) .

## <a name="defining-the-windows-powershell-provider"></a>Definiera Windows PowerShell-providern

En egenskaps leverantör måste skapa en .NET-klass som stöder [system. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) -gränssnittet. Här är standard klass deklarationen från den TemplateProvider.cs-fil som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Definiera grundläggande funktioner

Gränssnittet [system. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) kan kopplas till någon av leverantörs bas klasserna, med undantag av klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Lägg till de grundläggande funktioner som krävs av Bask Lassen som du använder. Mer information om bas klasser finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Hämtar egenskaper

För att hämta egenskaper måste providern implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) för att stödja anrop från `Get-ItemProperty` cmdleten. Med den här metoden hämtas egenskaperna för objektet som finns på den angivna providern-interna sökvägen (fullständigt kvalificerad).

`providerSpecificPickList` Parametern anger vilka egenskaper som ska hämtas. Om den här parametern `null` är eller tom ska metoden hämta alla egenskaper. Dessutom skriver [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) en instans av ett [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt som representerar en egenskaps uppsättning av de hämtade egenskaperna. Metoden ska inte returnera något.

Vi rekommenderar att du implementerar [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) stöder expansion av jokertecken för egenskaps namn för varje element i Plock listan. Det gör du genom att använda klassen [system. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) för att utföra mönster matchning med jokertecken.

Här är standard implementeringen av [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) från TemplateProvider.cs-filen som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Saker att komma ihåg om implementera GetProperty

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- När du definierar Provider-klassen kan en Windows PowerShell-egenskaps leverantör deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte hämta en läsare för objekt som är dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true`. Ett fel ska skrivas om sökvägen representerar ett objekt som är dolt från användaren och [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Koppla dynamiska parametrar till get-ItemProperty-cmdleten

`Get-ItemProperty` Cmdleten kan kräva ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-egenskapsvärdena implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) . Parametern anger en fullständigt kvalificerad Provider – intern sökväg, `providerSpecificPickList` medan parametern anger de providerspecifika egenskaper som anges på kommando raden. `path` Den här parametern kan `null` vara eller tom om egenskaperna är skickas till cmdleten. I det här fallet returnerar den här metoden ett objekt som har egenskaper och fält med parsa attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna i cmdleten.

Här är standard implementeringen av [system. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) från TemplateProvider.cs-filen från Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Ange egenskaper

Om du vill ange egenskaper måste Windows PowerShell-egenskapsvärden implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) för att stödja anrop från `Set-ItemProperty` cmdleten. Den här metoden anger en eller flera egenskaper för objektet på den angivna sökvägen och skriver över de angivna egenskaperna efter behov. [System. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) skriver också en instans av ett [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt som representerar en egenskaps uppsättning av de uppdaterade egenskaperna.

Här är standard implementeringen av [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) från TemplateProvider.cs-filen som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Saker att komma ihåg om att implementera Set-ItemProperty

Följande villkor kan gälla för en implementering av [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- När du definierar Provider-klassen kan en Windows PowerShell-egenskaps leverantör deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte hämta en läsare för objekt som är dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true`. Ett fel ska skrivas om sökvägen representerar ett objekt som är dolt från användaren och [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `false`.

- Din implementering av metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) måste anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och verifiera dess retur värde Innan du gör några ändringar i data lagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs i system tillstånd, till exempel att byta namn på filer. [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med Windows PowerShell-körningsmiljön och hanterar alla kommando rads inställningar eller variabler för att fastställa vad ska visas.

  Efter att anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returneras `true`, om potentiellt skadliga system ändringar kan göras, [ System. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metoden ska anropa metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Den här metoden skickar ett bekräftelse meddelande till användaren för att tillåta ytterligare feedback för att visa att åtgärden bör fortsätta.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Bifoga dynamiska parametrar för Set-ItemProperty-cmdleten

`Set-ItemProperty` Cmdleten kan kräva ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-egenskapsvärdena implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) . Den här metoden returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. `null` Värdet kan returneras om inga dynamiska parametrar ska läggas till.

Här är standard implementeringen av [system. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) från TemplateProvider.cs-filen från Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Egenskaper rensas

För att rensa egenskaper måste Windows PowerShell-egenskapsvärden implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) för att stödja anrop från `Clear-ItemProperty` cmdleten. Den här metoden anger en eller flera egenskaper för objektet som finns på den angivna sökvägen.

Här är standard implementeringen av [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) från TemplateProvider.cs-filen från Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Kom ihåg att implementera ClearProperty

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- När du definierar Provider-klassen kan en Windows PowerShell-egenskaps leverantör deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte hämta en läsare för objekt som är dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true`. Ett fel ska skrivas om sökvägen representerar ett objekt som är dolt från användaren och [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `false`.

- Din implementering av metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) måste anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och verifiera dess retur värde Innan du gör några ändringar i data lagret. Den här metoden används för att bekräfta körningen av en åtgärd innan en ändring görs i system tillstånd, t. ex. Rensa innehåll. [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på den resurs som ska ändras till användaren, med Windows PowerShell-körningsmiljön med hänsyn till eventuella kommando rads inställningar eller variabler för att fastställa vad som ska visas.

  Efter att anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returneras `true`, om potentiellt skadliga system ändringar kan göras, [ Metoden system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) anropa metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Den här metoden skickar ett bekräftelse meddelande till användaren för att tillåta ytterligare feedback för att ange att den potentiellt farliga åtgärden bör fortsätta.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Koppla dynamiska parametrar till cmdleten Clear-ItemProperty

`Clear-ItemProperty` Cmdleten kan kräva ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-egenskapsvärdena implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) . Den här metoden returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. `null` Värdet kan returneras om inga dynamiska parametrar ska läggas till.

Här är standard implementeringen av [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) från TemplateProvider.cs-filen från Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Skapa Windows PowerShell-providern

Se [hur du registrerar cmdlets, providers och värd program](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Se även

[Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)

[Utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)

[Utöka objekt typer och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Registrera cmdlets, providers och värd program](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)