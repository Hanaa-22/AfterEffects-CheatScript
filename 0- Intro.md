# 📚 Insérer du code dans After Effects (Expressions)

## 🎯 Pourquoi coder dans After Effects ?

> Coder dans After Effects permet d’ajouter **de la logique, des animations dynamiques, et des automatisations** à tes calques.
> Plutôt que d’animer tout manuellement, tu peux créer **des comportements intelligents**, réutilisables, qui s’adaptent en fonction du temps, des autres propriétés ou de l’interaction.
> 👉 Ce n’est pas pour compliquer, mais pour **gagner du temps** et **créer des animations avancées** impossibles à la main.

---

## 🧠 Comment insérer du code ?

1. Clique sur la propriété (ex : **Rotation**, **Position**, **Source Text**, etc.).
2. Appuie sur `ALT` + clic sur le **chronomètre** ⏱️ à gauche de la propriété.
3. Un champ de texte s’ouvre pour écrire ton **expression JavaScript**.

---

## 🧩 Propriétés acceptant du code

Les propriétés **ayant un chronomètre** peuvent recevoir du code :

* ✅ `Source Text` (texte)
* ✅ `Position`, `Scale`, `Anchor Point` (vecteurs → 2 ou 3 valeurs)
* ✅ `Rotation` (nombre)
* ✅ `Opacity` (nombre)

D'autres comme :

* ❌ `Fill`, `Stroke`, `Character Blending`, etc. ne peuvent **pas** recevoir de code car **pas de chronomètre**.

---

## 🧾 Types de valeurs

Chaque propriété attend un **type de valeur spécifique** :

| Propriété     | Type attendu             | Exemple                          |
| ------------- | ------------------------ | -------------------------------- |
| `Source Text` | Texte ou nombre          | `"Hello"` ou `123`               |
| `Rotation`    | Nombre                   | `45` ou `3.14`                   |
| `Position`    | Tableau (2 valeurs)      | `[100, 200]` (x = 100, y = 200)  |
| `Scale`       | Tableau (2 ou 3 valeurs) | `[100, 100]` ou `[50, 100, 100]` |

💡 Tu peux aussi mixer dans les tableaux :

```js
[123, "Test"] // Possible, mais pas toujours logique selon la propriété
```

---

## 🧱 Ajouter de la logique : plusieurs lignes de code

Pour écrire plusieurs lignes, on suit une **structure logique** :

### 1. Ordre d’exécution :

1. Définir les **valeurs de départ**
2. Faire les **calculs ou la logique**
3. Donner le **résultat final**

### 2. Utiliser des **variables**

> Une variable est une **boîte avec un nom et une valeur**.

#### 🅰️ Déclaration de variable

```js
var a = 5;
```

#### 🅱️ Modifier une variable

```js
a = a + 10;
```

#### 🅾️ Retourner une variable

```js
a;
```

---

## ✅ Exemple complet : contrôler la rotation

```js
var test_value = 5;
test_value = test_value + 10;
test_value; // Résultat = 15
```

💡 **Résultat** → le calque tournera de 15°.

---

## 🔁 Exemple pour `Position`

```js
var x = 100;
var y = time * 50;
[x, y]
```

💡 **Résultat** : le calque reste à 100px en X et descend automatiquement avec le temps en Y.
