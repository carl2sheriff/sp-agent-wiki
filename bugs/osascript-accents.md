---
title: "Chemins avec accents cassent osascript"
date: 2026-04-14
status: resolved
---

# Chemins avec accents cassent osascript

## Symptôme
Les fichiers avec des caractères français (à, é, è, apostrophe) dans le chemin échouent quand passés à Photoshop via osascript.

## Cause
osascript corrompt les caractères spéciaux quand le chemin est passé en inline via `-e '...'`.

## Solution
1. Utiliser `encodeURI()` côté Node.js pour encoder le chemin
2. Utiliser `decodeURI()` côté ExtendScript pour le décoder
3. Passer les scripts via fichier .scpt au lieu de `-e` inline

```javascript
// Node.js
_safeOpenFile(varName, filePath) {
  return `var ${varName} = new File(decodeURI("${encodeURI(filePath)}"));`;
}
```
