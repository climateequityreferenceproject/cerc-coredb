---
title: 'The Climate Equity Reference Calculator core database'
author:
  - Christian Holz
  - Tom Athanasiou
  - Sivan Kartha
date: 17 May 2022, v7.3.3
geometry: a4paper, margin=1in
linestretch: 1.1
bibliography: Database_Documentation_v7.3.3.bib
csl: ieee-with-url-or-doi.csl
---
The database for the _Climate Equity Reference Calculator_[^cerc-note] includes 197 countries: 196 of the 196 state parties[^eu-party-note] to the UNFCCC, plus Taiwan. Data for China, Macao, and Hong Kong, which are typically reported separately in most income and emissions databases, are combined.[^chk-gini-note] Likewise, we combine, where applicable, data for overseas dependencies of countries (e.g. we add Greenland and Faroe Island figures to Denmark).
The _Climate Equity Reference Calculator_ database is updated regularly with newly published data. The current calculator and published documentation are based primarily on data published up to May 2022 (see details below). For archival purposes it is database version 7.3.3.^[Starting with version 7.0 from 2015, all pubished versions of the core database are available in the Havard Dataverse [@coredb_dataverse].]

[^cerc-note]: The Climate Equity Reference calculator is available at <a href="https://calculator.climateequityreference.org">https://calculator.climateequityreference.org</a> and its open source code can be inspected on <a href="https://github.com/climateequityreferenceproject/cerc-web/">Github at https://github.com/climateequityreferenceproject/cerc-web</a>.
[^eu-party-note]: The UNFCCC has 197 parties, however, one of those is the European Union, which in our database is represented by its member states but in the calculator can also be examined as a single entity.
[^chk-gini-note]: Our methodology for combining the Gini coefficients for these entities as a weighted sum of lognormal distributions is described in more detail in [@Kemp-Benedict_Athanasiou_Baer_Holz_Kartha_2018].
[^no_forecase_countries_note]: For a small number of countries, the IMF WEO provides no or incomplete GDP projections, typically owing to highly uncertain political and/or economic situations. For these countries (Syria from 2011, Afghanistan and Lebanon from 2021, Ethiopia from 2022, Tunisia and Ukraine from 2023, and Venezuela from 2024), we use an arbitrary annual contraction rate of -10% for the missing years, until future IMF WEO updates resume projections for these countries. Additionally, due to the central role of GDP projections in our GHG baseline projections, we hold GHG emissions constant from these same years onwards. Owing to this, results for these countries should be interpreted with a high degree of caution.

## Income (GDP)

Recent historical income (GDP) data comes primarily from the World Bank’s _World Development Indicators Online_ [@Worldbank_2021], as the highest priority source, which contains data for national income from 1960 to 2020 for almost all of the countries in the database. For most of the missing countries or territories, data comes from the _CIA World Factbook_ [@CIA_2017], as a second-order priority source, For data prior to 1960 or other missing years, data comes from the Maddison data set [@Maddison_2009; @Maddison-Project_2013; @Bolt_van_Zanden_2014]. Where data is available for a country for any year from a higher priority source, we use the slopes, rather than absolute values from lower priority sources to extend, or fill in, the time series.
Data is reported in $2010 US, at market exchange rates (MER). Conversion to PPP (2005) is based on converting “Current US Dollars” for 2005 to PPP (Current International Dollars). The PPP conversion rate is held constant at this value.

Income (GDP) projections from 2021-2027 are from the IMF’s _World Economic Outlook_ (WEO), April 2022 [@WEO_Apr_2022].[^no_forecase_countries_note] Each country’s IMF-projected growth rate is applied to the most recent World Bank national GDP data (in most cases 2020); growth rates for long term estimates (2028 to 2030) are held constant at the value for 2027 from the IMF WEO database. Importantly, these data take the economic impact of the COVID-19 pandemic in to account, both in terms of the economic shock in 2020/21 as well as typically lower growth rate projectsions through 2027. The approach to use IMF WEO growth rates for 2027 as constants for the 2028-2030 period is a change from previous versions of the Climate Equity Reference Calculator database versions (v7.2 and earlier), where we extended the GDP growth rate time series beyond the horizon of the IMF WEO based on the median GDP growth rates across the models in the EMF27-Base-FullTech baseline scenario ensemble as reported in the IPCC's _Fifth Assessment Report_ (AR5) scenario database that are available for the five IPCC world regions [@IPCC_2015]. For the current database version, we considered the divergence of observed and IMF WEO-projected national growth rates, mostly due to the COVID-19 pandemic, compared to the regional-level data from the IPCC AR5 scenario database too large for the IPCC AR5 data to remain a suitable data source. This change in the GPD projection methodology for the years 2028-2030, combined with the IMF WEO-reported impacts of the COVID-19 pandemic on 2020/21 GDP and 2022-2027 projections, yields lower GDP projections and, consequently, lower GHG baseline projections than in previous Climate Equity Reference calculator database versions. E.g. the global level of projected CO~2~ emissions (excluding LULUCF) in 2030 was 46.7 Gt in database version 7.2 and is 42.4 Gt in this version v7.3.3.


## CO~2~ emissions (excluding LULUCF)

CO~2~ data for the period from 1850[^pre-1850-note] through to 2019 comes from the _PRIMAP-hist_ database [@PRIMAPhist_v2-3-1; @PRIMAPhist_MethArticle], which is a well-documented, well-constructed, and well-maintained composite dataset compiled at the Potsdam Institute for Climate Impact Research (PIK). _PRIMAP-hist_, in turn, is based on various authoritative data sources including the UNFCCC, the Carbon Dioxide Information and Analysis Center (CDIAC), the EDGAR database and others. For Palestine, we use data from the _Global Carbon Budget_ dataset [@GCP_2020_article; @GCP_2020_data] directly, and subtract those figures from Israel’s value as _PRIMAP-hist_ reports those countries together.

Since one of the main purposes of the _Climate Equity Reference Calculator_ is the assessment of national climate action pledges (for example, as expressed in countries’ Nationally Determined Contributions (NDCs) under the Paris Agreement), we project national baseline emissions starting after 2015, the year the Paris Agreement was adopted. For CO~2~ emissions, exclusive of emissions from Land Use, Land Use Change, and Forestry (LULUCF), these projections after 2015 are based on the median carbon intensity changes modelled in the EMF27-Base-FullTech scenario from the IPCC AR5 scenario database for each of the five IPCC regions [@IPCC_2015], combined with national GDP projections as described above.[^no-projection-countries-ghg-note] The EMF27-Base-FullTech scenario ensemble has been chosen since it represents a conventional baseline scenario that does not intentionally embed preferences for any particular technologies. It is worth noting that while we do not consider the EMF27-Base-FullTech baseline scenario ensemble to be a suitable data source for GDP projections anymore (see above), we continue to consider it suitable as a source of _baseline_ CO~2~ emissions intensity data because this type of data is not as volatile as GDP projections and, in particular, less sensitive to the impacts of the COVID-19 pandemic.

[^pre-1850-note]: Emissions before 1850 are ignored because most of the other variables required for our calculations have no reliable, country-level data sources for prior to 1850, and since pre-1850 emissions only represent about 0.3% of global cumulative CO~2~ emissions from fossil fuels, flaring and cement over the 1750-2020 period [@GCB_2020] and would therefore only have negligible impacts on results.
[^no-projection-countries-ghg-note]: For the seven countries for which the IMF WEO does not offer GDP projections (see above), and for which, therefore, this standard projection approach is unsuitable, we simply keep baseline emissions constant at the level of the last year for which the IMF WEO has data (see footnote above).

In previous database versions, we jointly calibrated our CO~2~ and non-CO~2~ (see below) baselines for their total to match the 2030 emissions in the median baseline scenario of the _UNEP Emissions Gap Report_ [@UNEP_2019]. However, the baseline projections of the current _Emissions Gap Report_ [@UNEP_2021] do not yet take the impact of the COVID-19 pandemic on baseline emissions into account. Therefore, for this current _Climate Equity Reference Calculator_ database version, we refrain from any calibration of baselines to external reference sources.


## Non-CO~2~ Greenhouse Gases

Values for non-CO~2~ GHGs are also taken directly from the _PRIMAP-hist_ database [@PRIMAPhist_v2-3-1; @PRIMAPhist_MethArticle]. All non-CO~2~ greenhouse gases are converted into CO~2~ equivalents (CO~2~eq) using the 100-year Global Warming Potential (GWP-100) values from the IPCC’s Fourth Assessment Report (AR4).

Baseline projections for 2016 to 2050 for all countries are based on the median annual absolute rates of change reported in the IPCC AR5 scenario database for the models of the EMF27-Base-FullTech scenario ensemble by region [@IPCC_2015].


## CO~2~ from Land Use, Land Use Change and Forestry (LULUCF)

This database update, like the versions since 7.2 before it, does not support Climate Equity Reference Calculator calculations that include CO~2~ emissions from Land Use, Land Use Change, and Forestry (LULUCF). This decision had been taken for several reasons. First, LULUCF emissions data is subject to very large uncertainties and fluctuations, which in some cases are large enough that for the same year and country one data source reports a land use sink while another reports a source. For example, for Annex I countries the UNFCCC data interface [@unfccc_data] reports removals three times as large in 2015 as the values of the _PRIMAP-hist_ database, which are in turn based on FAOSTAT [@faostat].[^primap-lulucf-note] Further, including LULUCF emissions in a single framework together with CO~2~ emissions from fossil fuel and industry and non-CO~2~ gases, presupposes the, in our view problematic, assumption that emissions from LULUCF and other sources are essentially fungible and emissions reductions in either space perfectly equivalent, with profound implications, for example, with regards to speed of the decarbonization of the energy system and the treatment of nature primarily as a carbon sink.

We are exploring the possibility of including LULUCF emissions again in future releases, albeit only in the context of the calculation of historical responsibility. However, users with specific projects where inclusion of LULUCF emissions is vital, should contact the authors to explore how this might be facilitated. Furthermore, even though the Climate Equity Reference Calculator does not support LULUCF anymore, the calculator database still contains values for LULUCF emissions (obtained using the approach described in the database description for core database v7.0, but with updated source datasets, where available). As a result, the LULUCF emissions time series will still be included in the files generated by the calculator’s “download complete Excel table” functionality but must be used with great caution.

[^primap-lulucf-note]: Starting with its v2.0 in December 2018, _PRIMAP-hist_ also stopped providing LULUCF data, for reasons similar to ours. This statement is based on data from the last _PRIMAP-hist_ version that still contained LULUCF data, v1.2. [@PRIMAPhist_v1-2]

## Gini Coefficients

Gini coefficients for the majority of countries in the Equity Calculator database are taken from the _World Income Inequality Database_ [@UNU-WIDER]. For countries which have reliable national or supranational sources (e.g., US Census Bureau, EU Europa database) newer Ginis are used where available. For some countries other sources are used, and for those for which no published figures are available, Gini coefficients are estimated on the basis of comparable countries.


## Population

Current, historical and projected population for most countries are taken from the 2019 Revision to the United Nations Population Division’s medium variant [@United_Nations_2019].


## Calculating the RCI from the Equity Calculator dataset

The Climate Equity Reference Calculator sets a country’s fair share of the global climate effort in proportion to its Responsibility and Capacity Index, or _RCI_, which in turn is calculated from a country’s capacity and responsibility. Capacity for a given year is defined as the sum of the income of all individuals in the country, excluding the total income of everyone under a user-specified income level referred to as the development threshold. Central to the calculation is the commonly-used assumption that national income distributions can be modeled as lognormal distributions. The lognormal distribution has been shown to provide a reasonable approximation of measured income distributions [@Lopez_Serven_2006]. With this assumption, any national income distribution can be estimated with just a Gini Coefficient and the per-capita income.

The Calculator’s initial setting for the development threshold is $7,500 per capita, PPP adjusted; so we will use that number in the following example. For people making more than $7,500 annually, only their income above that threshold counts towards the national measure of capacity (as a result, two countries with the same population and with the same per capita GDP will not have equal capacity; the country with the higher Gini coefficient has more income above the development threshold, and thus will have greater capacity).

Responsibility is calculated in a similar manner. Emissions are calculated from income based on a user-specified elasticity, which is initially set to one (i.e., all individuals in a country have emissions proportional to income); thus, all emissions are excluded for those whose incomes are under the development threshold, and emissions equivalent to $7,500 of consumption at the national average carbon intensity are excluded for those with income over the threshold. Unlike the calculation of capacity, however, responsibility is calculated on a cumulative basis, starting at a user-specified initial year, so that responsibility in (say) 2030 is the sum of responsibility calculated in this way for each year from the specified start year to 2030.

Capacity and responsibility are then expressed as a percentage of the global total, and combined into a single “Responsibility and Capacity Index” by taking a weighted average. In the Calculator, the Responsibility and Capacity weightings are initially set to be equal, but the calculator allows this to be user-specified, all the way from 100% Responsibility to 100% Capacity, to allow users to reflect their views that determining equitable shares of the global effort based on one of these factors alone is the appropriate ethical position to take.

A more detailed technical description of the algorithms and equations involved in these calculations is available elsewhere [@Kemp-Benedict_Athanasiou_Baer_Holz_Kartha_2018].

## References
