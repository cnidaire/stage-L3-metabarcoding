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