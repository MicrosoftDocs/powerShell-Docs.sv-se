---
ms.date: 2017-08-23
keywords: PowerShell-cmdlet
title: "avinstallera windows powershell-webbåtkomst"
ms.openlocfilehash: b6e6a2374e6b4b2be8742019c5f1e4d5b5d1abe3
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/29/2017
---
# <a name="uninstall-windows-powershell-web-access"></a>Avinstallera Windows PowerShell-webbåtkomst

Uppdaterad: Juni 24 2013

Gäller för: Windows Server 2012 R2, Windows Server 2012

Stegen i det här avsnittet Ta bort Windows PowerShell Web Access webbplats och motsvarande program från gateway-servern där den är installerad.

## <a name="notify-users"></a>Meddela användare

Innan du börjar, meddela användare av den webbaserade konsolen att du kommer ta bort webbplatsen.

Avinstallera Windows PowerShell Web Access avinstallerar inte IIS eller andra funktioner som installerades automatiskt eftersom Windows PowerShell Web Access kräver dem att köra.
Avinstallationsprocessen lämnar kvar installerade funktioner som Windows PowerShell Web Access var beroende; Du kan avinstallera de funktionerna separat, om det behövs.

## <a name="recommended-quick-uninstallation"></a>Rekommenderad (snabb) avinstallation

Procedurerna i det här avsnittet hjälper dig att avinstallera både:

- webbprogrammet för Windows PowerShell Web Access och
- funktionen Windows PowerShell-webbåtkomst
 
med hjälp av Windows PowerShell-cmdlets.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Steg 1: Ta bort webbprogrammet med hjälp av cmdlet: ar

1. Gör något av följande för att öppna en Windows PowerShell-session.

    -   Högerklicka på Windows-skrivbordet **Windows PowerShell** i Aktivitetsfältet.

    -   På Windows **starta** klickar du på **Windows PowerShell**.

2. Typen `Uninstall-PswaWebApplication`, och tryck sedan på **RETUR**.
   1. Om du har angett ditt eget, anpassade webbplatsnamn, lägg då till `-WebsiteName`-parametern till ditt kommando och ange webbplatsnamnet.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Om du har använt ett anpassat webbprogram (inte standardprogrammet, **pswa**, lägga till den `-WebApplicationName` parametern i kommandot och ange namnet på webbprogrammet.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Om du använder ett testcertifikat, lägger du till parametern `DeleteTestCertificate` till cmdleten, på det sätt som visas i följande exempel.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av cmdlet: ar

1. Gör något av följande för att öppna en Windows PowerShell-session med utökade användarrättigheter. Om en session redan är öppen, går du vidare till nästa steg.

    -   Högerklicka på Windows-skrivbordet **Windows PowerShell** Aktivitetsfältet och klickar sedan på **Kör som administratör**.

    -   På Windows **starta** , högerklicka på **Windows PowerShell**, och klicka sedan på **kör som administratör**.

1. Skriv följande och tryck sedan på **RETUR**, där *computer_name* motsvarar en fjärrserver som du vill ta bort Windows PowerShell Web Access. Parametern `-Restart`, startar automatiskt om målservrar om det krävs för borttagningen.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    För att ta bort roller och funktioner från en offline-VHD, behöver du lägga till både `-ComputerName`-parametern och `-VHD`-parametern. Parametern `-ComputerName` innehåller namnet på den server som du vill montera VHD:n på och parametern `-VHD` innehåller sökvägen till VHD-filen på den angivna servern.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. När borttagningen är klar kontrollerar du att du tagit bort Windows PowerShell Web Access genom att öppna den **alla servrar** i Serverhanteraren, välja en server som du tog bort funktionen och sedan visa den **roller och Funktioner** på sidan för den valda servern.

    Du kan också köra den `Get-WindowsFeature` med den valda servern som mål (Get-WindowsFeature - ComputerName &lt; *computer_name*&gt;) att visa en lista över roller och funktioner som är installerade på servern.

## <a name="custom-uninstallation"></a>Anpassad avinstallation

I det här avsnittet hjälper dig att avinstallera både Windows PowerShell Web Access-webbprogram och Windows PowerShell Web Access-funktionen med hjälp av ta bort roller och funktioner guide i Serverhanteraren och IIS Manager-konsolen.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Steg 1: Ta bort webbprogrammet med IIS-hanteraren


1. Öppna konsolen för IIS-hanteraren genom att göra något av följande. Om den redan är öppen, går du vidare till nästa steg.

    -   Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet. På den **verktyg** menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.

    -   På Windows **starta** skriver någon del av namnet **Internet Information Services (IIS) Manager**. Klicka på genvägen när den visas i den **appar** resultat.

1. Välj den webbplats som kör Windows PowerShell Web Access-webbprogrammet i trädvyn för IIS-hanteraren.

1. I den **åtgärder** rutan under **hantera webbplats**, klickar du på **stoppa**.

1. Högerklicka på webbprogrammet på webbplatsen som kör Windows PowerShell Web Access-webbprogrammet i trädvyn och klicka **ta bort**.

1. I trädvyn markerar **programpooler**, väljer programpools-mappen i Windows PowerShell Web Access, klickar du på **stoppa** i den **åtgärder** rutan och klicka sedan på  **Ta bort** i innehållsfönstret.

1. Stäng IIS-hanteraren.

> ![Varning Obs](images/SecurityNote.jpeg)**Observera**:
>
> Certifikatet tas inte bort under avinstallationen. 
>
> Om du skapat ett självsignerat certifikat eller om du använde ett testcertfikat och vill ta bort det, radera certifikatet i IIS-hanteraren. 

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av guiden Ta bort roller och funktioner

1. Gå vidare till nästa steg om Server Manager redan är öppen. Öppna genom att göra något av följande om Server Manager inte är redan öppen.

    -   Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet.

    -   På Windows **starta** klickar du på **Serverhanteraren**.

1. På den **hantera** -menyn klickar du på **ta bort roller och funktioner**.

1. På den **väljer målservern** väljer du den server eller offline-VHD som du vill ta bort en funktion. Du kan välja en offline-VHD genom att först välja på vilken server VHD:n ska monteras och sedan välja VHD-filen. När du har valt målservern klickar du på **nästa**.

1. Klicka på **nästa** igen för att hoppa till den **ta bort funktioner** sidan.

1. Avmarkera kryssrutan för **Windows PowerShell Web Access**, och klicka sedan på **nästa**.

1. På den **Bekräfta borttagningsinställningarna** klickar du på **ta bort**.

## <a name="see-also"></a>Se även

- [Installera och använda Windows PowerShell-webbåtkomst](install-and-use-windows-powershell-web-access.md)
- [Hjälpen för IIS-hanteraren 7.0](https://technet.microsoft.com/library/cc732664.aspx)