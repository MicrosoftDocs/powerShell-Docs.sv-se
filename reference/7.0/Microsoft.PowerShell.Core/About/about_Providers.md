---
description: Beskriver hur PowerShell-leverantörer ger åtkomst till data och komponenter som annars inte är lättillgängliga på kommando raden. Data presenteras i ett konsekvent format som liknar en fil system enhet.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: c0ae976c9f82a8a7481eda2bad136e7ba2689a44
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270014"
---
# <a name="about-providers"></a>Om leverantörer

## <a name="short-description"></a>Kort beskrivning
Beskriver hur PowerShell-leverantörer ger åtkomst till data och komponenter som annars inte är lättillgängliga på kommando raden.
Data presenteras i ett konsekvent format som liknar en fil system enhet.

## <a name="long-description"></a>Lång beskrivning

PowerShell-leverantörer är .NET-program som ger åtkomst till specialiserade data lager för enklare visning och hantering. Data visas i en enhet och du får åtkomst till data i en sökväg som du skulle göra på en hård disk. Du kan använda någon av de inbyggda cmdletarna som providern stöder för att hantera data i leverantörs enheten. Du kan också använda anpassade cmdlets som är utformade särskilt för data.

Providers kan också lägga till dynamiska parametrar till de inbyggda cmdletarna. Dessa parametrar är bara tillgängliga när du använder-cmdlet: en med providerns data.

## <a name="built-in-providers"></a>Inbyggda leverantörer

PowerShell innehåller en uppsättning inbyggda providers som du kan använda för att få åtkomst till olika typer av data lager.

| Leverantör   |   Enhet (er)  |OutputType                                                    |
|----------- |------------ |--------------------------------------------------------------|
|Alias       |Aliasuppsättning       |System. Management. Automation. AliasInfo                        |
|Certifikat |Certifikatet        |Microsoft. PowerShell. commands. X509StoreLocation               |
|            |             |System. Security. Cryptography. X509Certificates. X509Certificate2|
|Miljö |Kuvert         |System. Collections. typen DictionaryEntry                            |
|Filsystem  |C: (*)       |System. IO. FileInfo                                            |
|            |             |System. IO. DirectoryInfo                                       |
|Funktion    |Funktioner    |System. Management. Automation. FunctionInfo                     |
|Register    |HKLM: HKCU:  |Microsoft. Win32. RegistryKey                                   |
|Variabel    |Variabel    |System. Management. Automation. PSVariable                       |
|WSMan       |WSMan       |Microsoft. WSMan. Management. WSManConfigContainerElement        |

(*) Fil Systems enheterna varierar beroende på varje system.

Du kan också skapa egna PowerShell-leverantörer och du kan installera leverantörer som andra utvecklar. Om du vill visa en lista över tillgängliga providers i sessionen skriver du:

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a>Installera och ta bort providrar

Leverantörer installeras vanligt vis via PowerShell-moduler. Importera modulen läser in providern i sessionen. Du kan inte avinstallera inbyggda providers. Du kan avinstallera providrar som har lästs in av andra moduler.

Du kan ta bort en provider från den aktuella sessionen med hjälp av `Remove-Module` cmdleten. Denna cmdlet avinstallerar inte providern, men den gör att providern inte är tillgänglig i sessionen.

Du kan också använda `Remove-PSDrive` cmdleten för att ta bort alla enheter från den aktuella sessionen. Dessa data på enheten påverkas inte, men enheten är inte längre tillgänglig i den sessionen.

## <a name="viewing-providers"></a>Visa leverantörer

Om du vill visa PowerShell-providern på datorn skriver du:

```powershell
Get-PSProvider
```

I utdata visas de inbyggda providers och providers som du har lagt till i sessionen.

## <a name="the-provider-cmdlets"></a>Provider-cmdletar

Följande cmdletar är utformade för att fungera med data som exponeras av vilken provider som helst. Du kan använda samma cmdlets på samma sätt för att hantera de olika typer av data som providern visar. När du har lärt dig att hantera data från en leverantör kan du använda samma procedurer med data från valfri Provider.

Till exempel `New-Item` skapar cmdleten ett nytt objekt. I den `C:` enhet som stöds av **fil** tjänst leverantören kan du använda `New-Item` för att skapa en ny fil eller mapp. I de enheter som stöds av **Registry** -providern kan du använda `New-Item` för att skapa en ny register nyckel. I `Alias:` enheten kan du använda `New-Item` för att skapa ett nytt alias.

Om du vill ha detaljerad information om någon av följande cmdletar skriver du:

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a>ChildItem-cmdletar

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a>Innehålls-cmdletar

- [Lägg till innehåll](xref:Microsoft.PowerShell.Management.Add-Content)
- [Rensa innehåll](xref:Microsoft.PowerShell.Management.Clear-Content)
- [Hämta innehåll](xref:Microsoft.PowerShell.Management.Get-Content)
- [Ange innehåll](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a>Objekt-cmdletar

- [Rensa objekt](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Kopiera objekt](xref:Microsoft.PowerShell.Management.Copy-Item)
- [Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item)
- [Anropa-objekt](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Flytta objekt](xref:Microsoft.PowerShell.Management.Move-Item)
- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)
- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Byt namn – objekt](xref:Microsoft.PowerShell.Management.Rename-Item)
- [Ange objekt](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a>ItemProperty-cmdletar

- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Kopiera – ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Move-ItemProperty](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Byt namn – ItemProperty](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a>Plats-cmdletar

- [Get-location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Pop-location](xref:Microsoft.PowerShell.Management.Pop-Location)
- [Push-plats](xref:Microsoft.PowerShell.Management.Push-Location)
- [Ange plats](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a>Sök vägs-cmdletar

- [Anslut till sökväg](xref:Microsoft.PowerShell.Management.Join-Path)
- [Konvertera-sökväg](xref:Microsoft.PowerShell.Management.Convert-Path)
- [Dela-sökväg](xref:Microsoft.PowerShell.Management.Split-Path)
- [Lös-sökväg](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [Test-sökväg](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a>PSDrive-cmdletar

- [Get-PSDrive](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [New-PSDrive](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [Remove-PSDrive](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a>PSProvider-cmdletar

- [Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a>Visa leverantörs data

Den främsta fördelen med en provider är att den exponerar data på ett välbekant och konsekvent sätt. Modellen för data presentation är en fil systemen het.

Med providern kan du Visa, navigera och ändra objekt i data lagret som om de var data i ett fil system. Data lagret används av namnet på den enhet som stöds.

Enheten visas i standard visningen av `Get-PSProvider` cmdleten, men du kan hämta information om providerns enhet med hjälp av `Get-PSDrive` cmdleten. Om du till exempel vill hämta alla egenskaper för funktionen: enhet skriver du:

```powershell
Get-PSDrive Function | Format-List *
```

Du kan visa och flytta igenom data i en leverantörs enhet precis som på en fil systemen het.

Om du vill visa innehållet i en provider använder du Get-Item-eller Get-ChildItem-cmdletar. Skriv enhets namnet följt av ett kolon (:). Om du till exempel vill visa innehållet i aliaset: enhet skriver du:

```powershell
Get-Item alias:
```

Du kan visa och hantera data i alla enheter från en annan enhet genom att inkludera enhets namnet i sökvägen. Om du till exempel vill visa register nyckeln HKLM\Software i HKLM: Drive från en annan enhet, skriver du:

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

Använd Set-Location-cmdleten för att öppna enheten. Kom ihåg kolonet när du anger enhetens sökväg. Om du till exempel vill ändra platsen till rot katalogen för certifikatet: enhet skriver du:

```powershell
Set-Location cert:
```

Om du sedan vill visa innehållet i certifikatet: enhet skriver du:

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a>Flytta genom hierarkiska data

Du kan flytta genom en leverantörs enhet på samma sätt som en hård disk.
Om data är ordnade i en hierarki med objekt i objekt, använder du ett omvänt snedstreck ( `\` ) för att ange ett underordnat objekt. Använd följande format:

```
drive:\location\child-location\...
```

Om du till exempel vill ändra din plats till register nyckeln HKLM\Software skriver du ett Set-Location kommando, till exempel:

```powershell
Set-Location HKLM:\SOFTWARE\
```

Om något element i det fullständigt kvalificerade namnet innehåller blank steg måste du skriva namnet inom dubbla citat tecken ( `"` ). I följande exempel visas en fullkvalificerad sökväg som innehåller blank steg.

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

Du kan också använda relativa referenser till platser. En punkt ( `.` ) representerar den aktuella platsen. Om du till exempel är i `HKLM:\Software\Microsoft` register nyckeln och vill visa register under nycklarna i `HKLM:\Software\Microsoft\PowerShell` nyckeln, skriver du följande kommando:

```powershell
Get-ChildItem .\PowerShell
```

Dessutom refererar dubbla punkter ( `..` ) till katalogen eller behållaren direkt ovanför din aktuella plats. Du kan använda dubbla punkter ( `..` ) för att navigera i en dimensionshierarki.

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a>Start för Provider

Leverantörer har också en **Start** plats.  Den här platsen delas av alla `PSDrives` som har säkerhetskopierats av providern. Den kan hämtas genom att se providerns **Start** egenskap.

```powershell
Get-PSProvider | Format-Table Name, Home
```

```Output
Name        Home
----        ----
Registry
Alias
Environment
FileSystem  C:\Users\username
Function
Variable
Certificate
```

**Fil Systems** leverantören är den enda providern som har ett standardvärde för **Start**. Det är samma värde som `$Home` . Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md).

Du kan ställa in **arbets** katalogen för en provider för den aktuella sessionen med hjälp av egenskapen.

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

Du `~` kan använda det här alternativet för att representera providerns Hem Katalog.
Om providern inte har en **Start** plats som har angetts visas ett fel meddelande.

```powershell
Cert:\> Set-Location ~
```

```Output
Set-Location : Home location for this provider isn't set. To set the home
location, call "(get-psprovider 'Certificate').Home = 'path'".
At line:1 char:1
+ Set-Location ~
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Set-Location],
                              PSInvalidOperationException
...
```

## <a name="finding-dynamic-parameters"></a>Hitta dynamiska parametrar

Dynamiska parametrar är cmdlet-parametrar som läggs till i en cmdlet av en provider. Dessa parametrar är bara tillgängliga när cmdleten används med providern som lade till dem.

Enheten lägger till exempel till `Cert:` parametern **CodeSigningCert** i `Get-Item` `Get-ChildItem` cmdletarna och. Du kan bara använda den här parametern när du använder `Get-Item` eller `Get-ChildItem` i `Cert:` enheten.

En lista över de dynamiska parametrar som en provider stöder finns i Hjälp filen för providern. Ange:

```
Get-Help <provider-name>
```

Ett exempel:

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a>Lär dig om leverantörer

Även om alla leverantörs data visas i enheter och du använder samma metoder för att gå igenom dem, stannar likheten där. De data lager som providern visar kan vara lika varierande som Active Directory platser och Microsoft Exchange Server-postlådor.

Om du vill ha mer information om enskilda PowerShell-leverantörer skriver du:

```
Get-Help <ProviderName>
```

Ett exempel:

```powershell
Get-Help registry
```

Om du vill ha en lista över hjälp avsnitt om providern skriver du:

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a>Se även

[about_Locations](about_Locations.md)

[about_Path_Syntax](about_Path_Syntax.md)
