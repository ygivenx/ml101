# Running RStudio

* Go the (☰) navigation menu, expand `Projects` and click on the `RStudioPubmedTopicModeling` project pre-created for this section.

    [![(☰) Menu -> your project](../images/navigation/menu-projects.png)](../images/navigation/menu-projects.png)

* Open RStudio by clicking on `Launch IDE` and the `RStudio`.

    [![Open RStudio](../images/rstudio/rs-open-runtime.png)](../images/rstudio/rs-open-runtime.png)

* Select runtime `RStudio (2 vCPU and 2 GB RAM)` and click on `Launch` button.

    [![Select runtime](../images/rstudio/rs-select-runtime.png)](../images/rstudio/rs-select-runtime.png)


* Once the RStudio is open, click on the `project_data_asset` directory and click again to open the notebook

    [![Open assets](../images/rstudio/rs-open-assets.png)](../images/rstudio/rs-open-assets.png)

    [![Open notebook](../images/rstudio/rs-open-notebook.png)](../images/rstudio/rs-open-notebook.png)

* Sequentially from 1. to 6. run step by step clicking on the play button of each section
    
    1. **Load dependencies**
    1. **Fetch articles from Pubmed and persist dataset**. If this step fails you can still continue using the pre-loaded dataset.
    1. **Load and visualize articles dataset**
    1. **Prepare data**
    1. **Run LDA**. This can take a couple of minutes.
    1. **Generate visualization**

    [![Run step](../images/rstudio/rs-run-step.png)](../images/rstudio/rs-run-step.png)

* After step 6. successfully completes, you will see a new directory `serVis` under your `Files` tab on the lower right side. Click on `serVis`, then click on the `index.html` file and select `View in Web Browser`.

    [![Run step](../images/rstudio/rs-open-viz-1.png)](../images/rstudio/rs-open-viz-1.png)

    [![Run step](../images/rstudio/rs-open-viz-2.png)](../images/rstudio/rs-open-viz-2.png)

* A new window will open on your default browser. Feel free to play with the visualization you just generated.
    
    [![Run step](../images/rstudio/rs-lda-viz.png)](../images/rstudio/rs-lda-viz.png)