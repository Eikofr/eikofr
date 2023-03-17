<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Votre titre</title>
    <script>
        let Python_local_API;

        // Charger le fichier JSON
        async function loadJSON() {
            try {
                const response = await fetch('url.json');
                if (!response.ok) {
                    throw new Error('Erreur lors du chargement du fichier JSON');
                }
                const data = await response.json();

                // Récupérer la valeur associée à la clé "host"
                Python_local_API = data.host;

                // Utiliser la valeur stockée dans la variable Python_local_API
                console.log('Valeur de Python_local_API:', Python_local_API);

                // Appeler une autre fonction qui utilise la variable Python_local_API
                useAPI();
            } catch (error) {
                console.error('Erreur:', error);
            }
        }

        // Une fonction qui utilise la variable Python_local_API
        function useAPI() {
            console.log('Utiliser Python_local_API dans une autre fonction:', Python_local_API);
            // Votre code utilisant la variable Python_local_API
        }

        // Exécuter la fonction loadJSON lorsque le contenu de la page est chargé
        document.addEventListener('DOMContentLoaded', loadJSON);
    </script>
</head>
<body>
    <!-- Votre contenu HTML -->
</body>
</html>
