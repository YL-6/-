# Drinking-Water Quality: Regulatory and Domain Background

## 1. What counts as safe or potable water?

There is no single universal binary laboratory rule called "safe water".
Different concepts should be separated:

- **Potable/drinking water** generally means water suitable for human
  consumption.
- The WHO/UNICEF SDG concept of a **safely managed drinking-water service**
  concerns an improved source that is on premises, available when needed, and
  free from faecal and priority chemical contamination. It is a service-level
  indicator, not merely a list of chemical cut-offs.
- Under EU law, **water intended for human consumption** includes water used for
  drinking, cooking, food preparation, and other domestic purposes, whether
  supplied through a network, tanker, bottle, or container.

WHO guidelines are evidence-based international guidance used by countries to
develop standards. They are not themselves a directly enforceable global law.
In the EU, Directive (EU) 2020/2184 sets binding minimum requirements that
Member States transpose into national law; national rules may be stricter.

Safety is broader than the variables in this dataset. It includes:

- microbiological hazards;
- chemical hazards;
- radiological hazards;
- operational control and treatment;
- acceptability such as taste, odour, and appearance;
- monitoring from the catchment through treatment and distribution to the
  consumer.

## 2. Main authoritative frameworks

### World Health Organization

The current core reference is the *Guidelines for drinking-water quality:
fourth edition incorporating the first and second addenda*, published on
21 March 2022. WHO describes these guidelines as an authoritative basis for
national regulations and promotes health-based targets, catchment-to-consumer
water safety plans, and independent surveillance.

### European Union

Directive (EU) 2020/2184 is the EU's main drinking-water law. It entered into
force in January 2021 and Member States were required to transpose it by
12 January 2023. It uses a risk-based approach and covers microbiological,
chemical, and indicator parameters. EU rules also address emerging pollutants
such as PFAS.

## 3. Mapping the dataset to WHO and EU references

The table below assumes the common units used in drinking-water analysis. The
dataset documentation must confirm the actual units before numerical comparison.

| Dataset variable | EU Directive 2020/2184 | WHO interpretation | Project use |
|---|---:|---|---|
| pH | Indicator range 6.5-9.5 | No health-based guideline value; important for treatment, corrosion, and acceptability | Use range violation and continuous value |
| Iron | 200 micrograms/L = 0.20 mg/L, indicator parameter | No health-based guideline value at usual drinking-water levels; mainly acceptability/staining | Treat as indicator/operational, not automatically a toxic threshold |
| Nitrate | 50 mg/L | 50 mg/L as nitrate ion | Health-related threshold indicator |
| Chloride | 250 mg/L, indicator parameter | No health-based guideline value; high levels affect taste and corrosion | Acceptability/operational indicator |
| Lead | 10 micrograms/L until 12 January 2036; 5 micrograms/L thereafter | 10 micrograms/L provisional guideline value; exposure should be kept as low as reasonably practical | Health-related threshold; verify unit carefully |
| Zinc | No EU drinking-water parametric value in this Directive | No health-based guideline value; high levels affect acceptability | Do not present 3 mg/L as a legal EU limit |
| Color | Acceptable to consumers and no abnormal change | Acceptability parameter | Encode categorically; interpretation is ordinal only if justified |
| Turbidity | Acceptable and no abnormal change; also used operationally at treatment works | Low turbidity is important for effective disinfection; operational targets are context-dependent | Use continuous and possible operational threshold, not a universal health cut-off |
| Fluoride | 1.5 mg/L | 1.5 mg/L | Health-related threshold indicator |
| Copper | 2.0 mg/L | 2.0 mg/L | Health/acceptability threshold indicator |
| Odor | Acceptable to consumers and no abnormal change | Acceptability parameter | Encode carefully; confirm scale |
| Sulfate | 250 mg/L, indicator parameter | No formal health-based guideline value; high levels can affect taste and gastrointestinal tolerance | Indicator/acceptability threshold |
| Conductivity | 2,500 microsiemens/cm at 20 degrees C | No universal health-based guideline value | General mineralisation/operational indicator |
| Chlorine | The Directive regulates chlorate and chlorite separately; these are not the same as free chlorine | WHO guideline value for chlorine is 5 mg/L, while lower residual levels are used operationally for disinfection | Confirm whether the dataset means free residual chlorine; do not compare it with chlorate/chlorite limits |
| Manganese | 50 micrograms/L = 0.05 mg/L, indicator parameter | Provisional health-based guideline value 0.08 mg/L in the 2022 guidance | Compare EU indicator and WHO health-based values separately |
| Total Dissolved Solids | No EU parametric value in the Directive | No health-based guideline value; mainly palatability and scaling | Continuous acceptability/mineralisation indicator |
| Source | No single concentration limit | Risk depends on source, treatment, catchment, and distribution | Context variable, not proof of potability |
| Water Temperature | No dataset-wide EU potability limit | Influences microbial growth, taste, reactions, and treatment | Confirm unit and inspect implausible extremes |
| Air Temperature | No drinking-water parametric value | Environmental/contextual variable | Context variable |
| Month, Day, Time of Day | No direct potability limits | May capture seasonal or operational patterns | Context variables; watch for spurious associations |

## 4. What the dataset cannot establish

The dataset does not contain several decisive drinking-water parameters,
including *E. coli*, intestinal enterococci, arsenic, cadmium, nitrite,
pesticides, PFAS, and radiological indicators. Therefore:

> A model trained on this dataset predicts the dataset's `Target`; it does not
> certify that water is legally potable under WHO guidance or EU law.

The sampling point is also unknown. Drinking-water standards normally refer to
defined compliance points, whereas `Source` includes rivers, lakes, streams,
aquifers, wells, and reservoirs. Untreated source water and treated tap water
should not be interpreted as equivalent.

## 5. How regulatory knowledge should enter the analysis

Regulatory values can support three analytical layers:

1. **Descriptive layer:** calculate the proportion of observations above or
   outside reference values.
2. **Feature-engineering layer:** create clearly labelled exceedance indicators
   and exceedance ratios only after units are confirmed.
3. **Interpretation layer:** compare model importance with known health,
   operational, and acceptability parameters.

Do not define the target anew from the same thresholds unless the project
explicitly becomes a rule-based classification exercise. First test whether the
existing target was already generated from threshold exceedances.

## 6. Authoritative and selected peer-reviewed sources

- World Health Organization. [Guidelines for drinking-water quality: fourth
  edition incorporating the first and second addenda
  (2022)](https://www.who.int/publications/i/item/9789240045064)
- World Health Organization. [Drinking-water fact
  sheet](https://www.who.int/news-room/fact-sheets/detail/drinking-water)
- European Commission. [Drinking water policy and the recast Drinking Water
  Directive](https://environment.ec.europa.eu/topics/water/drinking-water_en)
- European Union. [Directive (EU) 2020/2184 on the quality of water intended for
  human consumption](https://eur-lex.europa.eu/eli/dir/2020/2184/oj/eng)
- U.S. Geological Survey. [pH and
  Water](https://www.usgs.gov/water-science-school/science/ph-and-water),
  [Turbidity and
  Water](https://www.usgs.gov/water-science-school/science/turbidity-and-water),
  and [Conductivity and
  Water](https://www.usgs.gov/water-science-school/science/conductivity-electrical-conductance-and-water)
- LeChevallier, M. W., Evans, T. M., and Seidler, R. J. (1981).
  [Effect of turbidity on chlorination efficiency and bacterial persistence in
  drinking water](https://doi.org/10.1128/AEM.42.1.159-167.1981).
  *Applied and Environmental Microbiology*, 42(1), 159-167.
- Ward, M. H. et al. (2018). [Drinking Water Nitrate and Human Health: An
  Updated Review](https://doi.org/10.3390/ijerph15071557).
  *International Journal of Environmental Research and Public Health*, 15(7),
  1557.
- Bouchard, M. F. et al. (2011). [Intellectual impairment in school-age
  children exposed to manganese from drinking
  water](https://doi.org/10.1289/ehp.1002321).
  *Environmental Health Perspectives*, 119(1), 138-143.
- Strobl, C. et al. (2007). [Bias in random forest variable importance
  measures: illustrations, sources and a
  solution](https://doi.org/10.1186/1471-2105-8-25).
  *BMC Bioinformatics*, 8, 25.
- Aas, K., Jullum, M., and Loland, A. (2021). [Explaining individual
  predictions when features are dependent: More accurate approximations to
  Shapley values](https://doi.org/10.1016/j.artint.2021.103502).
  *Artificial Intelligence*, 298, 103502.

## 7. Physicochemical Meaning and Interactions of Variables

This section translates the recorded variables into physicochemical meaning.
The expected relationships are hypotheses for analysis, not causal conclusions.
The data-specific comments are based on the initial audit of the supplied CSV.

| Variable | Domain interpretation | Expected relationship with `Target` and modelling implication |
|---|---|---|
| pH | pH measures acidity or alkalinity on a logarithmic scale. It affects metal solubility, pipe corrosion, chemical speciation, and chlorine disinfection. Low-pH water can dissolve metals more readily, while high pH can reduce chlorine effectiveness. | Expect a **nonlinear, approximately U-shaped** relationship: both low and high pH may be associated with `Target = 1`. In the full initial audit, 27.25% of class-1 samples but only 4.46% of class-0 samples were outside 6.5-9.5. Model pH with a quadratic term, spline, or regulatory-range indicator rather than only one linear coefficient. |
| Iron | Iron may originate from soil and rock weathering, reducing groundwater, treatment processes, or corrosion of iron pipes. It is often an acceptability and operational problem through colour, taste, staining, and deposits. | Expect higher iron to be positively associated with `Target = 1`, but not necessarily through direct toxicity. The class-1 mean was about 0.259 mg/L versus 0.071 mg/L in class 0. Iron may also help explain colour and turbidity. |
| Manganese | Manganese commonly enters water through geological sources and redox-controlled release from sediments or aquifers. It can cause colour and deposits, and sustained elevated exposure may also be a health concern. | Expect a positive, possibly threshold-like relationship. In the initial audit, 33.78% of class-1 samples and 5.53% of class-0 samples exceeded 0.05 mg/L. Test both the continuous concentration and a clearly labelled reference-value indicator. |
| Lead | Lead in drinking water often comes from service lines, solder, brass, or plumbing corrosion rather than directly from the raw-water source. Its concentration can depend strongly on pH and other corrosion-control conditions. | Expect higher lead to increase the probability of `Target = 1`, but the distribution is extremely right-skewed and contains many values near zero. Use `log1p`, robust scaling, or threshold indicators. Test a prespecified `pH x Lead` interaction. |
| Copper | Copper can come from natural minerals and corrosion of copper plumbing. Its release is affected by water chemistry, including pH and stagnation/contact conditions that are not recorded here. | Expect a positive and potentially nonlinear association. Copper was substantially higher in class 1, and values above 2 mg/L occurred in 7.63% of class-1 samples versus 1.25% of class-0 samples. Test `pH x Copper`. |
| Zinc | Zinc may originate from geological material, galvanised components, or corrosion. At drinking-water concentrations it is often more relevant to taste and acceptability than to direct health risk. | Expect a weaker positive relationship than for lead or manganese. Avoid calling zinc a legally unsafe contaminant without a matching regulatory value and verified unit. |
| Nitrate | Nitrate is highly soluble and commonly reflects agricultural fertiliser, manure, septic systems, wastewater, or oxidised nitrogen in groundwater. The regulatory limit was originally designed mainly to protect infants from methaemoglobinaemia. | Expect higher nitrate to be positively associated with `Target = 1`, although the dataset contains very few observations above 50 mg/L. The effect may therefore be gradual or may reflect the dataset's unknown label-generation rule rather than EU-limit exceedance alone. |
| Chloride | Chloride is a major dissolved ion that may reflect geology, wastewater, road salt, irrigation return flow, or saline influence. It affects taste and can contribute to corrosion and total mineralisation. | Expect a positive relationship at high values and possible overlap with TDS and conductivity. In this dataset, however, pairwise correlations with conductivity and TDS are unexpectedly weak, so this relationship must be tested rather than assumed. |
| Sulfate | Sulfate may derive from mineral dissolution, oxidation of sulfide minerals, industrial emissions, mine drainage, or wastewater. It contributes to dissolved solids and may affect taste or gastrointestinal tolerance at high concentrations. | Expect a positive or threshold-like association and possible redundancy with other dissolved-ion measures. The initial class-1 mean was about 160.7 mg/L versus 139.8 mg/L in class 0. |
| Fluoride | Fluoride can occur naturally through dissolution of fluoride-bearing minerals and can also be intentionally adjusted in some public supplies. Both insufficient and excessive exposure have different public-health meanings. | For this classification task, expect higher concentrations, especially above 1.5 mg/L, to be positively associated with `Target = 1`. Do not interpret low fluoride as automatically unsafe because the dataset label definition is unknown. |
| Turbidity | Turbidity measures light scattering by suspended particles and colloids. It can reflect erosion, runoff, sediment, metal precipitates, organic matter, or treatment failure. Particles can reduce disinfection efficiency and can shelter microorganisms. | Expect a strong positive and nonlinear association. Turbidity above 1 occurred in 27.29% of class-1 samples versus 6.52% of class-0 samples. Test its interaction with chlorine because a given chlorine level may be less effective when turbidity is high. |
| Color | Colour may arise from dissolved organic matter, iron, manganese, suspended material, or other compounds. It is primarily an acceptability indicator but can act as a proxy for unmeasured chemical processes. | Expect progressively more yellow categories to be associated with a higher probability of `Target = 1`. Treat `Color` as categorical unless the ordinal order is explicitly justified and checked. |
| Odor | Odour can reflect organic matter, algal metabolites, sulfur compounds, treatment chemicals, or contamination. The meaning of the dataset's numeric odour scale is not documented. | Expect higher odour scores to be associated with `Target = 1`, but interpretation remains provisional until the measurement scale is confirmed. |
| Conductivity | Conductivity measures the ability of water to conduct electrical current and normally increases with the concentration and mobility of dissolved ions. It is also temperature-dependent. | Domain knowledge suggests association with TDS and major ions. In this dataset, conductivity is almost identical across the target classes and its Pearson correlation with TDS is approximately zero in the current audit. Treat this as a data-quality or synthetic-data warning and do not force the expected relationship into the model. |
| Total Dissolved Solids (TDS) | TDS is an aggregate measure of dissolved inorganic and organic material. It is related to salinity, mineralisation, taste, scaling, and the sum of multiple ionic constituents. | Expect higher TDS to be associated with `Target = 1` and to overlap with conductivity, chloride, and sulfate. The target difference exists in this dataset, but the expected conductivity-TDS correlation is absent, which requires discussion. |
| Chlorine | If this field represents free residual chlorine, chlorine indicates disinfection capacity rather than a simple pollutant. Too little residual may provide inadequate protection, while very high levels may create taste, irritation, or by-product concerns. | Expect a potentially **non-monotonic** relationship. Confirm that the variable is free chlorine, not chlorate or chlorite. Test nonlinear terms and a `Turbidity x Chlorine` interaction rather than assuming that more chlorine is always worse. |
| Source | Source type represents different geological, land-use, microbial, and treatment contexts. Groundwater may show stronger mineral signatures, while surface water may be more responsive to runoff and turbidity. | Treat as a contextual categorical variable and possible effect modifier. The initial audit suggests little univariate separation between source categories, so it may become useful mainly through interactions rather than as a strong main effect. |
| Water and air temperature | Temperature affects reaction rates, gas solubility, microbial growth, chlorine decay, and conductivity measurements. Air temperature may also represent season or weather context. | Relationships may be nonlinear and context-dependent. The class means are almost identical in the initial audit, and implausible extremes require unit and data-quality checks before substantive interpretation. |
| Month, day, and time of day | These variables may capture seasonality, runoff, agricultural activity, temperature cycles, or operational sampling patterns. They are not contaminants themselves. | Month may be encoded cyclically using sine and cosine terms. The initial audit shows little univariate target separation by month, day, or time, so any detected importance should be checked carefully for sampling artefacts. |

## 8. Sources, Health Relevance, and Expected Relationships

### 8.1 Likely sources and health or operational relevance

| Parameter | Typical sources or processes | Main relevance in this project |
|---|---|---|
| Nitrate | Fertiliser, manure, septic systems, wastewater, and oxidation of nitrogen compounds | Direct health-related parameter; Ward et al. review infant methaemoglobinaemia and evidence concerning other health outcomes. |
| Lead and copper | Plumbing materials and corrosion, with water chemistry affecting release | Health-related metals; concentrations at the tap can reflect distribution-system conditions that are not represented by `Source`. |
| Iron and manganese | Geological minerals, reducing groundwater, sediment release, and pipe deposits/corrosion | Colour, staining, deposits, treatment problems, and, for manganese, potential health relevance at sustained elevated exposure. |
| Chloride and sulfate | Mineral dissolution, wastewater, road salt, irrigation return flow, industrial activity, or saline influence | Taste, corrosion, and general mineralisation; they can also contribute to TDS and conductivity. |
| Fluoride | Natural mineral dissolution, industrial sources, or deliberate adjustment in some water supplies | Health-related concentration range; excessive exposure is the relevant concern for the dataset's upper tail. |
| Turbidity, colour, and odour | Erosion, runoff, suspended sediment, metal precipitates, organic matter, algae, or treatment/distribution problems | Mainly indicator and operational variables. Turbidity can interfere with disinfection, as demonstrated experimentally by LeChevallier et al. |
| Conductivity and TDS | Combined dissolved ions from geology, pollution, salinity, and treatment | Aggregate mineralisation indicators rather than evidence of one specific contaminant. |
| Chlorine | Intentional disinfection and residual protection in distribution | Operational protection and possible acceptability/by-product concern; interpretation depends on the chemical form and sampling point. |

### 8.2 Relationships among indicators

Several variables describe overlapping processes rather than independent
causes:

- **Conductivity, TDS, chloride, and sulfate:** conductivity and TDS are broad
  mineralisation measures, while chloride and sulfate are individual ions that
  may contribute to both. Strong correlations are therefore scientifically
  plausible. However, the current data audit gives very weak Pearson
  correlations: conductivity-TDS is about `0.0003`,
  chloride-conductivity `-0.0008`, sulfate-conductivity `-0.0008`,
  chloride-TDS `0.035`, sulfate-TDS `0.022`, and chloride-sulfate `0.049`.
  This conflict with domain expectations should be presented as evidence that
  the data may be synthetic, independently generated by column, affected by
  undocumented units, or governed by an unknown construction process.
- **pH and metals:** pH controls metal solubility and corrosion chemistry, so
  interactions between pH and lead, copper, iron, or manganese are
  scientifically plausible. The raw linear correlations in this dataset are
  close to zero, but that does not exclude nonlinear or conditional effects.
  The analysis should test a small prespecified set of interaction terms rather
  than searching across every possible pair.
- **Turbidity, colour, iron, and manganese:** suspended particles and oxidised
  metal precipitates can increase turbidity and create visible colour. The
  initial data audit finds weak but positive correlations of turbidity with
  iron (`r` approximately `0.073`) and manganese (`r` approximately `0.080`).
  More yellow colour categories also appear more frequently in class 1.
- **Turbidity and chlorine:** turbidity can reduce effective disinfection by
  sheltering microorganisms or increasing disinfectant demand. Therefore the
  effect of chlorine may depend on turbidity even if each variable has a
  separate main effect.
- **Source, season, and chemical variables:** source type and month may change
  the background distribution of nitrate, dissolved ions, metals, and
  turbidity. They should be treated as contextual controls or possible effect
  modifiers, not as direct chemical hazards.

### 8.3 Multicollinearity and feature-importance precautions

For the inferential logistic-regression model:

1. Calculate a correlation matrix and variance inflation factors (VIFs) on the
   training data after finalising the predictor representation.
2. Use one reference category for each one-hot-encoded categorical variable to
   avoid the dummy-variable trap.
3. Treat `VIF < 5` as generally acceptable, `5-10` as requiring investigation,
   and `> 10` as strong multicollinearity. These are diagnostics, not automatic
   deletion rules.
4. If related variables are unstable, compare coefficient signs and confidence
   intervals across models, consider grouped interpretation, and use a
   regularised logistic regression as a sensitivity analysis.
5. Do not remove a scientifically important variable only because another
   variable can predict it. Record the scientific meaning of each alternative
   model.

Random-forest importance and SHAP values do **not** eliminate dependence
problems:

- Standard tree-based impurity importance can favour continuous variables or
  categorical variables with more possible split points, as shown by Strobl et
  al.
- When predictors are correlated or redundant, a model can substitute one for
  another. Importance may be divided between them, assigned mainly to one
  representative, or change across resamples.
- Standard SHAP implementations often rely on independence assumptions.
  Aas et al. show that ignoring predictor dependence can produce misleading
  explanations even for comparatively simple models.

The project should therefore compare three forms of evidence:

- standardized logistic-regression odds ratios and confidence intervals;
- permutation importance calculated on held-out data;
- SHAP values for the best nonlinear model, interpreted jointly for related
  feature groups.

No single ranking should be presented as the definitive causal importance of a
water-quality parameter.

## 9. Domain-Informed Hypotheses for Statistical Analysis

The hypotheses below are prespecified from domain knowledge and the initial data
audit. They concern associations with the dataset's `Target`, not causal effects
on real-world drinking-water safety.

### H1: pH has a nonlinear association with unsafe classification

- **Null hypothesis:** after adjustment for the other recorded variables, the
  probability of `Target = 1` does not vary with pH.
- **Alternative hypothesis:** observations at both low and high pH have a higher
  probability of `Target = 1` than observations in the central range.
- **Planned test:** compare a linear pH term with a quadratic term, restricted
  cubic spline, or indicators for `< 6.5`, `6.5-9.5`, and `> 9.5`. A single
  negative or positive linear coefficient is not an adequate test of this
  hypothesis.

### H2: turbidity and visible acceptability indicators are positively associated with `Target = 1`

- **Null hypothesis:** turbidity, colour, and odour provide no adjusted
  information about `Target`.
- **Alternative hypothesis:** higher turbidity, more visibly yellow colour, and
  higher odour scores are associated with a higher probability of `Target = 1`.
- **Planned test:** include turbidity as a transformed continuous variable and
  `Color` as a categorical variable; report global tests for the complete
  colour factor rather than only individual dummy-variable p-values.

### H3: elevated metal concentrations are positively associated with `Target = 1`

- **Null hypothesis:** iron, manganese, lead, copper, and zinc have no adjusted
  association with `Target`.
- **Alternative hypothesis:** higher concentrations, particularly of iron,
  manganese, lead, and copper, are associated with a higher probability of
  `Target = 1`.
- **Planned test:** use transformed continuous concentrations, standardized odds
  ratios, and a limited set of reference-value indicators. Because these
  variables are highly skewed, compare results before and after `log1p`
  transformation.

### H4: pH modifies the association between metals and `Target`

- **Null hypothesis:** the association of each selected metal with `Target` is
  constant across pH.
- **Alternative hypothesis:** the associations of lead, copper, iron, or
  manganese with `Target` vary with pH because acidity and alkalinity affect
  metal solubility and corrosion.
- **Planned test:** test only the prespecified interactions `pH x Lead`,
  `pH x Copper`, `pH x Iron`, and `pH x Manganese`, preferably with centred or
  spline-based pH. Apply a multiple-testing correction and retain the main
  effects whenever an interaction is included.

### H5: nitrate, chloride, sulfate, fluoride, and TDS provide positive but partly overlapping signals

- **Null hypothesis:** these dissolved-constituent variables provide no adjusted
  information about `Target`.
- **Alternative hypothesis:** higher values are associated with a greater
  probability of `Target = 1`, although their effects may be nonlinear and
  partly redundant.
- **Planned test:** compare continuous, transformed, and reference-value
  representations; examine VIFs and coefficient stability. Do not infer that a
  variable is unimportant merely because a correlated or composite variable
  receives more model importance.

### H6: the chlorine relationship depends on turbidity

- **Null hypothesis:** chlorine has no nonlinear effect and its association with
  `Target` does not depend on turbidity.
- **Alternative hypothesis:** chlorine has a non-monotonic association with
  `Target`, and high turbidity changes the apparent protective or risk-related
  pattern of chlorine.
- **Planned test:** after confirming the chemical definition of the field, test
  nonlinear chlorine terms and one prespecified `Turbidity x Chlorine`
  interaction. Interpret the result operationally, not as evidence that
  chlorine itself necessarily contaminates the water.

### H7: source and temporal variables mainly act as contextual controls

- **Null hypothesis:** `Source`, `Month`, `Day`, time of day, and temperature
  provide no additional information after physicochemical variables are
  included.
- **Alternative hypothesis:** at least some contextual variables retain an
  association or modify the effects of chemical variables.
- **Planned test:** use likelihood-ratio or joint Wald tests for each categorical
  block. Encode month and time cyclically where appropriate. Because the
  initial univariate differences are small, any large model importance should
  trigger a check for sampling artefacts or leakage.

### H8: feature-importance rankings are method-dependent

- **Null hypothesis:** the leading variables and their relative rankings are
  stable across inferential and predictive interpretation methods.
- **Alternative hypothesis:** rankings differ because of nonlinearity,
  interactions, correlated variables, scale, or algorithm-specific bias.
- **Planned test:** compare rankings from standardized logistic-regression
  effects, held-out permutation importance, and SHAP. Report stable feature
  groups and areas of disagreement rather than forcing one universal ranking.

For all hypotheses, emphasize effect sizes and 95% confidence intervals. With
approximately one million observations, very small and practically irrelevant
effects may produce extremely small p-values. Apply false-discovery-rate control
to families of exploratory tests and keep the confirmatory interaction set
small.
