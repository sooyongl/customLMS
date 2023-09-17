
# customLMS

## Customized LMS approach for FLPS models

- Customized EM algorithm is programmed for FLPS models based on `nlsem`
  pacakge.

- `customized_em.R` runs LMS for FLPS models (but there’s no missing
  data. Missing data could be treated by FIML)

  - `mvtnorm` package is needed for normal density
  - `gaussquad` is needed for Hermite-Gaussian quadrature
  - `nlme::fdHess` is needed to compute Hessian matrix for SE

- `Custom_LMS.RDS` is a result of `customized_em.R`

- `Mplus_LMS.out` is a result of Mplus for benchmark

## Data

    #> # A tibble: 1,069 × 6
    #>      x1    x2    x3    x4    x5    y1
    #>   <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
    #> 1  1.5   1.5   1     3      2   1    
    #> 2  1.75  2     1.67  2.67   1.5 0.778
    #> 3  3.75  3.25  3.67  2      2.5 1.22 
    #> 4  1.5   1.75  2     3.67   3   0.333
    #> 5  3.75  3.25  3     2.33   1.5 0.556
    #> # ℹ 1,064 more rows

## Model

- 3 continuous indicators (x1-x3 same as v1-v3)
- One cavariate (x5 same as x)
- Treatment assignment (x4 same as z)

<img src="Picture1.png" width="100%" />

## EM algorithm for LMS

- `customized_em.R`

## Results

    #>           paramHeader param Mplus_LMS Customized_LMS
    #> 1               F1.BY    V2     1.043          1.041
    #> 2               F1.BY    V3     0.909          0.924
    #> 3                Y.ON    F1     0.240          0.217
    #> 4                Y.ON     Z     0.113          0.092
    #> 5                Y.ON     X    -0.002          0.001
    #> 6  Residual.Variances    V1     0.088          0.096
    #> 7  Residual.Variances    V2     0.123          0.124
    #> 8  Residual.Variances    V3     0.129          0.129
    #> 9  Residual.Variances     Y     0.060          0.060
    #> 10          Variances    F1     0.488          0.470
    #> 11            F1.WITH     Z     0.084          0.082
    #> 12            F1.WITH     X     0.108          0.105
    #> 13         Intercepts    V2    -0.308         -0.292
    #> 14         Intercepts    V3    -0.080         -0.112
    #> 15         Intercepts     Y     0.137          0.202
    #> 16              Means    F1     2.698          2.634
    #> 17               Y.ON   F1Z    -0.027         -0.020

## Session info

    #> R version 4.2.1 (2022-06-23 ucrt)
    #> Platform: x86_64-w64-mingw32/x64 (64-bit)
    #> Running under: Windows 10 x64 (build 19045)
    #> 
    #> Matrix products: default
    #> 
    #> locale:
    #> [1] LC_COLLATE=Korean_Korea.utf8  LC_CTYPE=Korean_Korea.utf8   
    #> [3] LC_MONETARY=Korean_Korea.utf8 LC_NUMERIC=C                 
    #> [5] LC_TIME=Korean_Korea.utf8    
    #> 
    #> attached base packages:
    #> [1] stats     graphics  grDevices utils     datasets  methods   base     
    #> 
    #> other attached packages:
    #>  [1] forcats_0.5.2         stringr_1.4.1         dplyr_1.1.3          
    #>  [4] purrr_0.3.5           readr_2.1.3           tidyr_1.2.1          
    #>  [7] tibble_3.2.1          ggplot2_3.4.0         tidyverse_1.3.2      
    #> [10] MplusAutomation_1.1.0
    #> 
    #> loaded via a namespace (and not attached):
    #>  [1] httr_1.4.4          bit64_4.0.5         vroom_1.6.0        
    #>  [4] jsonlite_1.8.3      gsubfn_0.7          modelr_0.1.9       
    #>  [7] assertthat_0.2.1    highr_0.9           pander_0.6.5       
    #> [10] googlesheets4_1.0.1 cellranger_1.1.0    yaml_2.3.6         
    #> [13] pillar_1.9.0        backports_1.4.1     lattice_0.20-45    
    #> [16] glue_1.6.2          digest_0.6.30       checkmate_2.1.0    
    #> [19] rvest_1.0.3         colorspace_2.0-3    htmltools_0.5.3    
    #> [22] plyr_1.8.8          pkgconfig_2.0.3     broom_1.0.1        
    #> [25] haven_2.5.1         xtable_1.8-4        scales_1.2.1       
    #> [28] tzdb_0.3.0          googledrive_2.0.0   generics_0.1.3     
    #> [31] ellipsis_0.3.2      withr_2.5.0         cli_3.4.1          
    #> [34] proto_1.0.0         magrittr_2.0.3      crayon_1.5.2       
    #> [37] readxl_1.4.1        evaluate_0.17       fs_1.5.2           
    #> [40] fansi_1.0.3         xml2_1.3.3          tools_4.2.1        
    #> [43] data.table_1.14.4   hms_1.1.2           gargle_1.2.1       
    #> [46] lifecycle_1.0.3     munsell_0.5.0       reprex_2.0.2       
    #> [49] compiler_4.2.1      rlang_1.1.0         grid_4.2.1         
    #> [52] rstudioapi_0.14     texreg_1.38.6       rmarkdown_2.17     
    #> [55] boot_1.3-28         gtable_0.3.1        DBI_1.1.3          
    #> [58] R6_2.5.1            lubridate_1.8.0     knitr_1.40         
    #> [61] bit_4.0.4           fastmap_1.1.0       utf8_1.2.2         
    #> [64] stringi_1.7.8       parallel_4.2.1      Rcpp_1.0.9         
    #> [67] vctrs_0.6.2         fastDummies_1.6.3   dbplyr_2.2.1       
    #> [70] tidyselect_1.2.0    xfun_0.34           coda_0.19-4
