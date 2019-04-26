---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Med hjälp av konfigurationsdata
ms.openlocfilehash: f2d25b9ced805fb4c91378ebfe840104eb6ce52a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080228"
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="62b2a-103">Med hjälp av konfigurationsdata i DSC</span><span class="sxs-lookup"><span data-stu-id="62b2a-103">Using configuration data in DSC</span></span>

> <span data-ttu-id="62b2a-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="62b2a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="62b2a-105">Med hjälp av inbyggda DSC **ConfigurationData** parameter, kan du definiera data som kan användas i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="62b2a-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="62b2a-106">På så sätt kan du skapa en enda konfiguration som kan användas för flera noder eller för olika miljöer.</span><span class="sxs-lookup"><span data-stu-id="62b2a-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="62b2a-107">Exempelvis om du utvecklar ett program, kan du använda en konfiguration för utvecklings-och produktionsmiljöer och Använd konfigurationsdata för att ange data för varje miljö.</span><span class="sxs-lookup"><span data-stu-id="62b2a-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="62b2a-108">Det här avsnittet beskriver strukturen för de **ConfigurationData** hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="62b2a-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="62b2a-109">Exempel på hur du använder konfigurationsdata finns [att avgränsa konfigurations- och miljödata](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="62b2a-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="62b2a-110">Parametern ConfigurationData vanliga</span><span class="sxs-lookup"><span data-stu-id="62b2a-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="62b2a-111">En DSC-konfiguration tar en parameter för vanliga **ConfigurationData**, som du anger när du kompilera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="62b2a-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="62b2a-112">Läs om hur kompilera konfigurationer [DSC-konfigurationer](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="62b2a-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="62b2a-113">Den **ConfigurationData** parametern är en hash-tabell som måste ha minst en nyckel med namnet **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="62b2a-113">The **ConfigurationData** parameter is a hashtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="62b2a-114">Det kan också ha en eller flera nycklar.</span><span class="sxs-lookup"><span data-stu-id="62b2a-114">It can also have one or more other keys.</span></span>

> [!NOTE]
> <span data-ttu-id="62b2a-115">Exemplen i det här avsnittet använder en enda ytterligare nyckel (förutom de namngivna **AllNodes** nyckel) med namnet `NonNodeData`, men du kan innehålla valfritt antal ytterligare nycklar och kalla dem vad som helst.</span><span class="sxs-lookup"><span data-stu-id="62b2a-115">The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="62b2a-116">Värdet för den **AllNodes** nyckel är en matris.</span><span class="sxs-lookup"><span data-stu-id="62b2a-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="62b2a-117">Varje element i den här matrisen är också en hash-tabell som måste ha minst en nyckel med namnet **nodnamn**:</span><span class="sxs-lookup"><span data-stu-id="62b2a-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="62b2a-118">Du kan lägga till andra nycklar till varje hash-tabell:</span><span class="sxs-lookup"><span data-stu-id="62b2a-118">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="62b2a-119">Om du vill använda en egenskap för alla noder, du kan skapa en medlem i den **AllNodes** matris som har en **nodnamn** av `*`.</span><span class="sxs-lookup"><span data-stu-id="62b2a-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="62b2a-120">Till exempel för att ge varje nod en `LogPath` egenskapen, kan du göra detta:</span><span class="sxs-lookup"><span data-stu-id="62b2a-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="62b2a-121">Det här är detsamma som att lägga till en egenskap med namnet `LogPath` med värdet `"C:\Logs"` till var och en av de andra blocken (`VM-1`, `VM-2`, och `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="62b2a-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="62b2a-122">Definiera ConfigurationData hash-tabell</span><span class="sxs-lookup"><span data-stu-id="62b2a-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="62b2a-123">Du kan definiera **ConfigurationData** antingen som en variabel i samma skriptfilen som en konfiguration (som i vårt tidigare exempel) eller i en separat `.psd1` fil.</span><span class="sxs-lookup"><span data-stu-id="62b2a-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="62b2a-124">Definiera **ConfigurationData** i en `.psd1` fil, skapa en fil som innehåller bara den hash-tabell som representerar konfigurationsdata.</span><span class="sxs-lookup"><span data-stu-id="62b2a-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="62b2a-125">Du kan till exempel skapa en fil med namnet `MyData.psd1` med följande innehåll:</span><span class="sxs-lookup"><span data-stu-id="62b2a-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="62b2a-126">Kompilera en konfiguration med konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="62b2a-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="62b2a-127">För att kompilera en konfiguration som du har definierat konfigurationsdata, skicka konfigurationsdata som värdet för den **ConfigurationData** parametern.</span><span class="sxs-lookup"><span data-stu-id="62b2a-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="62b2a-128">Detta skapar en MOF-fil för varje post i den **AllNodes** matris.</span><span class="sxs-lookup"><span data-stu-id="62b2a-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="62b2a-129">Varje MOF-fil kommer att namnges med den `NodeName` egenskapen för motsvarande Matrisposten.</span><span class="sxs-lookup"><span data-stu-id="62b2a-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="62b2a-130">Exempel: Om du definierar konfigurationsdata som i den `MyData.psd1` filen ovan, kompilera en konfiguration skulle skapa dessa `VM-1.mof` och `VM-2.mof` filer.</span><span class="sxs-lookup"><span data-stu-id="62b2a-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="62b2a-131">Kompilera en konfiguration med konfigurationsdata med hjälp av en variabel</span><span class="sxs-lookup"><span data-stu-id="62b2a-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="62b2a-132">Att använda konfigurationsdata som har definierats som en variabel i samma `.ps1` filen som konfigurationen du skickar variabelnamnet som värde för den **ConfigurationData** parameter när kompilera konfigurationen:</span><span class="sxs-lookup"><span data-stu-id="62b2a-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="62b2a-133">Kompilera en konfiguration med konfigurationsdata med hjälp av en datafil</span><span class="sxs-lookup"><span data-stu-id="62b2a-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="62b2a-134">För att använda konfigurationsdata som har definierats i en .psd1-fil måste du skicka sökvägen och namnet på filen som värde för den **ConfigurationData** parameter när kompilera konfigurationen:</span><span class="sxs-lookup"><span data-stu-id="62b2a-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="62b2a-135">Använda ConfigurationData variabler i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="62b2a-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="62b2a-136">DSC tillhandahåller följande särskilda variabler som kan användas i ett konfigurationsskript:</span><span class="sxs-lookup"><span data-stu-id="62b2a-136">DSC provides the following special variables that can be used in a configuration script:</span></span>

- <span data-ttu-id="62b2a-137">**$AllNodes** refererar till hela uppsättningen av noder som definierats i **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="62b2a-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="62b2a-138">Du kan filtrera den **AllNodes** samlingen med hjälp av **. WHERE ()** och **. ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="62b2a-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="62b2a-139">**ConfigurationData** refererar till hela hash-tabellen som skickas som parametern när kompilera en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="62b2a-139">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>
- <span data-ttu-id="62b2a-140">**MyTypeName** innehåller den [configuration](configurations.md) variabeln används i namnet.</span><span class="sxs-lookup"><span data-stu-id="62b2a-140">**MyTypeName** contains the [configuration](configurations.md) name the variable is used in.</span></span> <span data-ttu-id="62b2a-141">Till exempel i konfigurationen `MyDscConfiguration`, `$MyTypeName` har värdet `MyDscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="62b2a-141">For example, in the configuration `MyDscConfiguration`, the `$MyTypeName` will have a value of `MyDscConfiguration`.</span></span>
- <span data-ttu-id="62b2a-142">**Noden** refererar till en viss post i den **AllNodes** samling när den har filtrerats med hjälp av **. WHERE ()** eller **. ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="62b2a-142">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
  - <span data-ttu-id="62b2a-143">Du kan läsa mer om de här metoderna i [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="62b2a-143">You can read more about these methods in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="62b2a-144">Använda icke-nod-data</span><span class="sxs-lookup"><span data-stu-id="62b2a-144">Using non-node data</span></span>

<span data-ttu-id="62b2a-145">Som vi har sett i föregående exempel kan den **ConfigurationData** hash-tabell kan ha en eller flera nycklar utöver de nödvändiga **AllNodes** nyckel.</span><span class="sxs-lookup"><span data-stu-id="62b2a-145">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="62b2a-146">I exemplen i det här avsnittet har vi används endast en extra nod och namnet `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="62b2a-146">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="62b2a-147">Du kan dock ange valfritt antal ytterligare nycklar och kalla dem vad du vill.</span><span class="sxs-lookup"><span data-stu-id="62b2a-147">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="62b2a-148">Ett exempel på hur du använder icke-noddatat finns i [att avgränsa konfigurations- och miljödata](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="62b2a-148">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62b2a-149">Se även</span><span class="sxs-lookup"><span data-stu-id="62b2a-149">See Also</span></span>

- [<span data-ttu-id="62b2a-150">Alternativ för autentiseringsuppgifter i konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="62b2a-150">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="62b2a-151">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="62b2a-151">DSC Configurations</span></span>](configurations.md)