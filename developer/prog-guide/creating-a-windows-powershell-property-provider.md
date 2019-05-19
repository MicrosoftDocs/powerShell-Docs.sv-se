---
title: Skapa en Windows PowerShell-egenskap-Provider | Microsoft Docs
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
ms.openlocfilehash: c503b17a670a5d1f07aa48e714d8a0eb0aa78ae9
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855007"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Skapa en Windows PowerShell-egenskapsprovider

Det här avsnittet beskriver hur du skapar en provider som gör att användaren kan ändra egenskaperna för objekt i ett datalager. Följaktligen kommer kallas den här typen av providern en provider för Windows PowerShell-egenskapen. Till exempel en register-provider som tillhandahålls av Windows PowerShell hanterar registernyckelvärden som egenskaper för viktiga registerobjekt. Den här typen av providern måste lägga till den [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) gränssnitt för implementeringen av .NET-klass.

> [!NOTE]
> Windows PowerShell innehåller en mallfil som du kan använda för att utveckla en Windows PowerShell-providern. TemplateProvider.cs-filen är tillgänglig på Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Den nedladdningsbara mallen finns i den  **\<PowerShell-exempel >** directory. Du bör göra en kopia av den här filen och använder kopian för att skapa en ny Windows PowerShell-provider, ta bort funktioner som du inte behöver.
>
> Läs mer om andra Windows PowerShell-providern implementeringar [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Metoderna i egenskapen-providern ska skriva eventuella objekt med hjälp av den [System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) metod.

## <a name="defining-the-windows-powershell-provider"></a>Definiera Windows PowerShell-providern

En Egenskapsprovider måste skapa en .NET-klass som har stöd för den [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) gränssnitt. Här är standard klassdeklarationen från filen TemplateProvider.cs som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Definiera grundfunktionen

Den [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) gränssnitt kan kopplas till någon av provider-basklasser, med undantag för den [ System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klass. Lägg till grundläggande funktioner som krävs av den basklass som du använder. Läs mer om basklasser [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Hämta egenskaper

Om du vill hämta egenskaper för providern måste implementera de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) metod för att stödja anrop från den `Get-ItemProperty` cmdlet. Den här metoden hämtar egenskaperna för objekt som finns på den angivna provider interna sökvägen (fullständigt).

Den `providerSpecificPickList` parametern anger vilka egenskaper du vill hämta. Om den här parametern `null` eller tom, metoden bör hämta alla egenskaper. Dessutom [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) skriver en instans av en [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objekt som representerar en Egenskapsuppsättning för egenskaperna hämtades. Metoden ska returnera ingenting.

Vi rekommenderar att implementeringen av [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) stöder jokertecken utökningen av egenskapsnamn för varje element i listan. Gör detta genom att använda den [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) klassen för att utföra den jokerteckensmönster.

Här är standardimplementering av [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) från filen TemplateProvider.cs som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Kom ihåg följande om hur du implementerar GetProperty

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- När du definierar providerklassen, en provider för Windows PowerShell-egenskapen kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning. I dessa fall är implementeringen av den [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) metod måste se till att sökvägen skickas till metoden uppfyller kraven för den angivna funktioner. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Som standard åsidosättningar av den här metoden ska inte att hämta en läsare för objekt som är dolda från användaren, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Ett fel ska skrivas om sökvägen representerar ett objekt som är dolda från användaren och [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Bifoga dynamiska parametrar till cmdleten Get-itemproperty-egenskap

Den `Get-ItemProperty` cmdlet kan kräva ytterligare parametrar som anges dynamiskt vid körning. För att ge dessa dynamiska parametrar, Windows PowerShell-egenskapen leverantören måste implementera de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) metod. Den `path` parametern indikerar en fullständiga provider-internt sökväg, medan den `providerSpecificPickList` parametern anger provider-specifik-egenskaper som anges på kommandoraden. Den här parametern kan vara `null` eller tom om egenskaperna är skickas till cmdleten. I det här fallet den här metoden returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till cmdleten.

Här är standardimplementering av [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) från filen TemplateProvider.cs som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Ange egenskaper

Om du vill ange egenskaper för Windows PowerShell-egenskapen leverantören måste implementera de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metod för att stödja anrop från den `Set-ItemProperty` cmdlet. Den här metoden anger en eller flera egenskaper för objektet på den angivna sökvägen och skriver över de angivna egenskaperna som krävs. [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) skriver också en instans av en [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objekt som representerar en egenskapsuppsättning för den uppdaterade Egenskaper.

Här är standardimplementering av [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) från filen TemplateProvider.cs som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Kom ihåg följande om hur du implementerar Set-itemproperty-egenskap

Följande villkor kan gälla för en implementering av [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- När du definierar providerklassen, en provider för Windows PowerShell-egenskapen kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning. I dessa fall är implementeringen av den [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metod måste se till att sökvägen skickas till metoden uppfyller kraven för den angivna funktioner. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Som standard åsidosättningar av den här metoden ska inte att hämta en läsare för objekt som är dolda från användaren, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Ett fel ska skrivas om sökvägen representerar ett objekt som är dolda från användaren och [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `false`.

- Implementeringen av den [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metoden ska anropa [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och verifiera dess returvärdet innan du gör några ändringar i datalagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs i systemtillståndet, till exempel byta namn på filer. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på resursen som ska ändras till användaren med Windows PowerShell-runtime och hantering av alla kommandoradsinställningar eller preferensvariabler fastställa Vad ska visas.

  Efter anropet till [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`om potentiellt skadliga system ändringar kan göras, den [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metoden ska anropa den [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metod. Den här metoden skickar en bekräftelse till användaren så att ytterligare feedback att indikera att åtgärden bör fortsätta.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Koppla dynamiska parametrar för cmdleten Set-itemproperty-egenskap

Den `Set-ItemProperty` cmdlet kan kräva ytterligare parametrar som anges dynamiskt vid körning. För att ge dessa dynamiska parametrar, Windows PowerShell-egenskapen leverantören måste implementera de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) metod. Den här metoden returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Den `null` värde kan returneras om inga dynamiska parametrar som ska läggas till.

Här är standardimplementering av [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) från filen TemplateProvider.cs som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Rensa egenskaper

Om du vill rensa egenskaper för Windows PowerShell-egenskapen leverantören måste implementera de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) metod för att stödja anrop från den `Clear-ItemProperty` cmdlet. Den här metoden anger en eller flera egenskaper för objekt som finns på den angivna sökvägen.

Här är standardimplementering av [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) från filen TemplateProvider.cs som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Viktigt att komma ihåg om hur du implementerar ClearProperty

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- När du definierar providerklassen, en provider för Windows PowerShell-egenskapen kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning. I dessa fall är implementeringen av den [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) metod måste se till att sökvägen skickas till metoden uppfyller kraven för den angivna funktioner. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Som standard åsidosättningar av den här metoden ska inte att hämta en läsare för objekt som är dolda från användaren, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Ett fel ska skrivas om sökvägen representerar ett objekt som är dolda från användaren och [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `false`.

- Implementeringen av den [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) metoden ska anropa [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och verifiera dess returvärdet innan du gör några ändringar i datalagret. Den här metoden används för att bekräfta körning av en åtgärd innan en ändring görs i systemtillstånd, t.ex Rensa innehåll. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med hänsyn till alla inställningar för kommandoraden eller variabler i Windows PowerShell-körningsmiljön bestämma vad som ska visas.

  Efter anropet till [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`om potentiellt skadliga system ändringar kan göras, den [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) metoden ska anropa den [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metod. Den här metoden skickar en bekräftelse till användaren så att ytterligare feedback att indikera att potentiellt skadliga åtgärden bör fortsätta.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Bifoga dynamiska parametrar till cmdleten Clear-itemproperty-egenskap

Den `Clear-ItemProperty` cmdlet kan kräva ytterligare parametrar som anges dynamiskt vid körning. För att ge dessa dynamiska parametrar, Windows PowerShell-egenskapen leverantören måste implementera de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) metod. Den här metoden returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Den `null` värde kan returneras om inga dynamiska parametrar som ska läggas till.

Här är standardimplementering av [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) från filen TemplateProvider.cs som tillhandahålls av Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Att skapa Windows PowerShell-providern

Se [hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Se även

[Windows PowerShell-providern](./designing-your-windows-powershell-provider.md)

[Utforma din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md)

[Utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)