<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <style>
        /* Navbar Styles */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            background-color: #333;
            border-radius: 0; /* Rounded rectangle */
        }
        /* Autres styles CSS */
    </style>
</head>
<body>

<!-- Navbar -->
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container">
        <a class="navbar-brand" href="#">KODAMA</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <!-- Contenu de la barre de navigation -->
        </div>
    </div>
</nav>

<!-- Sidebar -->
<div id="sidebar">
    <ul>
        <li id="introLink">Introduction</li>
        <li id="newsLink">News</li>
        <li id="installationLink">Installation</li>
        <li id="applicationsLink">Applications</li>
    </ul>
</div>

<!-- Metabolomic data Section -->
<section id="metabolomic-data">
    <div class="container">
        <h1>Metabolomic data</h1>
        <p> # Metabolomic data
            # Metabolomic data

The data belong to a cohort of 22 healthy donors (11 male and 11 female) where each provided about 40 urine samples over the time course of approximately 2 months, for a total of 873 samples. Each sample was analysed by Nuclear Magnetic Resonance Spectroscopy. Each spectrum was divided in 450 spectral bins.

## Tutorial

Here, we load the MetRef dataset. Columns with only zero values are removed. 

```
data(MetRef)
u=MetRef$data
u=u[,-which(colSums(u)==0)]
```
We apply the Probabilistic Quotient Normalization
```
u=normalization(u)$newXtrain
```
We mean-center and univariate scaling the data set.
```
u=scaling(u)$newXtrain
```
Two classification vectors are created
```
class=as.numeric(as.factor(MetRef$gender))
class2=as.numeric(as.factor(MetRef$donor))
```
# MDS, tSNE and UMAP
Different algorithms for dimensionality reduction are applied
```
res_MDS=cmdscale(dist(u))
res_tSNE=Rtsne(u)$Y
res_UMAP = umap(u)$layout
```
# KODAMA
We apply KODAMA with Partial Least Square Discriminant Analysis (PLS-DA) as classifier with 50 components to drive the accuracy maximixation. The KODAMA dissimilarity matrix's is converted in a low dimensionality space using three different methods (i.e., MDS, t-SNE, and UMAP).

```
kk=KODAMA.matrix(u,f.par = 50)
res_KODAMA_MDS=KODAMA.visualization(kk,method = "MDS")
res_KODAMA_tSNE=KODAMA.visualization(kk,method = "t-SNE")
res_KODAMA_UMAP=KODAMA.visualization(kk,method = "UMAP")
```

# Visualize the different clustering algorithmss:

  a) labelled by the gender

```
par(mfrow = c(2,3))
plot(res_MDS,pch=21,bg=rainbow(2)[class],main="MDS")
plot(res_tSNE,pch=21,bg=rainbow(2)[class],main="tSNE")
plot(res_UMAP,pch=21,bg=rainbow(2)[class],main="UMAP")
plot(res_KODAMA_MDS,pch=21,bg=rainbow(2)[class],main="KODAMA_MDS",)
plot(res_KODAMA_tSNE,pch=21,bg=rainbow(2)[class],main="KODAMA_tSNE")
plot(res_KODAMA_UMAP,pch=21,bg=rainbow(2)[class],main="KODAMA_UMAP")
```
<p>
  <p align="center">
    <img src="https://github.com/tkcaccia/KODAMA/blob/main/figures/metabolites.gender.png" alt="hello-light"  />
  </p>
</p>

  b) labelled by the donor

```
plot(res_MDS,pch=21,bg=rainbow(22)[class2],main="MDS")
plot(res_tSNE,pch=21,bg=rainbow(22)[class2],main="tSNE")
plot(res_UMAP,pch=21,bg=rainbow(22)[class2],main="UMAP")
plot(res_KODAMA_MDS,pch=21,bg=rainbow(22)[class2],main="KODAMA_MDS",)
plot(res_KODAMA_tSNE,pch=21,bg=rainbow(22)[class2],main="KODAMA_tSNE")
plot(res_KODAMA_UMAP,pch=21,bg=rainbow(22)[class2],main="KODAMA_UMAP")
```
<p>
  <p align="center">
    <img src="https://github.com/tkcaccia/KODAMA/blob/main/figures/metabolites.donor.png" alt="hello-light" />
  </p>
</p>


        </p>
    </div>
</section>

<!-- Vos scripts JavaScript -->
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.4/dist/umd/popper.min.js"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

<script>
    // JavaScript pour gérer le clic sur les éléments de la barre latérale et afficher la section metabolomic data
    $(document).ready(function(){
        $("#sidebar ul li").click(function(){
            var clickedItem = $(this).attr('id');
            if(clickedItem === "applicationsLink"){
                $('html, body').animate({
                    scrollTop: $("#metabolomic-data").offset().top
                }, 1000);
            }
        });
    });
</script>

</body>
</html>
