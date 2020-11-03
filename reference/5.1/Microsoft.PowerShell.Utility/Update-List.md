---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-list?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-List
ms.openlocfilehash: eccee5ad302395116430006ed4dc0395946696b6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264795"
---
# Update-List

## SAMMANFATTNING
Lägger till objekt i och tar bort objekt från ett egenskaps värde som innehåller en objekt samling.

## SYNTAX

### AddRemoveSet (standard)

```
Update-List [-Add <Object[]>] [-Remove <Object[]>] [-InputObject <PSObject>] [[-Property] <String>]
 [<CommonParameters>]
```

### ReplaceSet

```
Update-List -Replace <Object[]> [-InputObject <PSObject>] [[-Property] <String>] [<CommonParameters>]
```

## BESKRIVNING

`Update-List`Cmdleten lägger till, tar bort eller ersätter objekt i ett egenskaps värde för ett objekt och returnerar det uppdaterade objektet. Denna cmdlet är utformad för egenskaper som innehåller objekt samlingar.

Parametrarna **Lägg till** och **ta bort** lägger till enskilda objekt i och tar bort dem från samlingen.
**Ersättnings** parametern ersätter hela samlingen.

Om du inte anger någon egenskap i kommandot `Update-List` returneras ett objekt som beskriver uppdateringen i stället för att uppdatera objektet. Du kan skicka objektet Update till-cmdletar som ändrar objekt, till exempel `Set` cmdletar.

Den här cmdleten fungerar bara när den egenskap som uppdateras stöder **ilist** -gränssnittet som `Update-List` använder. Dessutom måste alla `Set` cmdletar som accepterar en uppdatering ha stöd för **ilist** -gränssnittet.

De grundläggande cmdletarna som installeras med PowerShell stöder inte det här gränssnittet. Information om hur en cmdlet stöder `Update-List` finns i hjälp avsnittet för cmdleten.

## EXEMPEL

### Exempel 1: Lägg till objekt i ett egenskaps värde

I det här exemplet skapar vi en klass som representerar en kortlek med kort där korten lagras som ett **list** samlings objekt. Metoden **NewDeck ()** använder `Update-List` för att lägga till en fullständig kortlek med kort värden i **kort** samlingen.

```powershell
class Cards {

    [System.Collections.Generic.List[string]]$cards
    [string]$name

    Cards([string]$_name) {
        $this.name = $_name
        $this.cards = [System.Collections.Generic.List[string]]::new()
    }

    NewDeck() {
        $_suits = [char]0x2663,[char]0x2666,[char]0x2665,[char]0x2660
        $_values = 'A',2,3,4,5,6,7,8,9,10,'J','Q','K'
        $_deck = foreach ($s in $_suits){ foreach ($v in $_values){ "$v$s"} }
        $this | Update-List -Property cards -Add $_deck | Out-Null
    }

    Show() {
        Write-Host
        Write-Host $this.name ": " $this.cards[0..12]
        if ($this.cards.count -gt 13) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[13..25]
        }
        if ($this.cards.count -gt 26) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[26..38]
        }
        if ($this.cards.count -gt 39) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[39..51]
        }
    }

    Shuffle() { $this.cards = Get-Random -InputObject $this.cards -Count 52 }

    Sort() { $this.cards.Sort() }
}
```

> [!NOTE]
> `Update-List`Cmdleten matar ut det uppdaterade objektet till pipelinen. Vi rör utdata för `Out-Null` att förhindra den oönskade visningen.

### Exempel 2: lägga till och ta bort objekt i en samlings egenskap

Om du fortsätter med koden i exempel 1 kommer vi att skapa instanser av **kort** klassen som representerar kort lekar och kort som innehas av två spelare. Vi använder `Update-List` cmdleten för att lägga till kort i spelarens händer och ta bort kort från däcket.

```powershell
$player1 = [Cards]::new('Player 1')
$player2 = [Cards]::new('Player 2')

$deck = [Cards]::new('Deck')
$deck.NewDeck()
$deck.Shuffle()
$deck.Show()

# Deal two hands
$player1 | Update-List -Property cards -Add $deck.cards[0,2,4,6,8] | Out-Null
$player2 | Update-List -Property cards -Add $deck.cards[1,3,5,7,9] | Out-Null
$deck | Update-List -Property cards -Remove $player1.cards | Out-Null
$deck | Update-List -Property cards -Remove $player2.cards | Out-Null

$player1.Show()
$player2.Show()
$deck.Show()
```

```Output
Deck :  4♦ 7♥ J♦ 5♣ A♣ 8♦ J♣ Q♥ 6♦ 3♦ 9♦ 6♣ 2♣
        K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣ Q♣ A♥ Q♠
        3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠ 4♣ 2♠ 2♥
        6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣ A♦ K♣ 8♥

Player 1 :  4♦ J♦ A♣ J♣ 6♦

Player 2 :  7♥ 5♣ 8♦ Q♥ 3♦

Deck :  9♦ 6♣ 2♣ K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣
        Q♣ A♥ Q♠ 3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠
        4♣ 2♠ 2♥ 6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣
        A♦ K♣ 8♥
```

Utmatningen visar kortets tillstånd innan korten behandlades för spelarna. Du kan se att varje spelare fick fem kort från däcket. Den slutliga utmatningen visar kortets tillstånd efter att korten har behandlats till spelarna. `Update-List` användes för att välja korten från däcket och lägga till dem i spelarens samling. Sedan togs spelarnas kort bort från däcket med hjälp av `Update-List` .

### Exempel 3: lägga till och ta bort objekt i ett enda kommando

`Update-List` gör att du kan använda parametrarna **Add** och **Remove** i ett enda kommando. I det här exemplet vill spelaren 1 ta bort `4♦` och `6♦` få två nya kort.

```powershell
# Player 1 wants two new cards - remove 2 cards & add 2 cards
$player1 | Update-List -Property cards -Remove $player1.cards[0,4] -Add $deck.cards[0..1] | Out-Null
$player1.Show()

# remove dealt cards from deck
$deck | Update-List -Property cards -Remove $deck.cards[0..1] | Out-Null
$deck.Show()
```

```Output
Player 1 :  J♦ A♣ J♣ 9♦ 6♣

Deck :  2♣ K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣ Q♣ A♥
        Q♠ 3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠ 4♣ 2♠
        2♥ 6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣ A♦ K♣
        8♥
```

## PARAMETRAR

### -Lägg till

Anger de egenskaps värden som ska läggas till i samlingen. Ange värdena i den ordning som de ska visas i samlingen.

```yaml
Type: System.Object[]
Parameter Sets: AddRemoveSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger de objekt som ska uppdateras. Du kan också skicka objektet som ska uppdateras till `Update-List` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Egenskap

Anger den egenskap som innehåller den samling som uppdateras. Om du utelämnar den här parametern `Update-List` returneras ett objekt som representerar ändringen i stället för att ändra objektet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Remove

Anger de egenskaps värden som ska tas bort från samlingen.

```yaml
Type: System.Object[]
Parameter Sets: AddRemoveSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ersätt

Anger en ny samling. Den här parametern ersätter alla objekt i den ursprungliga samlingen med de objekt som anges av den här parametern.

```yaml
Type: System.Object[]
Parameter Sets: ReplaceSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka vidare de objekt som ska uppdateras till `Update-List` .

## UTDATA

### Objekt eller system. Management. Automation. PSListModifier

`Update-List` Returnerar det uppdaterade objektet, eller returnerar ett objekt som representerar uppdaterings åtgärden.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Format-List](Format-List.md)

[Select-Object](Select-Object.md)
