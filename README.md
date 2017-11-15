# linuxTroubleResolver

solutions aux problèmes rencontrés sur Linux....

## installation de Xubuntu 16.04 (last LTS) sur mon Acer Aspire V 15 nitro 592g, port HDMI non reconnu, pas de bureau étendu etc

le 2 ème écran ne marche pas sur port HDMI. lié à l'optimus....
solution : 

### solution rapide : 

d'abord, tenter :

lancer Xubuntu en recovery mode (échap une fois pendant l'écran acer au boot)
puis options ubuntu avancées

activer le réseau
lancer dpkg. qui devrait restaurer XOrg (je crois que le port HDMI était débranché quand j'ai lancé le truc mais peut être pas)

puis redémarrer le pc, et ça devrait marcher....

### plan B

si ça n'a pas marché reproduire la procédure complète (y compris ce qui m'a détruit XOrg):

tenter d'installer xserver-xorg-video-nouveau  avec aptitude:

`aptitude install xserver-xorg-video-nouveau`

(en installant aptitude avant si nécessaire)
ça va péter complêtement XOrg

puis relancer Xubuntu en recovery et reprendre l'étape 1. 
Il y a surement une solution plus propre pour péter Xorg et le réinstaller mais bon... tant que ça marche. 


à tenter: rajouter les drivers NVidia à partir de maintenant. mais je tenterais ça avant de reformater le PC.


## powerline font pour thème agnoster de OhmyZsh

### le terminal n'affiche pas correctement les barres

`sudo apt-get install powerline`
