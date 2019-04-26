---
title: Att lägga till resurser till en Management OData-webbtjänst | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080789"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Lägga till resurser till en Management OData-webbtjänst

Det här exemplet visar hur du lägger till en resurs till en befintlig Management OData-webbtjänst med hjälp av Management OData Schema Designer. Den [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplet skapar en webbtjänst som exponerar Process- och datorresurser. I det här exemplet ska du lägga till en virtuell dator (VM)-resurs till webbtjänsten.

## <a name="prerequisites"></a>Förutsättningar

Det här avsnittet förutsätter att du har hämtat och installerat den [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exempel enligt beskrivningen i [skapar en Windows PowerShell-webbtjänst](./creating-a-management-odata-web-service.md), och att du har hämtat och installerat den [Management OData Schema Designer](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). Det här avsnittet förutsätter också att du har Hyper-V Windows PowerShell-modulen installerad på den dator där du konfigurerar Management Odata-slutpunkten.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Att lägga till virtuell dator som en resurs till webbtjänsten

Det första steget är att importera schemat från den befintliga Management OData-slutpunkten till schema designer. Följande procedur beskriver hur du gör.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importera ett befintligt schema till schema designer

1. Öppna Management OData Schema Designer.

2. Från den **filen** menyn och välj **filen** ; **Nya** ; **Filen**. Den **ny fil** dialogruta.

3. Klicka på **Management OData-modellen**, och klicka sedan på **öppna**.

4. Högerklicka i huvudfönstret och klicka på **schemafilen** ; **Import**. Den **öppna** dialogruta.

5. Navigera till mappen där du konfigurerar Management OData-webbtjänst för den [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplet. Om du använder Windows PowerShell-skriptet som medföljer det exemplet för att konfigurera slutpunkten utan att ändra skriptet, mappen är **C:\inetpub\wwwroot\Modata**. Välj Schema.mof och klicka på **öppna**.

   Då öppnar du Schema.mof och Schema.xml i en textredigerare och Lägg märke till att de innehåller mappningar för processen och Service-resurser. Filen Schema.mof använder [Distributed Management Task Force](https://www.dmtf.org/) (DTMF) hanterade objekt (MOF) standard. Filen schema.xml använder ett XML-schema som beskrivs i [Resource mappning schemat](./resource-mapping-schema.md).

   Följande procedur beskriver hur du importerar Hyper-V-cmdletar i schema-modellen.

#### <a name="importing-cmdlets-into-the-schema"></a>Importera cmdlet: ar till schemat

1. Högerklicka på ett tomt område på schema designer-fönstret och klicka på **Import-cmdletarna**. Den **Cmdlet Importguiden** dialogruta.

2. Se till att **lokala** är markerad och klicka på **nästa**.

3. Kontrollera att installerat Windows PowerShell-moduler är markerat och välj Hyper-V från den nedrullningsbara listan. Klicka på **nästa**. Klicka på **Nästa**.

4. I den **Cmdlet-substantiv** väljer **VM**. Klicka på **nästa**

5. I det här exemplet ska vi binda bara hämta och ta bort kommandona med cmdlet: ar. Rensa den **skapa** och **uppdatering** kryssrutor och se till att den **hämta** och **ta bort** kryssrutorna är markerade. Se till att den `Get-VM` cmdlet har valts för **hämta**, och `Remove-VM` cmdlet har valts för **ta bort**.

6. Eftersom metadata för VM-cmdlets inte anger en Utdatatyp, måste du köra cmdlet för att ange vilken Utdatatyp. Välj **ange utdatatypen** och klicka på **kör cmdlet**. Den **kör Cmdlet** dialogruta. Klicka på **Run** (Kör). Den **CLR-typen** fylls i med de `VirtualMachine` typen. Klicka på **OK**, klicka sedan på **nästa**.

7. Som standard markeras alla egenskaper i VirtualMachine-objektet. Du kan rensa eventuella egenskaper som du inte vill att som en del av de data som returneras när du begär den här resursen från webbtjänsten. Klicka på **Nästa**.

8. Du måste välja minst en egenskap som ska användas som en nyckel. Välj **namn** i listan och klicka på **nästa**.

9. Nästa fönster kan du mappa egenskaper för Management OData-resursen till egenskaperna för de underliggande cmdletarna. Guiden mappar egenskaper med samma namn som standard. Till exempel den `ComputerName` för resursgruppens egenskap är mappad till den `ComputerName` egenskapen cmdlet.  På så sätt kan du ange den `ComputerName` -egenskapen i en begäran till webbtjänst och har värdet som du anger ska skickas till den `Get-VM` cmdlet. `Id` och `Name` även mappas som standard.

   10. Klicka på **nästa**, klicka sedan på **Slutför**.

       Den Virtuella datorresursen visas nu i designer-fönstret för schemat. Du kan granska egenskaper och åtgärder som hör till resursen. Du kommer sedan exportera uppdaterade schemat filerna till den virtuella katalogen för webbtjänsten.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Exportera schemafiler från schema designer

1. Högerklicka på ett tomt område på schema designer-fönstret och klicka på **schemafilen** ; **Exportera**. Den **Spara som** dialogruta.

2. Navigera till samma katalog från där du importerade MOF-filen. Ge filen namnet samma som den ursprungliga MOF-filen (Schema.mof som standard) och klicka på **spara**. Bekräfta att du vill skriva över den befintliga filen.

   Även om det inte uttryckligen anges i den **Spara som** dialogrutan det här ersätter både Schema.mof och Schema.xml filer.

## <a name="next-steps"></a>Nästa steg

Innan du åtkomst till den nya VM-resursen från Management OData-webbtjänst måste du uppdatera filen RbacConfiguration.xml för att tillåta åtkomst till Hyper-V Windows PowerShell-modulen enligt beskrivningen i [konfigurera rollbaserad auktorisering](./configuring-role-based-authorization.md), och du måste också starta om webbtjänsten.