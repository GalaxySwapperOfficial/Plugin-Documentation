# Creating Your Base Backpack Plugin
To begin, create the base of your plugin file by specifying the type, itemName, itemDefinition, overrideItemDefinition as shown below:

```json
{
    "type": "backpack",
    "itemName": "Pea Buddies to Black Shield",
    "itemDefinition": "Backpack_SpeedyPeas",
    "overrideItemDefinition": "BID_004_BlackKnight"
}
```

- Key explanation
    - 'type' Signifies to the swapper that the plugin format is for 'backpack'.
    - 'itemName' This will be the name that is displayed within the swapper for your plugin file.
    - 'itemDefinition' This is the BID for the backpack you are swapping from. It is not required, but when specified the swapper will automatically load the backpack icon from the item definition.
    - 'overrideItemDefinition' This is the BID for the backpack you are swapping to. It is not required, but when specified the swapper will automatically load the backpack icon from the item definition.

# Creating Your Plugin Icon
Having a plugin icon is very important as it displays a preview of the backpack you are swapping to. To get started, begin by adding a JSON key 'icon' for the backpack you are swapping from and add the JSON key 'overrideIcon' for the backpack you are swapping to as shown below:
- Note: This is not required if you specified 'itemDefinition' or 'overrideItemDefinition' as the icon will be loaded from that.
```json
{
    "type": "backpack",
    "itemName": "Pea Buddies to Black Shield",
    "itemDefinition": "Backpack_SpeedyPeas",
    "overrideItemDefinition": "BID_004_BlackKnight",
    "icon": "https://fortnite-api.com/images/cosmetics/br/Backpack_SpeedyPeas/icon.png",
    "overrideIcon": "https://fortnite-api.com/images/cosmetics/br/BID_004_BlackKnight/icon.png"
}
```

- Key explanation
    - 'icon' This will be the URL for the backpack you are swapping from.
    - 'overrideIcon' This will be the URL for the backpack you are swapping to.

# Finding ItemDefinition
In order to find the ItemDefinition for your backpack, you can use a website called [Fortnite.gg](https://fortnite.gg/cosmetics?game=br&type=backpack). Locate the backpack you are swapping to using the search bar and click on the backpack. In the popup at the bottom right, you will see the 'ID' which will be our ItemDefinition."
  
  
![ItemDefinition Preview](/Images/OutfitItemDefinition.png)

# Finding CharacterParts
In order to find the CharacterParts for your backpack, we will use FModel. If you are not familiar with FModel, please refer to their [documtation](https://github.com/4sval/FModel/wiki/Getting-Started). To get started, locate 'Packages' and click 'Search'.
  

![FModel Search Preview](/Images/FModelSearch.png)

Paste your 'ItemDefinition' into the search bar and press enter on the keyboard. In the search results, you may encounter two results: one will be the ID asset we are looking for, and the other will be a DisplayAsset. Make sure to select the path that does not include 'DisplayAssets'.
  
  
![FModel Results Preview](/Images/FModelOutfitItemDefinitionResults.png)

Once you have located the correct asset, right-click on it and select 'Extract in new tab'.
  
  
![FModel Results Preview](/Images/FModelExtractAsset.png)

In the JSON preview section of FModel, you should see the 'CharacterParts' array. These will be your 'CharacterParts' for the plugin.
  
  
![FModel Results Preview](/Images/BackpackCharacterParts.png)

# Finding ItemDefinition Path
In order to find the CharacterParts for your backpack, we will use FModel. If you are not familiar with FModel, please refer to their [documtation](https://github.com/4sval/FModel/wiki/Getting-Started). To get started, locate 'Packages' and click 'Search'.
  

![FModel Search Preview](/Images/FModelSearch.png)

Paste your 'ItemDefinition' into the search bar and press enter on the keyboard. In the search results, you may encounter two results: one will be the ID asset we are looking for, and the other will be a DisplayAsset. Make sure to select the path that does not include 'DisplayAssets'.
  
  
![FModel Results Preview](/Images/FModelOutfitItemDefinitionResults.png)

Once you have located the correct asset, right-click on it and select 'Extract in new tab'.
  
  
![FModel Results Preview](/Images/FModelExtractAsset.png)

Above the JSON preview section of FModel, you should see your ItemDefinition in the tabs section. Right-click the tab and select 'Copy Package Path'.
  
  
![FModel Results Preview](/Images/FModelBackpackCopyPackagePath.png)


# Adding CharacterParts
In order for the swapper to know which CharacterPart to swap to, we need to add a 'customCharacterBackpackDatas' array containing the CharacterParts found in the itemDefinition and the itemDefinition path from the backpack we are swapping from.
```json
{
    "type": "backpack",
    "itemName": "Pea Buddies to Black Shield",
    "itemDefinition": "Backpack_SpeedyPeas",
    "overrideItemDefinition": "BID_004_BlackKnight",
    "customCharacterBackpackDatas": [
        {
            "athenaBackpackItemDefinition": {
                "objectPath": "/BRCosmetics/Athena/Items/Cosmetics/Backpacks/Backpack_SpeedyPeas"
            },
            "objectPath": "/BRCosmetics/Characters/CharacterParts/Backpacks/Male_Commando_BlackKnight"
        }
    ]
}
```
- Key explanation
    - 'athenaBackpackItemDefinition' This will be the 'ItemDefinition Path' from the backbling we are swapping from.
    - 'objectPath' This will be the asset path to the CharacterPart we are swapping to.

# Final Result
The final product should look something like this:
```json
{
    "type": "backpack",
    "itemName": "Pea Buddies to Black Shield",
    "itemDefinition": "Backpack_SpeedyPeas",
    "overrideItemDefinition": "BID_004_BlackKnight",
    "customCharacterBackpackDatas": [
        {
            "athenaBackpackItemDefinition": {
                "objectPath": "/BRCosmetics/Athena/Items/Cosmetics/Backpacks/Backpack_SpeedyPeas"
            },
            "objectPath": "/BRCosmetics/Characters/CharacterParts/Backpacks/Male_Commando_BlackKnight"
        }
    ]
}
```

# Additonal Features
These features are used to modify object paths within the character part you are swapping to. If you are a beginner or are not planning to modify any object paths within the character part, then this section is not for you.

# Modify SkeletalMesh
```json
{
    "type": "backpack",
    "itemName": "Pea Buddies to Black Shield",
    "itemDefinition": "Backpack_SpeedyPeas",
    "overrideItemDefinition": "BID_004_BlackKnight",
    "customCharacterBackpackDatas": [
        {
            "athenaBackpackItemDefinition": {
                "objectPath": "/BRCosmetics/Athena/Items/Cosmetics/Backpacks/Backpack_SpeedyPeas"
            },
            "objectPath": "/BRCosmetics/Characters/CharacterParts/Backpacks/Male_Commando_BlackKnight",
            "skeletalMesh": {
                "objectPath": "/BRCosmetics/Accessories/FORT_Backpacks/Backpack_F_MED_BrightIon/Meshes/F_MED_BrightIon_Pack.F_MED_BrightIon_Pack"
            }
        }
    ]
}
```
- Key explanation
    - 'skeletalMesh' This will be the object path to the skeletal mesh you want to override to.

# Modify AnimClass
```json
{
    "type": "backpack",
    "itemName": "Pea Buddies to Black Shield",
    "itemDefinition": "Backpack_SpeedyPeas",
    "overrideItemDefinition": "BID_004_BlackKnight",
    "customCharacterBackpackDatas": [
        {
            "athenaBackpackItemDefinition": {
                "objectPath": "/BRCosmetics/Athena/Items/Cosmetics/Backpacks/Backpack_SpeedyPeas"
            },
            "objectPath": "/BRCosmetics/Characters/CharacterParts/Backpacks/Male_Commando_BlackKnight",
            "animClass": {
                "objectPath": "/BRCosmetics/Accessories/FORT_Backpacks/Backpack_F_MED_BrightIon/Meshes/F_MED_BrightIon_Pack_AnimBP.F_MED_BrightIon_Pack_AnimBP_C"
            }
        }
    ]
}
```
- Key explanation
    - 'animClass' This will be the object path to the animClass you want to override to.

# Modify MaterialOverrides
```json
{
    "type": "backpack",
    "itemName": "Pea Buddies to Black Shield",
    "itemDefinition": "Backpack_SpeedyPeas",
    "overrideItemDefinition": "BID_004_BlackKnight",
    "customCharacterBackpackDatas": [
        {
            "athenaBackpackItemDefinition": {
                "objectPath": "/BRCosmetics/Athena/Items/Cosmetics/Backpacks/Backpack_SpeedyPeas"
            },
            "objectPath": "/BRCosmetics/Characters/CharacterParts/Backpacks/Male_Commando_BlackKnight",
            "materialOverrides": [
                {
                    "overrideMaterial": {
                        "objectPath": "/BRCosmetics/Accessories/FORT_Backpacks/Backpack_F_MED_Celestial/Materials/F_MED_Celestial_Backpack.F_MED_Celestial_Backpack"
                    },
                    "materialOverrideIndex": 0
                }
            ]
        }
    ]
}
```
- Key explanation
    - 'overrideMaterial' This will be the object path to the material you want to override to.
    - 'materialOverrideIndex' This will be the index that the material is applied to.

# Modify IdleEffect
```json
{
    "type": "backpack",
    "itemName": "Pea Buddies to Black Shield",
    "itemDefinition": "Backpack_SpeedyPeas",
    "overrideItemDefinition": "BID_004_BlackKnight",
    "customCharacterBackpackDatas": [
        {
            "athenaBackpackItemDefinition": {
                "objectPath": "/BRCosmetics/Athena/Items/Cosmetics/Backpacks/Backpack_SpeedyPeas"
            },
            "objectPath": "/BRCosmetics/Characters/CharacterParts/Backpacks/Male_Commando_BlackKnight",
            "idleEffect": {
                "objectPath": "/BRCosmetics/Accessories/FORT_Backpacks/M_MED_Wild_Card_Cube_Backpack/FX/P_WildCard_Cube_Backpack.P_WildCard_Cube_Backpack"
            }
        }
    ]
}
```
- Key explanation
    - 'idleEffect' This will be the object path to the idleEffect you want to override to.

# Modify IdleEffectNiagara
```json
{
    "type": "backpack",
    "itemName": "Pea Buddies to Black Shield",
    "itemDefinition": "Backpack_SpeedyPeas",
    "overrideItemDefinition": "BID_004_BlackKnight",
    "customCharacterBackpackDatas": [
        {
            "athenaBackpackItemDefinition": {
                "objectPath": "/BRCosmetics/Athena/Items/Cosmetics/Backpacks/Backpack_SpeedyPeas"
            },
            "objectPath": "/BRCosmetics/Characters/CharacterParts/Backpacks/Male_Commando_BlackKnight",
            "idleEffectNiagara": {
                "objectPath": "/BRCosmetics/Accessories/FORT_Backpacks/Backpack_M_MED_Carabus/FX/NS_Carabus_Hologram.NS_Carabus_Hologram"
            }
        }
    ]
}
```
- Key explanation
    - 'idleEffectNiagara' This will be the object path to the idleEffectNiagara you want to override to.

# Modify IdleFXSocketName
```json
{
    "type": "backpack",
    "itemName": "Pea Buddies to Black Shield",
    "itemDefinition": "Backpack_SpeedyPeas",
    "overrideItemDefinition": "BID_004_BlackKnight",
    "customCharacterBackpackDatas": [
        {
            "athenaBackpackItemDefinition": {
                "objectPath": "/BRCosmetics/Athena/Items/Cosmetics/Backpacks/Backpack_SpeedyPeas"
            },
            "objectPath": "/BRCosmetics/Characters/CharacterParts/Backpacks/Male_Commando_BlackKnight",
            "idleFXSocketName": "pack"
        }
    ]
}
```
- Key explanation
    - 'idleFXSocketName' This will be the socket you want the idle effect to be attached to.

# Modify PartModifierBlueprint
```json
{
    "type": "backpack",
    "itemName": "Pea Buddies to Black Shield",
    "itemDefinition": "Backpack_SpeedyPeas",
    "overrideItemDefinition": "BID_004_BlackKnight",
    "customCharacterBackpackDatas": [
        {
            "athenaBackpackItemDefinition": {
                "objectPath": "/BRCosmetics/Athena/Items/Cosmetics/Backpacks/Backpack_SpeedyPeas"
            },
            "objectPath": "/BRCosmetics/Characters/CharacterParts/Backpacks/Male_Commando_BlackKnight",
            "partModifierBlueprint": {
                "objectPath": "/BRCosmetics/Athena/Cosmetics/Blueprints/Part_Modifiers/B_Athena_PartModifier_Carabus_Backpack.B_Athena_PartModifier_Carabus_Backpack_C"
            }
        }
    ]
}
```
- Key explanation
    - 'partModifierBlueprint' This will be the object path to the partModifierBlueprint you want to override to.