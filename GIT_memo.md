# Débuter sur Git et Github

## Commandes

apt = npm
apt install "nomlogiciel"
'pour forcer' => sudo apt install "nomdulogiciel"

cat  / interroge
cd .

ls  / liste les documents présents
ls -lh  / voir la liste des dossiers sans fichiers cachés
la  / voir tout

rm -rf nomdossier  / efface le dossier

git add .  / ajoute

git branch -a  / liste toutes les branches

git branch -M main  / transforme la branche de master en main

git branch en alias devient
$ git config --global alias.br = git br

git commit -m "commentaire"  / valide plus commentaire de la modification apportée
/ exemple pour visualiser le dernier commit
en plus simple
$ git last

git init  / initialise

git pull
git pull upstream main

git push  / pousse le dossier
git push -u origin

git remote -v  / verbose  concerne notre dossier
git rm "nomfichier"  / supprime un fichier du dossier

gs  / git status (alias)
git status  / met à jour

git visual / alias gitk
/ exemple $ git config --global alias.visual "!g


-------------------------



## Création d'alias de commandes

Une fois acquis les commandes et compris les actions,
on peut commencer à créer des alias pour simplifier 
l'écriture.
Lire ce post :
[1] https://git-scm.com/book/fr/v2/Les-bases-de-Git-Les-alias-Git

Pour exemple :

ajouter : $ git config --global alias."motàaliaser"
cela donnera le raccourci git "2lettres" = gs / git status

-------------------------



# Memo des actions

La routine Git sur notre terminal



## creer un dossier

mkdir nomdudossier
cd nomdudossier
git init

tu as un dossier vide


## supprimer un dossier
action à réaliser si on ne souhaite pas 
conserver tout le contenu d'un dossier
ou supprimer un dossier vide 

rmdir nomdudossier

sinon on peut supprimer un sous-dossier (dit enfant) 
dans le dossier principal (considéré comme "parent")

rmdir/nomdossierparent/nomdossieràsupprimer

autre solution : pour supprimer tous les chemins liés à un dossier

rm -v nomduchemin/nomduchemin


## creer un fichier

touch test.txt
git add test.txt
git commit -m test.txt

on a cree le document mais sans le mettre dans un dossier


## ajouter un document
en exemple un document nommé index.html

git add index.html
git commit -m index.html
git pull origin


## supprimer un fichier du dossier

git rm nomdufichier
git commit -m "commentaire"
git push


## verifier si le doc est bon
action à réaliser par exemple après un add .
ou avant un commit -m

git status


## créer une branche

### Deux lignes: créer et basculer sur la nouvelle branch
git branch nom_de_ma_branch_nouvelle
git checkout nom_de_ma_branch_nouvelle

### Une seule ligne: créer et basculer
git checkout -b nom_de_ma_branch_nouvelle


## effacer une branche

### Si la branch est local et n'est pas créée sur le repo distant
git branch -d nom_de_ma_branch_local

### Si la branch est présente sur le repo distant
git push origin --delete nom_de_ma_branch_distante

-------------------------

## fusionner une branche

un article détaillé :
[2] https://www.pierre-giraud.com/git-github-apprendre-cours/fusion-rebasage-git/#:~:text=Pour%20fusionner%20nos%20deux%20branches%2C%20on%20va%20se,master%20au%20niveau%20du%20commit%20point%C3%A9%20par%20test.

### fusionner d'après une base
on se positionne sur la base de la branche que l'on souhaite fusionner
on se positionne sur la branche "main aussi appelée master sur certaines versions" et on fusionne avec une branche dite test

git checkout
git merge nombranchmain/nombranchtest

ensuite on efface la branche test

git branch -d

-------------------------

## fusionner deux branches avec un historique divergent

git merge

git crée un "instantané" avec les deux contenus en se basant sur le dernier commit
du dossier de base et du dernier commit des dossiers que l'on veut fusionner
et git émet ensuite un commit relatif aux 3 sources (donc plusieurs parents) : ce commit
a pour nom "commit de fusion"

si il y a conflit sur l'une des branches, il faudra le résoudre à part avant de retenter la fusion
pour identifier le problème faire : git status

une fois cela réalisé :

git add
git commit

ce commit termine le commit dit de fusion

-------------------------

## changer de branche

git checkout nombranche

GIT --version 2.23
git switch nombranche

-------------------------


# Les actions git/github

## faire la daily

il faut upstream le document du formateur depuis son github
vers notre terminal : il faut créer un dossier en local pour 
déposer les fichiers importés

on récupére donc son lien en cliquant sur le haut du dossier 
sur un picto représentant deux carrés superposés

git remote add upstream https://github.com/Simplon-hdf/daily-objectives-devinte-lil3.git
git remote -v

on l'importe sur notre local

git pull upstream main
git add .
git commit -m "commentaire"
git push

-------------------------

##récuperer un doc en local

pour une mise à jour (l'action de récupérer le dossier
ayant déjà été faite auparavant)

git clone https://leliendesondossier.git
ls

on ouvre le dossier pour le dailyobjective
et va déposer sur notre dossier créé pour le daily

cd dailyobjective...lil3
git init
git remove -v
remote remove origin
remote add origin git@github.com:votrenomsurubuntu/nomdudossierlocal.git
git remote -v

je depose en local

git branch -M main
git push -u origin main
code .


## envoyer un document vers un dossier sur github

cd nomdossier
ls (si vous avez besoin de voir le nom exact du dossier)

git init
cela permet de mettre le document ou dossier en .git

git add .
si vous voulez pointer un document précis :
git reset HEAD nomdossier

git commit -m nomdossier

creer le dossier sur github (il editera un .git)
et recuperer le lien, en ssh c'est mieux

git remote add origin liendudossiergithub(en ssh)
git remote -v
git push origin main

____________
