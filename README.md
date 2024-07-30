# Table of Contents

1.  [Mon astronomie](#orgd8fb093)
    1.  [Mon journal d'observation](#orgfb872c8)
        1.  [Logiciel utilisé](#orgdf7236d)
        2.  [Configuration](#org6bb36d7)

<a id="orgd8fb093"></a>

# Mon astronomie


<a id="orgfb872c8"></a>

## Mon journal d'observation


<a id="orgdf7236d"></a>

### Logiciel utilisé

J'utilise pour mes journaux d'observation, le logiciel GNU Emacs, avec le mode org-mode


<a id="org6bb36d7"></a>

### Configuration

1.  .emacs

    Ajouter ces éléments de configuration dans votre .emacs.
    
    {% highlight elisp %}
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
    {% endhighlight %}
