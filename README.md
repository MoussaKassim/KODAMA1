<KODAMA >
<html lang="fr">

<head>
    <meta charset="UTF-8">
    <meta name="generator" content="pandoc">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="author" content="stefano cacciatore">
    <meta name="date" content="2023-01-11">
    <title>Knowledge Discovery by Accuracy Maximization</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="site_libs/bootstrap-3.3.5/css/cosmo.min.css">
    <!-- Font Awesome CSS -->
    <link rel="stylesheet" href="site_libs/font-awesome-5.1.0/css/all.css">
    <link rel="stylesheet" href="site_libs/font-awesome-5.1.0/css/v4-shims.css">
    <!-- TOCify CSS -->
    <link rel="stylesheet" href="site_libs/tocify-1.9.1/jquery.tocify.css">
    <!-- Highlight.js CSS -->
    <link rel="stylesheet" href="site_libs/highlightjs-9.12.0/textmate.css">
    <!-- Custom CSS -->
    <style>
        /* Vos styles personnalisés ici */
    </style>
</head>

<body>

    <div class="container-fluid main-container">
        <div class="row">
            <div class="col-xs-12 col-sm-4 col-md-3">
                <div id="TOC" class="tocify"></div>
            </div>
            <div class="toc-content col-xs-12 col-sm-8 col-md-9">
                <div class="navbar navbar-default navbar-fixed-top" role="navigation">
                    <!-- Contenu de la barre de navigation -->
                </div>
                <div id="header">
                    <h1 class="title toc-ignore">Knowledge Discovery by Accuracy Maximization</h1>
                    <h4 class="author">Stefano Cacciatore</h4>
                    <h4 class="date">2023-01-11</h4>
                </div>
                <div id="Introduction" class="section level1">
                    <h1>Introduction</h1>
                    <p># KODAMA An unsupervised and semi-supervised learning algorithm to perform feature
                        extraction from noisy and high-dimensional data.</p>
                </div>
                <div id="News" class="section level1">
                    <h1>News</h1>
                    <p>KODAMA facilitates identification of patterns representing underlying groups on all
                        samples in a data set. This is an improved version of KODAMA algorithm for spatially-aware
                        dimensionality reduction. A landmarks procedure has been implemented to adapt the algorithm
                        to the analysis of data set with more than 10,000 entries. The KODAMA package has been
                        integrated with t-SNE and UMAP to convert the KODAMA's dissimilarity matrix in a low
                        dimensional space. [Zinga, M. M., Abdel-Shafy, E., Melak, T., Vignoli, A., Piazza, S.,
                        Zerbini, L. F., ... & Cacciatore, S. (2022). KODAMA exploratory analysis in metabolic
                        phenotyping. Frontiers in Molecular Biosciences, 9.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9887019/)
                        [Cacciatore, S., Tenori, L., Luchinat, C., Bennett, P. R., & MacIntyre, D. A. (2017).
                        KODAMA: an R package for knowledge discovery and data mining. Bioinformatics, 33(4),
                        621-623.](https://academic.oup.com/bioinformatics/article/33/4/621/2667156?login=false)
                        [Cacciatore, S., Luchinat, C., & Tenori, L. (2014). Knowledge discovery by accuracy
                        maximization. Proceedings of the National Academy of Sciences, 111(14), 5117-5122.](https://www.pnas.org/doi/abs/10.1073/pnas.1220873111)
                    </p>
                    <div id="Installation" class="section level2">
                        <h2>Installation</h2>
                        <p>The KODAMA is available on CRAN.</p>
                        <pre class="r"><code class="hljs">library(devtools)
install_github("tkcaccia/KODAMA")</code></pre>
                    </div>
                </div>
                <div id="Applications" class="section level2">
                    <h2>Applications</h2>
                    <p>Here below, we introduced three different applications of the KODAMA algorithm.</p>
                    <ol>
                        <li><a href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Metabolomics_data.md">Metabolomic
                                data</a></li>
                        <li><a href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Single_cell_RNA_seq.md">Single
                                cell RNA seq data</a></li>
                        <li><a href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Spatial%20_transcriptomic.md">Spatial
                                Transcriptomic data</a></li>
                    </ol>
                </div>
            </div>
        </div>
    </div>

    <!-- Bootstrap JavaScript -->
    <script src="site_libs/bootstrap-3.3.5/js/bootstrap.min.js"></script>
    <!-- jQuery -->
    <script src="site_libs/jquery-3.6.0/jquery-3.6.0.min.js"></script>
    <!-- jQuery UI -->
    <script src="site_libs/jqueryui-1.11.4/jquery-ui.min.js"></script>
    <!-- Highlight.js -->
    <script src="site_libs/highlightjs-9.12.0/highlight.js"></script>
    <!-- TOCify -->
    <script src="site_libs/tocify-1.9.1/jquery.tocify.js"></script>
    <!-- Navigation tabsets -->
    <script src="site_libs/navigation-1.1/tabsets.js"></script>
    <!-- Bootstrap shims for older browsers -->
    <script src="site_libs/bootstrap-3.3.5/shim/html5shiv.min.js"></script>
    <script src="site_libs/bootstrap-3.3.5/shim/respond.min.js"></script>
    <!-- Custom JavaScript -->
    <script>
        $(document).ready(function () {
            // Vos scripts personnalisés ici
            window.buildTabsets("TOC");
            $('.tabset-dropdown > .nav-tabs > li').click(function () {
                $(this).parent().toggleClass('nav-tabs-open');
            });
        });
        $(document).ready(function () {
            // Ajouter temporairement le sélecteur toc-ignore aux en-têtes pour la cohérence avec Pandoc
            $('.unlisted.unnumbered').addClass('toc-ignore')
            // Déplacer les sélecteurs toc-ignore des div.section aux en-têtes
            $('div.section.toc-ignore')
                .removeClass('toc-ignore')
                .children('h1,h2,h3,h4,h5').addClass('toc-ignore');
            // Établir les options
            var options = {
                selectors: "h1,h2,h3",
                theme: "bootstrap3",
                context: '.toc-content',
                hashGenerator: function (text) {
                    return text.replace(/[.\\/?&!#<>]/g, '').replace(/\s/g, '_');
                },
                ignoreSelector: ".toc-ignore",
                scrollTo: 0
            };
            options.showAndHide = true;
            options.smoothScroll = true;
            // TOCify
            var toc = $("#TOC").tocify(options).data("toc-tocify");
        });
    </script>
    <!-- MathJax pour la compatibilité avec les contenus autonomes -->
    <script>
        (function () {
            var script = document.createElement("script");
            script.type = "text/javascript";
            script.src = "https://mathjax.rstudio.com/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML";
            document.getElementsByTagName("head")[0].appendChild(script);
        })();
    </script>

</body>

</html>
