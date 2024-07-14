# Creating Your Base Outfit Plugin
To begin, create the base of your plugin file by specifying the type, itemName, itemDefinition as shown below:

```json
{
    "type": "outfit",
    "itemName": "Renegade Raider",
    "itemDefinition": "CID_028_Athena_Commando_F"
}
```

- Key explanation
    - 'type' Signifies to the swapper that the plugin format is for 'outfit'.
    - 'itemName' This will be the name that is displayed within the swapper for your plugin file.
    - 'itemDefinition' This is the CID for the outfit. It is not required, but when specified the swapper will automatically load the outfit icon from the item definition.

# Creating Your Plugin Icon
Having a plugin icon is very important as it displays a preview of the outfit you are swapping to. To get started, begin by adding a JSON key 'icon' as shown below:
- Note: This is not required if you specified an 'itemDefinition,' as the icon will be loaded from that.
```json
{
    "type": "outfit",
    "itemName": "Renegade Raider",
    "itemDefinition": "CID_028_Athena_Commando_F",
    "icon": "https://fortnite-api.com/images/cosmetics/br/cid_028_athena_commando_f/icon.png"
}
```

- Key explanation
    - 'icon' This will be the URL from which the icon for your outfit plugin will be loaded.

# Finding ItemDefinition
In order to find the ItemDefinition for your outfit, you can use a website called [Fortnite.gg](https://fortnite.gg/cosmetics?game=br&type=outfit). Locate the outfit you are swapping to using the search bar and click on the outfit. In the popup at the bottom right, you will see the 'ID' which will be our ItemDefinition."
  
  
![ItemDefinition Preview](/Images/OutfitItemDefinition.png)

# Finding CharacterParts
In order to find the CharacterParts for your outfit, we will use FModel. If you are not familiar with FModel, please refer to their [documtation](https://github.com/4sval/FModel/wiki/Getting-Started). To get started, locate 'Packages' and click 'Search'.
  

![FModel Search Preview](/Images/FModelSearch.png)

Paste your 'ItemDefinition' into the search bar and press enter on the keyboard. In the search results, you may encounter two results: one will be the ID asset we are looking for, and the other will be a DisplayAsset. Make sure to select the path that does not include 'DisplayAssets'.
  
  
![FModel Results Preview](/Images/FModelOutfitItemDefinitionResults.png)

Once you have located the correct asset, right-click on it and select 'Extract in new tab'.
  
  
![FModel Results Preview](/Images/FModelExtractAsset.png)

In the JSON preview section of FModel, you should see the 'BaseCharacterParts' array. These will be your 'CharacterParts'.
  
  
![FModel Results Preview](/Images/OutfitCharacterParts.png)

# Adding CharacterParts
In order for the swapper to know which CharacterPart to swap to, we need to add a 'characterParts' array containing the CharacterParts found in the itemDefinition, as shown below:
```json
{
    "type": "outfit",
    "itemName": "Renegade Raider",
    "itemDefinition": "CID_028_Athena_Commando_F",
    "characterParts": [
        {
            "objectPath": "/BRCosmetics/Athena/Heroes/Meshes/Bodies/CP_028_Athena_Body",
            "swaps": []
        },
        {
            "objectPath": "/BRCosmetics/Athena/Heroes/Meshes/Heads/F_MED_ASN_Sarah_Head_02_ATH",
            "swaps": []
        },
        {
            "objectPath": "/BRCosmetics/Characters/CharacterParts/Hats/Hat_F_Commando_08_V01",
            "swaps": []
        }
    ]
}
```
- Key explanation
    - 'objectPath' This will be the asset path to the CharacterPart.
    - 'swaps' This array can be used to swap the 'SkeletalMesh', 'MaterialOverrides', etc., inside the CharacterPart. If you are not performing advanced swaps, this array may not be needed and can be left empty.

# Setting Gender
Adding a gender is very important, as the swapper needs to know which options should be generated for the outfit plugin. To do this add the 'gender' key as shown below:
```json
{
    "type": "outfit",
    "itemName": "Renegade Raider",
    "itemDefinition": "CID_028_Athena_Commando_F",
    "characterParts": [
        {
            "objectPath": "/BRCosmetics/Athena/Heroes/Meshes/Bodies/CP_028_Athena_Body",
            "swaps": []
        },
        {
            "objectPath": "/BRCosmetics/Athena/Heroes/Meshes/Heads/F_MED_ASN_Sarah_Head_02_ATH",
            "swaps": []
        },
        {
            "objectPath": "/BRCosmetics/Characters/CharacterParts/Hats/Hat_F_Commando_08_V01",
            "swaps": []
        }
    ],
    "gender": "Female"
}
```

- Key explanation
    - 'gender' This value should be set to the gender of the outfit you are swapping to. For example: Female, Male.

# Final Result
The final product should look something like this:
```json
{
    "type": "outfit",
    "itemName": "Renegade Raider",
    "itemDefinition": "CID_028_Athena_Commando_F",
    "characterParts": [
        {
            "objectPath": "/BRCosmetics/Athena/Heroes/Meshes/Bodies/CP_028_Athena_Body",
            "swaps": []
        },
        {
            "objectPath": "/BRCosmetics/Athena/Heroes/Meshes/Heads/F_MED_ASN_Sarah_Head_02_ATH",
            "swaps": []
        },
        {
            "objectPath": "/BRCosmetics/Characters/CharacterParts/Hats/Hat_F_Commando_08_V01",
            "swaps": []
        }
    ],
    "gender": "Female"
}
```