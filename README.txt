<!DOCTYPE html>
<html>
<head>
	<title>Exemple de lecture de JSON en JavaScript</title>
</head>
<body>

	<h1>Valeur associée à la clé '1' dans le fichier JSON 'test.json'</h1>

	<!-- Ajouter un élément vide qui servira à afficher la valeur -->
	<div id="result"></div>

	<!-- Ajouter le script JavaScript qui lit le fichier JSON et stocke la valeur dans une variable -->
	<script>
		// Utiliser l'objet XMLHttpRequest pour lire le fichier JSON
		var xhr = new XMLHttpRequest();
		xhr.open("GET", "env/test.json", true);
		xhr.onreadystatechange = function() {
			if (this.readyState === 4 && this.status === 200) {
				// Convertir le texte JSON en objet JavaScript
				var data = JSON.parse(this.responseText);
				// Récupérer la valeur associée à la clé '1' et la stocker dans une variable
				var cle = data["1"];
				// Afficher la valeur dans l'élément prévu à cet effet
				document.getElementById("result").innerHTML = cle;
			}
		};
		xhr.send();
	</script>

</body>
</html>

