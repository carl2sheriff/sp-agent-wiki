---
title: "JSON.parse échoue sur retour Photoshop"
date: 2026-04-14
status: resolved
---

# JSON.parse échoue sur retour Photoshop

## Symptôme
"Bad control character in string literal in JSON" quand on parse le résultat de osascript.

## Cause
osascript injecte des caractères de contrôle (\r, \t) dans le stdout que JSON.parse rejette.

## Solution
Nettoyer le résultat avant de parser :
```javascript
result = result.replace(/[\x00-\x1F\x7F]/g, (ch) => {
  if (ch === '\n' || ch === '\r' || ch === '\t') return ' ';
  return '';
});
return JSON.parse(result);
```
