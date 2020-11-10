---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa en Windows PowerShell-egenskapsprovider
description: Skapa en Windows PowerShell-egenskapsprovider
ms.openlocfilehash: 5370624afa784598ca784b201f7e7345eb958ff9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390923"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Skapa en Windows PowerShell-egenskapsprovider

I det här avsnittet beskrivs hur du skapar en provider som gör det möjligt för användaren att ändra egenskaperna för objekt i ett data lager. Därför kallas den här typen av Provider en Windows PowerShell-egenskaps leverantör. Registry-providern som tillhandahålls av Windows PowerShell hanterar till exempel register nyckel värden som egenskaper för register nyckel posten. Den här typen av Provider måste lägga till gränssnittet [system. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) i implementeringen av .net-klassen.

> [!NOTE]
> Windows PowerShell innehåller en mallfil som du kan använda för att utveckla en Windows PowerShell-Provider. TemplateProvider.cs-filen finns i Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Den hämtade mallen är tillgänglig i **\<PowerShell Samples>** katalogen. Du bör göra en kopia av den här filen och använda kopian för att skapa en ny Windows PowerShell-Provider och ta bort alla funktioner som du inte behöver. Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Metoderna för egenskaps leverantören ska skriva alla objekt med metoden [system. Management. Automation. Provider. Cmdletprovider. Writepropertyobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) .

## <a name="defining-the-windows-powershell-provider"></a>Definiera Windows PowerShell-providern

En egenskaps leverantör måste skapa en .NET-klass som stöder [system. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) -gränssnittet. Här är standard klass deklarationen från den TemplateProvider.cs-fil som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Definiera grundläggande funktioner

Gränssnittet [system. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) kan kopplas till någon av leverantörs bas klasserna, med undantag av klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Lägg till de grundläggande funktioner som krävs av Bask Lassen som du använder. Mer information om bas klasser finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Hämtar egenskaper

För att hämta egenskaper måste providern implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) för att stödja anrop från `Get-ItemProperty` cmdleten. Med den här metoden hämtas egenskaperna för objektet som finns på den angivna providern-interna sökvägen (fullständigt kvalificerad).

`providerSpecificPickList`Parametern anger vilka egenskaper som ska hämtas. Om den här parametern är `null` eller tom ska metoden hämta alla egenskaper. Dessutom skriver [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) en instans av ett [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt som representerar en egenskaps uppsättning av de hämtade egenskaperna. Metoden ska inte returnera något.

Vi rekommenderar att du implementerar [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) stöder expansion av jokertecken för egenskaps namn för varje element i Plock listan. Det gör du genom att använda klassen [system. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) för att utföra mönster matchning med jokertecken.

Här är standard implementeringen av [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) från TemplateProvider.cs-filen som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Saker att komma ihåg om implementera GetProperty

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- När du definierar Provider-klassen kan en Windows PowerShell-egenskaps leverantör deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte hämta en läsare för objekt som är dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true` . Ett fel ska skrivas om sökvägen representerar ett objekt som är dolt från användaren och [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `false` .

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Bifoga dynamiska parametrar till Get-ItemProperty-cmdleten

`Get-ItemProperty`Cmdleten kan kräva ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-egenskapsvärdena implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) . `path`Parametern anger en fullständigt kvalificerad Provider – intern sökväg, medan `providerSpecificPickList` parametern anger de providerspecifika egenskaper som anges på kommando raden. Den här parametern kan vara `null` eller tom om egenskaperna är skickas till cmdleten. I det här fallet returnerar den här metoden ett objekt som har egenskaper och fält med parsa attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna i cmdleten.

Här är standard implementeringen av [system. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) från TemplateProvider.cs-filen från Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Ange egenskaper

Om du vill ange egenskaper måste Windows PowerShell-egenskapsvärden implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) för att stödja anrop från `Set-ItemProperty` cmdleten. Den här metoden anger en eller flera egenskaper för objektet på den angivna sökvägen och skriver över de angivna egenskaperna efter behov.
[System. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) skriver också en instans av ett [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt som representerar en egenskaps uppsättning av de uppdaterade egenskaperna.

Här är standard implementeringen av [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) från TemplateProvider.cs-filen som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Saker att komma ihåg om hur du implementerar Set-ItemProperty

Följande villkor kan gälla för en implementering av [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- När du definierar Provider-klassen kan en Windows PowerShell-egenskaps leverantör deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte hämta en läsare för objekt som är dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true` . Ett fel ska skrivas om sökvägen representerar ett objekt som är dolt från användaren och [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `false` .

- Din implementering av [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) -metoden ska anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och verifiera dess retur värde innan du gör några ändringar i data lagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs i system tillstånd, till exempel att byta namn på filer.
  [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med Windows PowerShell-körningsmiljön och hanterar alla kommando rads inställningar eller variabler för att fastställa vad som ska visas.

  Efter att anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returneras `true` , om potentiellt skadliga system ändringar kan göras, ska metoden system [. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) anropa metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Den här metoden skickar ett bekräftelse meddelande till användaren för att tillåta ytterligare feedback för att visa att åtgärden bör fortsätta.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Att bifoga dynamiska parametrar för Set-ItemProperty cmdlet

`Set-ItemProperty`Cmdleten kan kräva ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-egenskapsvärdena implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) . Den här metoden returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. `null`Värdet kan returneras om inga dynamiska parametrar ska läggas till.

Här är standard implementeringen av [system. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) från TemplateProvider.cs-filen från Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Egenskaper rensas

För att rensa egenskaper måste Windows PowerShell-egenskapsvärden implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) för att stödja anrop från `Clear-ItemProperty` cmdleten. Den här metoden anger en eller flera egenskaper för objektet som finns på den angivna sökvägen.

Här är standard implementeringen av [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) från TemplateProvider.cs-filen från Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Kom ihåg att implementera ClearProperty

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- När du definierar Provider-klassen kan en Windows PowerShell-egenskaps leverantör deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte hämta en läsare för objekt som är dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true` . Ett fel ska skrivas om sökvägen representerar ett objekt som är dolt från användaren och [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `false` .

- Din implementering av metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) ska anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och verifiera dess retur värde innan du gör några ändringar i data lagret. Den här metoden används för att bekräfta körningen av en åtgärd innan en ändring görs i system tillstånd, t. ex. Rensa innehåll.
  [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med Windows PowerShell-körningsmiljön med hänsyn till eventuella kommando rads inställningar eller variabler för att fastställa vad som ska visas.

  Efter att anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returneras `true` , om potentiellt skadliga system ändringar kan göras, ska metoden system [. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) anropa metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Den här metoden skickar ett bekräftelse meddelande till användaren för att tillåta ytterligare feedback för att ange att den potentiellt farliga åtgärden bör fortsätta.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Bifoga dynamiska parametrar till Clear-ItemProperty-cmdleten

`Clear-ItemProperty`Cmdleten kan kräva ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-egenskapsvärdena implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) . Den här metoden returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. `null`Värdet kan returneras om inga dynamiska parametrar ska läggas till.

Här är standard implementeringen av [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) från TemplateProvider.cs-filen från Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Skapa Windows PowerShell-providern

Se [hur du registrerar cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).

## <a name="see-also"></a>Se även

[Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)

[Utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)

[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))

[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))
