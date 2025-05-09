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

## Exercice 2 : Planification de tâches avec Cron

### Étapes à suivre

1. **Ouvrir la crontab avec l'éditeur de texte par défaut**  
    Utilisez la commande suivante :  
    ```bash
    crontab -e
    ```

2. **Ajouter une tâche récurrente**  
    Insérez la ligne suivante dans l'éditeur :  
    ```bash
    */2 08-20 * * Mon-Fri /bin/date >> my_first_cron_job.txt
    ```
    Ensuite, appuyez sur `Échap` et tapez `:wq` pour enregistrer et quitter l'éditeur.

3. **Vérifier les tâches récurrentes planifiées**  
    Utilisez la commande :  
    ```bash
    crontab -l
    ```

4. **Vérifier le contenu du fichier généré**  
    Assurez-vous que le fichier contient la sortie de la commande `date` :  
    ```bash
    cat my_first_cron_job.txt
    ```

5. **Supprimer toutes les tâches récurrentes**  
    Utilisez la commande :  
    ```bash
    crontab -r
    ```

6. **Confirmer la suppression des tâches**  
    Vérifiez qu'aucune tâche n'est planifiée :  
    ```bash
    crontab -l
    ```

### Icônes pour les commandes
- 🕒 **Planification récurrente** : `crontab`
- 📋 **Liste des tâches** : `crontab -l`
- 🗑️ **Suppression des tâches** : `crontab -r`
- 📂 **Vérification des fichiers** : `cat`
## Exercice 3 : Planification avancée avec Cron

### Étapes à suivre

1. **Planifier un job annuel pour le 2 février à 9h00**  
    Ouvrez la crontab avec :  
    ```bash
    crontab -e
    ```
    Ajoutez la ligne suivante :  
    ```bash
    0 9 2 2 * /local/bin/annual_backup
    ```

2. **Planifier un job pour afficher "tekup" toutes les cinq minutes, chaque vendredi de juillet entre 9h et 17h**  
    Ouvrez la crontab avec :  
    ```bash
    crontab -e
    ```
    Ajoutez la ligne suivante :  
    ```bash
    */5 9-16 * 7 5 echo "tekup"
    0 17 * 7 5 echo "tekup"
    ```

3. **Planifier un job quotidien pour exécuter `/local/bin/daily_report` à 23h58**  
    Ouvrez la crontab avec :  
    ```bash
    crontab -e
    ```
    Ajoutez la ligne suivante :  
    ```bash
    58 23 * * 1-5 /local/bin/daily_report
    ```

4. **Planifier un job pour envoyer un email avec `mutt` tous les jours ouvrables à 9h00**  
    Ouvrez la crontab avec :  
    ```bash
    crontab -e
    ```
    Ajoutez la ligne suivante :  
    ```bash
    0 9 * * 1-5 echo "Checking in" | mutt -s "Daily Update" boss@example.com
    ```
    ### Planification de tâches supplémentaires avec Cron

    1. **Planifier un job pour exécuter le script `full-backup` chaque 10 juin à 08:30**  
        Ouvrez la crontab avec :  
        ```bash
        crontab -e
        ```  
        Ajoutez la ligne suivante :  
        ```bash
        30 8 10 6 * /path/to/full-backup
        ```

    2. **Planifier une tâche pour écrire la date et l'heure dans un fichier nommé `date` toutes les 2 heures**  
        Ouvrez la crontab avec :  
        ```bash
        crontab -e
        ```  
        Ajoutez la ligne suivante :  
        ```bash
        2  8-11/2,14-17/2 * * * echo date >>deta
        ```

    3. **Planifier une tâche pour écrire le nom d'utilisateur connecté dans un fichier `user` toutes les 30 secondes**  
        Note : Les tâches avec une fréquence inférieure à une minute nécessitent une approche alternative.  
        Ajoutez la ligne suivante dans la crontab :  
        ```bash
        * * * * * sleep 30; whoami >> /path/to/user
        ```
        ```

    4. **Provoquer un reboot de la machine chaque 1er et 15 du mois à 02:30**  
        Ouvrez la crontab avec :  
        ```bash
        crontab -e
        ```  
        Ajoutez la ligne suivante :  
        ```bash
        30 2 1,15 * * /sbin/reboot
        ```

    5. **Écrire "hello" dans un fichier `test` tous les quarts d'heure de 15h à 19h, du lundi au vendredi, uniquement en 1ère quinzaine du troisième trimestre**  
        Ouvrez la crontab avec :  
        ```bash
        crontab -e
        ```  
        Ajoutez la ligne suivante :  
        ```bash
        */15 15-19 1-15 7-9 1-5 echo "hello" >> test //ac corriger
        ```
