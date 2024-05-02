<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Metabolomic data</title>
</head>

<body>

    <h1>Metabolomic data</h1>

    <p>
        The data belong to a cohort of 22 healthy donors (11 male and 11 female) where each provided about 40 urine
        samples over the time course of approximately 2 months, for a total of 873 samples. Each sample was analysed by
        Nuclear Magnetic Resonance Spectroscopy. Each spectrum was divided in 450 spectral bins.
    </p>

    <h2>Tutorial</h2>

    <p>
        Here, we load the MetRef dataset. Columns with only zero values are removed.
    </p>

    <pre><code>
data(MetRef)
u=MetRef$data
u=u[,-which(colSums(u)==0)]
    </code></pre>

    <p>
        We apply the Probabilistic Quotient Normalization
    </p>

    <pre><code>
u=normalization(u)$newXtrain
    </code></pre>

    <p>
        We mean-center and univariate scaling the data set.
    </p>

    <pre><code>
u=scaling(u)$newXtrain
    </code></pre>

    <p>
        Two classification vectors are created
    </p>

    <pre><code>
class=as.numeric(as.factor(MetRef$gender))
class2=as.numeric(as.factor(MetRef$donor))
    </code></pre>

    <h2>MDS, tSNE and UMAP</h2>

    <p>
        Different algorithms for dimensionality reduction are applied
    </p>

    <pre><code>
res_MDS=cmdscale(dist(u))
res_tSNE=Rtsne(u)$Y
res_UMAP = umap(u)$layout
    </code></pre>

    <h2>KODAMA</h2>

    <p>
        We apply KODAMA with Partial Least Square Discriminant Analysis (PLS-DA) as classifier with 50 components to
        drive the accuracy maximixation. The KODAMA dissimilarity matrix's is converted in a low dimensionality space
        using three different methods (i.e., MDS, t-SNE, and UMAP).
    </p>

    <pre><code>
kk=KODAMA.matrix(u,f.par = 50)
res_KODAMA_MDS=KODAMA.visualization(kk,method = "MDS")
res_KODAMA_tSNE=KODAMA.visualization(kk,method = "t-SNE")
res_KODAMA_UMAP=KODAMA.visualization(kk,method = "UMAP")
    </code></pre>

    <h2>Visualize the different clustering algorithms:</h2>

    <p>a) labelled by the gender</p>

    <pre><code>
par(mfrow = c(2,3))
plot(res_MDS,pch=21,bg=rainbow(2)[class],main="MDS")
plot(res_tSNE,pch=21,bg=rainbow(2)[class],main="tSNE")
plot(res_UMAP,pch=21,bg=rainbow(2)[class],main="UMAP")
plot(res_KODAMA_MDS,pch=21,bg=rainbow(2)[class],main="KODAMA_MDS",)
plot(res_KODAMA_tSNE,pch=21,bg=rainbow(2)[class],main="KODAMA_tSNE")
plot(res_KODAMA_UMAP,pch=21,bg=rainbow(2)[class],main="KODAMA_UMAP")
    </code></pre>

    <p>
        <img src="https://github.com/tkcaccia/KODAMA/blob/main/figures/metabolites.gender.png" alt="Gender" />
    </p>

    <p>b) labelled by the donor</p>

    <pre><code>
plot(res_MDS,pch=21,bg=rainbow(22)[class2],main="MDS")
plot(res_tSNE,pch=21,bg=rainbow(22)[class2],main="tSNE")
plot(res_UMAP,pch=21,bg=rainbow(22)[class2],main="UMAP")
plot(res_KODAMA_MDS,pch=21,bg=rainbow(22)[class2],main="KODAMA_MDS",)
plot(res_KODAMA_tSNE,pch=21,bg=rainbow(22)[class2],main="KODAMA_tSNE")
plot(res_KODAMA_UMAP,pch=21,bg=rainbow(22)[class2],main="KODAMA_UMAP")
    </code></pre>

    <p>
        <img src="https://github.com/tkcaccia/KODAMA/blob/main/figures/metabolites.donor.png" alt="Donor" />
    </p>

</body>

</html>
