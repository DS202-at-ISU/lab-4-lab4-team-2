
<!-- README.md is generated from README.Rmd. Please edit the README.Rmd file -->

# Lab report \#4 - instructions

Follow the instructions posted at
<https://ds202-at-isu.github.io/labs.html> for the lab assignment. The
work is meant to be finished during the lab time, but you have time
until Monday (after Thanksgiving) to polish things.

All submissions to the github repo will be automatically uploaded for
grading once the due date is passed. Submit a link to your repository on
Canvas (only one submission per team) to signal to the instructors that
you are done with your submission.

# Lab 4: Scraping (into) the Hall of Fame

``` r
Hof <- Lahman::HallOfFame
Hof %>% 
  ggplot(aes(x = yearID, y = votes/needed*100, group=playerID)) +
  geom_hline(yintercept = 100, colour="grey70") + 
  geom_line() +
  geom_point(aes(colour = "inducted"), 
    data = Hof %>% filter(inducted=="Y")) +
  xlim(c(2000, 2022)) +
  ylab("Percent of votes")
```

    ## Warning: Removed 5465 rows containing missing values or values outside the scale range
    ## (`geom_line()`).

    ## Warning: Removed 284 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](README_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

``` r
#Hall of Fame Players Inducted From 1936 to 2024
Hof %>% 
  ggplot(aes(x = yearID, fill = inducted)) +
  geom_bar() +
  xlim(c(1936, 2024)) +
  labs(
    title = "Hall of Fame Players Inducted From 1936 to 2024",
    x = "Year",
    y = "Count"
  )
```

    ## Warning: Removed 4 rows containing missing values or values outside the scale range
    ## (`geom_bar()`).

![](README_files/figure-gfm/unnamed-chunk-1-2.png)<!-- -->

``` r
#Exporting csv File
write.csv(Hof, file="HallOfFame.csv", row.names = FALSE)
readr::write_csv(Hof, file="HallOfFame.csv")
```
