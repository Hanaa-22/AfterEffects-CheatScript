# 🔗 Mouvement lié dans After Effects (Linked Movement)

## 🧠 Qu'est-ce que le "Linked Movement" ?

> C’est le fait de **lier le mouvement d’un calque à un autre**.
> Par exemple : faire en sorte que **le cercle suive le texte**, automatiquement.
> On appelle ça aussi du **"constrained movement"**, ou **expression-based parenting**.

> Cela permet de créer des **relations dynamiques entre les calques**, pour gagner du temps et créer des animations plus intelligentes.

---

## 🛠️ Comment faire ?

1. Clique sur la propriété **Position** d’un calque (par exemple le cercle).
2. **Sépare les dimensions** si tu veux agir sur X ou Y indépendamment :
   Clic droit → *Separate Dimensions*.
3. Tu verras maintenant **Position X** et **Position Y** comme deux lignes séparées.
4. ALT + clic sur le ⏱️ (chronomètre) de la propriété que tu veux lier.
5. Écris une expression comme :

```js
thisComp.layer("NomDuCalque").transform.position[0] // Pour X
thisComp.layer("NomDuCalque").transform.position[1] // Pour Y
```

> ℹ️ `position[0]` = axe horizontal (X)
> ℹ️ `position[1]` = axe vertical (Y)

---

## 🧪 Que se passe-t-il si...

### 👉 Tu mets ceci dans la **Position X** du cercle :

```js
thisComp.layer("Texte").transform.position[1]
```

> Tu dis :
> "Je veux que la **Position X du cercle** suive la **Position Y du texte**."

🧠 Résultat :

* Si tu **déplaces verticalement le texte**, le cercle bouge **horizontalement**.
* Ce n’est pas un lien "logique" X→X, mais ça peut créer des effets créatifs décalés (effets miroir, mouvements opposés, etc.).

---

### 👉 Tu ajoutes un **offset** :

```js
thisComp.layer("Texte").transform.position[1] + 500
```

🧠 Résultat :

* Le cercle suit toujours la **Position Y du texte**, mais sera **décalé de 500 pixels sur l’axe X**.
* Cela crée un **effet miroir diagonal** :

  > si le texte monte → le cercle va à droite
  > si le texte descend → le cercle va à gauche

---

## 🎯 Exemple de cas pratique

### 🎈 Objectif :

Faire en sorte que le cercle **suive la position X du texte**, avec **+100 pixels de décalage**.

### ✅ Code à mettre dans la **Position X** du cercle :

```js
thisComp.layer("Texte").transform.position[0] + 100
```

🧠 Résultat :

* Le cercle suivra **exactement le texte sur l’axe X**, mais toujours avec **100 pixels en plus à droite**.

---

## ❓ Astuces utiles

| Expression    | Description                           |
| ------------- | ------------------------------------- |
| `position[0]` | Valeur X de la position               |
| `position[1]` | Valeur Y de la position               |
| `+ 100`       | Ajoute un décalage de 100 pixels      |
| `- 50`        | Décalage négatif (ex : plus à gauche) |

---

## 🧱 Exemple avancé : combinaison X et Y

```js
var x = thisComp.layer("Texte").transform.position[0] + 100;
var y = thisComp.layer("Texte").transform.position[1];
[x, y]
```

🧠 Résultat :

* Le cercle **suivra totalement le texte** (X et Y), avec **un décalage de 100px sur l’axe X**.

---

## 💡 Idée bonus

Tu peux créer un **calque NULL** (vide), le placer comme un "contrôleur", et lier plusieurs éléments à lui.
Cela te permet de **contrôler un groupe entier de calques** avec un seul mouvement.
C’est très utilisé dans les rigs de personnages ou les interfaces animées.
