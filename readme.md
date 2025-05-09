# Exercice 1 

## Étapes à suivre

1. **Afficher les jobs en attente pour l'utilisateur actuel**  
    Utilisez la commande suivante :  
    ```bash
    atq
    # ou
    at -l
    ```

2. **Planifier un job dans trois minutes**  
    Planifiez un job pour enregistrer la sortie de la commande `date` dans `/student/myjob.txt` :  
    ```bash
    at now + 3 minutes
    ```
    at> echo date > /student/myjob.txt
    ```

3. **Lister tous les jobs planifiés**  
    Utilisez la commande :  
    ```bash
    atq
    ```

4. **Surveiller la file d'attente en temps réel**  
    Utilisez la commande :  
    ```bash
    watch atq
    ```

5. **Vérifier le contenu de `myjob.txt`**  
    Après l'exécution du job, utilisez :  
    ```bash
    cat /student/myjob.txt
    ```

6. **Planifier un job interactif pour `teatime` (16h00)**  
    Planifiez un job dans la file d'attente `g` pour afficher un message dans `tea.txt` :  
    ```bash
    at teatime -q g
    # Ensuite, entrez la commande suivante :
    echo "Il est temps de teatime" > tea.txt
    ```

7. **Planifier un autre job interactif pour 16h05**  
    Planifiez un job dans la file d'attente `b` pour afficher un message dans `cookies.txt` :  
    ```bash
    at 16:05 -q b
    # Ensuite, entrez la commande suivante :
    echo "Les cookies sont bons" > cookies.txt
    ```

8. **Afficher les numéros des jobs en attente**  
    Utilisez :  
    ```bash
    atq
    ```

9. **Voir les commandes associées au job 2**  
    Utilisez :  
    ```bash
    at -c 2
    ```

10. **Voir les commandes associées au job 3**  
     Utilisez :  
     ```bash
     at -c 3
     ```

11. **Supprimer le job prévu pour `teatime` (16h00)**  
     Identifiez le numéro du job avec `atq`, puis supprimez-le :  
     ```bash
     atrm <job_number>
     ```

12. **Confirmer la suppression du job `teatime`**  
     Vérifiez que le job n'existe plus :  
     ```bash
     atq
     ```

## Icônes pour les commandes
- 🕒 **Planification** : `at`
- 📋 **Liste des jobs** : `atq`
- 🔍 **Surveillance** : `watch`
- 🗑️ **Suppression** : `atrm`
- 📂 **Vérification des fichiers** : `cat`
