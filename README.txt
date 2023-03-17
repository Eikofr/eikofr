// Charger le fichier JSON
fetch('url.json')
  .then(response => {
    if (!response.ok) {
      throw new Error('Erreur lors du chargement du fichier JSON');
    }
    return response.json();
  })
  .then(data => {
    // Récupérer la valeur associée à la clé "host"
    const Python_local_API = data.host;

    // Utiliser la valeur stockée dans la variable Python_local_API
    console.log('Valeur de Python_local_API:', Python_local_API);

    // Votre code JavaScript utilisant la variable Python_local_API
  })
  .catch(error => {
    console.error('Erreur:', error);
  });
