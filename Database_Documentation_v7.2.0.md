---
title: 'The Climate Equity Reference Calculator core database'
author:
  - Christian Holz
  - Tom Athanasiou
  - Sivan Kartha
date: 22 September 2018
geometry: a4paper, margin=1in
linestretch: 1.1
bibliography: Database_Documentation_v7.2.0.bib
csl: ieee-with-url-or-doi.csl
---
The database for the _Climate Equity Reference Calculator_[^cerc-note] includes 197 countries: 196 of the 196 state parties^[The UNFCCC has 197 parties, however, one of those is the European Union, which in our database is represented by its member states but in the calculator can also be examined as a single entity.] to the UNFCCC, plus Taiwan. Data for China, Macao, and Hong Kong, which are typically reported separately in most income and emissions databases, are combined.[^chk-gini-note] Likewise, we combine, where applicable, data for overseas dependencies of countries (e.g. we add Greenland and Faroe Island figures to Denmark).
The _Climate Equity Reference Calculator_ database is updated regularly with newly published data. The current calculator and published documentation are based primarily on data published up to March 2018 (see details below). For archival purposes it is database version 7.2.0.^[Starting with version 7.0 from 2015, all versions of the core database are available in the Havard Dataverse [@coredb_dataverse]]

[^cerc-note]: The Climate Equity Reference calculator is available at <a href="https://calculator.climateequityreference.org">https://calculator.climateequityreference.org</a> and its open source code can be inspected at <a href="https://github.com/climateequityreferenceproject/cerc-web/">https://github.com/climateequityreferenceproject/cerc-web/</a>.
[^chk-gini-note]: Our methodology for combining the Gini coefficients for these entities as a weighted sum of lognormal distributions is described in more detail in [@Kemp-Benedict_Athanasiou_Baer_Holz_Kartha_2018]


## Income (GDP)

Recent historical income (GDP) data comes primarily from the World Bank’s _World Development Indicators Online_ [@World_Bank_2018], as the highest priority source, which contains data for national income from 1960 to 2016 for almost all of the countries in the database. For most of the missing countries or territories, data comes from the _CIA World Factbook_ [@CIA_2017], as a second-order priority source, For data prior to 1960 or other missing years, data comes from the Maddison data set [@Maddison_2009; @Maddison-Project_2013; @Bolt_van_Zanden_2014]. Where data is available for a country for any year from a higher priority source, we use the slopes, rather than absolute values from lower priority sources to extend, or fill in, the time series.
Data is reported in $2010 US, at market exchange rates (MER). Conversion to PPP (2005) is based on converting “Current US Dollars” for 2005 to PPP (Current International Dollars). The PPP conversion rate is held constant at this value.

Income (GDP) projections from 2017-2022 are from the IMF’s _World Economic Outlook_ (October 2017 [@IMF_2017] and January 2018 update [@IMF_2018]). Each country’s IMF-projected growth rate is applied to the most recent World Bank national GDP data (in most cases 2016); long term estimates (2023 to 2050) are based on the median GDP growth rates across the models in the EMF27-Base-FullTech baseline scenario ensemble as reported in the IPCC AR5 scenario database that are available for the five IPCC world regions [@IPCC_2015].


## CO~2~ emissions (excluding LULUCF)

CO~2~ data for the period from 1850^[Emissions before 1850 are ignored because most of the other varibales required for our calculations have no reliably, country-level data sources for prior to 1850, and since pre-1850 emissions only represent about 3% of global cumulative CO~2~ emissions from fossil fuels, flaring and cement [@CDIAC].] through to 2015 comes from the _PRIMAP-hist_ database [@Gutschow_Jeffery_Gieseke_Gebel_2018; @Gutschow_Jeffery_Gieseke_Gebel_Stevens_Krapp_Rocha_2016], which is a well-documented, well-constructed, and well-maintained composite dataset compiled at the Potsdam Institute for Climate Impact Research (PIK). _PRIMAP-hist_, in turn, is based on various authoritative data sources including the UNFCCC, the Carbon Dioxide Information and Analysis Center (CDIAC), the EDGAR database and others. For Palestine, we use data from the _Global Carbon Budget_ dataset [@Le_Quere_Andrew_Friedlingstein_Sitch_Pongratz_Manning_Korsbakken_Peters_Canadell_Jackson_et_al._2018a; @Le_Quere_Andrew_Friedlingstein_Sitch_Pongratz_Manning_Korsbakken_Peters_Canadell_Jackson_et_al._2018b] directly, and subtract those figures from Israel’s value as _PRIMAP-hist_ reports those countries together.

Since one of the main purposes of the _Climate Equity Reference Calculator_ is the assessment of national climate action pledges (for example, as expressed in countries’ Nationally Determined Contributions (NDCs) under the Paris Agreement), we project baseline emissions starting after 2015, the year the Paris Agreement was adopted. For CO~2~ emissions, exclusive of emissions from Land Use, Land Use Change, and Forestry (LULUCF), these projections after 2015 are based on the median carbon intensity changes modelled in the EMF27-Base-FullTech scenario from the IPCC AR5 scenario database for each of the five IPCC regions [@IPCC_2015], combined with the GDP projections as described above. The EMF27-Base-FullTech scenario ensemble is chosen since it represents a very conventional baseline scenario that does not intentionally embed preferences for any particular technologies.

Our CO~2~ and non-CO~2~ (see below) baselines are jointly calibrated for their total to match the median baseline scenario of the _UNEP Emissions Gap Report 2016_ [@UNEP_2016] in 2030. Our calibration algorithm takes account of the different treatment of Annex I LULUCF emissions and emissions from international aviation and shipping in our database compared to the UNEP report.


## Non-CO~2~ Greenhouse Gases

Values for non-CO~2~ GHGs are also taken directly from the _PRIMAP-hist_ database [@Gutschow_Jeffery_Gieseke_Gebel_2018; @Gutschow_Jeffery_Gieseke_Gebel_Stevens_Krapp_Rocha_2016]. All non-CO~2~ greenhouse gases are converted into CO~2~ equivalents (CO~2~eq) using the 100-year Global Warming Potential (GWP-100) values from the IPCC’s Fourth Assessment Report (AR4). This represents a shift from previous versions of this database, where we used the values from the Second Assessment Report. This change is consistent with recent trends (e.g. within UNFCCC reporting methodologies) to shift to AR4 values.

Baseline projections for 2016 to 2050 for all countries are based on the median annual absolute rates of change reported in the IPCC AR5 scenario database for the models of the EMF27-Base-FullTech scenario by region [@IPCC_2015].


## CO~2~ from Land Use, Land Use Change and Forestry (LULUCF)

With this update we decided to remove support for calculations that include CO~2~ emissions from Land Use, Land Use Change, and Forestry (LULUCF) from the Climate Equity Reference Calculator. This decision has been taken for several reasons. First, LULUCF emissions data is subject to very large uncertainties and fluctuations, which in some cases are large enough to lead to opposite results, depending on the data source chosen. For example, for Annex I countries the UNFCCC data interface [@unfccc_data] reports removals three times as large in 2015 as the values of the _PRIMAP-hist_ database, which are in turn based on FAOSTAT [@faostat]. Further, including LULUCF emissions in a single framework together with CO~2~ emissions from fossil fuel and industry and non-CO~2~ gases, perpetuates the problematic view that emissions from LULUCF and other sources are essentially fungible and emissions reductions in either space perfectly equivalent, with profound implications, for example, with regards to speed of the decarbonization of the energy system and the treatment of nature primarily as a carbon sink.

We are exploring the possibility of including LULUCF emissions again in future releases, albeit only in the context of the calculation of historical responsibility. However, if you have a specific project where inclusion of LULUCF emissions is vital, please contact us and we can explore how we might be able to help. Furthermore, even though the Climate Equity Reference Calculator does not support LULUCF anymore, the calculator database still contains values for LULUCF emissions (obtained using the methodology described in the previous database description, but new source datasets), which will be included in the files generated by the calculator’s “download complete Excel table” functionality.


## Gini Coefficients

Gini coefficients for the majority of countries in the Equity Calculator database are taken from the World Income Inequality Database [@UNU-WIDER]. For countries which have reliable national or supranational sources (e.g., US Census Bureau, EU Europa database) newer Ginis are used where available. For some countries other sources are used, and for those for which no published figures are available, Gini coefficients are estimated on the basis of comparable countries.


## Population

Current, historical and projected population for most countries are taken from the United Nations Population Division’s medium variant [@United_Nations_2017].


## Calculating the RCI from the Equity Calculator dataset

The Climate Equity Reference Calculator sets a country’s fair share of the global climate effort in proportion to its Responsibility and Capacity Index, or _RCI_, which in turn is calculated from a country’s capacity and responsibility. Capacity for a given year is defined as the sum of the income of all individuals in the country, excluding the total income of everyone under a user-specified income level referred to as the development threshold. Central to the calculation is the commonly used assumption that national income distributions can be modeled as lognormal distributions.^[Wikipedia [@Wikipedia_2017] offers a good technical description of the lognormal distribution] The lognormal distribution has been shown to provide a reasonable approximation of measured income distributions [@Lopez_Serven_2006]. With this assumption, any national income distribution can be estimated with just a Gini Coefficient and the per-capita income. The Calculator’s initial setting for the development threshold is $7,500 per capita, PPP adjusted; so we will use that number in the following example. For people making more than $7,500 annually, only their income above that threshold counts towards the national measure of capacity (as a result, two countries with the same population and with the same per capita GDP will not have equal capacity; the country with the higher Gini coefficient has more income above the development threshold, and thus will have greater capacity). Responsibility is calculated in a similar manner. Emissions are calculated from income based on a user-specified elasticity, which is initially set to one (i.e., all individuals in a country have emissions proportional to income); thus, all emissions are excluded for those whose incomes are under the development threshold, and emissions equivalent to $7,500 of consumption at the national average carbon intensity are excluded for those with income over the threshold. Unlike the calculation of capacity, however, responsibility is calculated on a cumulative basis, starting at a user-specified initial year, so that responsibility in (say) 2030 is the sum of responsibility calculated in this way for each year from the specified start year to 2030. Capacity and responsibility are then expressed as a percentage of the global total, and combined into a single “Responsibility and Capacity Index” by taking a weighted average. In the Calculator, the Responsibility and Capacity weightings are initially set to be equal, but the calculator allows this to be user-specified, all the way from 100% Responsibility to 100% Capacity, to allow users to reflect their views that determining equitable shares of the global effort based on one of these factors alone is the appropriate ethical position to take.

A more detailed technical description of the algorithms and equations involved in these calculations is available elsewhere [@Kemp-Benedict_Athanasiou_Baer_Holz_Kartha_2018].

## References
