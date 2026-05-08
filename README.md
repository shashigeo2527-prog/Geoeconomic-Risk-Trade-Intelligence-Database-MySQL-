# Geoeconomic Risk & Strategic Trade Dependency Analysis

## Project Overview

This project is a SQL-based geoeconomic intelligence and strategic trade dependency analysis system designed to study international trade relationships, strategic commodity dependence, sanctions exposure, and supply chain vulnerabilities among countries.

The project integrates country-level macroeconomic indicators, international trade flow data, sanctions information, and strategic commodity analysis into a relational SQL database.

The primary objective of the project is to analyze:

* Which countries are strategically dependent on other countries
* Which commodities create major geopolitical and economic vulnerabilities
* Which countries face high sanctions exposure
* Which sectors have concentrated supply chain risks
* Which countries are economically vulnerable during geopolitical disruptions

The project focuses particularly on strategic sectors such as:

* Petroleum and crude oil
* Petroleum gases and LNG
* Rare earth elements
* Lithium and alkaline-earth metals
* Semiconductors and integrated circuits
* Critical minerals and technology commodities

The project was implemented entirely using SQL queries and analytical operations.

# Datasets Used

The project uses four datasets:
1. Countries Dataset
2. Trade Flows Dataset
3. Sanctions Dataset
4. Strategic Goods Dataset
   
# 1. Countries Dataset
 Dataset Source
Source: World Bank Open Data
The countries dataset contains macroeconomic and geopolitical information regarding countries across different regions.
**##Columns Used**
 country_id
* country_name
* iso_code
* region
* subregion
* gdp_usmill
* currency
* population
* political_all
* risk_level

## Purpose of Dataset

This dataset was used to:
* Analyze country-level geoeconomic risk
* Compare GDP and population among countries
* Categorize countries according to geopolitical risk levels
* Study political alignment patterns
* Identify economically vulnerable countries

The dataset was further used in SQL filtering and subquery analysis to identify countries with:
* High geopolitical risk
* Lower-than-average GDP
* Higher-than-average population

# 2. Trade Flows Dataset
## Dataset Source
Source: UN Comtrade Database
The trade flows dataset is the core dataset of the project and contains bilateral trade relationships between countries.
## Columns Used
* trade_id
* year
* importer_country
* exporter_country
* commodity
* trade_flow
* trade_value
* strategic_cat
* dependency_percent
* supply_risk
* vulnerability_score

## Strategic Commodity Categories Used
The project focused on strategic commodities and critical goods derived from UN Comtrade commodity classifications.
Major commodities analyzed include:

* Petroleum oils and oils obtained from bituminous minerals
* Petroleum gases and other gaseous hydrocarbons
* Coal; briquettes, ovoids and similar solid fuels
* Electronic integrated circuits
* Rare-earth metals, scandium and yttrium
* Alkaline or alkaline-earth metals
* Lithium and critical minerals

These commodities were grouped into strategic categories:
* Energy
* Technology
* Critical Minerals

## Purpose of Dataset
This dataset was used to:
* Analyze international trade dependency
* Identify countries highly dependent on strategic imports
* Study supply chain concentration
* Measure strategic vulnerability in trade flows
* Analyze energy and technology dependence

# Dependency Percentage Formula
The dependency percentage measures the level of dependence of a country on a particular trading partner.
## Formula

Dependency Percentage =
(Imports from a specific country / Total imports of commodity) × 100

Higher dependency percentage indicates:
* Greater import concentration
* Greater geopolitical vulnerability
* Greater supply chain dependence
# Supply Risk Score
The supply risk score represents the strategic and geopolitical risk associated with a commodity.
## Risk Scores Used

| Category          | Supply Risk Score |
| ----------------- | ----------------- |
| Critical Minerals | 10                |
| Technology        | 9                 |
| Energy            | 7                 |
| Other             | 4                 |

The scoring was assigned based on:
* Strategic importance
* Supply chain concentration
* Geopolitical sensitivity
* Global production concentration

# Vulnerability Score Formula
The vulnerability score combines trade dependency and supply chain risk.
## Formula
Vulnerability Score =
(Dependency Percentage × Supply Risk Score) / 10

Higher vulnerability score indicates:
* Higher geoeconomic exposure
* Greater strategic dependence
* Increased geopolitical risk
* Higher probability of supply disruption
# 3. Sanctions Dataset
## Dataset Source
Source: OFAC SDN (Specially Designated Nationals) Dataset
The sanctions dataset contains sanctions-related information imposed primarily by the United States.
Due to data availability limitations, the project focused mainly on sanctions imposed by OFAC-USA.
## Columns Used
* sanction_id
* sanctioned_entity
* entity_type
* sanction_program
* country
* sanctioning_authority
* sanctioninf_targeted
* severity_score
* sanction_year
## Severity Score
The severity score represents the intensity and strategic significance of sanctions.
Higher severity scores indicate:
* Stronger economic restrictions
* Higher geopolitical pressure
* Greater trade and financial limitations
## Purpose of Dataset
This dataset was used to:
* Analyze sanctions exposure among countries
* Identify countries facing military and economic sanctions
* Study geopolitical coercion through economic restrictions
* Analyze the relationship between sanctions and strategic sectors
Countries identified with high sanctions exposure include:

* Russia
* Belarus
* Iran
* Syria
* Venezuela
* North Korea

# 4. Strategic Goods Dataset
## Dataset Source
Source: UN Comtrade Commodity Classification Data
The strategic goods dataset contains information about strategically important commodities.
## Columns Used

* good_id
* good_name
* hs_code
* category
* strategic_imp_score
* supply_risk
## Purpose of Dataset
This dataset was used to:
* Categorize strategic commodities
* Measure supply risk concentration
* Analyze strategic importance of goods
* Compare commodity-level vulnerability

# SQL Analysis Performed
The project involved several SQL analytical operations:
* Filtering
* ORDER BY
* Aggregate Functions
* GROUP BY
* Subqueries
* Risk Analysis
* Trade Dependency Analysis
* Sanctions Analysis
# Major Query Results and Insights

## 1. High-Risk Countries with Lower-than-Average GDP

### Query Objective
To identify countries with:
* High geopolitical risk
* GDP lower than average GDP
* Population higher than average population

### Result

The query identified countries such as:

| Country | GDP (USD Million) | Population |
| ------- | ----------------- | ---------- |
| Ukraine | 160,503           | 42,973,696 |

### Insight

The analysis suggests that countries with relatively lower economic strength but large populations remain highly vulnerable to geopolitical instability and external shocks.

## 2. Energy Dependency Analysis
### Query Objective

To identify highly vulnerable energy trade relationships.

### Result

The analysis identified several energy trade flows with:

* Dependency percentages above 80%
* Vulnerability scores above 70

Examples included:

* Petroleum oils and bituminous minerals
* Petroleum gases and gaseous hydrocarbons
* Coal and solid fuel products

### Insight

Countries highly dependent on concentrated energy suppliers face elevated geoeconomic risks during geopolitical conflicts, trade disruptions, and supply chain shocks.

## 3. Vulnerability Score Analysis

### Query Objective

To rank trade flows according to strategic vulnerability.

### Result

The highest vulnerability scores were observed in:

| Strategic Category | Average Supply Risk |
| ------------------ | ------------------- |
| Critical Minerals  | 10                  |
| Technology         | 9                   |
| Energy             | 7                   |

Several trade flows showed vulnerability scores above 75.

### Insight

Technology commodities and critical minerals exhibited the highest strategic vulnerability due to concentrated global production and supply chain dependence.

## 4. Sanctions Analysis

### Query Objective

To analyze OFAC-USA sanctions and identify heavily targeted sectors.

### Result

The sanctions analysis identified:

* Russia as one of the most heavily sanctioned countries
* Military-targeted sanctions with severity scores up to 10
* High sanctions exposure among Belarus, Iran, Syria, Venezuela, and North Korea

### Insight

The analysis demonstrates how sanctions are increasingly used as geoeconomic instruments for exerting political and economic pressure.

## 5. Strategic Goods Risk Analysis

### Query Objective

To compare supply risk across strategic commodity categories.

### Result

| Category          | Average Supply Risk |
| ----------------- | ------------------- |
| Critical Minerals | 10.00               |
| Technology        | 9.00                |
| Energy            | 7.00                |

### Insight

Critical minerals and technology commodities represent the highest-risk strategic sectors because of:

* Concentrated production networks
* Limited supplier diversification
* High geopolitical sensitivity
* Dependence on critical supply chains


# Key Project Insights

## 1. Strategic Trade Dependency

The analysis showed that several countries remain highly dependent on a limited number of suppliers for strategic commodities such as petroleum products, petroleum gases, coal products, semiconductors, and rare-earth metals. Multiple trade flows showed dependency percentages above 80%, indicating concentrated import structures.

This demonstrates that countries with concentrated trade partnerships face significantly higher exposure to geopolitical disruptions, trade restrictions, and supply chain shocks.

---

## 2. Energy Vulnerability and Geoeconomic Exposure

The project identified that energy-related commodities exhibited some of the highest vulnerability scores within the dataset. Petroleum oils, bituminous mineral products, and gaseous hydrocarbons showed very high strategic exposure because of strong dependence on external suppliers.

The results indicate that countries heavily dependent on imported energy commodities remain vulnerable during geopolitical crises, sanctions, conflicts, and disruptions in global energy markets.

---

## 3. Critical Minerals and Technology Supply Risk

The strategic goods analysis showed that Critical Minerals and Technology commodities had the highest average supply risk scores.

| Category          | Average Supply Risk |
| ----------------- | ------------------- |
| Critical Minerals | 10.00               |
| Technology        | 9.00                |
| Energy            | 7.00                |

This reflects the fact that strategic commodities such as lithium, rare-earth elements, and semiconductors are concentrated within a limited number of global suppliers. Such concentration increases global dependence and creates long-term strategic vulnerability.

---

## 4. Sanctions as a Geoeconomic Instrument

The sanctions analysis revealed that countries such as Russia, Belarus, Iran, Syria, Venezuela, and North Korea had high sanctions exposure under OFAC-USA sanctions programs.

Military-targeted sanctions frequently carried severity scores reaching 10, indicating strong economic and geopolitical pressure. The analysis demonstrates how sanctions increasingly function not only as political tools, but also as mechanisms of economic coercion and strategic containment.

---

## 5. Country-Level Geoeconomic Risk Patterns

The country-level analysis identified several countries with high geopolitical risk, relatively lower GDP levels, and large populations. For example:

| Country | GDP (USD Million) | Population |
| Ukraine | 160,503           | 42,973,696 |

This suggests that countries with weaker economic capacity but significant population pressures may face higher vulnerability to geopolitical instability, economic shocks, and external dependence.

---

## 6. Overall Project Outcome

The overall analysis demonstrated that strategic trade relationships, commodity concentration, sanctions exposure, and supply chain dependence collectively contribute to geoeconomic vulnerability.

The project successfully showed how SQL-based trade analysis can be used to identify:

* vulnerable trade networks
* concentrated supply chains
* high-risk strategic sectors
* sanctions exposure patterns
* geopolitical economic dependencies

The project therefore provides a structured framework for understanding global geoeconomic risk and strategic economic interdependence.
