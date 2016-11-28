This is a direct replication of the code from [Karthik Ram's `wesanderson` palette](https://github.com/karthik/wesanderson) and [David Miller's `beyonce` palette](https://github.com/dill/beyonce)

But, I generated Colour Palettes using the wonderful and inspirational palettes from [colorlisa.com](http://www.colorlisa.com/)

Installation
------------

``` r
devtools::install_github("skiptoniam/artists")
```

Usage
-----

``` r
library(artists)
```

Here is a complete list of artworks and their colour palettes.

``` r
par(mfrow=c(26,5))
for(i in 1:128) print(artist_palette(i))
```

![](readme_files/figure-markdown_github/all_palettes-1.png)

My only slight tweek is an abilitiy to view the art work your colour palette is based on. This can be achieved by setting `see_painting = TRUE`

This is one of my favorites

    ## Adobe (Variant): Luminous Day by Josef Albers

    ## Warning: package 'jpeg' was built under R version 3.2.3

![](readme_files/figure-markdown_github/luminous_day_josef_albers-1.png)

``` r
library(ggplot2)
```

    ## Warning: package 'ggplot2' was built under R version 3.2.5

``` r
df <- data.frame(
  x = runif(100),
  y = runif(100),
  z1 = rnorm(100),
  z2 = abs(rnorm(100))
)
ggplot(df, aes(x, y)) +
  geom_point(aes(colour = z1,size=z2)) +
  scale_colour_gradientn(colours = artist_palette(1,100,type ='continuous'))  
```

![](readme_files/figure-markdown_github/unnamed-chunk-1-1.png)

I also really like this one too. Which seems to make nice plots.

    ## Golden Cloud by Gretchen Albrecht

![](readme_files/figure-markdown_github/golden_cloud_gretchen_albrecht-1.png)

Here is an example of using this colour palette in `ggplot`.

``` r
library(ggplot2)
ggplot(diamonds, aes(x = price, fill = cut)) +
  geom_histogram(position = "dodge", binwidth = 1000)+
  scale_fill_manual(values = artist_palette(3))
```

![](readme_files/figure-markdown_github/diamonds_w_golden_cloud-1.png)

Bauhaus Stairway by Oskar Schlemmer is awesome for heat maps.

    ## Bauhaus Stairway by Oskar Schlemmer

![](readme_files/figure-markdown_github/Bauhaustreppe1-1.png)

Here is an example using the old faithful dataset.

``` r
cols <- artist_palette(104,100,type ='continuous')
ggplot(faithfuld, aes(waiting, eruptions)) +
     geom_raster(aes(fill = density))+
     scale_fill_gradientn(colours = cols) 
```

![](readme_files/figure-markdown_github/Bauhaustreppe2-1.png)
