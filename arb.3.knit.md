---
title: "Drawing inference from statistical models, and statistical power"
format: html
editor_options: 
  chunk_output_type: console
---


*ARBEIDSKRAV 3*


::: {.cell}

:::

::: {.cell}
::: {.cell-output .cell-output-stdout}
```

Call:
lm(formula = y ~ 1, data = samp1)

Residuals:
    Min      1Q  Median      3Q     Max 
-6.5322 -1.2523 -0.0883  1.3540  4.8692 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)
(Intercept)    1.840      1.251    1.47    0.185

Residual standard error: 3.539 on 7 degrees of freedom
```
:::

::: {.cell-output .cell-output-stdout}
```

Call:
lm(formula = y ~ 1, data = samp2)

Residuals:
    Min      1Q  Median      3Q     Max 
-5.6557 -2.2883  0.2636  2.2549  6.4212 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)   
(Intercept)   1.5642     0.4774   3.276  0.00221 **
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 3.019 on 39 degrees of freedom
```
:::

::: {.cell-output .cell-output-stdout}
```

Call:
lm(formula = y ~ 1, data = samp1)

Coefficients:
(Intercept)  
       1.84  
```
:::

::: {.cell-output .cell-output-stdout}
```
[1] 1.839727
```
:::

::: {.cell-output .cell-output-stdout}
```
(Intercept) 
   1.839727 
```
:::

::: {.cell-output .cell-output-stdout}
```
[1] 3.539191
```
:::

::: {.cell-output .cell-output-stdout}
```
[1] 1.251293
```
:::
:::



**Explain the estimate, SE, t-value, and p-value from the regression models that we created previously (m1 and m2)**

En lineær regresjon har funksjonen $y = ax + b$ og består av et stigningstall/slope (a) og et konstantledd/intercept (b). Det er ikke alltid det er like åpenlyst hvordan likningen skal se ut, og vi er derfor nødt til å bruke den kunnskapen vi har til å estimere både slope og intercept. Dette gjøres ved at R genererer en likning som avviker minst mulig fra alle datapunktene. Da får vi et estimat til koeffisientene som forteller oss hvor langt unna virkeligheten den estimerte likningen er. I m1 er estimatet 1,290 og i m2 er det 1,4799. 

Standard error (SE) forteller oss noe om hvor usikker koeffisienten er, og brukes ofte til å lage konfidensintervall. SE regnes ut slik: 
$$SE = \frac{SD}{\sqrt{n}}$$

I m1 er SE 1,290 mens den er 1,480 i m2. Det er veldig like SE men m1 kan se ut til å være noe mer sikker enn m2 da SE er lavere. 

T-verdien er koeffisienten delt på SE. Vi vil gjerne at t-verdien skal være høy fordi det betyr at SE er lite sammenliknet med koeffisienten og vi kan være mer sikker på resultatet vårt. I m1 er t-verdien 0,94 og i m2 er den 3,953. T-verdien er videre brukt til å finne p-verdien.

P-verdien forteller oss hvorvoidt noe er statistisk signifikant eller ikke. Grensen er ofte satt til 0,05 eller 5%, og dersom p-verdien er lavere enn dette er det statostisk signifikant. Det p-verdien forteller oss er hvor sannsynlig det er at vi vil observere det vi observerte eller noe mer ekstremt dersom vi repeter prosessen igjen. I m1 er p-verdien 0,378 og i m2 er den 0,000315. Her er begge under 0,05 men m2 er tilnærmet lik null. 

**Discuss what contributes to the different results in the two studies (m1 and m2)**

Totalt har vi en populasjon på 100000 stk med individer som har vært gjennom to ulike behandlinger. Ut fra denne populasjonen velger vi ut to grupper. Den ene gruppen (m1) har 8 idivider mens den andre gruppen (m2) har 40. Til tross for at de to gruppene består av tilfeldige individer fra den orignale populasjonen, kan man ikke være sikker på at så små grupper representerer en hel populasjon da fordelingen i gruppene ikke nødvendivis tilsvarer fordelingen i populajsonen til tross for randomisering. Dette gjelder særlig m1 da hvert enkelt individ utgjør en mye større prosentandel av gruppen, som gir rom for større skjevheter enn hva som er tilfellet i den faktiske populajsonen. Et lite utvalg slik som i m1 vil også bety større grad av usikkerhet, som kommer frem i estimatet og SE. 

**Why do we use the shaded area in the lower and upper tail of the t-distribution**

Målet med statistikken er å si noe om en populasjon vha. et utvalg. Hvis utvalget er et tilfeldig utvalg fra populasjonen, har vi mulighet til å estimere egenskaper i populasjonen med en estimert usikkerhet. Figuren viser en normalfordelingskurve. Vi kan beregne hvor mange teoretiske utvalg som vil være mer ekstreme enn f.eks. 95% av alle utvalg, og det er dette som er de mørke områdene i figuren. Med gjentatte utvalg, vil 95% av alle konfidensintervall inneholde gjennomsnittet i populasjonen. De siste 5% er de mest ekstreme tilfellene. Slike figurer illustrerer bl.a. standardavvik og hvor grensen for statistisk signifikans går, som er de mest ekstreme 5%.


::: {.cell}

:::


**Using the "results" data frame, calculate the standard deviation of the estimate variable, and the average of the se variable for each of the study sample sizes (8 and 40). Explain why these numbers are very similar. How can you define the Standard Error (SE) in light of these calculations?**


::: {.cell}
::: {.cell-output .cell-output-stdout}
```
[1] 0.4696954
```
:::

::: {.cell-output .cell-output-stdout}
```
[1] 1.021374
```
:::

::: {.cell-output .cell-output-stdout}
```
[1] 0.4838475
```
:::

::: {.cell-output .cell-output-stdout}
```
[1] 1.070843
```
:::
:::


Gjennomsnittet til "se" i gruppen med 40 er ~0,470 eller 47% mens det i gruppen med 8 er ~1,021 eller 102%. Det er et stort standard error i begge gruppene, men et meget stort standard error i gruppen med kun 8 stk. Dette viser til hvor stor usikkerhet det er i "se" resultatene fra dataene. For eksempel kan resultatene i gruppen med 40 variere med 47% både opp og ned. 

Standardavviket til "estimate" i gruppen med 40 deltakere er ~0,484 mens det i gruppen med 8 er ~1,071. Standardavviket forteller oss om spredningen av dataene rundt gjennomsnittet. Et lavt standardavvik betyr at det er lite spredning mens et større standardavvik betyr en større spredning som betyr større usikkerhet. 

For både "estimate" og "se" ser vi at usikkerheten er mye større i gruppen med kun 8 sammenliknet med gruppen med 40. Dette bidrar til å vise hvor viktig utvalgsstørrelsen er for resultatene og med hvor stir sikkerhet vi kan stole på dataene. 

**Using the "results" data frame, create a histogram (see example code below) of the p-values from each study sample-size. How do you interpret these histograms, what do they tell you about the effect of sample size on statistical power?**


::: {.cell}
::: {.cell-output .cell-output-stderr}
```
`stat_bin()` using `bins = 30`. Pick better value with `binwidth`.
```
:::

::: {.cell-output-display}
![](arb.3_files/figure-html/unnamed-chunk-5-1.png){width=672}
:::

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
      n sig_results
  <dbl>       <dbl>
1     8       0.227
2    40       0.865
```
:::

::: {.cell-output .cell-output-stdout}
```

     One-sample t test power calculation 

              n = 40
              d = 0.5
      sig.level = 0.05
          power = 0.8693981
    alternative = two.sided
```
:::
:::


**Using the "results" data frame, calculate the number of studies from each sample size that declare a statistical significant effect (specify a threshold for "a" your significance level)**


::: {.cell}
::: {.cell-output-display}
```{=html}
<div id="cowkjyvvkq" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#cowkjyvvkq table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#cowkjyvvkq thead, #cowkjyvvkq tbody, #cowkjyvvkq tfoot, #cowkjyvvkq tr, #cowkjyvvkq td, #cowkjyvvkq th {
  border-style: none;
}

#cowkjyvvkq p {
  margin: 0;
  padding: 0;
}

#cowkjyvvkq .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#cowkjyvvkq .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#cowkjyvvkq .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#cowkjyvvkq .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#cowkjyvvkq .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#cowkjyvvkq .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#cowkjyvvkq .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#cowkjyvvkq .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#cowkjyvvkq .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#cowkjyvvkq .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#cowkjyvvkq .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#cowkjyvvkq .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#cowkjyvvkq .gt_spanner_row {
  border-bottom-style: hidden;
}

#cowkjyvvkq .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#cowkjyvvkq .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#cowkjyvvkq .gt_from_md > :first-child {
  margin-top: 0;
}

#cowkjyvvkq .gt_from_md > :last-child {
  margin-bottom: 0;
}

#cowkjyvvkq .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#cowkjyvvkq .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#cowkjyvvkq .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#cowkjyvvkq .gt_row_group_first td {
  border-top-width: 2px;
}

#cowkjyvvkq .gt_row_group_first th {
  border-top-width: 2px;
}

#cowkjyvvkq .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#cowkjyvvkq .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#cowkjyvvkq .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#cowkjyvvkq .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#cowkjyvvkq .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#cowkjyvvkq .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#cowkjyvvkq .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}

#cowkjyvvkq .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#cowkjyvvkq .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#cowkjyvvkq .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#cowkjyvvkq .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#cowkjyvvkq .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#cowkjyvvkq .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#cowkjyvvkq .gt_left {
  text-align: left;
}

#cowkjyvvkq .gt_center {
  text-align: center;
}

#cowkjyvvkq .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#cowkjyvvkq .gt_font_normal {
  font-weight: normal;
}

#cowkjyvvkq .gt_font_bold {
  font-weight: bold;
}

#cowkjyvvkq .gt_font_italic {
  font-style: italic;
}

#cowkjyvvkq .gt_super {
  font-size: 65%;
}

#cowkjyvvkq .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}

#cowkjyvvkq .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#cowkjyvvkq .gt_indent_1 {
  text-indent: 5px;
}

#cowkjyvvkq .gt_indent_2 {
  text-indent: 10px;
}

#cowkjyvvkq .gt_indent_3 {
  text-indent: 15px;
}

#cowkjyvvkq .gt_indent_4 {
  text-indent: 20px;
}

#cowkjyvvkq .gt_indent_5 {
  text-indent: 25px;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col" id="n">n</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col" id="antall">antall</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="n" class="gt_row gt_right">8</td>
<td headers="antall" class="gt_row gt_right">227</td></tr>
    <tr><td headers="n" class="gt_row gt_right">40</td>
<td headers="antall" class="gt_row gt_right">865</td></tr>
  </tbody>
  
  
</table>
</div>
```
:::
:::


I datasettet med 40 er det 865 som har en statistisk signifikant effekt, mens det i datasettet med 8 kun er 227 som har en statistisk signifikant effekt.

**Using the pwr package, calculate the power of a one-sample t-test, with a effect size of 1.5/3, your specified significance level and sample sizes 8 and 40. Explain the results in the light of your simulations**


::: {.cell}
::: {.cell-output .cell-output-stdout}
```

     One-sample t test power calculation 

              n = 40
              d = 0.5
      sig.level = 0.05
          power = 0.8693981
    alternative = two.sided
```
:::

::: {.cell-output .cell-output-stdout}
```

     One-sample t test power calculation 

              n = 8
              d = 0.5
      sig.level = 0.05
          power = 0.232077
    alternative = two.sided
```
:::
:::


For gruppene med både 40 og 8 er effektstørrelen (d) 0,5, mens "power" er ~0,869 i gruppen med 40 og ~0,232 i gruppen med 8. Testens "power" er et tall mellom 0 og 1 som indikerer hvor sannsynlig det er å observere en signifikant endring dersom den faktisk eksisterer en endring. Jo nærmere 1 "power" er, desto mer sannsynlig er det at testen klarer å påvise en endring. Her kommer et også frem at det er en stor forskjell mellom gruppen med 8 og gruppen med 40, der gruppen med 40 har en mye høyere power enn gruppen med 8.

**Using the new data frame with results from studies of a population with an average effect of zero, create new histograms with a significance level of 5%. How many studies would give you a “false positive” result if you did many repeated studies?**


::: {.cell}

:::

::: {.cell}
::: {.cell-output .cell-output-stderr}
```
`stat_bin()` using `bins = 30`. Pick better value with `binwidth`.
```
:::

::: {.cell-output-display}
![](arb.3_files/figure-html/unnamed-chunk-9-1.png){width=672}
:::
:::


Dersom vi har 2000 observasjoner, slik som i results_null, og signifikansnivået settes til 0,05 eller 5% kan vi anta at 100 av disse vil gi en falsk positiv. $0.05 * 2000 = 100$


