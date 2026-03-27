Ce projet propose une suite d'outils pour résoudre le problème de la couverture maximale (Maximum K-Coverage), un défi classique d'optimisation combinatoire. Il permet de sélectionner un nombre limité de sites (k) pour couvrir un maximum de population ou de points d'intérêt.DescriptionL'objectif est de choisir au plus $k$ candidats parmi un ensemble pour maximiser la couverture totale. Ce projet implémente deux approches distinctes :Approche Exacte (MIP) : Utilise le solveur Gurobi pour trouver la solution mathématiquement optimale via la programmation linéaire en nombres entiers.Approche Heuristique (Greedy) : Un algorithme glouton rapide utilisant une structure de données KDTree pour une recherche spatiale efficace, idéal pour les grands jeux de données.Fonctionnalités principalesRésolution optimale avec Gurobi Optimizer.Approximation rapide avec un algorithme glouton (Greedy).Interface graphique (GUI) pour une interaction facilitée avec le solveur.Gestion de données spatiales (coordonnées de population et de candidats).Support pour le chargement de données via fichiers CSV.PrérequisAvant d'exécuter le projet, assurez-vous d'avoir :Gurobi Optimizer installé sur votre machine.Une licence Gurobi valide (Académique ou Commerciale).Python 3.8+ installé.InstallationCloner le dépôt :Bashgit clone https://github.com/Narimane-Mezned/max-k-coverage-optimization.git
cd max-k-coverage-optimization
Installer les dépendances :Bashpip install -r requirements.txt
Note : Le fichier requirements.txt inclut gurobipy, scipy, numpy et pandas.Usage rapideInterface Graphique (GUI)Pour lancer l'application avec interface utilisateur :Bashpython src/gui_gurobi.py
Utilisation programmatiqueSolution Exacte (Gurobi)Pythonfrom src.gurobi_maxkcover import solve_max_k_coverage
# Utilise les données de population.csv et candidates.csv
selected, coverage = solve_max_k_coverage(elements, sets, k=5)
Solution Rapide (Greedy + KDTree)Pythonfrom src.greedy_fast import FastGreedyCoverage
solver = FastGreedyCoverage(points, radius=0.5)
selected_indices = solver.fit(k=5)
Comparaison des méthodesCaractéristiqueGurobi (MIP)Greedy (KDTree)Précision100% (Optimal)Approximation (>63%)VitesseDépend de la complexitéUltra-rapideUsagePetit/Moyen volumeBig Data / Temps réelInterfaceSupportée (GUI)Script / APIStructure du projetPlaintext.
├── src/
│   ├── gurobi_maxkcover.py  # Moteur d'optimisation MIP
│   ├── greedy_fast.py       # Algorithme glouton optimisé
│   ├── gui_gurobi.py        # Interface graphique utilisateur
│   ├── candidates.csv       # Données des sites candidats
│   └── population.csv       # Données de la population à couvrir
├── requirements.txt         # Liste des dépendances Python
└── README.md                # Documentation
Résultats attendusLe programme affiche les indices des candidats sélectionnés, le nombre total d'individus ou de points couverts, ainsi que le temps d'exécution. L'interface graphique permet de visualiser ces résultats de manière interactive.
