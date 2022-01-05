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