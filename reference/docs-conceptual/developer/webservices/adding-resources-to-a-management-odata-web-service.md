---
title: Lägga till resurser till en hantering av OData-webbtjänsten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: 2f6ad8ee9f303d3dea92a633996e9248d2e87a21
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561908"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Lägga till resurser till en Management OData-webbtjänst

Det här exemplet visar hur du lägger till en resurs i en befintlig hantering av OData-webbtjänsten med hjälp av hanterings verktyget OData schema designer. [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) -exemplet skapar en webb tjänst som visar process-och Server resurserna. I det här exemplet ska du lägga till en virtuell dator resurs (VM) till webb tjänsten.

## <a name="prerequisites"></a>Krav

Det här avsnittet förutsätter att du har laddat ned och installerat [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) -exemplet enligt beskrivningen i [skapa en Windows PowerShell-webbtjänst](./creating-a-management-odata-web-service.md)och att du har laddat ned och installerat [hanterings verktyget OData schema designer](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). Det här avsnittet förutsätter också att du har Windows PowerShell-modulen för Hyper-V installerad på den dator där du konfigurerar OData-slutpunkten för hantering.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Lägga till en virtuell dator som en resurs i webb tjänsten

Det första steget är att importera schemat från den befintliga hanterings-OData-slutpunkten till schema designern. Följande procedur beskriver hur du gör det.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importera ett befintligt schema till schema designern

1. Öppna hanterings verktyget OData schema designer.

2. På **Arkiv** -menyn väljer du **fil** . **Ny** ; **Filen**. Dialog rutan **ny fil** visas.

3. Klicka på **hantering av OData-modell**och klicka sedan på **Öppna**.

4. Högerklicka på huvud fönstret och klicka på **schema fil** . **Importera**. Dialog rutan **Öppna** visas.

5. Navigera till mappen där du ställer in webb tjänsten för hantering av OData för [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) -exemplet. Om du använde Windows PowerShell-skriptet som medföljer exemplet för att konfigurera slut punkten utan att ändra skriptet, är den mappen **C:\inetpub\wwwroot\Modata**. Välj schema. MOF och klicka på **Öppna**.

   Öppna i så fall schemat. MOF-och schema-XML-filer i en text redigerare och Lägg märke till att de innehåller mappningar för process-och tjänst resurserna. Filen schema. MOF använder MOF-standarden ( [Distributed Management Task Force](https://www.dmtf.org/) ), hanterad objekt. Filen schema. XML använder ett XML-schema som beskrivs i [resurs mappnings schema](./resource-mapping-schema.md).

   I följande procedur beskrivs hur du importerar Hyper-V-cmdletar i till schema modellen.

#### <a name="importing-cmdlets-into-the-schema"></a>Cmdlets importeras till schemat

1. Högerklicka på ett tomt utrymme i fönstret schema design och klicka på **Importera cmdlets**. Dialog rutan **import guiden för cmdlet** visas.

2. Se till att den **lokala datorn** är markerad och klicka på **Nästa**.

3. Kontrol lera att installerade Windows PowerShell-moduler är markerat och välj Hyper-V i list rutan. Klicka på **Nästa**. Klicka på **Nästa**.

4. I **cmdlet Substantiv** -listan väljer du **virtuell dator**. Klicka på **Nästa**

5. I det här exemplet binder vi bara get-och Delete-kommandona med cmdletar. Avmarkera kryss rutorna **skapa** och **Uppdatera** och kontrol lera att kryss rutorna **Hämta** och **ta bort** är markerade. Kontrol lera att `Get-VM` cmdleten har valts för **Get**och att `Remove-VM` cmdleten har valts för **borttagning**.

6. Eftersom metadata för VM-cmdletarna inte anger någon Utdatatyp måste du köra cmdleten för att ange utdatatypen. Välj **Ange Utdatatyp** och klicka på **kör cmdlet**. Dialog rutan **kör cmdlet** visas. Klicka på **Kör**. Rutan **CLR-typ** fylls i med `VirtualMachine` typen. Klicka på **OK**och sedan på **Nästa**.

7. Som standard är alla egenskaper för VirtualMachine-objektet markerade. Du kan ta bort alla egenskaper som du inte vill ha som en del av de data som returneras när du begär den här resursen från webb tjänsten. Klicka på **Nästa**.

8. Du måste markera minst en egenskap som ska användas som nyckel. Välj **namn** i listan och klicka på **Nästa**.

9. I nästa fönster kan du mappa egenskaper för hanterings-OData-resursen till egenskaper för de underliggande cmdletarna. Guiden mappar egenskaper med identiska namn som standard. Till exempel `ComputerName` mappas resursens egenskap till- `ComputerName` egenskapen för-cmdletarna.  På så sätt kan du ange `ComputerName` egenskapen i en begäran till webb tjänsten och ha det värde som du anger för `Get-VM` cmdleten. `Id`och `Name` mappas också som standard.

   10. Klicka på **Nästa**och sedan på **Slutför**.

       Den virtuella dator resursen visas nu i fönstret schema designer. Du kan granska de egenskaper och åtgärder som är associerade med resursen. Nu ska du exportera de uppdaterade schemafiler till webb tjänstens virtuella katalog.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Exportera schemafiler från schema designern

1. Högerklicka på ett tomt utrymme i fönstret schema design och klicka på **schema fil** . **Exportera**. Dialog rutan **Spara som** visas.

2. Navigera till samma katalog som du importerade MOF-filen från. Ge filen namnet samma som den ursprungliga MOF-filen (schema. mof som standard) och klicka på **Spara**. Bekräfta att du vill skriva över den befintliga filen.

   Även om det inte uttryckligen anges i dialog rutan **Spara som** , ersätter detta både filen schema. MOF och schema. xml.

## <a name="next-steps"></a>Nästa steg

Innan du får åtkomst till den nya virtuella dator resursen från webb tjänsten för hantering av OData måste du uppdatera filen RbacConfiguration. xml för att tillåta åtkomst till Windows PowerShell-modulen för Hyper-V enligt beskrivningen i [Konfigurera rollbaserad auktorisering](./configuring-role-based-authorization.md). du måste också starta om webb tjänsten.
