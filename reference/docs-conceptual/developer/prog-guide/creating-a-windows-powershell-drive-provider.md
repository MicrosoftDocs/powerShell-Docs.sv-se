---
title: Skapa en provider för Windows PowerShell-enheter | Microsoft Docs
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
ms.openlocfilehash: 2e3d97e224b06bdf36ac0bc1237911e029ea762d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357206"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Skapa en Windows PowerShell-enhetsprovider

I det här avsnittet beskrivs hur du skapar en Windows PowerShell-provider som ger ett sätt att komma åt ett data lager via en Windows PowerShell-enhet. Den här typen av Provider kallas även för Windows PowerShell-tjänstleverantörer. De Windows PowerShell-enheter som används av providern ger möjlighet att ansluta till data lagret.

Leverantören av Windows PowerShell-enheten som beskrivs här ger åtkomst till en Microsoft Access-databas. För den här providern representerar Windows PowerShell-enheten databasen (det går att lägga till valfritt antal enheter i en enhets leverantör), behållare på den översta nivån på enheten representerar tabellerna i databasen och objekten i behållarna representerar raderna i tabellerna.

## <a name="defining-the-windows-powershell-provider-class"></a>Definiera klassen Windows PowerShell-Provider

Leverantören av enheten måste definiera en .NET-klass som är härledd från Bask Lassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Här är klass definitionen för den här enhets leverantören:

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

Observera att i det här exemplet anger attributet [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) ett användarvänligt namn för providern och de Windows PowerShell-funktioner som providern exponerar för Windows PowerShell-körningsmiljön under kommando bearbetning. Möjliga värden för providerns funktioner definieras av [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. Den här enhets leverantören stöder inte någon av dessa funktioner.

## <a name="defining-base-functionality"></a>Definiera grundläggande funktioner

Som det beskrivs i [utforma Windows PowerShell-providern](./designing-your-windows-powershell-provider.md)härleds klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) från Bask Lassen [system. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) som definierar de metoder som behövs för att initiera och avinitiera providern. Om du vill implementera funktioner för att lägga till datorspecifik initierings information och släppa resurser som används av providern, se [skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md). De flesta leverantörer (inklusive providern som beskrivs här) kan dock använda standard implementeringen av den här funktionen som tillhandahålls av Windows PowerShell.

## <a name="creating-drive-state-information"></a>Skapar information om enhets tillstånd

Alla Windows PowerShell-leverantörer betraktas som tillstånds lösa, vilket innebär att din enhets leverantör måste skapa all statusinformation som krävs av Windows PowerShell-körningsmiljön när den anropar din Provider.

I den här enhets leverantören inkluderar tillståndsinformation anslutningen till databasen som behålls som en del av enhets informationen. Här är koden som visar hur informationen lagras i objektet [system. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) som beskriver enheten:

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Skapa en enhet

För att Windows PowerShell-körningsmiljön ska kunna skapa en enhet måste providern implementera metoden [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) . Följande kod visar implementeringen av metoden [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) för den här enhets leverantören:

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

Din åsidosättning av den här metoden bör göra följande:

- Kontrol lera att [system. Management. Automation. PSDriveinfo. root *](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member finns och att en anslutning till data lagret kan göras.

- Skapa en enhet och fyll i anslutnings medlemmen, som stöd för cmdleten `New-PSDrive`.

- Verifiera objektet [system. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) för den föreslagna enheten.

- Ändra objektet [system. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) som beskriver enheten med all nödvändig prestanda-eller Tillförlitlighets information, eller ange extra data för anropare som använder enheten.

- Hantera felen med metoden [system. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) och returnera sedan `null`.

  Den här metoden returnerar antingen enhets informationen som skickades till metoden eller en leverantörsspecifik version av den.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Koppla dynamiska parametrar till NewDrive

Den `New-PSDrive`-cmdlet som stöds av enhets leverantören kan behöva ytterligare parametrar. För att koppla dessa dynamiska parametrar till-cmdleten implementerar providern metoden [system. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) . Den här metoden returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt.

Den här enhets leverantören åsidosätter inte den här metoden. Följande kod visar dock standard implementeringen av den här metoden:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Ta bort en enhet

För att stänga databas anslutningen måste enhets leverantören implementera metoden [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) . Den här metoden stänger anslutningen till enheten när all leverantörsspecifik information har rensats.

Följande kod visar implementeringen av metoden [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) för den här enhets leverantören:

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Om enheten kan tas bort ska metoden returnera den information som skickas till metoden via `drive`-parametern. Om enheten inte kan tas bort ska metoden skriva ett undantag och sedan returnera `null`. Om din Provider inte åsidosätter den här metoden returnerar standard implementeringen av den här metoden bara enhets informationen som skickas som indata.

## <a name="initializing-default-drives"></a>Initierar standard enheter

Din enhets leverantör implementerar-metoden [system. Management. Automation. Provider. Drivecmdletprovider. Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) för att montera enheter. Active Directory leverantören kan till exempel montera en enhet för standard namngivnings kontexten om datorn är ansluten till en domän.

Den här metoden returnerar en samling enhets information om de initierade enheterna eller en tom samling. Anropet till den här metoden görs efter att Windows PowerShell-körningen anropar metoden [system. Management. Automation. Provider. Cmdletprovider. start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) för att initiera providern.

Den här enhets leverantören åsidosätter inte metoden [system. Management. Automation. Provider. Drivecmdletprovider. Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) . Följande kod visar dock standard implementeringen, som returnerar en tom enhets samling:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Saker att komma ihåg om att implementera InitializeDefaultDrives

Alla enhets leverantörer ska montera en rot enhet som hjälper användaren att identifiera sig. Rot enheten kan ange platser som fungerar som rötter för andra monterade enheter. Active Directory-providern kan till exempel skapa en enhet som visar namngivnings kontexterna som finns i `namingContext` attribut på root Distributed system Environment (DSE). Detta hjälper användarna att identifiera monterings punkter för andra enheter.

## <a name="code-sample"></a>Kod exempel

Fullständig exempel kod finns i [kod exemplet för AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Testa providern för Windows PowerShell-enheter

När din Windows PowerShell-provider har registrerats med Windows PowerShell kan du testa den genom att köra cmdlets som stöds på kommando raden, inklusive alla cmdletar som gjorts tillgängliga av härledning. Nu ska vi testa leverantören av exempel enheten.

1. Kör cmdleten `Get-PSProvider` för att hämta listan över providrar för att se till att providern för AccessDB-enhet finns:

   **PS > `Get-PSProvider`**

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

2. Se till att det finns ett databas server namn (DSN) för databasen genom att komma åt **data källorna** i **administrations verktyg** för operativ systemet. I tabellen **användar-DSN** dubbelklickar du på **MS Access-databas** och lägger till enhets Sök vägen C:\ps\northwind.mdb.

3. Skapa en ny enhet med hjälp av exempel enhets leverantören:

   **PS > New-PSDrive-Name mindb-root c:\ps\northwind.mdb-PSProvider AccessDb**

   Följande utdata visas:

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Verifiera anslutningen. Eftersom anslutningen definieras som medlem i enheten kan du kontrol lera den med hjälp av cmdleten Get-PDDrive.

   > [!NOTE]
   > Användaren kan ännu inte interagera med providern som en enhet eftersom providern behöver container funktioner för interaktionen. Mer information finns i [skapa en Windows PowerShell container-Provider](./creating-a-windows-powershell-container-provider.md).

   **PS > (Get-PSDrive mindb). anslutning**

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

5. Ta bort enheten och avsluta gränssnittet:

   **PS > Remove-PSDrive mindb**

   **PS >-Avsluta**

## <a name="see-also"></a>Se även

[Skapa Windows PowerShell-leverantörer](./how-to-create-a-windows-powershell-provider.md)

[Utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)

[Skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md)
