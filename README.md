# customLMS

## Customized LMS approach for FLPS models
- Customized EM algorithm is programmed for FLPS models based on `nlsem` pacakge.

- `customized_em.R` runs LMS for FLPS models (but there's no missing data. Missing data could be treated by FIML)
  - `mvtnorm` package is needed for normal density
  - `gaussquad` is needed for Hermite-Gaussian quadrature
  - `nlme::fdHess` is needed to compute Hessian matrix for SE
- `Custom_LMS.RDS` is a result of `customized_em.R`
- `Mplus_LMS.out` is a result of Mplus for benchmark
