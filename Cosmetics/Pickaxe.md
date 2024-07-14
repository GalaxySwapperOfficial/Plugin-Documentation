# Creating Your Base Pickaxe Plugin
To begin, create the base of your plugin file by specifying the type, itemName, itemDefinition, overrideItemDefinition as shown below:

```json
{
    "type": "pickaxe",
    "itemName": "Default Pickaxe to Raider's Revenge",
    "itemDefinition": "DefaultPickaxe",
    "overrideItemDefinition": "Pickaxe_Lockjaw"
}
```

- Key explanation
    - 'type' Signifies to the swapper that the plugin format is for 'pickaxe'.
    - 'itemName' This will be the name that is displayed within the swapper for your plugin file.
    - 'itemDefinition' This is the BID for the pickaxe you are swapping from. It is not required, but when specified the swapper will automatically load the pickaxe icon from the item definition.
    - 'overrideItemDefinition' This is the BID for the pickaxe you are swapping to. It is not required, but when specified the swapper will automatically load the pickaxe icon from the item definition.

# Creating Your Plugin Icon
Having a plugin icon is very important as it displays a preview of the pickaxe you are swapping to. To get started, begin by adding a JSON key 'icon' for the pickaxe you are swapping from and add the JSON key 'overrideIcon' for the pickaxe you are swapping to as shown below:
- Note: This is not required if you specified 'itemDefinition' or 'overrideItemDefinition' as the icon will be loaded from that.
```json
{
    "type": "pickaxe",
    "itemName": "Default Pickaxe to Raider's Revenge",
    "itemDefinition": "DefaultPickaxe",
    "overrideItemDefinition": "Pickaxe_Lockjaw",
    "icon": "https://fortnite-api.com/images/cosmetics/br/DefaultPickaxe/icon.png",
    "overrideIcon": "https://fortnite-api.com/images/cosmetics/br/Pickaxe_Lockjaw/icon.png"
}
```

- Key explanation
    - 'icon' This will be the URL for the pickaxe you are swapping from.
    - 'overrideIcon' This will be the URL for the pickaxe you are swapping to.

# Finding ItemDefinition
In order to find the ItemDefinition for your pickaxe, you can use a website called [Fortnite.gg](https://fortnite.gg/cosmetics?game=br&type=pickaxe). Locate the pickaxe you are swapping to using the search bar and click on the pickaxe. In the popup at the bottom right, you will see the 'ID' which will be our ItemDefinition."
  
  
![ItemDefinition Preview](/Images/OutfitItemDefinition.png)

# Finding WeaponDefinition
In order to find the WeaponDefinition for your pickaxe, we will use FModel. If you are not familiar with FModel, please refer to their [documtation](https://github.com/4sval/FModel/wiki/Getting-Started). To get started, locate 'Packages' and click 'Search'.
  

![FModel Search Preview](/Images/FModelSearch.png)

Paste your 'ItemDefinition' into the search bar and press enter on the keyboard. In the search results, you may encounter two results: one will be the ID asset we are looking for, and the other will be a DisplayAsset. Make sure to select the path that does not include 'DisplayAssets'.
  
  
![FModel Results Preview](/Images/FModelOutfitItemDefinitionResults.png)

Once you have located the correct asset, right-click on it and select 'Extract in new tab'.
  
  
![FModel Results Preview](/Images/FModelExtractAsset.png)

In the JSON preview section of FModel, you should see the WeaponDefinition ObjectPath. This will be your 'WeaponDefinition' for the plugin.
  
  
![FModel Results Preview](/Images/PickaxeWeaponDefinition.png)

# Adding WeaponDefinition
In order for the swapper to know which WeaponDefinition to swap to, we need to add a 'weaponDefinitions' array containing the WeaponDefinition we are swapping from and to these can be find In the itemDefinitions.
```json
{
    "type": "pickaxe",
    "itemName": "Default Pickaxe to Raider's Revenge",
    "itemDefinition": "DefaultPickaxe",
    "overrideItemDefinition": "Pickaxe_Lockjaw",
    "weaponDefinitions": [
        {
            "objectPath": "/Game/Athena/Items/Weapons/WID_Harvest_Pickaxe_Athena_C_T01",
            "overrideObjectPath": "/Game/Athena/Items/Weapons/WID_Harvest_Pickaxe_Lockjaw_Athena_C_T01"
        }
    ]
}
```
- Key explanation
    - 'objectPath' This will be the asset path to the WeaponDefinition we are swapping from.
    - 'overrideObjectPath' This will be the asset path to the WeaponDefinition we are swapping to.

# Final Result
The final product should look something like this:
```json
{
    "type": "pickaxe",
    "itemName": "Default Pickaxe to Raider's Revenge",
    "itemDefinition": "DefaultPickaxe",
    "overrideItemDefinition": "Pickaxe_Lockjaw",
    "weaponDefinitions": [
        {
            "objectPath": "/Game/Athena/Items/Weapons/WID_Harvest_Pickaxe_Athena_C_T01",
            "overrideObjectPath": "/Game/Athena/Items/Weapons/WID_Harvest_Pickaxe_Lockjaw_Athena_C_T01"
        }
    ]
}
```

# Additonal Features
These features are used to modify object paths within the WeaponDefinition you are swapping to. If you are a beginner or are not planning to modify any object paths within the WeaponDefinition, then this section is not for you.

# Modify WeaponMeshOverride
```json
{
    "type": "pickaxe",
    "itemName": "Default Pickaxe to Raider's Revenge",
    "itemDefinition": "DefaultPickaxe",
    "overrideItemDefinition": "Pickaxe_Lockjaw",
    "weaponDefinitions": [
        {
            "objectPath": "/Game/Athena/Items/Weapons/WID_Harvest_Pickaxe_Athena_C_T01",
            "overrideObjectPath": "/Game/Athena/Items/Weapons/WID_Harvest_Pickaxe_Lockjaw_Athena_C_T01",
            "weaponMeshOverride": {
                "objectPath": "/Game/Weapons/FORT_Melee/Pickaxe_AgentXFemale1H/Skin/Koi/Meshes/AgentXKoi1h_Axe.AgentXKoi1h_Axe"
            }
        }
    ]
}
```
- Key explanation
    - 'weaponMeshOverride' This will be the object path to the skeletal mesh you want to override to.

# Modify WeaponMaterialOverrides
```json
{
    "type": "pickaxe",
    "itemName": "Default Pickaxe to Raider's Revenge",
    "itemDefinition": "DefaultPickaxe",
    "overrideItemDefinition": "Pickaxe_Lockjaw",
    "weaponDefinitions": [
        {
            "objectPath": "/Game/Athena/Items/Weapons/WID_Harvest_Pickaxe_Athena_C_T01",
            "overrideObjectPath": "/Game/Athena/Items/Weapons/WID_Harvest_Pickaxe_Lockjaw_Athena_C_T01",
            "weaponMaterialOverrides": [
              {
                "materialOverride": {
                  "objectPath": "/Game/Weapons/FORT_Melee/Materials/MI_FORT_Melee_Pick_Celestial.MI_FORT_Melee_Pick_Celestial"
                },
                "materialIndex": 0
              }
            ]
        }
    ]
}
```
- Key explanation
    - 'materialOverride' This will be the object path to the material you want to override to.
    - 'materialIndex' This will be the index that the material is applied to.