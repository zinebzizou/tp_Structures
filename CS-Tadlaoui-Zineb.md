# **Algorithmique et programmation avancée**

##  Objectif : Manipulation des structures


Dans une unité d'assemblage des ordinateurs, les composants électroniques utilisés peuvent être réalisés par plusieurs fabricants. Selon le mode de communication, les composants sont regroupés par classes (PCI, ISA,...). Pour une meilleure organisation, la direction opte de représenter les informations techniques de ces composants par un tableau de structures et de les gérer par un programme C. on suppose qu'un composant est caractérisé par un Code, un Nom, une Classe, un Fabricant, une date de fabrication (Date fab).
<br>
<br>


> **Définir les structures date et composant**


```java script
//définir la structure date qui a trois attribues : jour, mois, annee
typedef struct date{
    int jour ;
    int mois;
    int annee;
}DATE;
//définir la structure composant qui se caracterise par : un code, un nom , une classe, un fabricant et une date de fabrication
typedef struct composant{
    int code;
    char nom[20];
    char classe[20];
    char fabricant[30];
    DATE datefab;
}COMPOSANT;
```

<br>

> **Ecrire une fonction qui saisit une date**
<br>

```java script
//saisir une date 
void SaisirDate(DATE *D)
{
    //on demande a l utilisateur de saisir le jour 
    printf("Veuillez entrer le jour : \n");
    //puis on stock la valeur entree par l utilisateur dans  l attribue 'jour'
    scanf("%d",&D->jour);
    //on demande a l utilisateur de saisir le mois
     printf("Veuillez entrer le mois : \n");
    //puis on stock la valeur entree par l utilisateur dans  l attribue 'mois'
    scanf("%d",&D->mois);
    //on demande a l utilisateur de saisir l annee
     printf("Veuillez entrer l'annee : \n");
    //puis on stock la valeur entree par l utilisateur dans  l attribue 'annee'
    scanf("%d",&D->annee);
};


```
<br>


> **Ecrire une fonction qui affiche une date**

<br>


```java script
//cette fonction nous permet d afficher les contribues dans la structure date
void AfficherDate (DATE X)
{
    printf("la date est %d / %d / %d",D.jour,D.mois,D.annee);
} 
```

> **Ecrire une fonction qui saisit un composant**

<br>

```java script
//pour saisir un composant un composant 
void SaisirComposant (COMPOSANT * c){
    //on demande a l utilisateur de saisir le code 
    printf("Veuillez entrer  le code : \n");
    // on stock la valeur entree par l utilisateur dans  l attribue 'code'
    scanf("%d",&c->code);
    //on demande a l utilisateur de saisir le nom du composant
    printf("Veuillez entrer  le nom : \n");
    // on stock la valeur entree par l utilisateur dans  l attribue 'nom'
    scanf("%s",&c->nom);
    //on demande a l utilisateur de saisir la classe du composant 
    printf("Veuillez entrer  la classe : \n");
    // on stock la valeur entree par l utilisateur dans  l attribue 'classe'
    scanf("%s",&c->classe);
    //on demande a l utilisateur de saisir le nom du fabricant
    printf("Veuillez entrer le fabricant : \n");
    // on stock la valeur entree par l utilisateur dans  l attribue 'fabricant'
    scanf("%s",&c->fabricant);
    //pour saisir la date on fait appel a la fonction qui nous permet de SaisirDate
    SaisirDate(&c->datefab);

}
```

<br>

> **Ecrire une fonction qui affiche un composant**

<br>

```java script
//pour afficher un composant
void AfficherComposants(COMPOSANT c){
    printf("\nle code du composant est : %d\n le nom est: %s \nla classe est %s\nle fabricant est %s\n",c.code,c.nom,c.classe,c.fabricant);
  //pour afficher un date on fait appel a la fonction Afficher date
    AfficherDate(c.datefab);   
}

```

<br>

> **Ecrire une fonction qui saisit un tableau de composant**

<br>

```java script

//la fonction nous permet de remplir un tableau de composants

void TableauComposants(COMPOSANT *c, int taille ){
    int i;
    //la boucle for nous permet de remplir le tableau jusau a la taille entree
    for(i=0;i<taille;i++){
         //on fait appel a la fonction SaisirComposant 
        SaisirComposant(&c[i]);
    }
}

```

<br>

> **Ecrire une fonction qui affiche un tableau de composants**

<br>

```java script

//fonction nous permet d afficher un tableau de COMPOSANTS 

void AfficherTableau(COMPOSANT *c ,int taille){
   	int i;
   	for(i=0;i<taille;i++){
        //on fait appel a la fonction AfficherComposant 
   		AfficheComposants (c[i]);
	   }
}
```

<br>


> **Ecrire le programme principal qui réalise le scénario suivant :**
> 

 *  Déclaration d'un tableau dynamique de composantes.

 *  Saisie d'un tableau de composants.

 *  Affichage d'un tableau de composants.


<br>

```java script
//dans le programme principale 
int main (){
//on declare uen date
DATE d;
//on declare un nouveau composant
COMPOSANT c;
//on donne une taille fixe aue le programme va proceder
int taille =1;

//on declare un tableau dynamique de composants 
COMPOSANT *T =malloc(taille*sizeof(COMPOSANT));
//puis pour saisir un tableau de composant on fait appel a la fonction TableauComposants
TableauComposants(&c,taille);
//pour afficher le tableau des composants on a recours a la fonction AfficherTableau
AfficherTableau(&c,taille);

```

<br>

> **Ecrire une fonction qui calcule le nombre de composants réalisés par un fabricant donne**

<br>

```java script

//fonction qui calcule le nombre de composants realise par un fabricant
int nbrComposantsFab(COMPOSANT *c ,int taille ,char fabricant[]){
int count=0;	
int i=0;
for(i=0;i<taille;i++){
//strcmp est une fonction qui nous permet de comparer deux chaines de caractère
 if(strcmp(fabricant,c[i].fabricant)==0){
	count++;
	}
} return count;	
}
```

<br>

> **Ecrire une fonction qui calcule le nombre de composants de deux classes données (exemple "PCI" ou "ISA")**

<br>

```java script

//fonction qui nous permet de calculer le nombre de COMPOSANTS de deux classes données

int nbrComposant (COMPOSANT *c, int taille, char classe1[],char classe2[]){
	 
int i, couunter=0;
for(i=0;i<taille;i++){
	if(strcmp(classe1,c[i].classe)==0||strcmp(classe2,c[i].classe)==0){
		couunter++;
	}
}return couunter;	
}
``` 

<br>

> **Ecrire une fonction qui affiche les composants fabriqués entre deux dates d1 et d2**

<br>

```java script
// fonction pour comparer les deux dates
int composantsEntreDates (COMPOSANTS*c ,int taille ,DATE d1,DATE d2{
int couterr=0;
int i;
//pour comparer les dates on passe d abord par comparer les années 
for(i=0;i<taille;i++){
    //premierement on compare  les annees 
  if(c[i].datefab.annee>=d1.annee&&c[i].datefab.annee<=d2.annee){
      //puis les mois
	if(c[i].datefab.mois>=d1.mois&&c[i].datefab.mois<=d2.mois){
        //et finalement les jours 
	        if(c[i].datefab.jour>=d1.jour&&c[i].datefab.jour<=d2.jour){
	               counterr++;
		}
	}
   }
}return counterr;
}

```

<br>

> **Ajouter au programme principal précédent les fonctionnalités suivantes :**

*  Calcul du nombre de composants réalisés par un fabricant donne.
  
*  Calcul du nombre de composants de deux classes données (exemple "PCI ou "ISA").
  
*  Affichage des composants fabriqués entre deux dates d1 et d2

<br>


```java script
	//dans le programme principale 
int main (){

DATE d;
COMPOSANTS c;
int taille =1;
//on declare les deux dates qu'on souhaite comparer
DATE d1={17,07,2000};
DATE d2={17,04,200};

//pour calculer de nombre composant réalisé par un fabricant on fait appel a la fonction nbrFabricant
printf("\n le nombre de composants realises par le fabricant est %d \n",nbrFabricant(&c ,taille, "Aineb");

//pour calcuer le nombre de composants de deux classes on fait appel a la fonction nbrComposant
printf("le nombre de composants des deux classes pci et isa est %d  \n",nbrComposant (&c,taille, "pci","isa"));

//pour afficher les composants fabriques entre les deux dates donnees on fait appel a la fonction ComposantsEntreDates
printf("le  de composants entre d1 et d2 est %d ",ComposantsEntreDates (&c, taille, d1, d2));

} 
```

---


<br>


## **Réalisé par : Tadlaoui Zineb (CS)**
## **Encadré par : Pr.AMAMOU Ahmed**

<br>

---

# **Merci**
