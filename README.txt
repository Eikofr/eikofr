import requests

url = "URL_DE_L'API"
api_key = "VOTRE_CLÉ_API"

headers = {
    "X-API-Key": api_key,
    "Content-Type": "application/json"  # Ajoutez d'autres en-têtes selon les besoins de l'API
}

# Envoyer une requête GET
response = requests.get(url, headers=headers)

# Envoyer une requête POST
data = {
    "paramètre1": "valeur1",
    "paramètre2": "valeur2"
}
response = requests.post(url, headers=headers, json=data)

# Traiter la réponse
if response.status_code == 200:
    # Succès
    print(response.json())
else:
    # Erreur
    print("Erreur :", response.status_code)
    print(response.text)
