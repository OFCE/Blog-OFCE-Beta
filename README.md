
# Version du blog OFCE sous Quarto

Le blog de l'OFCE va prochainement évoluer pour pouvoir intégrer de nouveaux types de contenus (comme des graphes interactifs), mais également s'inscrire dans un processus de publication simplifié.
Il s'appuie sur l'éditeur de contenus scientifiques multi-langages [Quarto](https://quarto.org/), qui lui même s'intègre à des Logiciels d'interfacage comme [R Studio](https://posit.co/download/rstudio-desktop/) ou Visual Code Studio (https://code.visualstudio.com/) associé à une gestion des circuits de relecture et de mise en ligne qui elles se feront intégralement via  l'espace [GitHub](https://github.com/OFCE) de l'[OFCE](https://www.ofce.sciences-po.fr/)
Ses principes de fonctionnement découlent de ceux de [Markdown](https://www.markdownguide.org/), et permettent notamment de concilier plusieurs types de contenus (texte, images, code, liens) au sein d'un même script qui lui-même peut intégrer  différents langages.

Le fonctionnement du blog repose sur la compilation de plusieurs de ces scripts qui s'articulent autour d'une page d'accueil et des différents posts qui l'alimente comme le montre la structure du dossier repository du blog (voir la structure de fichiers du repository). 

# Post de blog sous Quarto 
La rédaction d'un post de blog se fait désormais intégralement sous ce format Quarto (extension .qmd), auquel est associé l'ensemble des fichiers et commandes qui en permettent la compilation pour produire sa version publiable.
Une version *simple*[^1] qui combine du texte avec des images (figures et tableaux) de post se trouve [ici](https://github.com/OFCE/Blog-OFCE-Beta/blob/main/posts/post_test/index.qmd), une autre, plus complexe, qui intègre des élements de code se trouve [là](https://github.com/OFCE/Blog-OFCE-Beta/blob/main/posts/post_test_2/post.qmd). 

La structure du script se décompose en deux parties. 
Une première qui est commune à l'ensemble des fichiers regroupe les *métadonnées* associées à chaque post, à savoir le titre du billet, son ou ses auteur.s, la langue, etc... (voir ci dessus le bloc de code) : 
  
```
  ---
  title: "L’effet des chocs conjoncturels sur le déficit commercial français"
  author:
    - name: Raul Sampognaro
      url: https://www.ofce.sciences-po.fr/pages-chercheurs/page.php?id=109
      affiliation: OFCE 
      affiliation-url: https://www.ofce.sciences-po.fr/
  date: "2022-11-09"
  categories: [conjoncture, commerce international, déficit commercial]
  subtitle: "L'économie française fait face à une multitude de chocs ayant un fort impact sur les perspectives de croissance du PIB. Au-delà de   la crise du pouvoir d'achat, ces chocs se sont traduits par la dégradation du solde extérieur français au point qu'au troisième trimestre       2022 la France a connu son plus fort déficit commercial depuis 1949 selon les comptes nationaux publiés par l'Insee : le solde commercial       s'établit à -- 4,6 % du PIB."
  image: "image.jpg"
  ---
``` 

La seconde regroupe le texte rédigé, qui inclut via des lignes de commande les différents types de contenus qui y sont associés (figures, tableaux, code). 
L'interface est légerement différente que celle proposée par les éditeurs de texte type word, mais intègre les principales fonctionnalités (italique, gras, mise en place de liste,...). 

Un fichier html sera ensuite généré directement à partir de ce script, en intégrant les élements de mise en forme, les contenus associés, et son intégration au site du blog. 

# Commandes principales

L'intégration de ces élements connexes se fait via des commandes spécifiques à Quarto. Celles qui seront le plus utilisé sont présentés à la suite de ce paragraphe et pour des fonctionnalités plus avancés, il est utile de se réferer directement au [guide officiel](https://quarto.org/docs/guide/) de Quarto.



## Intégrer une image
Pour intégrer une image, il suffit de renseigner un chemin d'accès qui renvoi vers un ficher image localisé dans le même dossier que celui du script qmd, en précisant le format utilisé en utilisant la commande suivante. 
```
![Image_1](image.png)
```

Des fonctions supplémentaires sont possibles et sont données sur cette [page](https://quarto.org/docs/authoring/figures.html) du guide Quarto


## Note de bas de page
L'intégration d'une note de bas de page peut se faire de deux façons. Une première où l'intégration de la note se fait via un indicateur de reference entre crochets [^1], à la place où elle se situe dans le texte, et ensuite cet indicateur est associé à la note en fin de texte. 
La seconde est plus directe et inscrit directement entre crochet la note. 
Les deux manières présentées ci-dessous sont équivalentes. 
```
L'économie française fait face à une multitude de chocs ayant un fort impact sur les perspectives de croissance du PIB[^1].
```

A la fin du texte:
```
[^1]: Département analyse et prévision de l'OFCE, sous la direction d'Éric Heyer et Xavier Timbeau, 2022, « Du coup de chaud au coup de froid : perspectives 2022-2023 pour l'économie mondiale », OFCE Policy brief, n° 109, 12 octobre.
```

ou alternativement:
```
L'économie française fait face à une multitude de chocs ayant un fort impact sur les perspectives de croissance du PIB^[Département analyse et prévision de l'OFCE, sous la direction d'Éric Heyer et Xavier Timbeau, 2022, « Du coup de chaud au coup de froid : perspectives 2022-2023 pour l'économie mondiale », OFCE Policy brief, n° 109, 12 octobre.].

```

Des fonctions supplémentaires sont possibles et sont données sur cette [page](https://quarto.org/docs/authoring/figures.html) du guide Quarto
