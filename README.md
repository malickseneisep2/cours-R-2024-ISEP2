# cours-R-2024-ISEP2
Cours R ISEP2 2024
##Exercice de maison numéro2
#1: creer une base de données fictive ayant au moins 5 variables
#avec les types numériques , caractère , facteur
#2: creer une matrice à partir de vos données , renommer les lignes
#et les colonnes 
#3 Faites des statistiques descriptive : min max quartile 
#Histogramme camenbert

# Créer des vecteurs de différents types
nom <- c("Niass", "MBB", "KD", "Célina", "Bathie")
age <- c(67, 94, 93, 70, 5)
sexe <- factor(c("M", "M", "M", "F", "M"), levels = c("F", "M"))
Region <- c("Saint-Louis", "Touba", "Ndayane", "Dakar", "Fatick")
note <- c(15.2, 12.5, 14.7, 16.3, 17.8)
# Creation de la base de données
donnees <- data.frame(nom, age, sexe, Region, note)
# Afficher la base de données
View(donnees)
#Voir les Statistiques
summary(note)

# Autre méthode avec les matrices
donnee=matrix(list("Niass", "MBB", "FAYE", "Célina", "Bathie",67, 94, 93, 70, 5,"M", "M", "M", "F", "M","Saint-Louis", "Touba", "Ndayane", "Dakar", "Fatick",15.2, 12.5, 14.7, 16.3, 17.8),nrow=5,ncol=5)
colnames(donnee)<- c("Nom","Age","Sexe","Région","Note")
rownames(donnee)<- c(1:5)
donnee

#Diagrammes
barplot(note, names.arg=nom, xlab="Noms", ylab="Notes", main="Histogramme des notes par nom")
pie(sexe, labels = sexe, main = "Répartition du sexe")
# Calcul des proportions
proportions <- table(sexe)
# Tracé du diagramme circulaire
pie(proportions, labels = c("Femme", "Homme"), main = "Répartition par sexe")


#Résolution d'un problème d'optimisation:

#Résoudre min f(x)=3x1-x2 sc x1+3x2<=3 ; x1+x2<=2 x1>=0 , x2>=0

install.packages("lpSolve")

# Charger le package lpSolve
library(lpSolve)
# Définir les coefficients de la fonction objectif
f.obj <- c(3, -1)
# Définir les coefficients des contraintes
f.con <- matrix(c(1, 3, 1, 1), nrow=2, byrow=TRUE)
# Définir les côtés droits des contraintes
f.rhs <- c(3, 2)
# Définir les directions des contraintes
f.dir <- c("<=", "<=")
# Résoudre le problème d'optimisation
result <- lp("min", f.obj, f.con, f.dir, f.rhs, all.int=TRUE)
# Afficher la solution
print(result$solution)
