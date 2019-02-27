---
title: Designa din Windows PowerShell-Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 518040df4df7260a974bfda252c606a051cc35ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847413"
---
# <a name="designing-your-windows-powershell-provider"></a>Designa en Windows PowerShell-provider

Om din produkt eller konfiguration visar en uppsättning lagrade data, till exempel en databas som du vill navigera eller bläddra bör du implementera en Windows PowerShell-providern. Om din produkt innehåller en behållare, även om det inte är en behållare med flera nivåer, är det dessutom meningsfullt att implementera en Windows PowerShell-providern. Du kanske vill implementera en provider för Windows PowerShell-behållare om cmdlet verb kopiera, flytta, byta namn, ny, eller ta bort rimligt som en åtgärd på din produkt eller configuration-data.

## <a name="windows-powershell-paths-identify-your-provider"></a>Windows PowerShell-sökvägar identifiera din Provider

Windows PowerShell-runtime använder Windows PowerShell-sökvägar till lämplig Windows PowerShell-leverantör. När en cmdlet anger någon av dessa sökvägar, vet körningen vilken provider som ska användas för att få åtkomst till den associerade datalagringen. Dessa sökvägar är enheten kvalificerade sökvägar, provider kvalificerade sökvägar, provider-direct-sökvägar och provider-interna sökvägar. Varje Windows PowerShell-providern måste ha stöd för en eller flera av dessa sökvägar.

Mer information om Windows PowerShell-sökvägar finns i så här fungerar i Windows PowerShell.

### <a name="defining-a-drive-qualified-path"></a>Definiera en enhet sökväg

Om du vill tillåta användare att komma åt data som finns på en fysisk enhet kan måste dina Windows PowerShell-providern stödja en enhet sökväg. Den här sökvägen börjar med enhetsnamnet följt av ett kolon (:), till exempel mydrive:\abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Definiera en Provider sökväg

Windows PowerShell-providern måste stödja en provider sökväg för att tillåta Windows PowerShell-körning för att initiera och uninitialize providern. Till exempel filsystem::\\\uncshare\abc\bar är sökvägen med provider för filsystem-providern som tillhandahålls av Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Definiera en Provider-Direct-sökväg

För att tillåta fjärråtkomst till Windows PowerShell-providern, bör det stöder en provider-direct sökväg skickas direkt till Windows PowerShell-providern för den aktuella platsen. Windows PowerShell-providern registret kan till exempel använda \\\server\regkeypath som en provider-direct-sökväg.

### <a name="defining-a-provider-internal-path"></a>Definiera en Provider-internt sökväg

Om du vill tillåta provider-cmdlet för att få åtkomst till data med hjälp av icke - Windows PowerShell programgränssnitt (API: er), Windows PowerShell-providern ska ha stöd en provider-internt sökväg. Den här sökvägen anges i ”::” i sökvägen med providern. Till exempel den provider-interna sökvägen för Windows PowerShell-providern filsystem är \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>Ändra lagrade Data

När åsidosätter metoder som ändrar det underliggande datalagringen kan alltid anropar den [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) sättet med den senaste versionen av objektet ändras utifrån det metoden. Providern infrastrukturen avgör om objektet objekt som ska skickas till pipelinen genom att till exempel när användaren anger parametern - PassThru. Om hämtar det senaste objektet är en kostsam åtgärd (performance-wise), kan du testa Context.PassThru-egenskapen för att avgöra om du verkligen behöver skriva det resulterande objektet.

## <a name="choose-a-base-class-for-your-provider"></a>Välj en basklass för din Provider

Windows PowerShell innehåller ett antal basklasser som du kan använda för att implementera dina egna Windows PowerShell-providern. När du designar en provider, Välj basklass, som beskrivs i det här avsnittet, som är mest lämplig för dina krav.

Varje basklass för Windows PowerShell-providern tillhandahåller en uppsättning cmdlets. Det här avsnittet beskrivs cmdletarna, men det beskriver inte deras parametrar.

Med hjälp av sessionens tillstånd, Windows PowerShell-runtime gör flera plats-cmdletar tillgängliga för vissa Windows PowerShell-leverantörer, till exempel den `Get-Location`, `Set-Location`, `Pop-Location`, och `Push-Location` cmdletar. Du kan använda den `Get-Help` cmdlet för att få information om dessa cmdletar för platsen.

### <a name="cmdletprovider-base-class"></a>CmdletProvider basklass

Den [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klassen definierar en grundläggande Windows PowerShell-providern. Den här klassen stöder provider-deklarationen och tillhandahåller ett antal egenskaper och metoder som är tillgängliga för alla Windows PowerShell-leverantörer. Klassen anropas av den `Get-PSProvider` cmdlet för att lista alla tillgängliga providers för en session. Implementeringen av denna cmdlet tillhandahålls genom sessionens tillstånd.

> [!NOTE]
> Windows PowerShell-providers är tillgängliga för alla scope i Windows PowerShell-språket.

### <a name="drivecmdletprovider-base-class"></a>DriveCmdletProvider basklass

Den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klassen definierar en provider för Windows PowerShell-enhet som stöder åtgärder för att lägga till nya enheter, ta bort befintliga enheter och initiering av standard-enheter. Till exempel initierar filsystem-providern som tillhandahålls av Windows PowerShell enheter för alla volymer som är monterade, till exempel hårddiskar och enheter för CD/DVD-enhet.

Den här klassen härleds från den [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) basklassen. I följande tabell visas de cmdletar som exponeras av den här klassen. Förutom de som anges, den `Get-PSDrive` cmdlet (exponeras av sessionstillstånd) är en relaterade cmdlet som används för att hämta tillgängliga enheter.

|Cmdlet|Definition|
|------------|----------------|
|`New-PSDrive`|Skapar en ny enhet för sessionen och strömmar enhetsinformationen.|
|`Remove-PSDrive`|Tar bort en enhet från sessionen.|

### <a name="itemcmdletprovider-base-class"></a>ItemCmdletProvider basklass

Den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klassen definierar en provider för Windows PowerShell-objekt som utför åtgärder på de olika artiklarna för datalagret och det förutsätter inte någon behållare eller navigering funktioner. Den här klassen härleds från den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basklassen. I följande tabell visas de cmdletar som exponeras av den här klassen.

|Cmdlet|Definition|
|------------|----------------|
|`Clear-Item`|Tar bort det aktuella innehållet i objekt på den angivna platsen och ersätter den med ”Rensa” värdet som anges av providern. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|
|`Get-Item`|Hämtar objekt från den angivna platsen och strömmar de resulterande objekten.|
|`Invoke-Item`|Anropar standardåtgärden för objektet på den angivna sökvägen.|
|`Set-Item`|Anger ett objekt på den angivna platsen med det angivna värdet. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|
|`Resolve-Path`|Matchar jokertecken för en Windows PowerShell-sökväg och strömmar sökvägsinformation.|
|`Test-Path`|Kontrollerar för den angivna sökvägen och ger `true` om den finns och `false` annars. Denna cmdlet har införts för att stödja den `IsContainer` parametern för den [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metod.|

### <a name="containercmdletprovider-base-class"></a>ContainerCmdletProvider basklass

Den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klassen definierar en provider för Windows PowerShell-behållare som Exponerar en behållare för dataobjekt store till användaren. Tänk på att en Windows PowerShell-providern för behållare kan användas endast när det är en behållare (inga kapslade behållare) med objekt i den. Om det finns kapslade behållare, måste du implementera en Windows PowerShell-providern för navigering.

Den här klassen härleds från den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) basklassen. I följande tabell definieras de cmdletar som implementeras av den här klassen.

|Cmdlet|Definition|
|------------|----------------|
|`Copy-Item`|Kopior objekt från en plats till en annan. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|
|`Get-Childitem`|Hämtar de underordnade objekten på den angivna platsen och skickar dem som objekt.|
|`New-Item`|Skapar nya objekt på den angivna platsen och strömmar det resulterande objektet.|
|`Remove-Item`|Tar bort objekt från den angivna platsen.|
|`Rename-Item`|Byter namn på ett objekt på den angivna platsen. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|

### <a name="navigationcmdletprovider-base-class"></a>NavigationCmdletProvider basklass

Den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klassen definierar en navigering Windows PowerShell-providern som utför åtgärder för objekt som använder flera behållare. Den här klassen härleds från den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) basklassen. I följande tabell listas de cmdletar som exponeras av den här klassen.

|Cmdlet|Definition|
|------------|----------------|
|Combine-Path|Kombinerar två sökvägar till en enskild sökväg, med en provider-specifik avgränsare mellan sökvägar. Denna cmdlet strömmar strängar.|
|`Move-Item`|Flyttar objekt till den angivna platsen. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|

En relaterad cmdlet är den grundläggande parsa-Path-cmdlet som tillhandahålls av Windows PowerShell. Denna cmdlet kan användas för att parsa en Windows PowerShell-sökväg för den `Parent` parametern. Sökvägssträngen överordnade strömning.

## <a name="select-provider-interfaces-to-support"></a>Välj Provider gränssnitt till Support

Förutom härledning från en Windows PowerShell-basklasserna ersätts, kan din Windows PowerShell-providern stöd för andra funktioner av som härleds från en eller flera av följande gränssnitt för providern. Det här avsnittet definierar dessa gränssnitt och stöds av varje-cmdletar. Det beskriver inte parametrarna för cmdletarna gränssnitt som stöds. Cmdlet-parameterinformation är tillgänglig med hjälp av den `Get-Command` och `Get-Help` cmdletar.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

Den [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -gränssnittet definierar en innehållsleverantör som utför åtgärder på innehållet i ett dataobjekt. I följande tabell visas de cmdletar som exponeras av det här gränssnittet.

|Cmdlet|Definition|
|------------|----------------|
|`Add-Content`|Lägger till värdet indikerade längden på innehållet i det angivna objektet. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|
|`Clear-Content`|Anger innehållet i det angivna objektet till värdet ”Rensa”. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|
|`Get-Content`|Hämtar innehållet i de angivna objekt och strömmar de resulterande objekten.|
|`Set-Content`|Ersätter det befintliga innehållet i det angivna elementet. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

Den [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) -gränssnittet definierar en egenskap Windows PowerShell-providern som utför åtgärder på egenskaperna för objekt i datalagret. I följande tabell visas de cmdletar som exponeras av det här gränssnittet.

> [!NOTE]
> Den `Path` parametern på dessa cmdlets anger en sökväg till ett objekt i stället för att identifiera en egenskap.

|Cmdlet|Definition|
|------------|----------------|
|`Clear-ItemProperty`|Anger egenskaperna för de angivna objekt till värdet ”Rensa”. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|
|`Get-ItemProperty`|Hämtar egenskaper från de angivna objekt och strömmar de resulterande objekten.|
|`Set-ItemProperty`|Anger egenskaperna för de angivna objekt med angivna värden. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

Den [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) -gränssnittet härleds från [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), definierar en providern som anger dynamiska parametrar för dess stöds cmdletar. Den här typen av providern hanterar åtgärder som egenskaper kan definieras vid körningstillfället, till exempel en ny egenskap operation. Sådana åtgärder är inte möjliga på objekten som statiskt har definierats egenskaper. I följande tabell visas de cmdletar som exponeras av det här gränssnittet.

|Cmdlet|Definition|
|------------|----------------|
|`Copy-ItemProperty`|Kopierar en egenskap från det angivna objektet till ett annat objekt. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|
|`Move-ItemProperty`|Flyttar en egenskap från det angivna objektet till ett annat objekt. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|
|`New-ItemProperty`|Skapar en egenskap på de angivna objekt och strömmar de resulterande objekten.|
|`Remove-ItemProperty`|Tar bort en egenskap för de angivna objekt.|
|`Rename-ItemProperty`|Byter namn på en egenskap för de angivna objekt. Denna cmdlet inte skicka ett objekt genom pipelinen om inte dess `PassThru` parameter har angetts.|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

Den [System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) gränssnittet lägger till security descriptor funktioner till en leverantör. Det här gränssnittet gör att användaren att hämta och ange informationen för säkerhetsbeskrivningen för ett objekt i datalagret. I följande tabell visas de cmdletar som exponeras av det här gränssnittet.

|Cmdlet|Definition|
|------------|----------------|
|`Get-Acl`|Hämtar information i en åtkomstkontrollista (ACL) som är en del av en säkerhetsbeskrivning som används för att skydda resurser i operativsystemet, till exempel, en fil eller ett objekt.|
|`Set-Acl`|Anger information för en Åtkomstkontrollista. Det är i form av en instans av [System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) på objekt för den angivna sökvägen. Denna cmdlet kan ange information om filer, nycklar och undernycklar i registret eller några andra providern objektet, om Windows PowerShell-providern har stöd för inställningen av säkerhetsinformation.|

## <a name="see-also"></a>Se även

[Skapa Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md)

[Så här fungerar Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Så här fungerar Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)