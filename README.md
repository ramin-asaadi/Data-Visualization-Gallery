# Data-Visualization-Gallery

### Significant increase of life expectancy over time  


```{r}
library(tidyverse)
library(ggpubr)
library(extrafont) # getting extra fonts

gapminder::gapminder %>%
  rename(Year = year) %>%
  filter(Year %in% c(1952, 2007), # years 1952 & 2007
         continent == "Asia") %>%
  mutate(paired = rep(1:(n()/2),each=2),
         Year=factor(Year)) %>%
  ggplot(aes(lifeExp, reorder(country, lifeExp))) +
  geom_line(aes(group = paired), color = "black") +
  geom_point(aes(color = Year), size = 5) +
  theme_pubclean() +
  scale_color_brewer(palette="Accent", direction = -1) +
  labs(title = "Life Expectancy in Aisa in 1952 & 2007",
       caption = "Plot by Ramin Asadi"
       ) +
  theme(axis.title.y = element_blank(),
        axis.title.x = element_blank(),
        text = element_text(family = "Palatino", face = "bold"))
```
