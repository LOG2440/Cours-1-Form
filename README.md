# Animalerie Malou

Exemple simple d'un formulaire HTML avec une validation personnalisée.

![Animalerie Malou](https://i.imgur.com/781IkkZ.png)

## Structure du formulaire

Le formulaire est composé de 3 sections distinctes contenues dans un élément `<fieldset>`.

Chaque section contient un titre descriptif dans un élément `<legend>` et plusieurs champs de saisie représentés par des éléments `<input>` ainsi qu'un menu déroulant dans un élément `<select>`.

### Attribut `type`

L'attribut `type` des éléments `<input>` permet de mieux gérer les types d'entrées acceptées par le champ. En fonction de la valeur de l'attribut, l'élément peut avoir un comportement et/ou un visuel différent.

### Attribut `for`

L'élément `<label>` représentant les étiquettes des champs de saisie possède l'attribut `<for>` dont la valeur doit être la valeur de l'attribut `<id>` d'un élément du formulaire. Cet attribut permet de lier les 2 éléments ensemble et un clic sur l'étiquette est interprété comme un clic sur l'élément dont l'`id` est pointé par `for`.

À noter que lorsque l'élément à lier est enfant d'un `<label>`, la liaison est implicite. Les déclarations suivantes ont donc le même comportement :
```html
<label for="chat"><input id="chat" type="checkbox" /> Chat</label>
<label>           <input id="chat" type="checkbox" /> Chat</label>
```

## Validation du formulaire

Les champs ayant la couleur jaune sont requis pour la soumission du formulaire à travers l'attribut `required` sur leurs balises ouvrantes.

Tous les champs sauf le champ _Commentaires_ possèdent une validation HTML native.
Par exemple, le code HTML suivant indique que le champ n'accepte que des chiffres de 0 à 120 qui peuvent être modifiés par des incréments de 0.5  :
```html
<input id="age" type="number" min="0" max="120" step="0.5" required />
```

Le champ _Commentaires_ possède une validation personnalisée à travers du code JavaScript et la fonction `validateComments(input)`. Cette fonction est exécutée à chaque modification de l'élément `<textarea>` en tant que gestionnaire de l'événement `input` :
```html
<textarea id="comments" oninput="validateComments(this)" required>
```
La fonction permet d'afficher un message personnalisé lorsque le critère de validité pour le champ n'est pas respecté.
```js
function validateComments(input) {
    if (input.value.length < 20) {
        input.setCustomValidity("Plus de détails svp.");
    } else {
        input.setCustomValidity("");
    }
}
```


## Démo

Le site est déployé sur GitHub sur le [lien suivant](https://log2440.github.io/Form-Cours-1/).

