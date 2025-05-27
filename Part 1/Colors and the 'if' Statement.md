# 🎨 Colors & `if` Statement dans After Effects

## 🧠 Objectif

> Apprendre à :
>
> * Définir une **couleur via le code** dans After Effects.
> * Utiliser une **condition `if`** pour changer dynamiquement une propriété selon une situation donnée.

---

## 🌈 Créer une couleur avec du code

En After Effects, une couleur est définie par **un tableau de 4 valeurs** :

```js
var ma_couleur = [R, G, B, A]
```

| Élément | Signification        | Valeur  |
| ------- | -------------------- | ------- |
| `R`     | Rouge                | 0 à 255 |
| `G`     | Vert                 | 0 à 255 |
| `B`     | Bleu                 | 0 à 255 |
| `A`     | Alpha (transparence) | 0 à 255 |

➡️ **Important** : pour que ça fonctionne dans After Effects, **il faut diviser chaque valeur par 255**.

### ✅ Exemple :

```js
var red = [255, 68, 63, 255] / 255;
var black = [51, 58, 55, 255] / 255;
```

---

## ⚙️ Cas pratique

### 🎯 Objectif :

> Créer un cercle qui **change de couleur selon sa position** :
>
> * Si le cercle est **à droite de l’écran** → rouge
> * Sinon (à gauche) → noir

### 📍 Étapes :

1. Créer un cercle (ellipse) de base.
2. Aller dans :
   `Contents → Ellipse 1 → Fill 1 → Color`
3. Alt + clic sur le **⏱️** de `Color` pour écrire du code.
4. Sélectionner la propriété `Color` et la **lier (parenting)** à `transform.xPosition`.
5. Écrire ce code :

```js
var red = [255, 68, 63, 255] / 255;
var black = [51, 58, 55, 255] / 255;

if (transform.xPosition > 950) {
  red;
} else {
  black;
}
```

🧠 Résultat :

> Le cercle devient **rouge quand il est à droite**, sinon il reste **noir**.

---

## 🔁 Utiliser un `if` Statement

### 📘 Syntaxe :

```js
if (condition) {
  // action si la condition est vraie
} else {
  // action si la condition est fausse
}
```

➡️ Cela permet de **faire un choix en fonction d’une condition**, par exemple la position du cercle.

---

## 🎯 Exercice : changer la transparence

### ✏️ Énoncé :

> Faire en sorte que la **transparence du cercle change** selon sa position :
>
> * Si le cercle est à droite → **85%**
> * Sinon → **50%**

### ✅ Solution (dans `Fill 1 → Color` ou une autre propriété liée à l’opacité) :

```js
if (transform.xPosition > 960) {
  85;
} else {
  50;
}
```

---

## ✅ Bonus : valeurs booléennes

Une **valeur booléenne** peut être :

* `true` (vrai)
* `false` (faux)

Exemple :

```js
transform.xPosition > 960
```

➡️ Cela **retourne un booléen** :

* Vrai si la position est au-dessus de 960
* Faux sinon

### 🔍 Opérateurs de comparaison :

| Opérateur | Signification     | Exemple    |
| --------: | ----------------- | ---------- |
|       `>` | Supérieur à       | `x > 500`  |
|       `<` | Inférieur à       | `x < 960`  |
|      `==` | Égal à            | `x == 100` |
|      `!=` | Différent de      | `x != 100` |
|      `>=` | Supérieur ou égal | `x >= 950` |
|      `<=` | Inférieur ou égal | `x <= 950` |

---

✅ Tu peux maintenant créer des animations **interactives et intelligentes** avec seulement quelques lignes de code dans After Effects !
