---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: 9a51c97def7cddf45c391ed91ff67ad97fbedf77
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/10/2020
ms.locfileid: "93269463"
---
# Add-Type

## SAMMANFATTNING
Lägger till en Microsoft .NET Core-klass till en PowerShell-session.

## SYNTAX

### FromSource (standard)

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### FromMember

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### FromPath

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### FromLiteralPath

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### FromAssemblyName

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## BESKRIVNING

Med `Add-Type` cmdleten kan du definiera en Microsoft .net Core-klass i din PowerShell-session. Du kan sedan instansiera objekt med hjälp av `New-Object` cmdleten och använda objekten på samma sätt som du använder ett .net Core-objekt. Om du lägger till ett `Add-Type` kommando i din PowerShell-profil, är klassen tillgänglig i alla PowerShell-sessioner.

Du kan ange typen genom att ange en befintlig sammansättning eller källfiler, eller så kan du ange käll koden infogad eller Sparad i en variabel. Du kan även ange en metod och `Add-Type` definiera och generera klassen. I Windows kan du använda den här funktionen för att göra plattforms anrop (P/Invoke)-anrop till ohanterade funktioner i PowerShell. Om du anger käll kod `Add-Type` kompilerar den angivna käll koden och genererar en minnes intern sammansättning som innehåller de nya .net Core-typerna.

Du kan använda parametrarna för `Add-Type` för att ange ett alternativt språk och en kompilerare, C# är standard, kompilator alternativ, sammansättnings beroenden, klass namn område, namn på typen och den resulterande sammansättningen.

## EXEMPEL

### Exempel 1: Lägg till en .NET-typ i en session

I det här exemplet läggs klassen **BasicTest** till i sessionen genom att du anger käll koden som lagras i en variabel. **BasicTest** -klassen används för att lägga till heltal, skapa ett objekt och multiplicera heltal.

```powershell
$Source = @"
public class BasicTest
{
  public static int Add(int a, int b)
    {
        return (a + b);
    }
  public int Multiply(int a, int b)
    {
    return (a * b);
    }
}
"@

Add-Type -TypeDefinition $Source
[BasicTest]::Add(4, 3)
$BasicTestObject = New-Object BasicTest
$BasicTestObject.Multiply(5, 2)
```

`$Source`Variabeln lagrar käll koden för klassen. Typen har en statisk metod som kallas `Add` och en icke-statisk metod som kallas `Multiply` .

`Add-Type`Cmdleten lägger till klassen i sessionen. Eftersom den använder infogad källkod använder kommandot **TypeDefinition** -parametern för att ange koden i `$Source` variabeln.

Den `Add` statiska metoden i **BasicTest** -klassen använder dubbla kolon tecken ( `::` ) för att ange en statisk medlem i klassen. Heltalen läggs till och summan visas.

`New-Object`Cmdlet: en instansierar en instans av klassen **BasicTest** . Det sparar det nya objektet i `$BasicTestObject` variabeln.

`$BasicTestObject` använder- `Multiply` metoden. Heltalen multipliceras och produkten visas.

### Exempel 2: granska en tillagd typ

I det här exemplet används `Get-Member` cmdleten för att undersöka de objekt som `Add-Type` `New-Object` cmdletarna och skapade i **exempel 1**.

```powershell
[BasicTest] | Get-Member
```

```Output
   TypeName: System.RuntimeType

Name                 MemberType Definition
----                 ---------- ----------
AsType               Method     type AsType()
Clone                Method     System.Object Clone(), System.Object ICloneable.Clone()
Equals               Method     bool Equals(System.Object obj), bool Equals(type o)
FindInterfaces       Method     type[] FindInterfaces(System.Reflection.TypeFilter filter...
...
```

```powershell
[BasicTest] | Get-Member -Static
```

```Output
  TypeName: BasicTest

Name            MemberType Definition
----            ---------- ----------
Add             Method     static int Add(int a, int b)
Equals          Method     static bool Equals(System.Object objA, System.Object objB)
new             Method     BasicTest new()
ReferenceEquals Method     static bool ReferenceEquals(System.Object objA, System.Object objB)
```

```powershell
$BasicTestObject | Get-Member
```

```Output
   TypeName: BasicTest

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
Multiply    Method     int Multiply(int a, int b)
ToString    Method     string ToString()
```

`Get-Member`Cmdleten hämtar typ och medlemmar i **BasicTest** -klassen som `Add-Type` har lagts till i sessionen. `Get-Member`Kommandot visar att det är ett **system. RuntimeType** -objekt, som härleds från klassen **system. Object** .

Den `Get-Member` **statiska** parametern hämtar statiska egenskaper och metoder för klassen **BasicTest** . Utdata visar att `Add` metoden ingår.

`Get-Member`Cmdlet: en hämtar medlemmarna i objektet som lagras i `$BasicTestObject` variabeln.
`$BasicTestObject` har skapats med hjälp av `New-Object` cmdleten med klassen **BasicTest** . Utdata visar att värdet för `$BasicTestObject` variabeln är en instans av klassen **BasicTest** och att den innehåller en medlem som kallas `Multiply` .

### Exempel 3: lägga till typer från en sammansättning

I det här exemplet läggs klasserna från `NJsonSchema.dll` sammansättningen till den aktuella sessionen.

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

`Set-Location` använder parametern **Path** för att ange `$PSHOME` variabeln. Variabeln refererar till PowerShell-installations katalogen där DLL-filen finns.

`$AccType`Variabeln lagrar ett objekt som skapats med `Add-Type` cmdleten. `Add-Type` använder parametern **AssemblyName** för att ange namnet på sammansättningen. Med jokertecknet asterisk ( `*` ) kan du hämta rätt sammansättning även om du inte är säker på namnet eller stavningen. Parametern **Passthru** genererar objekt som representerar de klasser som läggs till i sessionen.

### Exempel 4: anropa inbyggda Windows-API: er

Det här exemplet visar hur du anropar inbyggda Windows-API: er i PowerShell. `Add-Type` använder mekanismen för plattforms anrop (P/Invoke) för att anropa en funktion i `User32.dll` från PowerShell. Det här exemplet fungerar endast på datorer som kör operativ systemet Windows.

```powershell
$Signature = @"
[DllImport("user32.dll")]public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);
"@

$ShowWindowAsync = Add-Type -MemberDefinition $Signature -Name "Win32ShowWindowAsync" -Namespace Win32Functions -PassThru

# Minimize the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $pid).MainWindowHandle, 2)

# Restore the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $Pid).MainWindowHandle, 4)
```

`$Signature`Variabeln lagrar C#-signaturen för `ShowWindowAsync` funktionen. För att säkerställa att den resulterande metoden visas i en PowerShell-session har `public` nyckelordet lagts till i standard-signaturen. Mer information finns i [ShowWindowAsync-funktionen](/windows/win32/api/winuser/nf-winuser-showwindowasync).

`$ShowWindowAsync`Variabeln lagrar objektet som skapats av parametern `Add-Type` **Passthru** .
`Add-Type`Cmdleten lägger till `ShowWindowAsync` funktionen i PowerShell-sessionen som en statisk metod. Kommandot använder parametern **MemberDefinition** för att ange den metod definition som sparats i `$Signature` variabeln. Kommandot använder **namn** och namn **områdes** parametrar för att ange ett namn och ett namn område för klassen. Parametern **Passthru** genererar ett objekt som representerar typerna.

Den nya `ShowWindowAsync` statiska metoden används i kommandona för att minimera och återställa PowerShell-konsolen. Metoden tar två parametrar: fönster handtaget och ett heltal som anger hur fönstret visas.

För att minimera PowerShell-konsolen, `ShowWindowAsync` använder `Get-Process` cmdleten med den `$PID` automatiska variabeln för att hämta den process som är värd för den aktuella PowerShell-sessionen. Sedan används egenskapen **MainWindowHandle** för den aktuella processen och värdet `2` , som representerar `SW_MINIMIZE` värdet.

För att återställa fönstret `ShowWindowAsync` använder värdet `4` för fönstrets position, som representerar `SW_RESTORE` värdet.

Maximera fönstret genom att använda värdet för `3` som representerar `SW_MAXIMIZE` .

## PARAMETRAR

### -AssemblyName

Anger namnet på en sammansättning som innehåller typerna. `Add-Type` tar typer från den angivna sammansättningen. Den här parametern krävs när du skapar typer baserat på ett sammansättnings namn.

Ange det fullständiga eller enkla namnet, även kallat det partiella namnet för en sammansättning. Jokertecken tillåts i sammansättnings namnet. Om du anger ett enkelt eller partiellt namn `Add-Type` matchas det med det fullständiga namnet och sedan används det fullständiga namnet för att läsa in sammansättningen.

Den här parametern accepterar inte en sökväg eller ett fil namn. Om du vill ange sökvägen till DLL-filen för Assembly-DLL-filen använder du parametern **Path** .

```yaml
Type: System.String[]
Parameter Sets: FromAssemblyName
Aliases: AN

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -CompilerOptions

Anger alternativ för käll kods kompileraren. De här alternativen skickas till kompilatorn utan revidering.

Med den här parametern kan du dirigera kompilatorn för att generera en körbar fil, bädda in resurser eller ange kommando rads alternativ, till exempel `/unsafe` alternativet.

Du kan inte använda parametrarna **CompilerOptions** och **ReferencedAssemblies** i samma kommando.

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreWarnings

Ignorerar kompilator varningar. Använd den här parametern för att förhindra `Add-Type` hantering av kompilator varningar som fel.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Språk

Anger det språk som används i käll koden. Det acceptabla värdet för den här parametern är **csharp**.

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägen till käll kods filer eller sammansättnings-DLL-filer som innehåller typerna. Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det skrivs. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MemberDefinition

Anger nya egenskaper eller metoder för klassen. `Add-Type` skapar den mallkod som krävs för att stödja egenskaper eller metoder.

I Windows kan du använda den här funktionen för att göra plattforms anrop (P/Invoke)-anrop till ohanterade funktioner i PowerShell.

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger namnet på den klass som ska skapas. Den här parametern krävs när en typ skapas från en medlems definition.

Typ namnet och namn området måste vara unikt inom en session. Du kan inte ta bort en typ eller ändra den.
Om du vill ändra koden för en typ måste du ändra namnet eller starta en ny PowerShell-session.
Annars Miss lyckas kommandot.

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Namnrymd

Anger ett namn område för typen.

Om den här parametern inte ingår i kommandot skapas typen i namn området **Microsoft. PowerShell. commands. AddType. AutoGeneratedTypes** . Om parametern ingår i kommandot med ett tomt sträng värde eller ett värde av `$Null` genereras typen i det globala namn området.

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputAssembly

Genererar en DLL-fil för sammansättningen med det angivna namnet på platsen. Ange en valfri sökväg och ett fil namn. Jokertecken är tillåtna. Som standard `Add-Type` genererar sammansättningen endast i minnet.

```yaml
Type: System.String
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – OutputType

Anger utdatatypen för den utgående sammansättningen. Som standard har ingen Utdatatyp angetts. Den här parametern är endast giltig när en utgående sammansättning anges i kommandot. Mer information om värdena finns i OutputAssemblyType- [uppräkning](/dotnet/api/microsoft.powershell.commands.outputassemblytype).

De acceptabla värdena för den här parametern är följande:

- ConsoleApplication
- Bibliotek
- WindowsApplication

> [!IMPORTANT]
> `ConsoleApplication`Värdena och kan inte `WindowsApplication` producera fungerande utdata och bör inte användas.

```yaml
Type: Microsoft.PowerShell.Commands.OutputAssemblyType
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OT
Accepted values: ConsoleApplication, Library, WindowsApplication

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Returnerar ett **system. Runtime** -objekt som representerar de typer som har lagts till. Som standard genererar denna cmdlet inga utdata.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger sökvägen till käll kods filer eller sammansättnings-DLL-filer som innehåller typerna.

Om du skickar källfiler `Add-Type` kompilerar koden i filerna och skapar en minnes intern sammansättning av typerna. Fil tillägget som anges i **Path** -värdet avgör vilken kompilator som `Add-Type` använder.

Om du skickar en sammansättnings fil, `Add-Type` tar de olika typerna från sammansättningen. Om du vill ange en minnes intern sammansättning eller Global Assembly Cache använder du parametern **AssemblyName** .

```yaml
Type: System.String[]
Parameter Sets: FromPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferencedAssemblies

Anger de sammansättningar som typen är beroende av. Som standard `Add-Type` refererar `System.dll` och `System.Management.Automation.dll` . De sammansättningar som du anger med hjälp av den här parametern refereras till utöver standard sammansättningarna.

Från och med PowerShell 6 inkluderar **ReferencedAssemblies** inte standard-.net-sammansättningarna. Du måste inkludera en speciell referens till dem i värdet som skickas till den här parametern.

Du kan inte använda parametrarna **CompilerOptions** och **ReferencedAssemblies** i samma kommando.

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: RA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeDefinition

Anger den käll kod som innehåller typ definitionerna. Ange käll koden i en sträng eller här – sträng, eller ange en variabel som innehåller käll koden. Mer information om här – strängar finns [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).

Ta med en namn områdes deklaration i din typ definition. Om du utelämnar namn områdes deklarationen kan typen ha samma namn som en annan typ eller genvägen till en annan typ, vilket orsakar en oavsiktlig överskrivning. Om du till exempel definierar en typ som heter **Exception** , kommer skript som använder **undantag** som genväg för **system. Exception** inte att fungera.

```yaml
Type: System.String
Parameter Sets: FromSource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UsingNamespace

Anger andra namn områden som krävs för klassen. Detta är ungefär som nyckelordet C#, `Using` .

Som standard `Add-Type` refererar **system** namn området. När parametern **MemberDefinition** används `Add-Type` refererar även namn området **system. Runtime. InteropServices** som standard. De namn områden som du lägger till med hjälp av parametern **UsingNamespace** refereras till utöver standard namn områdena.

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases: Using

Required: False
Position: Named
Default value: System namespace
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka objekt nedåt i pipelinen till `Add-Type` .

## UTDATA

### Ingen eller system. Type

När du använder parametern **Passthru** `Add-Type` returneras ett **system. Type** -objekt som representerar den nya typen. Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

De typer som du lägger till finns bara i den aktuella sessionen. Om du vill använda typerna i alla sessioner lägger du till dem i din PowerShell-profil. Mer information om profilen finns [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

Typ namn och namn områden måste vara unika inom en session. Du kan inte ta bort en typ eller ändra den. Om du behöver ändra koden för en typ måste du ändra namnet eller starta en ny PowerShell-session.
Annars Miss lyckas kommandot.

I Windows PowerShell (version 5,1 och senare) måste du använda `Add-Type` för allt som inte redan har lästs in. Oftast gäller detta för sammansättningar som finns i GAC (Global Assembly Cache).
I PowerShell 6 och senare finns det ingen GAC, så PowerShell installerar sina egna sammansättningar i `$PSHome` .
Dessa sammansättningar läses in automatiskt på begäran, så du behöver inte använda `Add-Type` för att läsa in dem. Användningen tillåts dock `Add-Type` fortfarande tillåta skript att vara implicit kompatibla med vilken version av PowerShell som helst.

Sammansättningar i GAC kan läsas in med typnamn i stället för sökväg. Inläsning av sammansättningar från en godtycklig sökväg kräver `Add-Type` , eftersom dessa sammansättningar inte kan läsas in automatiskt.

## RELATERADE LÄNKAR

[about_Profiles](../Microsoft.PowerShell.Core/About/about_profiles.md)

[about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[Lägg till medlem](Add-Member.md)

[Nytt – objekt](New-Object.md)

[OutputAssemblyType](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[Plattforms anrop (P/Invoke)](/dotnet/standard/native-interop/pinvoke)

[Where-objekt](../Microsoft.PowerShell.Core/Where-Object.md)
