---
ms.date: 08/23/2017
keywords: PowerShell, cmdlet
title: Avinstallera Windows PowerShell-Webbåtkomst
ms.openlocfilehash: 3c2c83525f5a240976eef215b5eac939796c91e8
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279018"
---
# <a name="uninstall-windows-powershell-web-access"></a>Avinstallera Windows PowerShell-webbåtkomst

Uppdaterad: 24 juni 2013

Gäller för: Windows Server 2012 R2, Windows Server 2012

Stegen i det här avsnittet tar bort webbplatsen för Windows PowerShell-webbåtkomsten och motsvarande program från Gateway-servern där den är installerad.

## <a name="notify-users"></a>Meddela användare

Innan du börjar, meddela användare av den webbaserade konsolen att du kommer ta bort webbplatsen.

Om du avinstallerar Windows PowerShell-webbåtkomsten avinstalleras inte IIS eller andra funktioner som installerades automatiskt eftersom Windows PowerShell-webbåtkomsten kräver att de körs. Avinstallations processen lämnar funktioner som är installerade när Windows PowerShell-webbåtkomsten var beroende. Du kan avinstallera dessa funktioner separat om det behövs.

## <a name="recommended-quick-uninstallation"></a>Rekommenderad (snabb) avinstallation

Procedurerna i det här avsnittet hjälper dig att avinstallera båda:

- webb programmet för Windows PowerShell-webbåtkomst och
- Windows PowerShell-funktionen för webb åtkomst

med hjälp av Windows PowerShell-cmdletar.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Steg 1: ta bort webb programmet med cmdletar

1. Gör något av följande för att öppna en Windows PowerShell-session.

   - På Windows-skrivbordet, högerklickar du på **Windows PowerShell** i aktivitetsfältet.
   - På **Start**skärmen i Windows klickar du på **Windows PowerShell**.

2. Skriv `Uninstall-PswaWebApplication`och tryck sedan på **RETUR**.

   1. Om du har angett ditt eget, anpassade webbplatsnamn, lägg då till `-WebsiteName`-parametern till ditt kommando och ange webbplatsnamnet.

      `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`

   1. Om du har använt ett anpassat webb program (inte standard programmet, **pswa**, lägger du till parametern `-WebApplicationName` till ditt kommando och anger namnet på webb programmet.

      `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`

   1. Om du använder ett testcertifikat, lägger du till parametern `DeleteTestCertificate` till cmdleten, på det sätt som visas i följande exempel.

      `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av cmdletar

1. Gör något av följande för att öppna en Windows PowerShell-session med utökade användar rättigheter. Om en session redan är öppen, går du vidare till nästa steg.

    - På Windows-skrivbordet högerklickar du på **Windows PowerShell** i aktivitets fältet och klickar sedan på **Kör som administratör**.
    - På Windows **start**skärm högerklickar du på **Windows PowerShell** och klickar sedan på **Kör som administratör**.

1. Skriv följande och tryck sedan på **RETUR**, där *computer_name* representerar en fjärrserver från vilken du vill ta bort Windows PowerShell-webbåtkomst. Parametern `-Restart`, startar automatiskt om målservrar om det krävs för borttagningen.

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart`

    För att ta bort roller och funktioner från en offline-VHD, behöver du lägga till både `-ComputerName`-parametern och `-VHD`-parametern. Parametern `-ComputerName` innehåller namnet på den server som den virtuella hård disken ska monteras på och parametern `-VHD` innehåller sökvägen till VHD-filen på den angivna servern.

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart`

1. När borttagningen är klar kontrollerar du att du har tagit bort Windows PowerShell-webbåtkomsten genom att öppna sidan **alla servrar** i Serverhanteraren, välja en server som du tog bort funktionen från och sedan Visa panelen **roller och funktioner** på sidan för den valda servern.

    Du kan också köra den `Get-WindowsFeature`-cmdlet som är riktad mot den valda servern (Get-WindowsFeature-ComputerName &lt;*computer_name*&gt;) om du vill visa en lista över roller och funktioner som är installerade på servern.

## <a name="custom-uninstallation"></a>Anpassad avinstallation

Procedurerna i det här avsnittet hjälper dig att avinstallera både webb programmet Windows PowerShell-webbåtkomst och Windows PowerShell-webbåtkomst med hjälp av guiden ta bort roller och funktioner i Serverhanteraren och konsolen IIS-hanteraren.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Steg 1: ta bort webb programmet med IIS-hanteraren

1. Öppna IIS-hanteringskonsolen genom att göra något av följande. Om den redan är öppen, går du vidare till nästa steg.

   - På Windows-skrivbordet startar du Serverhanteraren genom att klicka på **Serverhanteraren** i aktivitets fältet i Windows. I **verktyg** -menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.

   - På Windows **Start**-skärmen, fyller du i valfri del av namnet **IIS (Internet Information Services)-hanteraren**. Klicka på genvägen när den visas i **Appar**-resultaten.

1. I träd fönstret i IIS-hanteraren väljer du den webbplats som kör webb programmet för Windows PowerShell-webbåtkomst.

1. I **Åtgärds**-panelen, under **Hantera webbplats**, klickar du på **Stoppa**.

1. I trädvyn högerklickar du på webb programmet på webbplatsen som kör webb programmet för Windows PowerShell-webbåtkomst och klickar sedan på **ta bort**.

1. I trädvyn väljer du **programpooler**, väljer mappen programpool för Windows PowerShell-programpool, klickar på **stoppa** i rutan **åtgärder** och klickar sedan på **ta bort** i innehålls rutan.

1. Stäng IIS-hanteraren.

   > [!WARNING]
   > Certifikatet tas inte bort under avinstallationen. Om du skapat ett självsignerat certifikat eller om du använde ett testcertfikat och vill ta bort det, radera certifikatet i IIS-hanteraren.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av guiden ta bort roller och funktioner

1. Om Serverhanteraren redan är öppet går du vidare till nästa steg. Om Serverhanteraren inte redan är öppet öppnar du det genom att göra något av följande.

    - På Windows-skrivbordet startar du Serverhanteraren genom att klicka på **Serverhanteraren** i aktivitets fältet i Windows.
    - På **Start**skärmen i Windows klickar du på **Serverhanteraren**.

1. I **Hantera**-menyn, klickar du på **Ta bort roller och funktioner**.

1. På sidan **Välj målserver**, väljer du den server eller offline-VHD som du vill ta bort funktionen från. Om du vill välja en offline-VHD väljer du först den server som du vill montera den virtuella hård disken på och väljer sedan VHD-filen. När du har valt målservern klickar du på **Nästa**.

1. Klicka på **Nästa** igen för att hoppa vidare till sidan **Ta bort funktioner**.

1. Avmarkera kryssrutan för **Windows PowerShell-webbåtkomst** och klicka sedan på **Nästa**.

1. På sidan **Bekräfta borttagnings inställningarna** klickar du på **ta bort**.

## <a name="see-also"></a>Se även

- [Installera och använda Windows PowerShell-Webbåtkomst](install-and-use-windows-powershell-web-access.md)
- [Hjälp om IIS-hanteraren 7,0](https://technet.microsoft.com/library/cc732664.aspx)