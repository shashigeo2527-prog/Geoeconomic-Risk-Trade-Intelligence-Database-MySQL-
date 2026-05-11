SQL-Based Geoeconomic Intelligence and Strategic Trade Dependency Analysis System

Project Overview

This project is a SQL-based geoeconomic intelligence and strategic trade dependency analysis system designed to study international trade relationships, strategic commodity dependence, sanctions exposure, and supply chain vulnerabilities among countries.
The project integrates country-level macroeconomic indicators, international trade flow data, sanctions information, and strategic commodity analysis into a relational SQL database.
The primary objective of the project is to analyze:
Which countries are strategically dependent on other countries
Which commodities create major geopolitical and economic vulnerabilities
Which countries face high sanctions exposure
Which sectors have concentrated supply chain risks
Which countries are economically vulnerable during geopolitical disruptions


The project focuses particularly on strategic sectors such as:
Petroleum and crude oil
Petroleum gases and LNG
Rare earth elements
Lithium and alkaline-earth metals
Semiconductors and integrated circuits
Critical minerals and technology commodities
The project was implemented entirely using SQL queries and analytical operations.


---

Datasets Used
The project uses four datasets:
1. Countries Dataset
2. Trade Flows Dataset
3. Sanctions Dataset
4. Strategic Goods Dataset

---

1. Countries Dataset
Dataset Source
Source: World Bank Open Data
The countries dataset contains macroeconomic and geopolitical information regarding countries across different regions.

Columns Used
country_id
country_name
iso_code
region
subregion
gdp_usmill
currency
population
political_all
risk_level


Purpose of Dataset

This dataset was used to:
Analyze country-level geoeconomic risk
Compare GDP and population among countries
Categorize countries according to geopolitical risk levels
Study political alignment patterns
Identify economically vulnerable countries
The dataset was further used in SQL filtering and subquery analysis to identify countries with:

High geopolitical risk
Lower-than-average GDP
Higher-than-average population


2. Trade Flows Dataset
Dataset Source
Source: UN Comtrade Database
The trade flows dataset is the core dataset of the project and contains bilateral trade relationships between countries.
Columns Used
trade_id
year
importer_country
exporter_country
commodity
trade_flow
trade_value
strategic_cat
dependency_percent
supply_risk
vulnerability_score

Strategic Commodity Categories Used
The project focused on strategic commodities and critical goods derived from UN Comtrade commodity classifications.
Major commodities analyzed include:
Petroleum oils and oils obtained from bituminous minerals
Petroleum gases and other gaseous hydrocarbons
Coal; briquettes, ovoids and similar solid fuels
Electronic integrated circuits
Rare-earth metals, scandium and yttrium
Alkaline or alkaline-earth metals
Lithium and critical minerals


These commodities were grouped into strategic categories:
Energy
Technology
Critical Minerals
Purpose of Dataset
This dataset was used to:
Analyze international trade dependency
Identify countries highly dependent on strategic imports
Study supply chain concentration
Measure strategic vulnerability in trade flows
Analyze energy and technology dependence

Dependency Percentage Formula
Dependency Percentage = (Imports from a specific country / Total imports of commodity) × 100

Higher dependency percentage indicates:
Greater import concentration
Greater geopolitical vulnerability
Greater supply chain dependence


Supply Risk Score

The supply risk score represents the strategic and geopolitical risk associated with a commodity.
Category	Supply Risk Score

Critical Minerals	10
Technology	9
Energy	7
Other	4


The scoring was assigned based on:
Strategic importance
Supply chain concentration
Geopolitical sensitivity
Global production concentration


Vulnerability Score Formula

Vulnerability Score = (Dependency Percentage × Supply Risk Score) / 10

Higher vulnerability score indicates:
Higher geoeconomic exposure
Greater strategic dependence
Increased geopolitical risk
Higher probability of supply disruption


3. Sanctions Dataset

Dataset Source
Source: OFAC SDN (Specially Designated Nationals) Dataset
The sanctions dataset contains sanctions-related information imposed primarily by the United States.
Due to data availability limitations, the project focused mainly on sanctions imposed by OFAC-USA.

Columns Used
sanction_id
sanctioned_entity
entity_type
sanction_program
country
sanctioning_authority
sanctioninfo_targeted
severity_score
sanction_year


Severity Score
The severity score represents the intensity and strategic significance of sanctions.
Higher severity scores indicate:
Stronger economic restrictions
Higher geopolitical pressure
Greater trade and financial limitations

Purpose of Dataset
This dataset was used to:
Analyze sanctions exposure among countries
Identify countries facing military and economic sanctions
Study geopolitical coercion through economic restrictions
Analyze the relationship between sanctions and strategic sectors


Countries identified with high sanctions exposure include:
Russia
Belarus
Iran
Syria
Venezuela
North Korea

---

4. Strategic Goods Dataset

Dataset Source
Source: UN Comtrade Commodity Classification Data
The strategic goods dataset contains information about strategically important commodities.

Columns Used
good_id
good_name
hs_code
category
strategic_imp_score
supply_risk

Purpose of Dataset
This dataset was used to:
Categorize strategic commodities
Measure supply risk concentration
Analyze strategic importance of goods
Compare commodity-level vulnerability

---

SQL Analysis Performed

The project involved several SQL analytical operations:
Filtering
ORDER BY
Aggregate Functions
GROUP BY
Subqueries
Risk Analysis
Trade Dependency Analysis
Sanctions Analysis
_______________

Major Query Results and Insights

1. Country-Level Geoeconomic Risk Analysis
Query Objective
To identify countries with:
High geopolitical risk
GDP lower than the global average
Population higher than the global average


SQL Logic Used
The analysis used subqueries with AVG() functions to compare country GDP and population against overall averages.

Result Table
Country	GDP (USD Million)	Population	Risk Level
Ukraine	160,503	42,973,696	High


Insight
The analysis identified Ukraine as a country with high geopolitical risk despite having lower-than-average economic strength and a relatively large population base. Such countries are more vulnerable to:

Economic shocks
External dependence
Conflict-related instability
Supply disruptions
This demonstrates how geopolitical risk can significantly affect economically weaker but strategically important states.

---

2. GDP Ranking Analysis
Query Objective
To rank countries according to GDP size.
SQL Logic Used

SELECT *
FROM countries
ORDER BY gdp_usmill DESC;

Sample Results
Country	GDP (USD Million)
United States	25,462,700
China	17,963,171
Japan	4,231,141
Germany	4,072,192
India	3,385,090


Insight
The analysis highlights the concentration of global economic power among a small group of countries. Larger economies generally possess:
Higher strategic resilience
Greater supply chain diversification
Stronger geopolitical influence
Lower external dependency risks
However, even major economies remain vulnerable in sectors such as semiconductors, energy, and critical minerals.

---

3. Trade Dependency Analysis

Query Objective
To identify trade flows with high dependency percentages.
SQL Logic Used
SELECT *
FROM trade_flows
ORDER BY dependency_percent DESC;

Key Findings
Several trade relationships showed dependency percentages above 80%, indicating highly concentrated import structures.
Strategic Commodities Identified
Petroleum oils and bituminous minerals
Petroleum gases and LNG
Coal and solid fuels
Electronic integrated circuits
Rare-earth metals
Lithium and critical minerals


Insight
High dependency percentages indicate:
Import concentration
Supplier dominance
Elevated geopolitical exposure
Increased supply chain vulnerability
Countries heavily dependent on a limited number of suppliers become highly exposed during sanctions, trade wars, conflicts, or geopolitical crises.

---

4. Energy Dependency Analysis
Query Objective

To analyze highly vulnerable energy trade relationships.
SQL Logic Used

SELECT *
FROM trade_flows
WHERE strategic_cat = 'energy'
ORDER BY dependency_percent DESC;

Key Commodities Identified
Commodity
Petroleum oils and oils obtained from bituminous minerals
Petroleum gases and other gaseous hydrocarbons
Coal and solid fuel products

Result Highlights
Several energy-related trade flows showed:

Dependency percentages above 80%
Extremely high trade values
High vulnerability scores

Insight
Energy commodities showed some of the highest strategic vulnerabilities in the database. Countries dependent on imported energy face significant risks from:
Supply disruptions
Maritime chokepoints
Sanctions
Geopolitical conflicts
Export restrictions
The results demonstrate the strategic importance of energy security in geoeconomic policy.

---

5. Vulnerability Score Analysis

Query Objective
To rank trade flows according to vulnerability score.
SQL Logic Used

SELECT *
FROM trade_flows
WHERE dependency_percent > 50
ORDER BY dependency_percent DESC;

Result Highlights
Several trade flows recorded vulnerability scores above 70, particularly in:
Technology commodities
Critical minerals
Energy products


Insight

Higher vulnerability scores indicate:
Strong supplier concentration
Strategic commodity dependence
Elevated supply chain risk
Greater geopolitical exposure
Technology and critical mineral sectors exhibited especially high vulnerability because production is concentrated within a small number of countries globally.

---

6. USA Trade Flow Analysis

Query Objective
To analyze trade flows involving the United States.
SQL Logic Used

SELECT *
FROM trade_flows
WHERE importer_country = 'USA'
OR exporter_country = 'USA';

Key Strategic Sectors Identified
Strategic Category
Technology
Energy
Critical Minerals


Insight
The United States was heavily involved in:
Semiconductor trade
Energy imports and exports
Critical mineral trade

This demonstrates the central role of the US within global strategic trade networks and highlights the importance of maintaining resilient supply chains for strategic goods.

---

7. Strategic Goods Risk Analysis

Query Objective
To compare supply risk across strategic commodity categories.
SQL Logic Used

SELECT category,
ROUND(AVG(supply_risk),2) AS avg_supply_risk
FROM strategicgoods
GROUP BY category
ORDER BY avg_supply_risk DESC;

Result Table
Category	Average Supply Risk
Critical Minerals	10.00
Technology	9.00
Energy	7.00


Insight

Critical minerals and technology commodities exhibited the highest supply risks because of:
Concentrated production networks
Limited supplier diversification
High geopolitical sensitivity
Strategic military and technological importance
These sectors represent major long-term geoeconomic vulnerabilities globally.

---

8. Combined Strategic Risk Analysis

Query Objective
To calculate combined strategic importance and supply risk.
SQL Logic Used

SELECT good_name,
strategic_imp_score,
supply_risk,
(strategic_imp_score + supply_risk) AS combined_risk
FROM strategicgoods
ORDER BY combined_risk DESC;

Result Table
Commodity	Strategic Importance Score	Supply Risk	Combined Risk

Lithium	10	10	20
Rare Earth Elements	10	10	20
Semiconductor Chips	10	9	19
Integrated Circuits	10	9	19
Crude Oil	9	8	17
LNG	8	7	15
Coal	7	6	13


Insight
Lithium, rare-earth elements, semiconductors, and integrated circuits emerged as the most strategically sensitive commodities because they are essential for:
Advanced technology production
Energy transition systems
Defense manufacturing
Semiconductor industries
Electric vehicle production
The concentration of these commodities within limited supplier networks creates major long-term geopolitical and geoeconomic vulnerabilities.

---

9. Sanctions Exposure Analysis
Query Objective
To identify countries with the highest sanctions exposure.

SQL Logic Used

SELECT country,
COUNT(*) AS total_sanctions
FROM sanctions
GROUP BY country
ORDER BY total_sanctions DESC;

Result Table
Country	Total Sanctions
North Korea	84
Belarus	83
Myanmar	75
Iran	74
China	73
Syria	73
Russia	72
Venezuela	70


Insight
The analysis demonstrates that sanctions are increasingly used as instruments of:
Economic coercion
Strategic containment
Financial pressure
Geopolitical influence


Countries with high sanctions exposure face:
Trade restrictions
Financial isolation
Technology denial
Investment barriers
Supply chain disruptions
This highlights the growing importance of sanctions within modern geoeconomic competition.


---

Key Project Insights

1. Strategic Trade Dependency

The analysis showed that several countries remain highly dependent on a limited number of suppliers for strategic commodities such as petroleum products, petroleum gases, coal products, semiconductors, and rare-earth metals.
Multiple trade flows showed dependency percentages above 80%, indicating concentrated import structures.
This demonstrates that countries with concentrated trade partnerships face significantly higher exposure to geopolitical disruptions, trade restrictions, and supply chain shocks.


---

2. Energy Vulnerability and Geoeconomic Exposure
The project identified that energy-related commodities exhibited some of the highest vulnerability scores within the dataset.
Petroleum oils, bituminous mineral products, and gaseous hydrocarbons showed very high strategic exposure because of strong dependence on external suppliers.
The results indicate that countries heavily dependent on imported energy commodities remain vulnerable during geopolitical crises, sanctions, conflicts, and disruptions in global energy markets.


---

3. Critical Minerals and Technology Supply Risk
The strategic goods analysis showed that Critical Minerals and Technology commodities had the highest average supply risk scores.
Category	Average Supply Risk
Critical Minerals	10.00
Technology	9.00
Energy	7.00
This reflects the fact that strategic commodities such as lithium, rare-earth elements, and semiconductors are concentrated within a limited number of global suppliers.
Such concentration increases global dependence and creates long-term strategic vulnerability.


---

4. Sanctions as a Geoeconomic Instrument
The sanctions analysis revealed that countries such as Russia, Belarus, Iran, Syria, Venezuela, and North Korea had high sanctions exposure under OFAC-USA sanctions programs.
Military-targeted sanctions frequently carried severity scores reaching 10, indicating strong economic and geopolitical pressure.
The analysis demonstrates how sanctions increasingly function not only as political tools, but also as mechanisms of economic coercion and strategic containment.


---

5. Country-Level Geoeconomic Risk Patterns

The country-level analysis identified several countries with high geopolitical risk, relatively lower GDP levels, and large populations.
Country	GDP (USD Million)	Population
Ukraine	160,503	42,973,696
This suggests that countries with weaker economic capacity but significant population pressures may face higher vulnerability to geopolitical instability, economic shocks, and external dependence.


---

6. Overall Project Outcome

The overall analysis demonstrated that strategic trade relationships, commodity concentration, sanctions exposure, and supply chain dependence collectively contribute to geoeconomic vulnerability.
Vulnerable trade networks
Concentrated supply chains
High-risk strategic sectors
Sanctions exposure patterns
Geopolitical economic dependencies
The project demonstrates how SQL and relational database systems can be effectively used for geoeconomic intelligence, strategic trade analysis, and geopolitical risk assessment.
