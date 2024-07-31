
# Table of Contents

1.  [Mon astronomie](#org5ec2e94)
    1.  [Planification séance d'observation astronomique](#org2742bfc)
        1.  [Logiciel de planification de séance d'observation astronomique](#orgd3aefcc)
    2.  [Mon journal d'observation](#org9a5dae4)
        1.  [Logiciel utilisé](#org5926b1f)
    3.  [Météo astronomique](#orgbf30f21)
        1.  [Logiciel de météo astronomique](#org4a4e036)
    4.  [Références](#org38a21cf)
        1.  [Médias sociaux](#orgd53ed83)


<a id="org5ec2e94"></a>

# Mon astronomie


<a id="org2742bfc"></a>

## Planification séance d'observation astronomique

astroGenerator est un programme écrit par Vincent Gallouedec pour organiser les soirées d'observation du ciel.
La version originale était disponible à l'adresse suivante :
<http://www.univers-astronomie.fr/>
<http://www.univers-astronomie.fr/generateur-soiree/astrogenerator>
Cependant, le site web est souvent hors ligne et la dernière version est la version 2.0 publiée en 2013.
Actuellement, le seul moyen d'obtenir le programme et ses sources est de télécharger l'installation depuis la Wayback Machine de l'Internet Archive :
<https://web.archive.org/web/20160910193551/http://www.univers-astronomie.fr/generateur-soiree/astrogenerator/telecharger.php?name=astroGenerator-2.0-setup.exe&version=2.0>
Voici le dépot Github ou une personne a pour but de faire revenir à la vie ce logiciel.
<https://github.com/bterrier/astrogenerator/tree/master>
J'en ai fait un Fork au cas :
<https://github.com/steveprudhomme/astrogenerator>


<a id="orgd3aefcc"></a>

### Logiciel de planification de séance d'observation astronomique

J'utilise pour faire la planification de mes séances d'observations astronomique le logiciel astrogenerator. 


<a id="org9a5dae4"></a>

## Mon journal d'observation


<a id="org5926b1f"></a>

### Logiciel utilisé

J'utilise pour mes journaux d'observation, le logiciel GNU Emacs, avec le mode org-mode.
<https://www.gnu.org/software/emacs/>
<https://orgmode.org/>

1.  Configuration

    1.  .emacs
    
        Ajouter ces éléments de configuration dans votre .emacs.
		```elisp
        
            ;; Afin de pouvoir installer le convertisseur Org-mode à MD ox-md
            
            (require 'package)
            (add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/") t)
            (package-initialize)
            
            ;; Activer le mode Org
            
            (require 'org)
            (setq org-log-done 'time)
            
            ;; Configurer les modèles Org-Capture avec les nouveaux champs
            
            (setq org-capture-templates
                  '(("a" "Astronomy Journal Entry" entry
                     (file+headline "~/Documents/Astronomy/journal.org" "Observations")
                     (concat
                      "\n* Date : %^{Date}, Heure : %^{Heure}, Désignations : %^{Désignations}\n"
                      ":PROPERTIES:\n"
                      ":CUSTOM_ID: %^{ID}\n"
                      ":END:\n"
                      "- Description : %^{Description}\n"
                      "- Catégorie : %^{Catégorie|Nébuleuse|Planétaire|Galaxie|Amas globulaire|Amas ouvert|Autre}\n"
                      "- Découverte : %^{Découverte}\n"
                      "- Numéro catalogue Messier : %^{Numéro catalogue Messier}\n"
                      "- Numéro catalogue NGC : %^{Numéro catalogue NGC}\n"
                      "- Numéro catalogue IC : %^{Numéro catalogue IC}\n"
                      "- Numéro catalogue Caldwell : %^{Numéro catalogue Caldwell}\n"
                      "- Numéro autres catalogues : %^{Numéro autres catalogues}\n"
                      "- Nom du lieu : %^{Nom du lieu}\n"
                      "- Durée d'observation recommandé par le logiciel de Vaonis : %^{Durée d'observation recommandé par le logiciel de Vaonis}\n"
                      "- Durée (min.) : %^{Durée (min.)}\n"
                      "- Longueur de la pause (s) : %^{Longueur de la pause (s)}\n"
                      "- Coordonnés du lieu : %^{Coordonnés du lieu}\n"
                      "- Magnitude qualité du ciel : %^{Magnitude qualité du ciel}\n"
                      "- Bortle : %^{Bortle}\n"
                      "- Pourcentage lunaire : %^{Pourcentage lunaire}\n"
                      "- Nuages : %^{Nuages}\n"
                      "- Seeing : %^{Seeing}\n"
                      "- Transparence : %^{Transparence}\n"
                      "- Vent : %^{Vent}\n"
                      "- Température : %^{Température}\n"
                      "- Température ressentie : %^{Température ressentie}\n"
                      "- Point de rosée : %^{Point de rosée}\n"
                      "- Humidité : %^{Humidité}\n"
                      "- Direction : %^{Direction}\n"
                      "- Au-dessus de l'horizon : %^{Au-dessus de l'horizon}\n"
                      "- Instrument : %^{Instrument}\n"
                      "- Filtre : %^{Filtre}\n"
                      "- Distance (al) : %^{Distance (al)}\n"
                      "- Taille réelle : %^{Taille réelle}\n"
                      "- Taille apparente : %^{Taille apparente}\n"
                      "- Bords de l'objet : %^{Bords de l'objet}\n"
                      "- Forme de l'objet : %^{Forme de l'objet}\n"
                      "- Couleur de l'objet : %^{Couleur de l'objet}\n"
                      "- Densité : %^{Densité}\n"
                      "- Nombre d'étoiles estimé : %^{Nombre d'étoiles estimé}\n"
                      "- Apparence : %^{Apparence}\n"
                      "- Magnitude apparente : %^{Magnitude apparente}\n"
                      "- Appréciation : %^{Appréciation}\n"))))
            
            ;; Activer Org-Capture pour ajouter une entrée
            (global-set-key (kbd "C-c c") 'org-capture)
            (custom-set-variables
             ;; custom-set-variables was added by Custom.
             ;; If you edit it by hand, you could mess it up, so be careful.
             ;; Your init file should contain only one such instance.
             ;; If there is more than one, they won't work right.
             '(package-selected-packages '(ox-jekyll-md ox-mdx-deck)))
            (custom-set-faces
             ;; custom-set-faces was added by Custom.
             ;; If you edit it by hand, be careful.
             ;; Your init file should contain only one such instance.
             ;; If there is more than one, they won't work right.
             )
```
2.  Export en MD (Markdown languge) pour Github

    J'ai installé le package ox-md
    
    1.  Exporter un org en MD en utilisant ox-md
    
        1.  M-x
        2.  org-md-export-to-md
    
    2.  Problème d'exportation org à MD lorsqu'il y a des bloc de code


<a id="orgbf30f21"></a>

## Météo astronomique


<a id="org4a4e036"></a>

### Logiciel de météo astronomique

J'utilise le logiciel pour ios pour iphone Clear Outside.
Voici le lien vers le logiciel :
<https://apps.apple.com/us/app/clear-outside/id921555752>
<https://clearoutside.com/page/app/>

1.  Prise de capture pendant observation

    Je prend des capture de la météo astronomique juste avant une observation.
    Voici comment je procède :
    
    1.  Je clique sur l'onglet Current Location afin de me géolocaliser
    2.  Je prend une première capture,
    3.  Je dessend jusqu'à la ligne 71 Cloud
    4.  Je reprend une capture
    5.  Je descend jusqu'à la ligne Chance et je prend une capture.
    
    Note : Ces capture s'enregistre dans mon iCloud à côté de la photo astronomique je j'ai prise, cela me permet d'avoir les informations liées à la météo astronomique nécessaire pour mon journal d'observation.


<a id="org38a21cf"></a>

## Références


<a id="orgd53ed83"></a>

### Médias sociaux

1.  Tiktok

    1.  Astrophotojulie
    
        Julie Pomerleau
        AstroJulie | Astronomie 
        <https://www.tiktok.com/@astrophotojulie?lang=fr>
        Astronerd Joke/amateur Astrophoto,Planètes,lune, Soleil
        Live : Clear skies
        <https://linktr.ee/astrophotojulie>

2.  Instagram

    1.  astrophotohykue
    
        Julie Pomerleau
        AstroJulie | Astronomie
        Astronerd Joke/amateur Astrophoto,Planètes,lune, Soleil
        Live : Clear skies

