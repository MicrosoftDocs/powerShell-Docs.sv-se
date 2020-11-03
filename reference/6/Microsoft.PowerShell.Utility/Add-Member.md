---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: cbac0c87ea58acc198fcf981edfd934679e4b3cf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267195"
---
# Add-Member

## SAMMANFATTNING
Lägger till anpassade egenskaper och metoder till en instans av ett PowerShell-objekt.

## SYNTAX

### TypeNameSet (standard)

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### NotePropertyMultiMemberSet

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### NotePropertySingleMemberSet

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### Mängd

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## BESKRIVNING

Med `Add-Member` cmdleten kan du lägga till medlemmar (egenskaper och metoder) till en instans av ett PowerShell-objekt. Du kan till exempel lägga till en NoteProperty-medlem som innehåller en beskrivning av objektet eller en **ScriptMethod** -medlem som kör ett skript för att ändra objektet.

Om du vill använda `Add-Member` , pipe objektet till `Add-Member` , eller Använd parametern **InputObject** för att ange objektet.

Parametern **MemberType** anger vilken typ av medlem som du vill lägga till. Parametern **Name** tilldelar ett namn till den nya medlemmen och **värde** parametern anger medlemmens värde.

De egenskaper och metoder som du lägger till läggs bara till i den specifika instansen av det objekt som du anger. `Add-Member` ändrar inte objekt typen. Använd cmdleten om du vill skapa en ny objekt typ `Add-Type` .

Du kan också använda `Export-Clixml` cmdleten för att spara instansen av objektet, inklusive ytterligare medlemmar, i en fil. Sedan kan du använda `Import-Clixml` cmdleten för att återskapa instansen av objektet från den information som lagras i den exporterade filen.

Från och med Windows PowerShell 3,0 `Add-Member` har nya funktioner som gör det enklare att lägga till antecknings egenskaper till objekt.
Du kan använda parametrarna **NotePropertyName** och **NotePropertyValue** för att definiera en antecknings egenskap eller använda parametern **NotePropertyMembers** , som tar en hash-tabell med antecknings egenskaps namn och värden.

Från och med Windows PowerShell 3,0 krävs även parametern **Passthru** , som genererar ett utgående objekt, vilket är mindre ofta. `Add-Member` nu läggs de nya medlemmarna direkt till i indatamängden av fler typer. Mer information finns i Beskrivning av **Passthru** -parametern.

## EXEMPEL

### Exempel 1: Lägg till en antecknings egenskap i en PSObject

I följande exempel läggs en **status** antecknings egenskap till med värdet "utfört" till **fileinfo** -objektet som representerar `Test.txt` filen.

Det första kommandot använder `Get-ChildItem` cmdleten för att hämta ett **fileinfo** -objekt som representerar `Test.txt` filen. Den sparar den i `$a` variabeln.

Det andra kommandot lägger till antecknings egenskapen i objektet i `$a` .

Det tredje kommandot använder punkt notation för att hämta värdet för objektets **status** egenskap i `$a` . När utdata visas är värdet "klar".

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### Exempel 2: Lägg till en Ali Aset-egenskap i en PSObject

I följande exempel lägger du till en **storleks** Ali Aset-egenskap till objektet som representerar `Test.txt` filen. Den nya egenskapen är ett alias för egenskapen **length** .

Det första kommandot använder `Get-ChildItem` cmdleten för att hämta `Test.txt` **fileinfo** -objektet.

Det andra kommandot lägger till egenskapen **storleks** Ali Aset.
Det tredje kommandot använder punkt notation för att hämta värdet för egenskapen ny **storlek** .

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### Exempel 3: lägga till en StringUse antecknings egenskap i en sträng

I det här exemplet läggs **StringUse** -antecknings egenskapen till i en sträng.
Eftersom `Add-Member` det inte går att lägga till typer till **stränga** indata-objekt kan du ange parametern **Passthru** för att generera ett utdata-objekt. Det sista kommandot i exemplet visar den nya egenskapen.

I det här exemplet används parametern **NotePropertyMembers** . Värdet för parametern **NotePropertyMembers** är en hash-tabell. Nyckeln är anteckningens egenskaps namn, **StringUse** och värdet är anteckningens egenskaps värde, **Visa**.

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### Exempel 4: Lägg till en skript metod till ett FileInfo-objekt

I det här exemplet läggs skript metoden **att sizeinmb** till i ett **fileinfo** -objekt som beräknar fil storleken till närmaste megabyte. Det andra kommandot skapar en **script block** som använder den **avrundade** statiska metoden från `[math]` typen för att runda av fil storleken till den andra decimal platsen.

Parametern **Value** använder också den `$This` automatiska variabeln som representerar det aktuella objektet. `$This`Variabeln är endast giltig i skript block som definierar nya egenskaper och metoder.

Det sista kommandot använder punkt notation för att anropa den nya **att sizeinmb** -skript metoden i objektet i `$A` variabeln.

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### Exempel 5: kopiera alla egenskaper för ett objekt till ett annat

Den här funktionen kopierar alla egenskaper för ett objekt till ett annat objekt.

`foreach`Slingan använder `Get-Member` cmdleten för att hämta var och en av egenskaperna för **from** -objektet. Kommandona i `foreach` slingan utförs i serien för varje egenskap.

`Add-Member`Kommandot lägger till egenskapen för **from** -objektet i objektet **till** som en **NoteProperty**. Värdet kopieras med parametern **Value** . Den använder **Force** -parametern för att lägga till medlemmar med samma medlems namn.

```powershell
function Copy-Property ($From, $To)
{
    $properties = Get-Member -InputObject $From -MemberType Property
    foreach ($p in $properties)
    {
        $To | Add-Member -MemberType NoteProperty -Name $p.Name -Value $From.$($p.Name) -Force
    }
}
```

### Exempel 6: skapa ett anpassat objekt

Det här exemplet skapar ett anpassat **till gångs** objekt.

`New-Object`Cmdleten skapar en **PSObject**. Exemplet sparar **PSObject** i `$Asset` variabeln.

Det andra kommandot använder `[ordered]` typen Accelerator för att skapa en ordnad ord lista med namn och värden. Kommandot sparar resultatet i `$D` variabeln.

Det tredje kommandot använder **NotePropertyMembers** -parametern för `Add-Member` cmdleten för att lägga till ord listan i `$D` variabeln till **PSObject**.
Egenskapen **TypeName** tilldelar ett nytt namn, **till gång** , till **PSObject**.

Det sista kommandot rör det nya **till gångs** objekt till `Get-Member` cmdleten. Utdata visar att objektet har ett typ namn för **till gång** och de antecknings egenskaper som vi definierade i den ordnade ord listan.

```powershell
$Asset = New-Object -TypeName PSObject
$d = [ordered]@{Name="Server30";System="Server Core";PSVersion="4.0"}
$Asset | Add-Member -NotePropertyMembers $d -TypeName Asset
$Asset | Get-Member
```

```Output
   TypeName: Asset

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty System.String Name=Server30
PSVersion   NoteProperty System.String PSVersion=4.0
System      NoteProperty System.String System=Server Core
```

## PARAMETRAR

### -Force

Anger att denna cmdlet lägger till en ny medlem även om objektet har en anpassad medlem med samma namn.
Du kan inte använda **Force** -parametern för att ersätta en standard medlem av en typ.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger objektet som den nya medlemmen ska läggas till i.
Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – MemberType

Anger vilken typ av medlem som ska läggas till.
Den här parametern är obligatorisk.
De acceptabla värdena för den här parametern är:

- NoteProperty
- AliasProperty
- ScriptProperty
- CodeProperty
- ScriptMethod
- CodeMethod

Information om dessa värden finns i [PSMemberTypes-uppräkning](/dotnet/api/system.management.automation.psmembertypes) i MSDN-biblioteket.

Alla objekt har inte alla typer av medlemmar.
Om du anger en medlems typ som objektet inte har, returnerar PowerShell ett fel.

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: MemberSet
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger namnet på medlemmen som denna cmdlet lägger till.

```yaml
Type: System.String
Parameter Sets: MemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyMembers

Anger en hash-tabell eller en ordnad ord lista med namn och värden för antecknings egenskaper.
Ange en hash-tabell eller-ordlista där nycklarna är antecknings egenskaps namn och värdena är antecknings egenskaps värden.

Mer information om hash-tabeller och beställda ord listor i PowerShell finns [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: NotePropertyMultiMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyName

Anger anteckningens egenskaps namn.

Använd den här parametern med parametern **NotePropertyValue** .
Den här parametern är valfri.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyValue

Anger anteckningens egenskaps värde.

Använd den här parametern med parametern **NotePropertyName** .
Den här parametern är valfri.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Object
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med.
Som standard genererar denna cmdlet inga utdata.

För de flesta objekt `Add-Member` lägger till de nya medlemmarna i objektet.
När inobjektet är en sträng kan du dock `Add-Member` inte lägga till medlemmen i objektet.
För dessa objekt använder du parametern **Passthru** för att skapa ett utgående objekt.

I Windows PowerShell 2,0, `Add-Member` lades endast till medlemmar till **PSObject** -omslutningen av objekt, inte för objektet.
Använd parametern **Passthru** för att skapa ett utgående objekt för alla objekt som har ett **PSObject** -gränssnitt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecondValue

Anger ytterligare information om **AliasProperty** -, **ScriptProperty** -, **CodeProperty** -eller **CodeMethod** -medlemmar.

Om den här parametern används för att lägga till en **AliasProperty** måste den vara av data typen.
En konvertering till den angivna data typen läggs till i värdet för **AliasProperty**.

Om du till exempel lägger till en **AliasProperty** som ger ett alternativt namn för en sträng egenskap, kan du även ange en **SecondValue** -parameter för **system. Int32** för att indikera att värdet för den sträng egenskapen ska konverteras till ett heltal vid åtkomst med motsvarande **AliasProperty**.

Du kan använda parametern **SecondValue** för att ange ytterligare en **script block** när du lägger till en **ScriptProperty** -medlem. Den första **script block** , som anges i parametern **Value** , används för att hämta värdet för en variabel. Den andra **script block** som anges i parametern **SecondValue** används för att ange värdet för en variabel.

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Värde

Anger det inledande värdet för den tillagda medlemmen.
Om du lägger till en **AliasProperty** -, **CodeProperty** -, **ScriptProperty** -eller **CodeMethod** -medlem kan du ange valfri, ytterligare information med hjälp av parametern **SecondValue** .

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

Anger ett namn för typen.

När typen är en klass i **system** namn området eller en typ som har en typ Accelerator, kan du ange det korta namnet för typen. Annars krävs det fullständiga typ namnet.
Den här parametern är endast effektiv när **InputObject** är en **PSObject**.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: TypeNameSet, NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: True (TypeNameSet), False (NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka vidare valfri objekt typ till denna cmdlet.

## UTDATA

### Ingen eller system. Object

När du använder parametern **Passthru** returnerar denna cmdlet det nyligen utökade objektet.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

Du kan bara lägga till medlemmar i **PSObject** -objekt. Använd operatorn för att avgöra om ett objekt är ett **PSObject** -objekt `-is` .

Om du till exempel vill testa ett objekt som lagras i `$obj` variabeln skriver du `$obj -is [PSObject]` .

Namnen på parametrarna **MemberType** , **Name** , **Value** och **SecondValue** är valfria.
Om du utelämnar parameter namnen måste de parameter värden som inte är namngivna visas i den här ordningen: **MemberType** , **Name** , **Value** och **SecondValue**.

Om du inkluderar parameter namnen kan parametrarna visas i vilken ordning som helst.

Du kan använda den `$this` automatiska variabeln i skript block som definierar värdena för nya egenskaper och metoder.
`$this`Variabeln refererar till den instans av objektet som egenskaper och metoder läggs till i. Mer information om `$this` variabeln finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

## RELATERADE LÄNKAR

[Exportera – CliXml](Export-Clixml.md)

[Hämta medlem](Get-Member.md)

[Importera – CliXml](Import-Clixml.md)

[Nytt – objekt](New-Object.md)

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)
