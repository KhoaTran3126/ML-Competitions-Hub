# R Tutorial
A folder for tutorials in R.

## R setup
<pre>
  <code>
library(tidyverse)
library(GGally) # use ggpairs(columns=c(...)) for pair plots of predictors
library(patchwork)
library(data.table)
library(marginaleffects)
library(emmeans)
library(MASS)
library(car)
library(lme4) #  Use boot_summary(lmer_model, type = "perc") from library(boot.pval) for p-values
library(mgcv) # use gam, gam.check(), plot(), plot_predictions()
library(bayesplot) # use bayes_R2(brm_model), mcmc_acf(as.array(brm_model), pars = vector_slope_intercept_names)
library(brms) # use brm, prior_summary(), posterior_summary(), pp_check(), plot(), plot_predictions(), conditional_effects(), print(loo(brm_model))

theme_custom <- theme_classic() +
                theme(## Axis labels
                      axis.text.y  = element_text(size=16, face="bold", color="#333333"),
                      axis.text.x  = element_text(size=20, color="#333333"),
                      ## Title, subtitle, caption, legend
                      plot.title   = element_text(size=26, face="bold", color="#333333"),
                      plot.subtitle = element_text(size=23, color="#333333"),
                      plot.caption = element_text(size=12, colour="#333333", hjust=0),
                      legend.position = "top",
                      legend.text = element_text(size=20),
                      legend.title = element_blank(),
                      legend.key.spacing.x = unit(1.0, "cm"),
                      axis.title.x = element_text(size=20, margin=margin(t=10,b=10)),
                      axis.title.y = element_text(size=20, margin=margin(l=10,r=10)),
                      strip.text = element_text(size=20),
                      ## axis lines
                      panel.grid.major.y = element_line(color="#6F8793"),
                      axis.ticks.y = element_blank(),
                      axis.ticks.x = element_blank(),
                     )
                     
figsize <- function(width=22, height=8){
    options(repr.plot.width=width, repr.plot.height=height)
}
figsize()
  </code>
</pre>


