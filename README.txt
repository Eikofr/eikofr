# Vérification de la colonne à utiliser pour la fusion

if 'col' not in finma.columns or 'col' not in six_filtered.columns:

    raise ValueError("Les colonnes nécessaires pour la fusion n'existent pas dans les deux DataFrames.")

# Vérification que les données à fusionner sont identiques dans les deux fichiers

if not (finma['col'].unique() == six_filtered['col'].unique()).all():

    raise ValueError("Les colonnes utilisées pour la fusion contiennent des données différentes dans les deux fichiers.")

# Vérification des doublons dans les colonnes utilisées pour la fusion

if finma['col'].duplicated().any() or six_filtered['col'].duplicated().any():

    raise ValueError("Les colonnes utilisées pour la fusion contiennent des doublons dans l'un des fichiers.")

# Vérification des valeurs manquantes dans les colonnes utilisées pour la fusion

if finma['col'].isnull().any() or six_filtered['col'].isnull().any():

    raise ValueError("Les colonnes utilisées pour la fusion contiennent des valeurs manquantes dans l'un des fichiers.")
    
