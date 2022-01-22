# Lundi 3 janvier
## Rencontre avec mon encadrant
- Discussion sur le contenu et objectifs du stage en visio. Tout est expliqué dans [ce document](doc/stageL3Remi.pdf)
- Installation de ROBITOOLS qui permet de calculer les distances entre deux séquences.
  - Téléchargement de l'archive à partir de  https://git.metabarcoding.org/obitools/ROBITools/
  - Ouverture du répertoire dans Rstudio puis installation des dépendances
  
## Prise en main des données
Jusqu'à "étude de la distance entre les variants" dans [mon sujet](doc/stageL3Remi.pdf).

# Mardi 3 janvier

- mise en place de l'indicateur de biodiversité, pour les séquences répertoriées de motus, pour toutes les séquence de motus, (avec le problème de dvp limité pour q = 1).
- rentre l'indicateur dans une fonction puis le plotter avec l'aide de sapply en fonction de la valeur de q.
- tracer l'histogramme des ps afin de voir quelle est leurs distribution et le plotter en deux graph séparés selon si les séquences sont présentes dans le base de donnée de référence.

# Mercredi 4 janvier

- mise à jour du journal qui n'avais quasi pas été faite.
- data%>%group_by(motu)%>%summarise(count = sum(count)) est une manière d'écrire super pratique et efficace
- verification qu'il y a bien la meme nombre de lecture par motu dans le fichier data et dans le fichier motu
- j'ai appris à créer proprement un data frame:
        df <- NULL
        length(unique(data$sample))*4
        for (ech in unique(data$sample) ) {
          df <- rbind(df, data.frame(sample=ech,
                      q=nombre_q,
                      Qd=NA))
        }
        df
- façon super d'effectuer de calculs sur des data frame:
        q = 
        somme = 0
        if (q == 1) {
        
            ps=((data[data$sample == "~04A_1",]$count)/(sum(data[data$sample == "~04A_1",]$count)))
            somme = sum(ps*log(ps))
          Hill <- exp(-somme)
        }else{
              ps=((data[data$sample == "~04A_1",]$count)/(sum(data[data$sample == "~04A_1",]$count)))
            somme = sum(ps^q)
            print("b")
          Hill <- somme^(1/(1-q))
        }
        print(Hill)
        
# Jeudi 5 janvier

- un peu de tris dans le code car il devenait illisible, j'ai retiré tout les bouts de code inutiles, si besoin du cheminement de penssée, se réferrer au git d'avant le netoyage.
- unique et class sont objets très pratiques
- str() donne le type et la structure de l'objet

# Vendredi 6 janvier

- centrer les titres
- tracé des graphs avec le nombre de de variants et de lectures par échantillons
- mise en place d'une table des matières flottante dans Html pour avoir un deuxième écran dans lequel je puisse naviguer facilement
- début du calcul d'une matrice de distance et de proba d'appartenance à une espèce ou non.
- ébauche d'un digramme décisionnel pour savoir que faire afin de calculer les probas qu'un motus appartienne à un autre motu

# Lundi 10 janvier

- rédaction du code pour obtenir une matrice de proba
- apprentissage de igrah qui permet de réaliser des graphs et tracé des premier graphs

# Mardi 11 janvier

- ajout d'une couleur différente pour les espèces nouvellement définies. cependant, il semblerait qu'il n'y en ai pas alors que la définition d'une nouvelle espèce est très large dans le cas où on ne la définit que en étant la plus lue à un de distance.
- mise en place d'un programme permettant de compter le nomre de count théoriques pour chaque espèce.
- tracé du spectre de Hill théorique
- comparaison entre le spectre de hill que nous avions tracé avec les données brut et celui théorique en observant jusqu'à une distance de 1
- retracer un graph avec un jeu de donné plus important
- filtrer les données pour que le calcul ne mette pas trop de temps.

# Mercredi 12 janvier

- petit récap de quel matrice correspond à quoi:
  - matrice ditance
  - matrice proba
  - matrice adj
  - matrice distance2
  - matrice adj2
  - matrice adj 2bis
- début de la mise en fonction de la matrice de distance et de si les données figurent dans la base de ref
  
# jeudi 13 janvier

## pour mettre les graphiques dans un pdf
pdf("ajustement_qpcr_2.pdf") 
boucle for avec des prints gglot # applique le code dans le pdf
dev.off() # ferme le pdf

- fin de ce qui n'avais pas été fait la journée précédente, mise en fonction pour la matrice d'adjacence, pour la liste de couleur ainsi que pour le tracé du graphe.


# Vendredi 14 janvier

- plot du spectre de hill des échantillons pour une espèce afin comparer si le nombre d'échantillons influe beaucoup sur le spectre de Hill de l'alimentation d'une espèce


# Lundi 17 Janvier
- rédaction de la matrice de proba agrégée permettant d'attribuer les motu à l'espèce dont ils sont dérivés
- produit matriciel afin d'obtenir le nombre de count agrégé en regroupant les mutants avec leurs potentiel parent.
- tracé du spectre de hill brut et de celui rectifié

# Mardi 18 janvier

- tracé des spectre de hill pour les bases de données avec les motus dans la ref et ceux dans la ref avec leurs variants.
- pareil pour les différentes espèces pour le spectre brut et celui rectifié

# Mercredi 19 Janvier

- correction des erreurs avec l'aide de sylvain
- tracé des spectre des hill brutes selon le filtre leurs étant appliqué
- tracé des spectre de Hills rectifié pour chacune des espèces
- acp

# Jeudi 20 Janvier

-présentation à sylvain Moinard et Eric Coissac de ce que j'ai fait durant mon stage

# Samedi 22 Janvier

- fin de la rédaction de la synthèse, il faudra cependant revenir dessus quand je saurais mieux faire de tidyverse pour rédiger plus efficacement.