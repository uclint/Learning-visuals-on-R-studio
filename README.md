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

![image](https://user-images.githubusercontent.com/86573734/128097387-363a8c71-b05c-4c94-b9d0-98205cd76bcc.png)


    ggplot(data=penguins, mapping = aes(x= flipper_length_mm, y = body_mass_g)) + geom_point()

 ![image](https://user-images.githubusercontent.com/86573734/128097465-8220c22b-68e7-4f5d-b8f7-d557b3c2d901.png)

    ggplot(penguins, aes(flipper_length_mm, body_mass_g))+geom_point()
    
![image](https://user-images.githubusercontent.com/86573734/128097479-790db66b-8357-448b-8420-76b46c2b5467.png)


## Facet\_wrap

Using facet wrap to create multiple chart plots to view each specie
seperately

    ggplot(data = penguins) +
      geom_point(mapping = aes(x = flipper_length_mm, y = body_mass_g, color = species)) + 
      facet_wrap(~species)

![image](https://user-images.githubusercontent.com/86573734/128097528-eedfa6a6-75c9-431e-8479-934f28651478.png)


## facet\_grid

    ggplot(data = penguins)+
      geom_point(mapping = aes(x = flipper_length_mm, y = body_mass_g, color = species)) +
      facet_grid(species~sex)

![image](https://user-images.githubusercontent.com/86573734/128097597-dbbef80a-c09d-444d-93c9-382ddf599478.png)


## labels and annotations

Adding titles, subtitles and captions to plots

    ggplot(data = penguins)+
      geom_point(mapping = aes(x = flipper_length_mm, y = body_mass_g, color = species))+
      labs(title = "Palmer Penguins: Body Mass vs Flipper Length", subtitle = "Sample of Three Penguin Species", caption = "Data collected by Dr. Kristen Gorman")+
      annotate("text", x = 220, y = 3500, label = "The Gentoos are the largest", color = "gold", fontface = "bold")
![image](https://user-images.githubusercontent.com/86573734/128097636-bf7a3e75-9480-44a3-8e09-fcb59fccaa29.png)

