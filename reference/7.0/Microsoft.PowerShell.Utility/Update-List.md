---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-list?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-List
ms.openlocfilehash: 00ada05f52967c0857cfad63a94cd23c49b69367
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262485"
---
# <span data-ttu-id="94d6e-103">Update-List</span><span class="sxs-lookup"><span data-stu-id="94d6e-103">Update-List</span></span>

## <span data-ttu-id="94d6e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="94d6e-104">SYNOPSIS</span></span>
<span data-ttu-id="94d6e-105">Lägger till objekt i och tar bort objekt från ett egenskaps värde som innehåller en objekt samling.</span><span class="sxs-lookup"><span data-stu-id="94d6e-105">Adds items to and removes items from a property value that contains a collection of objects.</span></span>

## <span data-ttu-id="94d6e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="94d6e-106">SYNTAX</span></span>

### <span data-ttu-id="94d6e-107">AddRemoveSet (standard)</span><span class="sxs-lookup"><span data-stu-id="94d6e-107">AddRemoveSet (Default)</span></span>

```
Update-List [-Add <Object[]>] [-Remove <Object[]>] [-InputObject <PSObject>] [[-Property] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="94d6e-108">ReplaceSet</span><span class="sxs-lookup"><span data-stu-id="94d6e-108">ReplaceSet</span></span>

```
Update-List -Replace <Object[]> [-InputObject <PSObject>] [[-Property] <String>] [<CommonParameters>]
```

## <span data-ttu-id="94d6e-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="94d6e-109">DESCRIPTION</span></span>

<span data-ttu-id="94d6e-110">`Update-List`Cmdleten lägger till, tar bort eller ersätter objekt i ett egenskaps värde för ett objekt och returnerar det uppdaterade objektet.</span><span class="sxs-lookup"><span data-stu-id="94d6e-110">The `Update-List` cmdlet adds, removes, or replaces items in a property value of an object and returns the updated object.</span></span> <span data-ttu-id="94d6e-111">Denna cmdlet är utformad för egenskaper som innehåller objekt samlingar.</span><span class="sxs-lookup"><span data-stu-id="94d6e-111">This cmdlet is designed for properties that contain collections of objects.</span></span>

<span data-ttu-id="94d6e-112">Parametrarna **Lägg till** och **ta bort** lägger till enskilda objekt i och tar bort dem från samlingen.</span><span class="sxs-lookup"><span data-stu-id="94d6e-112">The **Add** and **Remove** parameters add individual items to and remove them from the collection.</span></span>
<span data-ttu-id="94d6e-113">**Ersättnings** parametern ersätter hela samlingen.</span><span class="sxs-lookup"><span data-stu-id="94d6e-113">The **Replace** parameter replaces the entire collection.</span></span>

<span data-ttu-id="94d6e-114">Om du inte anger någon egenskap i kommandot `Update-List` returneras ett objekt som beskriver uppdateringen i stället för att uppdatera objektet.</span><span class="sxs-lookup"><span data-stu-id="94d6e-114">If you do not specify a property in the command, `Update-List` returns an object that describes the update instead of updating the object.</span></span> <span data-ttu-id="94d6e-115">Du kan skicka objektet Update till-cmdletar som ändrar objekt, till exempel `Set` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="94d6e-115">You can submit the update object to cmdlets that change objects, such as `Set` cmdlets.</span></span>

<span data-ttu-id="94d6e-116">Den här cmdleten fungerar bara när den egenskap som uppdateras stöder **ilist** -gränssnittet som `Update-List` använder.</span><span class="sxs-lookup"><span data-stu-id="94d6e-116">This cmdlet works only when the property that is being updated supports the **IList** interface that `Update-List` uses.</span></span> <span data-ttu-id="94d6e-117">Dessutom måste alla `Set` cmdletar som accepterar en uppdatering ha stöd för **ilist** -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="94d6e-117">Also, any `Set` cmdlets that accept an update must support the **IList** interface.</span></span>

<span data-ttu-id="94d6e-118">De grundläggande cmdletarna som installeras med PowerShell stöder inte det här gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="94d6e-118">The core cmdlets that are installed with PowerShell do not support this interface.</span></span> <span data-ttu-id="94d6e-119">Information om hur en cmdlet stöder `Update-List` finns i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="94d6e-119">To determine whether a cmdlet supports `Update-List`, see the cmdlet Help topic.</span></span>

<span data-ttu-id="94d6e-120">Den här cmdleten introducerades om i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="94d6e-120">This cmdlet was reintroduced in PowerShell 7.</span></span>

## <span data-ttu-id="94d6e-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="94d6e-121">EXAMPLES</span></span>

### <span data-ttu-id="94d6e-122">Exempel 1: Lägg till objekt i ett egenskaps värde</span><span class="sxs-lookup"><span data-stu-id="94d6e-122">Example 1: Add items to a property value</span></span>

<span data-ttu-id="94d6e-123">I det här exemplet skapar vi en klass som representerar en kortlek med kort där korten lagras som ett **list** samlings objekt.</span><span class="sxs-lookup"><span data-stu-id="94d6e-123">In this example we create a class that represents a deck of cards where the cards are stored as a **List** collection object.</span></span> <span data-ttu-id="94d6e-124">Metoden **NewDeck ()** använder `Update-List` för att lägga till en fullständig kortlek med kort värden i **kort** samlingen.</span><span class="sxs-lookup"><span data-stu-id="94d6e-124">The **NewDeck()** method uses `Update-List`to add a complete deck of card values to the **cards** collection.</span></span>

```powershell
class Cards {

    [System.Collections.Generic.List[string]]$cards
    [string]$name

    Cards([string]$_name) {
        $this.name = $_name
        $this.cards = [System.Collections.Generic.List[string]]::new()
    }

    NewDeck() {
        $_suits = "`u{2663}","`u{2666}","`u{2665}","`u{2660}"
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
> <span data-ttu-id="94d6e-125">`Update-List`Cmdleten matar ut det uppdaterade objektet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="94d6e-125">The `Update-List` cmdlet outputs the updated object to the pipeline.</span></span> <span data-ttu-id="94d6e-126">Vi rör utdata för `Out-Null` att förhindra den oönskade visningen.</span><span class="sxs-lookup"><span data-stu-id="94d6e-126">We pipe the output to `Out-Null` to suppress the unwanted display.</span></span>

### <span data-ttu-id="94d6e-127">Exempel 2: lägga till och ta bort objekt i en samlings egenskap</span><span class="sxs-lookup"><span data-stu-id="94d6e-127">Example 2: Add and remove items of a collection property</span></span>

<span data-ttu-id="94d6e-128">Om du fortsätter med koden i exempel 1 kommer vi att skapa instanser av **kort** klassen som representerar kort lekar och kort som innehas av två spelare.</span><span class="sxs-lookup"><span data-stu-id="94d6e-128">Continuing with the code in Example 1, we will create instances of the **Cards** class to represent a deck of cards and the cards held by two players.</span></span> <span data-ttu-id="94d6e-129">Vi använder `Update-List` cmdleten för att lägga till kort i spelarens händer och ta bort kort från däcket.</span><span class="sxs-lookup"><span data-stu-id="94d6e-129">We use the `Update-List` cmdlet to add cards to the players' hands and to remove cards from the deck.</span></span>

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

<span data-ttu-id="94d6e-130">Utmatningen visar kortets tillstånd innan korten behandlades för spelarna.</span><span class="sxs-lookup"><span data-stu-id="94d6e-130">The output shows the state of the deck before the cards were dealt to the players.</span></span> <span data-ttu-id="94d6e-131">Du kan se att varje spelare fick fem kort från däcket.</span><span class="sxs-lookup"><span data-stu-id="94d6e-131">You can see that each player received five cards from the deck.</span></span> <span data-ttu-id="94d6e-132">Den slutliga utmatningen visar kortets tillstånd efter att korten har behandlats till spelarna.</span><span class="sxs-lookup"><span data-stu-id="94d6e-132">The final output shows the state of the deck after dealing the cards to the players.</span></span> <span data-ttu-id="94d6e-133">`Update-List` användes för att välja korten från däcket och lägga till dem i spelarens samling.</span><span class="sxs-lookup"><span data-stu-id="94d6e-133">`Update-List` was used to select the cards from the deck and add them to the players' collection.</span></span> <span data-ttu-id="94d6e-134">Sedan togs spelarnas kort bort från däcket med hjälp av `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="94d6e-134">Then the players' cards were removed from the deck using `Update-List`.</span></span>

### <span data-ttu-id="94d6e-135">Exempel 3: lägga till och ta bort objekt i ett enda kommando</span><span class="sxs-lookup"><span data-stu-id="94d6e-135">Example 3: Add and remove items in a single command</span></span>

<span data-ttu-id="94d6e-136">`Update-List` gör att du kan använda parametrarna **Add** och **Remove** i ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="94d6e-136">`Update-List` allows you to use the **Add** and **Remove** parameters in a single command.</span></span> <span data-ttu-id="94d6e-137">I det här exemplet vill spelaren 1 ta bort `4♦` och `6♦` få två nya kort.</span><span class="sxs-lookup"><span data-stu-id="94d6e-137">In this example, Player 1 wants to discard the `4♦` and `6♦` and get two new cards.</span></span>

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

## <span data-ttu-id="94d6e-138">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="94d6e-138">PARAMETERS</span></span>

### <span data-ttu-id="94d6e-139">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="94d6e-139">-Add</span></span>

<span data-ttu-id="94d6e-140">Anger de egenskaps värden som ska läggas till i samlingen.</span><span class="sxs-lookup"><span data-stu-id="94d6e-140">Specifies the property values to be added to the collection.</span></span> <span data-ttu-id="94d6e-141">Ange värdena i den ordning som de ska visas i samlingen.</span><span class="sxs-lookup"><span data-stu-id="94d6e-141">Enter the values in the order that they should appear in the collection.</span></span>

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

### <span data-ttu-id="94d6e-142">– InputObject</span><span class="sxs-lookup"><span data-stu-id="94d6e-142">-InputObject</span></span>

<span data-ttu-id="94d6e-143">Anger de objekt som ska uppdateras.</span><span class="sxs-lookup"><span data-stu-id="94d6e-143">Specifies the objects to be updated.</span></span> <span data-ttu-id="94d6e-144">Du kan också skicka objektet som ska uppdateras till `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="94d6e-144">You can also pipe the object to be updated to `Update-List`.</span></span>

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

### <span data-ttu-id="94d6e-145">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="94d6e-145">-Property</span></span>

<span data-ttu-id="94d6e-146">Anger den egenskap som innehåller den samling som uppdateras.</span><span class="sxs-lookup"><span data-stu-id="94d6e-146">Specifies the property that contains the collection that is being updated.</span></span> <span data-ttu-id="94d6e-147">Om du utelämnar den här parametern `Update-List` returneras ett objekt som representerar ändringen i stället för att ändra objektet.</span><span class="sxs-lookup"><span data-stu-id="94d6e-147">If you omit this parameter, `Update-List` returns an object that represents the change instead of changing the object.</span></span>

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

### <span data-ttu-id="94d6e-148">-Remove</span><span class="sxs-lookup"><span data-stu-id="94d6e-148">-Remove</span></span>

<span data-ttu-id="94d6e-149">Anger de egenskaps värden som ska tas bort från samlingen.</span><span class="sxs-lookup"><span data-stu-id="94d6e-149">Specifies the property values to be removed from the collection.</span></span>

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

### <span data-ttu-id="94d6e-150">-Ersätt</span><span class="sxs-lookup"><span data-stu-id="94d6e-150">-Replace</span></span>

<span data-ttu-id="94d6e-151">Anger en ny samling.</span><span class="sxs-lookup"><span data-stu-id="94d6e-151">Specifies a new collection.</span></span> <span data-ttu-id="94d6e-152">Den här parametern ersätter alla objekt i den ursprungliga samlingen med de objekt som anges av den här parametern.</span><span class="sxs-lookup"><span data-stu-id="94d6e-152">This parameter replaces all items in the original collection with the items specified by this parameter.</span></span>

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

### <span data-ttu-id="94d6e-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="94d6e-153">CommonParameters</span></span>

<span data-ttu-id="94d6e-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="94d6e-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="94d6e-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="94d6e-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="94d6e-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="94d6e-156">INPUTS</span></span>

### <span data-ttu-id="94d6e-157">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="94d6e-157">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="94d6e-158">Du kan skicka vidare de objekt som ska uppdateras till `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="94d6e-158">You can pipe the objects to be updated to `Update-List`.</span></span>

## <span data-ttu-id="94d6e-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="94d6e-159">OUTPUTS</span></span>

### <span data-ttu-id="94d6e-160">Objekt eller system. Management. Automation. PSListModifier</span><span class="sxs-lookup"><span data-stu-id="94d6e-160">Objects or System.Management.Automation.PSListModifier</span></span>

<span data-ttu-id="94d6e-161">`Update-List` Returnerar det uppdaterade objektet, eller returnerar ett objekt som representerar uppdaterings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="94d6e-161">`Update-List` returns the updated object, or it returns an object that represents the update action.</span></span>

## <span data-ttu-id="94d6e-162">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="94d6e-162">NOTES</span></span>

## <span data-ttu-id="94d6e-163">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="94d6e-163">RELATED LINKS</span></span>

[<span data-ttu-id="94d6e-164">Format-List</span><span class="sxs-lookup"><span data-stu-id="94d6e-164">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="94d6e-165">Select-Object</span><span class="sxs-lookup"><span data-stu-id="94d6e-165">Select-Object</span></span>](Select-Object.md)
