# Learning-visuals-on-R-studio
## Setting up my environment

Notes: loading R packages necessary for visuals.including the “palmer
penguins” packages

    library(tidyverse)

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.5     v purrr   0.3.4
    ## v tibble  3.1.2     v dplyr   1.0.7
    ## v tidyr   1.1.3     v stringr 1.4.0
    ## v readr   1.4.0     v forcats 0.5.1

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

    library(ggplot2)
    library(palmerpenguins)

## Scatterplot

Trying out different ggplot format for a scatter plot showing
relationship between flipper length and body mass

    ggplot(data = penguins)+ geom_point(mapping = aes(x=flipper_length_mm, y = body_mass_g))

    ## Warning: Removed 2 rows containing missing values (geom_point).

![](Visuals_files/figure-markdown_strict/unnamed-chunk-1-1.png)

    ggplot(data=penguins, mapping = aes(x= flipper_length_mm, y = body_mass_g)) + geom_point()

    ## Warning: Removed 2 rows containing missing values (geom_point).

![](Visuals_files/figure-markdown_strict/unnamed-chunk-1-2.png)

    ggplot(penguins, aes(flipper_length_mm, body_mass_g))+geom_point()

    ## Warning: Removed 2 rows containing missing values (geom_point).

![](Visuals_files/figure-markdown_strict/unnamed-chunk-1-3.png)

## Facet\_wrap

Using facet wrap to create multiple chart plots to view each specie
seperately

    ggplot(data = penguins) +
      geom_point(mapping = aes(x = flipper_length_mm, y = body_mass_g, color = species)) + 
      facet_wrap(~species)

    ## Warning: Removed 2 rows containing missing values (geom_point).

![](Visuals_files/figure-markdown_strict/unnamed-chunk-2-1.png)

## facet\_grid

    ggplot(data = penguins)+
      geom_point(mapping = aes(x = flipper_length_mm, y = body_mass_g, color = species)) +
      facet_grid(species~sex)

    ## Warning: Removed 2 rows containing missing values (geom_point).

![](Visuals_files/figure-markdown_strict/unnamed-chunk-3-1.png)

## labels and annotations

Adding titles, subtitles and captions to plots

    ggplot(data = penguins)+
      geom_point(mapping = aes(x = flipper_length_mm, y = body_mass_g, color = species))+
      labs(title = "Palmer Penguins: Body Mass vs Flipper Length", subtitle = "Sample of Three Penguin Species", caption = "Data collected by Dr. Kristen Gorman")+
      annotate("text", x = 220, y = 3500, label = "The Gentoos are the largest", color = "gold", fontface = "bold")

    ## Warning: Removed 2 rows containing missing values (geom_point).

![](Visuals_files/figure-markdown_strict/unnamed-chunk-4-1.png)
