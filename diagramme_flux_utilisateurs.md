# Diagramme des flux utilisateurs

Ce diagramme illustre les interactions des utilisateurs (Élève, Parent, Professeur, Admin) avec la plateforme. Il est généré avec Mermaid pour une visualisation facile.

## Instructions
- Copiez ce fichier dans votre repository GitHub (`diagramme_flux_utilisateurs.md`).
- Visualisez-le dans GitHub, VS Code (extension Mermaid), ou Mermaid Live Editor (https://mermaid.live/).
- Vous pouvez également recréer ce flux dans Draw.io pour une version graphique.

## Diagramme Mermaid

```mermaid
graph TD
    A[Début] --> B{Utilisateur connecté ?}
    B -->|Non| C[Page d'inscription]
    B -->|Oui| I[Tableau de bord]
    %% Inscription
    C --> D[Entrer email, mot de passe, prenom, nom, telephone]
    D --> E[Appeler Sign Up]
    E --> F[Insérer dans users via admin_info_post]
    F --> G{Insertion réussie ?}
    G -->|Oui| H[Connecté]
    G -->|Non| C
    %% Connexion
    B -->|Non| J[Page de connexion]
    J --> K[Entrer email, mot de passe]
    K --> L[Appeler Login]
    L --> M{Connexion réussie ?}
    M -->|Oui| H
    M -->|Non| J
    %% Tableau de bord (tous les rôles)
    H --> I
    I --> N[Voir profil users]
    N --> O[Modifier profil]
    O --> P[Mettre à jour users]
    I --> Q[Voir notifications notification]
    %% Élève
    I -->|Élève| R[Voir notes]
    R --> S[Afficher note, bulletin_moyenne]
    S --> T[Calculer moyenne via calculer_moyenne]
    I -->|Élève| U[Voir emploi du temps]
    U --> V[Afficher emploi_du_temps]
    I -->|Élève| W[Voir devoirs]
    W --> X[Afficher devoir]
    X --> Y[Soumettre devoir]
    Y --> Z[Insérer dans devoir_rendu]
    I -->|Élève| AA[Voir messages]
    AA --> AB[Afficher conversation, message]
    AB --> AC[Envoyer message]
    AC --> AD[Insérer dans message]
    %% Parent
    I -->|Parent| AE[Voir enfants parent_eleve]
    AE --> AF[Sélectionner un enfant]
    AF --> AG[Voir notes]
    AG --> AH[Afficher note, bulletin_moyenne]
    AF --> AI[Voir emploi du temps]
    AI --> AJ[Afficher emploi_du_temps]
    AF --> AK[Voir présences]
    AK --> AL[Afficher presence]
    AF --> AM[Voir infractions]
    AM --> AN[Afficher infraction_eleve]
    %% Professeur
    I -->|Professeur| AO[Voir matières matiere]
    AO --> AP[Sélectionner une matière]
    AP --> AQ[Ajouter note]
    AQ --> AR[Insérer dans note]
    AP --> AS[Marquer présence]
    AS --> AT[Insérer dans presence]
    AP --> AU[Assigner devoir]
    AU --> AV[Insérer dans devoir]
    I -->|Professeur| AW[Voir élèves via classe]
    AW --> AX[Afficher eleve, eleve_resume]
    %% Admin
    I -->|Admin| AY[Gérer années scolaires]
    AY --> AZ[Créer/Modifier annee_scolaire]
    I -->|Admin| BA[Gérer classes]
    BA --> BB[Créer/Modifier classe]
    I -->|Admin| BC[Gérer utilisateurs]
    BC --> BD[Créer eleve, parent, professeur]
    I -->|Admin| BE[Voir logs]
    BE --> BF[Afficher audit_log]
