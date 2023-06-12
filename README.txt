import requests

def call_api(url, api_key):
    headers = {'API-Key': api_key}
    response = requests.get(url, headers=headers)
    
    if response.status_code == 200:
        print(response.json())  # Affiche la réponse au format JSON
    else:
        print('Erreur lors de la requête :', response.status_code)

# Exemple d'utilisation
api_url = 'https://exemple-api.com/endpoint'
api_key = 'votre_clé_api'

call_api(api_url, api_key)
