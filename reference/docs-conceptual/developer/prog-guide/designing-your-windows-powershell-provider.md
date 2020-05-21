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
ms.openlocfilehash: 6112e64a4a15d9dc8ac28ba51259b6647db4c064
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560057"
---
# <a name="designing-your-windows-powershell-provider"></a>Designa en Windows PowerShell-provider

Du bör implementera en Windows PowerShell-Provider om din produkt eller konfiguration visar en uppsättning lagrade data, till exempel en databas som användaren vill navigera i eller bläddra i. Om din produkt Dessutom tillhandahåller en behållare, även om den inte är en behållare med flera nivåer, är det klokt att implementera en Windows PowerShell-Provider. Du kanske till exempel vill implementera en Windows PowerShell container-Provider om cmdlet-verbet kopiera, flytta, byta namn, ny eller ta bort är meningsfullt som en åtgärd på din produkt-eller konfigurations data.

## <a name="windows-powershell-paths-identify-your-provider"></a>Windows PowerShell-sökvägar identifierar din Provider

Windows PowerShell-körningsmiljön använder sökvägar i Windows PowerShell för att få åtkomst till lämplig Windows PowerShell-Provider. När en cmdlet anger någon av dessa sökvägar vet körnings platsen vilken provider som ska användas för att få åtkomst till det tillhör ande data lagret. Dessa sökvägar inkluderar enhets kvalificerade sökvägar, Provider-kvalificerade sökvägar, Provider-direkta sökvägar och Provider-interna sökvägar. Varje Windows PowerShell-Provider måste ha stöd för en eller flera av dessa sökvägar.

Mer information om sökvägar i Windows PowerShell finns i så här fungerar Windows PowerShell.

### <a name="defining-a-drive-qualified-path"></a>Definiera en enhet-kvalificerad sökväg

Om du vill ge användaren åtkomst till data som finns på en fysisk enhet måste Windows PowerShell-providern ha stöd för en enhets kvalificerad sökväg. Den här sökvägen börjar med enhets namnet följt av ett kolon (:), till exempel min enhet: \ abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Definiera en provider-kvalificerad sökväg

Windows PowerShell-providern måste ha stöd för en provider-kvalificerad sökväg för att Windows PowerShell-körningsmiljön ska kunna initiera och avinitiera providern. Till exempel är fil systemet:: \\ \uncshare\abc\bar den provider-kvalificerade sökvägen för fil Systems leverantören som tillhandahålls av Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Definiera en provider – direkt sökväg

Om du vill tillåta fjärråtkomst till Windows PowerShell-providern ska den stödja en provider-direkt sökväg för att skicka direkt till Windows PowerShell-providern för den aktuella platsen. Till exempel kan registrets Windows PowerShell-Provider använda \\ \server\regkeypath som en provider-direkt sökväg.

### <a name="defining-a-provider-internal-path"></a>Definiera en provider – intern sökväg

Om du vill tillåta Provider-cmdleten att komma åt data med icke-Windows PowerShell-API: er (Application Programming Interfaces) ska din Windows PowerShell-Provider stödja en provider-intern sökväg. Den här sökvägen anges efter "::" i providerns kvalificerade sökväg. Till exempel är providerns interna sökväg för Windows PowerShell-providern för fil systemet \\ \uncshare\abc\bar.

## <a name="changing-stored-data"></a>Ändra lagrade data

När du åsidosätter metoder som ändrar det underliggande data lagret ska du alltid anropa metoden [system. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) med den senaste versionen av objektet som har ändrats av den metoden. Providerns infrastruktur bestämmer om objektet måste skickas till pipelinen, till exempel när användaren anger parametern-PassThru. Om du hämtar det senaste aktuella objektet är en kostsam åtgärd (prestanda-och prestanda) kan du testa egenskapen context. PassThru för att avgöra om du verkligen behöver skriva det resulterande objektet.

## <a name="choose-a-base-class-for-your-provider"></a>Välj en basklass för din Provider

Windows PowerShell innehåller ett antal bas klasser som du kan använda för att implementera din egen Windows PowerShell-Provider. När du skapar en Provider väljer du Bask Lassen, som beskrivs i det här avsnittet, som passar bäst för dina behov.

Varje basklass i Windows PowerShell-providern gör en uppsättning cmdletar tillgängliga. I det här avsnittet beskrivs cmdletarna, men det beskriver inte deras parametrar.

Med hjälp av sessionstillstånd gör Windows PowerShell-körningsmiljön flera plats-cmdletar tillgängliga för vissa Windows PowerShell-leverantörer, till exempel `Get-Location` `Set-Location` `Pop-Location` cmdletarna,, och `Push-Location` . Du kan använda `Get-Help` cmdleten för att hämta information om dessa plats-cmdletar.

### <a name="cmdletprovider-base-class"></a>CmdletProvider Bask lass

Klassen [system. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) definierar en grundläggande Windows PowerShell-Provider. Den här klassen stöder providerns deklaration och tillhandahåller ett antal egenskaper och metoder som är tillgängliga för alla Windows PowerShell-leverantörer.
Klassen anropas av `Get-PSProvider` cmdleten för att visa en lista över alla tillgängliga providers för en session.
Implementeringen av denna cmdlet tillhandahålls av sessionstillstånd.

> [!NOTE]
> Windows PowerShell-providers är tillgängliga för alla språk omfattningar i Windows PowerShell.

### <a name="drivecmdletprovider-base-class"></a>DriveCmdletProvider Bask lass

Klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) definierar en Windows PowerShell-tjänstleverantör som stöder åtgärder för att lägga till nya enheter, ta bort befintliga enheter och initiera standard enheter. Till exempel initierar fil tjänst leverantören som tillhandahålls av Windows PowerShell enheter för alla volymer som är monterade, till exempel hård diskar och CD-/DVD-enheter.

Den här klassen härleds från Bask Lassen [system. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . I följande tabell visas de cmdletar som exponeras av den här klassen. Förutom de som listas, `Get-PSDrive` är cmdleten (exponerad efter sessionstillstånd) en relaterad cmdlet som används för att hämta tillgängliga enheter.

|      Cmdlet      |                             Definition                              |
| ---------------- | ------------------------------------------------------------------- |
| `New-PSDrive`    | Skapar en ny enhet för sessionen och strömmar enhets information. |
| `Remove-PSDrive` | Tar bort en enhet från sessionen.                                   |

### <a name="itemcmdletprovider-base-class"></a>ItemCmdletProvider Bask lass

Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) definierar en Windows PowerShell-dataprovider som utför åtgärder på de enskilda objekten i data lagret och som inte förutsätter några funktioner för behållare eller navigering. Den här klassen härleds från Bask Lassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . I följande tabell visas de cmdletar som exponeras av den här klassen.

|     Cmdlet     |                                                                                                                                                            Definition                                                                                                                                                            |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-Item`   | Rensar det aktuella innehållet i objekt på den angivna platsen och ersätter det med värdet "Rensa" som anges av providern. Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges.                                                                                   |
| `Get-Item`     | Hämtar objekt från den angivna platsen och strömmar de resulterande objekten.                                                                                                                                                                                                                                                  |
| `Invoke-Item`  | Anropar standard åtgärden för objektet på den angivna sökvägen.                                                                                                                                                                                                                                                                   |
| `Set-Item`     | Anger ett objekt på den angivna platsen med det angivna värdet. Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges.                                                                                                                                                   |
| `Resolve-Path` | Matchar jokertecken för sökväg till Windows PowerShell och information om strömmar.                                                                                                                                                                                                                                              |
| `Test-Path`    | Testar för den angivna sökvägen och returnerar `true` om den finns och `false` annars. Denna cmdlet implementeras för att stödja `IsContainer` parametern för metoden [system. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) . |

### <a name="containercmdletprovider-base-class"></a>ContainerCmdletProvider Bask lass

Klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) definierar en Windows PowerShell container-provider som exponerar en behållare för data lagrings objekt till användaren. Tänk på att en Windows PowerShell container-Provider bara kan användas när det finns en behållare (inga kapslade behållare) med objekten i den. Om det finns kapslade behållare måste du implementera en Windows PowerShell-navigerings-Provider.

Den här klassen härleds från Bask Lassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . I följande tabell definieras de cmdletar som implementeras av den här klassen.

|     Cmdlet      |                                                                        Definition                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Copy-Item`     | Kopierar objekt från en plats till en annan. Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges. |
| `Get-Childitem` | Hämtar de underordnade objekten på den angivna platsen och strömmar dem som objekt.                                                                        |
| `New-Item`      | Skapar nya objekt på den angivna platsen och strömmar det resulterande objektet.                                                                           |
| `Remove-Item`   | Tar bort objekt från den angivna platsen.                                                                                                               |
| `Rename-Item`   | Byter namn på ett objekt på den angivna platsen. Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges. |

### <a name="navigationcmdletprovider-base-class"></a>NavigationCmdletProvider Bask lass

Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) definierar en Windows PowerShell-navigerings-provider som utför åtgärder för objekt som använder mer än en behållare. Den här klassen härleds från Bask Lassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . I följande tabell visas en lista över de cmdletar som exponeras av den här klassen.

|    Cmdlet    |                                                                      Definition                                                                      |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Kombinera-sökväg | Kombinerar två sökvägar till en enda sökväg med hjälp av en leverantörsspecifik avgränsare mellan sökvägar. Denna cmdlet strömmar strängar.                               |
| `Move-Item`  | Flyttar objekt till den angivna platsen. Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges. |

En relaterad cmdlet är den grundläggande parsar-Sök vägs cmdleten som tillhandahålls av Windows PowerShell. Denna cmdlet kan användas för att tolka en Windows PowerShell-sökväg som stöd för `Parent` parametern. Den överordnade Sök vägs strängen strömmas.

## <a name="select-provider-interfaces-to-support"></a>Välj Provider-gränssnitt som ska stödjas

Förutom att härleda från en av bas klasserna i Windows PowerShell kan din Windows PowerShell-Provider stödja andra funktioner genom att härledas från ett eller flera av följande Provider-gränssnitt. I det här avsnittet definieras de gränssnitt och cmdlets som stöds av var och en. Den beskriver inte parametrarna för cmdlets som stöds av gränssnittet. Information om cmdlet-parametrar är tillgänglig online `Get-Command` med `Get-Help` cmdletarna och.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

Gränssnittet [system. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) definierar en innehålls leverantör som utför åtgärder för innehållet i ett data objekt. I följande tabell visas de cmdlets som exponeras av det här gränssnittet.

|     Cmdlet      |                                                                                        Definition                                                                                        |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Add-Content`   | Lägger till angivna värde längder till innehållet i det angivna objektet. Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges. |
| `Clear-Content` | Ställer in innehållet i det angivna objektet till värdet "Rensa". Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges.               |
| `Get-Content`   | Hämtar innehållet i de angivna objekten och strömmar de resulterande objekten.                                                                                                         |
| `Set-Content`   | Ersätter det befintliga innehållet för de angivna objekten. Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges.                     |

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

Gränssnittet [system. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) definierar en egenskap Windows PowerShell-provider som utför åtgärder på egenskaperna för objekt i data lagret. I följande tabell visas de cmdlets som exponeras av det här gränssnittet.

> [!NOTE]
> `Path`Parametern i dessa cmdletar anger en sökväg till ett objekt i stället för att identifiera en egenskap.

|        Cmdlet        |                                                                                   Definition                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-ItemProperty` | Anger egenskaperna för de angivna objekten till värdet "Rensa". Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges.      |
| `Get-ItemProperty`   | Hämtar egenskaper från de angivna objekten och strömmar de resulterande objekten.                                                                                                |
| `Set-ItemProperty`   | Anger egenskaperna för de angivna objekten med de angivna värdena. Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges. |

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

Gränssnittet [system. Management. Automation. Provider. Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) , härlett från [system. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), definierar en provider som anger dynamiska parametrar för de cmdlet: ar som stöds. Den här typen av provider hanterar åtgärder för vilka egenskaper kan definieras vid körning, till exempel en ny egenskaps åtgärd. Sådana åtgärder är inte möjliga för objekt med statiskt definierade egenskaper.
I följande tabell visas de cmdlets som exponeras av det här gränssnittet.

|        Cmdlet         |                                                                                Definition                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Copy-ItemProperty`   | Kopierar en egenskap från det angivna objektet till ett annat objekt. Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges. |
| `Move-ItemProperty`   | Flyttar en egenskap från det angivna objektet till ett annat objekt. Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges.  |
| `New-ItemProperty`    | Skapar en egenskap för de angivna objekten och strömmar de resulterande objekten.                                                                                             |
| `Remove-ItemProperty` | Tar bort en egenskap för de angivna objekten.                                                                                                                              |
| `Rename-ItemProperty` | Byter namn på en egenskap för de angivna objekten. Denna cmdlet skickar inte ett utgående objekt via pipelinen om inte dess `PassThru` parameter anges.                 |

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

Gränssnittet [system. Management. Automation. Provider. Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) lägger till säkerhets beskrivar funktioner till en provider. Med det här gränssnittet kan användaren hämta och ange information om säkerhets beskrivningen för ett objekt i data lagret. I följande tabell visas de cmdlets som exponeras av det här gränssnittet.

|  Cmdlet   |                                                                                                                                                                                                          Definition                                                                                                                                                                                                          |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Get-Acl` | Hämtar informationen som finns i en åtkomst kontrol lista (ACL), som är en del av en säkerhets beskrivning som används för att skydda operativ system resurser, till exempel en fil eller ett objekt.                                                                                                                                                                                                                                      |
| `Set-Acl` | Anger information för en ACL. Den är i form av en instans av [system. Security. AccessControl. ObjectSecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) på de objekt som har angetts för den angivna sökvägen. Den här cmdleten kan ange information om filer, nycklar och under nycklar i registret, eller andra leverantörs objekt, om Windows PowerShell-providern stöder inställningen av säkerhets information. |

## <a name="see-also"></a>Se även

[Skapa Windows PowerShell-leverantörer](./how-to-create-a-windows-powershell-provider.md)

[Så här fungerar Windows PowerShell](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
