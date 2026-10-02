# UIDeviceExtension

Extension Swift de `UIDevice` qui expose le nom commercial de l’appareil courant à partir de son identifiant matériel (`utsname`).

## Contenu

- `modelName` : nom lisible (ex. `iPhone 16 Pro`, `iPad Air 7 M3`, `Simulator`).
- `modelType` : premier mot de ce nom (ex. `iPhone`, `iPad`, `Mac`).

Sur Mac (app iOS via Mac Catalyst / “Designed for iPad”), `modelName` renvoie `"Mac"`.

## Usage

```swift
let name = UIDevice.current.modelName
let type = UIDevice.current.modelType
```

## Couverture

iPod touch, iPhone (jusqu’aux identifiants récents du fichier), iPad / iPad Air / iPad mini / iPad Pro, Apple TV, HomePod, Vision Pro, simulateur (`i386`, `x86_64`, `arm64`).

Un identifiant inconnu est renvoyé tel quel.

## Notes

- Dépend de `UIKit` et de `uname` (`Darwin`).
- Les libellés sont figés dans le `switch` : un nouveau modèle Apple n’apparaîtra sous son nom commercial qu’après mise à jour du mapping.
- Quelques entrées du fichier (suffixes `-A`/`-B`, générations récentes) ne correspondent pas toujours aux identifiants officiels renvoyés par `uname` ; à vérifier avant de s’en servir en production.
