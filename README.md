# english-devolution
Centre for Cities' proposal for reform of local government and local finance

## Getting Started
This repo contains the map and associated shapefiles, council tax workbook and scripts, and geography lookup for MSOAs for the English devolution proposal. Each of these is 

### Dependencies

STATA, R, RStudio, Windows 10, Updated Postcode Lookup, qgis

Price paid data: https://www.gov.uk/government/statistical-data-sets/price-paid-data-downloads

Postcode lookup:https://geoportal.statistics.gov.uk/datasets/ons::national-statistics-postcode-lookup-2011-census-november-2023/about

## The Council Tax Proposals

### Getting Started

The modelling in this briefing takes the same methodology used to model council tax reform within In Place of Centralisation and our Welsh council tax briefing and scales it England-wide. circumstances. In essence, the revenues raised by the current council tax system in 2023 are used to set the estimated revenues under a new system where, after revaluation, a hypothetical set of percentage-based tax rates for each council tax band and local authority.

The workbook uses some shorthand to make it easier to navigate the workbook:

* LA - Local authority council tax bills
* CA - Combined authority/GLA/PCC council tax precepts
* Combo - Both of these added together

* URBA - Proposal borough/county geography
* URSA - Proposal metro mayor geography

Upon opening the workbook, you will see the tool as shown on the Centre for Cities website. The results tabs shows how the hypothetical tax rates set out in the Modelling section change bills and how many households benefit.

These are estimates of the tax rate levied on properties of the average price in each band. They therefore make assumptions about the council tax bill faced by a property of that price in each authority and weight accordingly. For this reason, the percentage of properties that benefit from council tax cuts in this workbook and those in the "Results" tab will not always align,. The estimates in the Results tab are tighter as they do not rely on these assumptions.

### Council Tax Methodology

The council tax bills for each band in each local authority in England in 2023 (including police precepts but excluding community council precepts) are multiplied by the number of homes in each band to generate an estimate of total revenues in 2023 under the current system.

For simplicity’s sake, the current council tax bands are kept and revalued by 397 per cent, which is how much house prices have increased in Wales by from 1992 to 2003. House price data from transactions is then used to generate an estimate of the number of homes within each Welsh local authority that fall into each revalued band. Three new bands are created - A+, I, and J.

The median house price within each band (with conservative estimates for Bands A+ and J) is then multiplied by the number of houses within each revalued band to estimate the total value of all Welsh residential property by band by local authority. 

A hypothetical set of percentage tax rates by band is then applied to each local authority to raise a near-equal amount of revenue to the current estimated revenue for council tax.

To estimate for how this then changes bills for households, the model needs to account for how revaluation changes the bands of individual dwellings. It therefore assumes that the current distribution of bands by local authority maps onto the current distribution of prices, such that if 15 per cent of dwellings in Somerset are currently in Band A, then the prices of the 15 per cent cheapest properties in Somerset are the prices of its Band A properties, and so on. 

These current bands are then joined to the revalued bands by price to generate an estimate for how many properties of each current band are in each revalued band. The change in bills is then calculated for each possible combination of current and revalued bands by local authority, which is then used to generate an estimate for how many households see their council tax bills rise and fall after revaluation in the new hypothetical revalued council tax structure.

Council tax reliefs (such as the single adult discount, exemptions for students)  are not explicitly taken into account in this model, but can be easily incorporated by policymakers.

Many of the equilibrium effects (e.g. effects on house prices) set out in the IFS report will have similar directional effects as in this proposal (e.g. higher/lower council tax bills will decrease/increase property values), but the magnitude will vary depending on the choices made by each local authority.

### Understanding the Scripts

There are currently two scripts in this folder that process the price paid data

* Wales Script - A STATA script that produces the 2022 revaluation, as well as the collapsed version of the join between 2003 and 2022 bands

* Council Tax Bands Assign - an R script that joins the 2003 bands to the 2022 bands

