# Utils.py"

TAUX_TVA = 0.2  # constante globale

def moyenne(notes):
    """Renvoie la moyenne d'une liste de notes."""
    if not notes:
        return 0
    return sum(notes) / len(notes)

def est_admis(note, seuil=10):
    """Retourne True si la note est >= au seuil."""
    return note >= seuil

def prix_ttc(prix_ht, taux=TAUX_TVA):
    """Calcule le prix TTC."""
    return prix_ht * (1 + taux)

def formater_rapport(notes):
    """Génère un rapport complet sous forme de texte."""
    moyenne_classe = moyenne(notes)
    notes_valides = [note for note in notes if est_admis(note)]
    lignes = [
        "=== Rapport des notes ===",
        f"Notes : {notes}",
        f"Moyenne : {moyenne_classe:.2f}",
        f"Nombre d'étudiants admis : {len(notes_valides)}",
    ]
    return "\n".join(lignes)

# --- 2. الجزء الخاص بالتنفيذ (Exécution) ---

if __name__ == "__main__":
  
    notes_test = [12, 9, 15, 8, 17, 13, 19, 10]
    prix_ht = 100

    print("--- Exécution du script principal ---\n")
    
    
    print(formater_rapport(notes_test))
    
    
    resultat_ttc = prix_ttc(prix_ht)
    print(f"\nPrix TTC pour {prix_ht} € (TVA {TAUX_TVA*100:.0f}%) : {resultat_ttc:.2f} €")
