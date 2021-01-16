# Introduction à Spark

## Utilisation du projet
Pour pouvoir exécuter les exemples de ce projet, il faut disposer d'un environnement Spark/Jupyter.
Plusieurs possibilités existent pour cela.

### Installation locale
Il faut installer [Spark](https://spark.apache.org/) et [Jupyter](https://jupyter.org/) puis connecter les deux.
Des tutoriels sont disponibles sur le web (par exemple [How to install PySpark and Jupyter Notebook in 3 Minutes](https://www.sicara.ai/blog/2017-05-02-get-started-pyspark-jupyter-notebook-3-minutes)).

Plutôt que d'utiliser un notebook, il est aussi possible d'exécuter les exemples avec `spark-shell` (Scala) ou avec `pyspark` (Python).

### Lancement d'un notebook Jupyter/Spark avec docker
Le [projet Jupyter](http://jupyter.org/) propose un ensemble d'[images docker](https://hub.docker.com/u/jupyter/) ([github](https://github.com/jupyter/docker-stacks)).
En particulier, l'image [all-spark-notebook](https://hub.docker.com/r/jupyter/all-spark-notebook/) intègre Spark et Jupyter.

```bash
docker run -it --rm -p 8888:8888 -v `pwd`:/home/jovyan jupyter/all-spark-notebook
```

### Utilisation d'un service en ligne
[Databricks](https://databricks.com/fr/spark/about) fournit un environnement gratuit pour des notebooks Spark nommé [Databricks Community](https://community.cloud.databricks.com/login.html).

## Construction du support de cours
Les slides sont au format [asciidoctor](http://asciidoctor.org/).

```bash
bundle install
rake
```

## Mettre à jour le projet
* La version de [`revealjs`](https://revealjs.com/) pour les slides est à configurer dans [`Rakefile`](./Rakefile)
* Les versions de [`asciidoctor`](https://asciidoctor.org/) sont configurables dans [`Gemfile`](./Gemfile) (cf. [rubygems.org](https://rubygems.org/?locale=fr))
    ```bash
    bundle update --bundler
    bundle update
    ```
