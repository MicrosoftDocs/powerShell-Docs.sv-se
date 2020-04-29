---
ms.date: 08/23/2017
keywords: PowerShell, cmdlet
title: Avinstallera Windows PowerShell-Webbåtkomst
ms.openlocfilehash: 3c2c83525f5a240976eef215b5eac939796c91e8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78279018"
---
# <a name="uninstall-windows-powershell-web-access"></a>Avinstallera Windows PowerShell-Webbåtkomst

Uppdaterad: 24 juni 2013

Gäller för: Windows Server 2012 R2, Windows Server 2012

Stegen i det här avsnittet tar bort webbplatsen för Windows PowerShell-webbåtkomsten och motsvarande program från Gateway-servern där den är installerad.

## <a name="notify-users"></a>Meddela användarna

Innan du börjar ska du meddela användarna om den webbaserade konsolen som du tar bort webbplatsen.

Om du avinstallerar Windows PowerShell-webbåtkomsten avinstalleras inte IIS eller andra funktioner som installerades automatiskt eftersom Windows PowerShell-webbåtkomsten kräver att de körs. Avinstallations processen lämnar funktioner som är installerade när Windows PowerShell-webbåtkomsten var beroende. Du kan avinstallera dessa funktioner separat om det behövs.

## <a name="recommended-quick-uninstallation"></a>Rekommenderad (snabb) avinstallation

Procedurerna i det här avsnittet hjälper dig att avinstallera båda:

- webb programmet för Windows PowerShell-webbåtkomst och
- Windows PowerShell-funktionen för webb åtkomst

med hjälp av Windows PowerShell-cmdletar.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Steg 1: ta bort webb programmet med cmdletar

1. Gör något av följande för att öppna en Windows PowerShell-session.

   - På Windows-skrivbordet högerklickar du på **Windows PowerShell** i aktivitets fältet.
   - På Windows **Start** -skärmen klickar du på **Windows PowerShell**.

2. Skriv `Uninstall-PswaWebApplication`och tryck sedan på **RETUR**.

   1. Om du har angett ett eget namn på en anpassad webbplats lägger `-WebsiteName` du till parametern till ditt kommando och anger namnet på webbplatsen.

      `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`

   1. Om du har använt ett anpassat webb program (inte standard programmet, **pswa**, lägger du till `-WebApplicationName` parametern till ditt kommando och anger namnet på webb programmet.

      `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`

   1. Om du använder ett test certifikat lägger du till `DeleteTestCertificate` parametern i cmdleten, som du ser i följande exempel.

      `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av cmdletar

1. Gör något av följande för att öppna en Windows PowerShell-session med utökade användarrättigheter. Om en session redan är öppen går du vidare till nästa steg.

    - På Windows-skrivbordet högerklickar du på **Windows PowerShell** i aktivitetsfältet och klickar sedan på **Kör som administratör**.
    - På **Start** skärmen i Windows högerklickar du på **Windows PowerShell**och klickar sedan på **Kör som administratör**.

1. Skriv följande och tryck sedan på **RETUR**, där *computer_name* representerar en fjärrserver från vilken du vill ta bort Windows PowerShell-webbåtkomst. `-Restart` Parametern startar automatiskt om mål servrarna om det krävs för borttagningen.

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart`

    Om du vill ta bort roller och funktioner från en offline-VHD måste du `-ComputerName` lägga till både `-VHD` parametern och parametern. Parametern `-ComputerName`, innehåller namnet på servern på vilken du vill montera VHD:n, och parametern `-VHD` innehåller sökvägen till VHD-filen på den angivna servern.

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart`

1. När borttagningen är klar kontrollerar du att du har tagit bort Windows PowerShell-webbåtkomsten genom att öppna sidan **alla servrar** i Serverhanteraren, välja en server som du tog bort funktionen från och sedan Visa panelen **roller och funktioner** på sidan för den valda servern.

    `Get-WindowsFeature` Du kan också köra cmdleten som är riktad mot den valda servern (get- &lt;WindowsFeature-ComputerName *computer_name*&gt;) om du vill visa en lista över roller och funktioner som är installerade på servern.

## <a name="custom-uninstallation"></a>Anpassad avinstallation

Procedurerna i det här avsnittet hjälper dig att avinstallera både webb programmet Windows PowerShell-webbåtkomst och Windows PowerShell-webbåtkomst med hjälp av guiden ta bort roller och funktioner i Serverhanteraren och konsolen IIS-hanteraren.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Steg 1: ta bort webb programmet med IIS-hanteraren

1. Öppna konsolen IIS-hanteraren genom att göra något av följande. Om det redan är öppet går du vidare till nästa steg.

   - Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet. I **verktyg** -menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.

   - På **Start** skärmen i Windows skriver du valfri del av namnet **Internet Information Services (IIS) Manager**. Klicka på genvägen när den visas i **appens** resultat.

1. I träd fönstret i IIS-hanteraren väljer du den webbplats som kör webb programmet för Windows PowerShell-webbåtkomst.

1. I rutan **åtgärder** under **Hantera webbplats**klickar du på **stoppa**.

1. I trädvyn högerklickar du på webb programmet på webbplatsen som kör webb programmet för Windows PowerShell-webbåtkomst och klickar sedan på **ta bort**.

1. I trädvyn väljer du **programpooler**, väljer mappen programpool för Windows PowerShell-programpool, klickar på **stoppa** i rutan **åtgärder** och klickar sedan på **ta bort** i innehålls rutan.

1. Stäng IIS-hanteraren.

   > [!WARNING]
   > Certifikatet tas inte bort under avinstallationen. Om du har skapat ett självsignerat certifikat eller använt ett test certifikat och vill ta bort det, tar du bort certifikatet i IIS-hanteraren.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av guiden ta bort roller och funktioner

1. Gå vidare till nästa steg om Server Manager redan är öppen. Öppna genom att göra något av följande om Server Manager inte är redan öppen.

    - Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet.
    - På Windows **Start** -skärmen klickar du på **Serverhanteraren**.

1. Klicka på **ta bort roller och funktioner**på **Hantera** -menyn.

1. På sidan **Välj mål server** väljer du den server eller offline-VHD som du vill ta bort funktionen från. Du kan välja en offline-VHD genom att först välja på vilken server VHD:n ska monteras och sedan välja VHD-filen. När du har valt mål servern klickar du på **Nästa**.

1. Klicka på **Nästa** igen för att hoppa till sidan **ta bort funktioner** .

1. Avmarkera kryss rutan för **Windows PowerShell-webbåtkomst**och klicka sedan på **Nästa**.

1. På sidan **Bekräfta borttagningsinställningarna** klickar du på **Ta bort**.

## <a name="see-also"></a>Se även

- [Installera och använda Windows PowerShell-Webbåtkomst](install-and-use-windows-powershell-web-access.md)
- [Hjälp om IIS-hanteraren 7,0](https://technet.microsoft.com/library/cc732664.aspx)