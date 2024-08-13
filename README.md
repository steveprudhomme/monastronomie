
# Table of Contents

1.  [Mon astronomie](#orgea4f0f7)
    1.  [Planification séance d'observation astronomique](#org69ba751)
        1.  [Logiciel de planification de séance d'observation astronomique](#orgbf41cc1)
    2.  [Mon journal d'observation](#orgfe87972)
        1.  [Logiciel utilisé](#org6f88cd4)
        2.  [Journal par catalogue](#org59dea82)
    3.  [Météo astronomique](#org8b4865f)
        1.  [Logiciel de météo astronomique](#org7039d60)
    4.  [Références](#orgac8e28c)
        1.  [Médias sociaux](#org6a71c83)


<a id="orgea4f0f7"></a>

# Mon astronomie


<a id="org69ba751"></a>

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


<a id="orgbf41cc1"></a>

### Logiciel de planification de séance d'observation astronomique

J'utilise pour faire la planification de mes séances d'observations astronomique le logiciel astrogenerator. 


<a id="orgfe87972"></a>

## Mon journal d'observation


<a id="org6f88cd4"></a>

### Logiciel utilisé

J'utilise pour mes journaux d'observation, le logiciel GNU Emacs, avec le mode org-mode.
<https://www.gnu.org/software/emacs/>
<https://orgmode.org/>

1.  Configuration

    1.  .emacs
    
        
		Ajouter ces éléments de configuration dans votre .emacs.
```
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


<a id="org59dea82"></a>

### Journal par catalogue

1.  Catalogue du ciel profond en fichier excel et PDF Michael Swanson

    <https://www.nexstarsite.com/Book/DSO.htm>

2.  Liens vers mes journal par catalogue en ligne

    1.  Journal NGC
    
    2.  Journal IC
    
    3.  Journal Cardwell


<a id="org8b4865f"></a>

## Météo astronomique


<a id="org7039d60"></a>

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


<a id="orgac8e28c"></a>

## Références


<a id="org6a71c83"></a>

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

    1.  astrophotojulie
    
        Julie Pomerleau
        AstroJulie | Astronomie
        Astronerd Joke/amateur Astrophoto,Planètes,lune, Soleil
        Live : Clear skies

3.  Youtube

    1.  AstroBackyard(ANGLAIS)
    
        Cette chaîne est entièrement dédiée à l'astrophotographie. Je vous emmènerai avec moi pour capturer des nébuleuses, des galaxies et des amas d'étoiles avec mon appareil photo et mon télescope dans mon jardin. Que vous soyez en plein cœur de la ville avec une forte pollution lumineuse ou chanceux avec un ciel étoilé sombre à la campagne, je vous montrerai comment capturer le ciel nocturne. Voici ce que vous pouvez attendre :
        
        -   Tutoriels d'astrophotographie
        -   Équipement nécessaire pour l'astrophotographie
        -   Réglages de l'appareil photo que j'utilise
        -   Conseils et astuces pour le traitement d'images
        -   Exemples de résultats avec du matériel similaire
        
        Pour plus d'informations, rendez-vous sur : <https://astrobackyard.com/>
        <https://www.youtube.com/@AstroBackyard>
    
    2.  AstronoGeek
    
        1.  À propos
        
            AstronoGeek, c'est une chaîne dédiée à la vulgarisation de l'astronomie. Bordel de merde.
        
        2.  Informations de la chaîne
        
            www.youtube.com/@AstronoGeek
    
    3.  Gdelaculturegeek
    
        1.  À propos
        
            Chaîne dédiée à la vulgarisation scientifique et à l'astronomie.
            Vous pouvez également nous retrouver sur TikTok et Instagram.
        
        2.  Autres médias scoiaux
        
            <https://www.tiktok.com/@gdelaculturegeek?lang=fr>
            <https://www.instagram.com/gdelaculturegeek/>
            <https://fr.tipeee.com/gdelaculture>
        
        3.  Informations de la chaîne
        
            <https://www.youtube.com/@gdelaculturegeek>
    
    4.  La Chaine Astro - cdls48
    
        1.  À propos
        
            Bienvenue sur notre chaîne YouTube entièrement dédiée à l'astronomie amateur, et ce, gratuitement ! Découvrez 18 playlists riches en contenu pour approfondir vos connaissances et perfectionner vos compétences en astronomie :
            
            Astrophoto : Explorez divers types d'astrophotographie, y compris le ciel profond, les objets planétaires, la Lune, le Soleil, et les timelapses.
            Tutoriels : Apprenez à utiliser votre télescope et bien plus encore grâce à nos guides pratiques.
            Conférences et dossiers : Assistez à des conférences fascinantes et consultez des dossiers complets sur divers sujets astronomiques.
            Matériel et bricolage : Découvrez des conseils pour l'achat de matériel, le bricolage et la construction de télescopes.
        
        2.  Liens Utiles
        
            Discord : <https://discord.com/invite/comastro>
            Facebook : <https://www.facebook.com/groups/1790411764559026>
        
        3.  Informations de la chaîne :
        
            Chaîne YouTube : <https://www.youtube.com/user/cdlc48/featured>
    
    5.  Astro Nico
    
        1.  À propos
        
            Hopla les gens!!! c'est moi le mec qui fait de l'astro sur twitch et youtube!!! Je m’appelle nico et je vie en Alsace (La mode de la Hoplattitude est en route!!!).
            
            Mon métier est de réparer le matos astro et d'aider les gens dans leurs choix mais également de les aider dans l'utilisation de leur matériel. Alors vous vous dites mais c'est quoi son métier au juste ??????? Ben vendre et réparer du matos astro à Colmar (pas de nom mais vous trouverez très facilement le nom de la boutique sur google ^^).
            
            Dans ma vie de tous les jours, je suis amené à réparer les montures, accueillir les gens en boutique, au téléphone tous ça tous ça!
            
            En plus d’être mon boulot, c'est ma passion et en gros je bosse jour et nuit à la fois pour satisfaire les clients qui passe en boutique en leur donnant les bons conseils et le soir quand je suis en direct avec vous et même pendant mes vidéos tuto
            
            N'oubliez pas de vous abonnez et d'activer la cloche ;)
        
        2.  Liens
        
            -   TWITCH : <http://twitch.tv/astronico67>
            -   LE FACEBOOK: <http://facebook.com/groups/1207946152894577>
            -   POUR ME SOUTENIR! <http://youtube.com/channel/UCFijY4dKrxCqlVdfAY32fGw/join>
            -   MON TIPEE : <http://tipeeestream.com/astronico67>
        
        3.  Informations de la chaîne
        
            -   Courriel : <mailto:astronicolachaine@gmail.com>
            -   <http://www.youtube.com/@astronico>
    
    6.  ASTRONOMIE A LA LUNETTE
    
        1.  À propos
        
            "Astronomie à la Lunette" c'est une chaîne dédiée à l'observation du ciel avec de petits instruments. Initiez-vous en découvrant le système solaire, le Soleil et ses planètes&#x2026; Découvrez le ciel profond avec ses nébuleuses et les amas d'étoiles&#x2026; Apprenez à bricoler votre télescope, initiez-vous à l'astrodessin, à l'astrophotographie&#x2026; Prenez plaisir à pratiquer l'astronomie amateur.
        
        2.  Liens
        
            ASTRODESSIN ; <http://Padletpadlet.com/70900mm/zkbe6pweq2fbdsxi>
            SvBony Store : <http://s.click.aliexpress.com/e/_oBpWsCZ>
        
        3.  Informations de la chaîne
        
            -   <mailto:oumar.laurent@gmail.com>
            -   <http://www.youtube.com/@ASTRONOMIEALALUNETTE>
    
    7.  Astronomie Pratique
    
        1.  À propos
        
            Chasseuse de nébuleuses ★
        
        2.  Liens
        
            Site : <http://cours.astronomie-pratique.com>
            Astrobin : <http://astrobin.com/users/Laura_Astronomie_Pratique>
            Instagram : <http://instagram.com/astronomiepratique>
        
        3.  Informations de la chaîne
        
            -   <mailto:laura@astronomie-pratique.com>
            -   <http://www.youtube.com/@AstronomiePratique>
    
    8.  Le Petit Astronome
    
        1.  À propos
        
            Je raconte des histoires un peu mystérieuses sur l'Univers qui nous entoure, et c'est sympa.
        
        2.  Liens
        
            Facebook : <http://facebook.com/profile.php?id=100086130316488>
        
        3.  Informations de la chaîne
        
            -   <mailto:lepetitastronome74@gmail.com>
            -   <http://www.youtube.com/@PetitAstronome>
    
    9.  Proxima Astronomie
    
        -   Équipement nécessaire pour l'astrophotographie
        -   Réglages de l'appareil photo que j'utilise
        -   Conseils et astuces pour le traitement d'images
        -   Exemples de résultats avec du matériel similaire
        
        Pour plus d'informations, rendez-vous sur : <https://astrobackyard.com/>
        <https://www.youtube.com/@AstroBackyard>
    
    10. AstronoGeek
    
        1.  À propos
        
            AstronoGeek, c'est une chaîne dédiée à la vulgarisation de l'astronomie. Bordel de merde.
        
        2.  Informations de la chaîne
        
            www.youtube.com/@AstronoGeek
    
    11. Gdelaculturegeek
    
        1.  À propos
        
            Chaîne dédiée à la vulgarisation scientifique et à l'astronomie.
            Vous pouvez également nous retrouver sur TikTok et Instagram.
        
        2.  Autres médias scoiaux
        
            <https://www.tiktok.com/@gdelaculturegeek?lang=fr>
            <https://www.instagram.com/gdelaculturegeek/>
            <https://fr.tipeee.com/gdelaculture>
        
        3.  Informations de la chaîne
        
            <https://www.youtube.com/@gdelaculturegeek>
    
    12. La Chaine Astro - cdls48
    
        1.  À propos
        
            Bienvenue sur notre chaîne YouTube entièrement dédiée à l'astronomie amateur, et ce, gratuitement ! Découvrez 18 playlists riches en contenu pour approfondir vos connaissances et perfectionner vos compétences en astronomie :
            
            Astrophoto : Explorez divers types d'astrophotographie, y compris le ciel profond, les objets planétaires, la Lune, le Soleil, et les timelapses.
            Tutoriels : Apprenez à utiliser votre télescope et bien plus encore grâce à nos guides pratiques.
            Conférences et dossiers : Assistez à des conférences fascinantes et consultez des dossiers complets sur divers sujets astronomiques.
            Matériel et bricolage : Découvrez des conseils pour l'achat de matériel, le bricolage et la construction de télescopes.
        
        2.  Liens Utiles
        
            Discord : <https://discord.com/invite/comastro>
            Facebook : <https://www.facebook.com/groups/1790411764559026>
        
        3.  Informations de la chaîne :
        
            Chaîne YouTube : <https://www.youtube.com/user/cdlc48/featured>
    
    13. Astro Nico
    
        1.  À propos
        
            Hopla les gens!!! c'est moi le mec qui fait de l'astro sur twitch et youtube!!! Je m’appelle nico et je vie en Alsace (La mode de la Hoplattitude est en route!!!).
            
            Mon métier est de réparer le matos astro et d'aider les gens dans leurs choix mais également de les aider dans l'utilisation de leur matériel. Alors vous vous dites mais c'est quoi son métier au juste ??????? Ben vendre et réparer du matos astro à Colmar (pas de nom mais vous trouverez très facilement le nom de la boutique sur google ^^).
            
            Dans ma vie de tous les jours, je suis amené à réparer les montures, accueillir les gens en boutique, au téléphone tous ça tous ça!
            
            En plus d’être mon boulot, c'est ma passion et en gros je bosse jour et nuit à la fois pour satisfaire les clients qui passe en boutique en leur donnant les bons conseils et le soir quand je suis en direct avec vous et même pendant mes vidéos tuto
            
            N'oubliez pas de vous abonnez et d'activer la cloche ;)
        
        2.  Liens
        
            -   TWITCH : <http://twitch.tv/astronico67>
            -   LE FACEBOOK: <http://facebook.com/groups/1207946152894577>
            -   POUR ME SOUTENIR! <http://youtube.com/channel/UCFijY4dKrxCqlVdfAY32fGw/join>
            -   MON TIPEE : <http://tipeeestream.com/astronico67>
        
        3.  Informations de la chaîne
        
            -   Courriel : <mailto:astronicolachaine@gmail.com>
            -   <http://www.youtube.com/@astronico>
    
    14. ASTRONOMIE A LA LUNETTE
    
        1.  À propos
        
            "Astronomie à la Lunette" c'est une chaîne dédiée à l'observation du ciel avec de petits instruments. Initiez-vous en découvrant le système solaire, le Soleil et ses planètes&#x2026; Découvrez le ciel profond avec ses nébuleuses et les amas d'étoiles&#x2026; Apprenez à bricoler votre télescope, initiez-vous à l'astrodessin, à l'astrophotographie&#x2026; Prenez plaisir à pratiquer l'astronomie amateur.
        
        2.  Liens
        
            ASTRODESSIN ; <http://Padletpadlet.com/70900mm/zkbe6pweq2fbdsxi>
            SvBony Store : <http://s.click.aliexpress.com/e/_oBpWsCZ>
        
        3.  Informations de la chaîne
        
            -   <mailto:oumar.laurent@gmail.com>
            -   <http://www.youtube.com/@ASTRONOMIEALALUNETTE>
    
    15. Astronomie Pratique
    
        1.  À propos
        
            Chasseuse de nébuleuses ★
        
        2.  Liens
        
            Site : <http://cours.astronomie-pratique.com>
            Astrobin : <http://astrobin.com/users/Laura_Astronomie_Pratique>
            Instagram : <http://instagram.com/astronomiepratique>
        
        3.  Informations de la chaîne
        
            -   <mailto:laura@astronomie-pratique.com>
            -   <http://www.youtube.com/@AstronomiePratique>
    
    16. Le Petit Astronome
    
        1.  À propos
        
            Je raconte des histoires un peu mystérieuses sur l'Univers qui nous entoure, et c'est sympa.
        
        2.  Liens
        
            Facebook : <http://facebook.com/profile.php?id=100086130316488>
        
        3.  Informations de la chaîne
        
            -   <mailto:lepetitastronome74@gmail.com>
            -   <http://www.youtube.com/@PetitAstronome>
    
    17. Proxima Astronomie
    
        1.  À propos
        
            Proxima est une chaîne communautaire de vulgarisation scientifique sur l'astronomie, l'astronautique, et la conquête spatiale reliée au serveur discord du même nom.
            
            Le principe est simple : chaque membre du serveur peut aider à réaliser des vidéos sur les sujets qu'il VEUT en lien avec le thème de la chaîne.
            
            Chacun peut faire ce qu'il sait faire le mieux : montage, voix off, script, miniature, ect&#x2026;
            
            Pour plus de renseignements, rejoignez notre discord et abonnez-vous pour voir nos nouvelles vidéos.
        
        2.  Liens
        
            Notre Discord ! <http://discord.gg/vNSxxD6>
            Twitter  : <http://twitter.com/ProximAstro>
            Instagram : <http://instagram.com/proximastro>
            Facebook : <http://facebook.com/ProximaAstronomie>
            Twitch : <http://twitch.tv/proximastronomie>

