---
title: Skapa en Provider för Windows PowerShell-enhet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 2696d78cae7739310b7684161b597ce436dabe92
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855209"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Skapa en Windows PowerShell-enhetsprovider

Det här avsnittet beskriver hur du skapar en provider för Windows PowerShell-enhet som är ett sätt att komma åt ett datalager genom en Windows PowerShell-enhet. Den här typen av providern kallas också Windows PowerShell-enhet providers. Windows PowerShell-enheter som används av providern ger metoder för att ansluta till datalagret.

Windows PowerShell-enhet-providern som beskrivs här ger åtkomst till en Microsoft Access-databas. För den här providern Windows PowerShell-enhet är databasen (det är möjligt att lägga till valfritt antal enheter till en leverantör av enhet), de översta behållarna rotmapp representerar tabeller i databasen och objekten i behållarna representerar raderna i tabeller.

## <a name="defining-the-windows-powershell-provider-class"></a>Definiera klassen Windows PowerShell-providern

Din enhet-provider måste definiera en .NET-klass som härleds från den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basklassen. Här är klassdefinitionen för den här enhetsprovidern:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

Observera att i det här exemplet på [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attributet anger ett användarvänligt namn för providern och de specifika funktionerna i Windows PowerShell som providern Visar Windows PowerShell-runtime under bearbetning av kommandot. De möjliga värdena för funktioner för providern definieras av den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning. Den här enhetsprovidern stöder inte någon av dessa funktioner.

## <a name="defining-base-functionality"></a>Definiera grundfunktionen

Mer information finns i [Design Your Windows PowerShell-providern](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klassen härleds från den [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) basklassen som definierar de metoder som behövs för att initiera och Avinitierar providern. Om du vill implementera funktioner för att lägga till sessionen-specifika initieringsinformation och för att frisläppa resurser som används av providern, se [skapar en grundläggande Windows PowerShell-providern](./creating-a-basic-windows-powershell-provider.md). De flesta leverantörer (inklusive providern som beskrivs här) kan dock använda standardimplementering av den här funktionen som tillhandahålls av Windows PowerShell.

## <a name="creating-drive-state-information"></a>Skapar statusinformation för enhet

Alla Windows PowerShell-leverantörer anses vara tillståndslösa, vilket innebär att din enhet-provider måste skapa all tillståndsinformation som krävs av Windows PowerShell-körningen när anropas av din provider.

För den här enhetsprovidern innehåller information om tillstånd anslutningen till databasen som sparas som en del av enhetsinformationen. Här är kod som visar hur den här informationen lagras i den [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objekt som beskriver enheten:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Skapa en enhet

För att Windows PowerShell-körning för att skapa en enhet måste enheten-leverantören måste implementera de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metod. Följande kod visar implementeringen av den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metod för den här enhetsprovidern:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

Åsidosättningen av den här metoden bör göra följande:

- Kontrollera att den [System.Management.Automation.PSDriveinfo.Root*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) medlem finns och att en anslutning till datalagret kan göras.

- Skapa en enhet och fylla i medlemmen anslutning stöd i `New-PSDrive` cmdlet.

- Verifiera den [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objekt för den föreslagna enheten.

- Ändra den [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objekt som beskriver enheten som har nödvändiga prestanda eller tillförlitlighetsinformation eller extra data för anropare som använder enheten.

- Hantera fel med den [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metoden och sedan återgå `null`.

  Den här metoden returnerar antingen enhetsinformationen som skickades till metoden eller en provider-specifik version av den.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Bifoga dynamiska parametrar till NewDrive

Den `New-PSDrive` cmdlet som stöds av din enhetsprovidern kan kräva ytterligare parametrar. Om du vill koppla dessa dynamiska parametrar till cmdleten providern implementerar den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metod. Den här metoden returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt.

Den här enhetsprovidern åsidosätts inte den här metoden. Följande kod visar dock standardimplementering av den här metoden:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Ta bort en enhet

Om du vill stänga anslutningen till databasen, enhetsprovidern måste implementera de [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metod. Den här metoden stängs anslutningen till enheten när du rensar provider-specifik information.

Följande kod visar implementeringen av den [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metod för den här enhetsprovidern:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Om enheten kan tas bort, ska metoden returnera information som skickas till metoden via den `drive` parametern. Om enheten inte kan tas bort, metoden ska skriva ett undantag och returnerar sedan `null`. Om din leverantör inte åsidosätter den här metoden returnerar standardimplementering av den här metoden bara enhetsinformationen angavs som indata.

## <a name="initializing-default-drives"></a>Initiering av standard-enheter

Din enhet providern implementerar den [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metoden att montera enheter. Providern för Active Directory kan till exempel montera en enhet för standardnamngivningskontext om datorn är ansluten till en domän.

Den här metoden returnerar en samling med enhetsinformationen om initierad enheter eller en tom samling. Anrop till den här metoden görs efter anrop för Windows PowerShell-runtime den [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metod för att initiera providern.

Den här enhetsprovidern åsidosätts inte den [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metod. Följande kod visar dock standardimplementering som returnerar en tom enhet samling:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Kom ihåg följande om hur du implementerar InitializeDefaultDrives

Alla leverantörer av enheten ska ansluta ett rotenhet som hjälper användaren med identifieringsmöjlighet. Rotenheten kan en lista över platser som fungerar som rötter för andra monterade enheter. Providern för Active Directory kan till exempel skapa en enhet som visar en lista över namngivningskontexterna som finns i den `namingContext` attribut rot distribuerade systemmiljö (DSE). Detta hjälper användare att identifiera monteringspunkter för andra enheter.

## <a name="code-sample"></a>Kodexempel

Komplett exempel finns i [AccessDbProviderSample02 kodexempel](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Testa Provider för Windows PowerShell-enhet

När din Windows PowerShell-provider har registrerats med Windows PowerShell kan testa du den genom att köra cmdletarna stöds på kommandoraden, inklusive alla cmdletar som gjorts tillgängliga av härledning. Nu ska vi testa enhetsprovidern exemplet.

1. Kör den `Get-PSProvider` cmdlet för att hämta listan med providers för att säkerställa att enhetsprovidern AccessDB finns:

   **PS> `Get-PSProvider`**

   Följande utdata visas:

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. Kontrollera att Databasservernamnet (DSN) finns för databasen genom att öppna den **datakällor** delen av den **Administrationsverktyg** för operativsystemet. I den **användar-DSN** tabellen genom att dubbelklicka på **MS Access-databas** och Lägg till enhetssökväg C:\ps\northwind.mdb.

3. Skapa en ny enhet med hjälp av exemplet enhetsprovidern:

   **PS > Ny psdrive-namnet mindb-rot c:\ps\northwind.mdb - psprovider AccessDb**

   Följande utdata visas:

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Verifiera anslutningen. Eftersom anslutningen har definierats som en medlem i enheten kan kontrollera du den med hjälp av cmdleten Get-PDDrive.

   > [!NOTE]
   > Användaren kan inte ännu interagera med leverantören som en enhet som providern måste behållare funktioner för den interaktionen. Mer information finns i [skapar en Windows PowerShell-providern för behållaren](./creating-a-windows-powershell-container-provider.md).

   **PS > (get-psdrive mindb) .connection**

   Följande utdata visas:

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. Ta bort enheten och lämna gränssnittet:

   **PS > Ta bort psdrive mindb**

   **PS > Avsluta**

## <a name="see-also"></a>Se även

[Skapa Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md)

[Utforma din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md)

[Skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md)