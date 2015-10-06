Représentation d'une ligne de toits:
question 1
- (2,0)(2,5)(4,5)(4,7)(5,7)(5,0)

question 2
Si on pose que la liste est circulaire, une polyligne est représenté par une liste paire de cordonées. Cette liste doit avoir un x identique au x du couple suivant, le y du deuxiéme couple doit etre identique au y du couple suivant et ainsi de suite. la premiére et la derniére coordonée on un y égale à 0.

question 3
(1,0)(1,1)(5,1)(5,13)(9,13)(9,20)(12,20)(12,27)(16,27)(16,3)(19,3)(19,18)(22,18)(22,3)(25,3)(25,0)

Premières approches

question 4

list est une list qui contiendra les cordonées de la polyligne.
tab est un tableau d'entiers de taille de l'image.
w est la largeur de l'image.
h est la hauteur de l'image.
Pour i = 0 à w-1
     Pour j = 0 à h-1
     	  tab[i][j] = 0.
     fin pour.
fin pour.
Pour tout les imeubles
     Pour i = x jusqu'a x + la largeur de l'imeuble 
     	  Pour j = y jusqu'a y + la hauteur de l'imeuble 
	       tab[i][j] = 1.
	  fin pour.
     fin pour.
fin pour.
aux1 et aux2 sont des entier qui valent 0.
Pour i = 0 à w-1
     Pour j = 0 à h-1
     	  Si tab[i][j] = 1
	     Si j > aux2 
	     	on ajoute (i,aux2) dans list.
	     	on ajoute (i,j) dans list.
	     	aux1 = i.
		aux2 = j.
	     fin si.
	     Si j < aux2 
	     	on ajoute (i-1,aux2) dans list.
	     	on ajoute (i-1,j) dans list.
	     	aux1 = i-1.
		aux2 = j.
	     fin si.
	  fin si.
          On sort de la boucle.
     fin pour.
fin pour.
on retourne list.

Cette algorithme à une complexité de O(n*m) où n et la largeur et m la longueur de l'image. La complexité ici ne dépend pas du nombre d'imenuble mais de l'image qui peut etre bien plus importante que le nombre de batiments.

question 5
list est une liste qui contiendra les cordonées de la fusion de la polyligne et des imeuble.
list1, list2 sont des liste de coordonée.
x et y sont les cordonées de départ d'un ineuble, w est sa largeur, h sa hauteur et se sont tous des entiers.
On initialise x,y,w et h avec les valeurs du premier imeuble.
on ajoute à list les coordonées (x,y), (x,h), (w,h) et (w,y).
Pour tous les autres imeubles
     list1 = list.
     on initialise anclist1 à vrai.
     on affecte x,y,w et h avec les valeur de l'imeuble.
     on vide list2.
     cpt1 et cp2 sont des entiers initialiser à 1.
     on ajoute à list2 les coordonées (x,y), (x,h), (w,h) et (w,y).
     Si list1[0].x < list2[0].x
     	on ajoute list1[0] et list1.[1] dans list.
	cpt1++.
     Sinon
	on ajoute list2[0] et list2[1] dans list.
	cpt2++.
	anclist1 = faux.
     fin si.
     Pour tout les éléments de list1 à partir de cpt1
     	  Si list1[cpt1].y > list2[cpt2].y
	     Si anclist1 est faux
	     	on ajoute dans list la coordonée (x du dernier élément de list,list1[cpt1].y).
	     fin si.
	     on ajoute list1[cpt1] dans list.
	     cpt1++.
	  Sinon 
	     Si anclist1 est vrai
	     	on ajoute dans list la coordonée (x du dernier élément de list,list2[cpt2].y).
	     fin si.
	     on ajoute list2[cpt2] dans list.
	     cpt2++.
	     cpt1++.
	  fin si.
      fin pour.
fin pour.
on retourn list.
