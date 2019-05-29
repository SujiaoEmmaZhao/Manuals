<meta charset="utf-8"/>
# Central de Balanços (Central Balance Sheet Database) - Harmonized Panel Data

## Data manual

`extraction`: June 2018

`date`: 16 July 2018



**Abstract**: In 2010, the national accounting standards underwent some changes, and *Plano Oficial de Contabilidade* (POC, National Plan of Accounts) was replaced by *Sistema de Normalização Contabilística* (SNC, Accounting Normalization System). This had an impact on the base information in the Central Balance Sheet Database. This manual describes the panel data of *Central de Balanços* with harmonized variables over time available at BPLIM.


# Table of contents
1. [General Information](#general-information)
2. [Geographical Coverage](#geographical-coverage)
3. [Population](#population)
4. [Methodology](#methodology)
5. [Description of files](#description-of-files)
6. [Description of variables](#description-of-variables)
    1. [General Information File (Cover Sheet)](#a.-general-information-file-cover-sheet)
    2. [Economic and Financial Information File](#b.-economic-and-financial-information-file)
    3. [Employment Information File](#c.-employment-information-file)
    4. [Trade Information per Market File](#d.-trade-information-per-market-file)
    6. [Economic and Financial Indicators File](#e.-economic-and-financial-indicators)
7. [Basic Descriptive Statistics](#basic-descriptive-statistics)
8. [Citation of this dataset](#citation-of-this-dataset)
9. [Auxiliary Files](#auxiliary-files)
10. [References](#references)
11. [Appendix](#appendix)



# General Information
> `Data Type`: Longitudinal Data

> `Units of Analysis`: Firms

> `Frequency`: Annual

> `Start Date`: 2006

>`Most recent year`: 2016

> `Reference date`: The data reports to the fiscal period declared by the firm. For most cases, the fiscal period coincides with the civil year. For those firms with fiscal period different than the civil year, the reference year is the one covering most of the days of the fiscal period.

> `Data Organization`: Data is organized in four files:

- General Information on the firm (Cover Sheet),
- Economic and Financial Information (Balance Sheet and Profit and Loss Statements),
- Employment Information,
- Trade Information per Market.

In all files each row corresponds to one firm in a given year. All files are available in Stata format, version 15.

> `Version of the Data`: The data made available by BPLIM corresponds to a data freeze at a certain time of the year.[^1] Therefore, all files contain the information as reported in the extraction date. The most recent update of the data occurred in June 2018.

[^1]: For more information, see the manual on the Annual Data of Central Balance Sheet Database.

> `Languages Available`: Variable labels and value labels are available in Portuguese and for most of the variables also in English. [^2]

[^2]: To see the labels in English type the following command line in Stata: 'label language en'.


> `Related Datasets`: This product is built based on the information from Central Balance Sheet Database.



# Geographical Coverage
The data refers to firms located in the Mainland Portugal and Autonomous Regions – Azores and Madeira.


# Population
The population of the panel dataset of *Central de Balanços* is the same as in the annual data, i.e. the population of all Portuguese non-financial corporations. For more information, please see the manual on [*Central Balance Sheet Database - Annual Data*](../../CB/Jun2018/Pack_CB_Empresas_Jun18/manual_CB_Jun2018.html).


# Methodology

Central Balance Sheet Database provides economic and financial information on Portuguese non-financial corporations. The data is collected through *Informação Empresarial Simplicada* (IES) since 2006. In 2010, the national accounting standards underwent some changes, and *Plano Oficial de Contabilidade* (POC, National Plan of Accounts) was replaced by *Sistema de Normalização Contabilística* (SNC, Accounting Normalization System), which is closer to the International Accounting Standards (IAS) and International Financial Reporting Standards (IFRS). This had an impact on the base information in the Central Balance Sheet Database (Banco de Portugal, 2014).

![](./attachments/accounting_years.png)

With the introduction of SNC, some accounting items were simply redenominated, some were aggregated or disaggregated, and others have no correspondence at all in the old accounting system. The Interest income (VF16150) and Net non-current assets held for sale (VF16035) are some examples of variables that are not reported in the financial statements written according to POC. Also, the asset items in POC accounting system were reported in gross terms and the amortizations and adjustments were reported separately for each item of the Balance Sheet. The financial statement written according to SNC does not have a separate item for depreciations as POC did and all variables are being reported in net terms.
Finally, SNC introduced different reporting standards for firms with different sizes. After 2010, Micro-Entities and Small-sized Entities [^3] were required to report a lower number of variables.

In this section, we describe the procedure to compute the harmonized variables available in the panel data of Central Balance Sheet Database. For a complete account on how each variable made available in the panel was computed, check the [Description of Variables](#description-of-variables).
All the calculations are done based on the annual files of *Central de Balanços*. Therefore, the number of firms and the time period available are the same as in the annual files. The panel dataset is updated once per year around the month of June, at the same time as the annual data of *Central de Balanços*. The most recent extraction occurred in June 2018.

Some variables had to be aggregated to guarantee the comparability before and after 2010. Besides, the harmonized variables can only be calculated if their components are reported for all entities according to the reporting standards adopted by the firm. Therefore, the panel dataset contains a lower number of variables than those included in the annual files.
Currently we make available approximately 60 harmonized variables on the Balance Sheet and Profit and Loss Statement. In the Employment Information file, we make available 18 variables and in the Trade Information per market file, 12 variables are available. All variables in the Cover Sheet File are available given that this type of information were not affected by the accounting standards.

Table 1 – Number of Harmonized Variables by type of information

| Type of Information	| Number of Harmonized Variables |	Time Period |
| :------ | :----: | :---: |
| General Information (Cover sheet) File	| 23	| 2006-2016 |
| Economic and Financial Information File | 59 | 2006-2016 |
| Employment Information File | 18 | 2006-2016 |
| Trade Information per Market File | 12 | 2006-2016 |

The harmonization procedure is different for each file described in Table 1. While the information in the Cover sheet did not suffer any significant change with the introduction of SNC, the harmonization of the Economic and Financial Information is not a straightforward task. Therefore, we classified the harmonization methodology in three different categories:

- **Type 1**: covers the information unaffected by the change in the accounting system, which includes the Cover Sheet File. In this case, we simply append the annual datasets. The name of the variables remain the same since no change on the original data was undertaken.

- **Type 2**: covers the information that was directly affected by the change in the accounting system, i.e., the Economic and Financial Information and Trade Information per Market. It also includes the Employment Information because the variables are collected through different tables in IES and have different denominations under POC and SNC accounting systems.
For this type of files, we rely on the definition of the variables under the current accounting system (SNC) and compute a formula using the POC items needed to ensure the comparability over time.
For example, the procedure to compute the item Turnover (D001) is illustrated below:

| | | | | | | | |
| :---: | :-------: | :---: | :------: | :------: | :------: | :------: | :------: |
| **ano** |	**tina** | planocont | VF03045	| VF03046	| VF03047	| VF16132	| **D001** |
| **2006** | **500000000** | POC | . | . | . | . | **0** |
| **2007** | **500000000** | POC | 100 | 100 | 100 | . | **300** |
| **2008** | **500000000** | POC | 100 | 100 | . | . | **200** |
| **2009** | **500000000** | POC | 100 | 100 | 100 | . | **300** |
| **2010** | **500000000** | SNC | . | . | . | 100 | **100** |
| **2011** | **500000000** | SNC | . | . | . | 100 | **100** |
| **2012** | **500000000** | SNC | . | . | . | 100 | **100** |
| **2013** | **500000000** | SNC | . | . | . | 100 | **100** |
| **2014** | **500000000** | SNC | . | . | . | 100 | **100** |
| **2015** | **500000000** | SNC | . | . | . | 100 | **100** |
| **2016** | **500000000** | SNC | . | . | . | 100 | **100** |

The SNC variable - VF16132 (Turnover) - corresponds to the sum of the variables VF03045, VF03046 and VF03047 in the POC accounting system. Therefore, a new harmonized variable is computed - D001 - using these auxiliary variables. After calculating the harmonized variable, the auxiliary variables are dropped and only the variables in bold are kept in the dataset.
All missing values in the auxiliary variables are treated as zeros. The report of IES is mandatory for all firms that are required to send the financial statements to the Ministry of Finance. Therefore, all items have to be completed in a consistent manner so that the firm is able to submit the declaration. Therefore, the real value of a specific variable is assumed to be zero if it is not reported.
The naming convention for Balance Sheet variables in the panel data is B(L)xxx, for Profit and Loss Statement is D(L)xxx, for Employment Information is Exxx and for Trade Information per Market is MGxxx.


After identifying all variables that can be potentially included in the panel dataset, we produced and analyzed technical reports on each variable. Namely, we did the following checks to ensure the compatibility of the panel variables over time:

1. analyze the evolution of the mean and medium values of the relative changes over time. [^4] We try to identify whether there is any discontinuity in 2010, the first year in which most of the firms reported under *Sistema de Normalização Contabilística*.[^5]
2. check whether abnormal relative changes (relative changes above 100%) are found more often in the transition to the new accounting system.
3. decomposition of the yearly variation of the total value of each variable due to the expansion and contraction of incumbents and the entry and exit of firms.
4. regression of each variable on time dummies to detect any structural change in the variable after 2010.

The link to the report on each variable is available in the section [Description of Variables](#description-of-variables).
The harmonization procedure tries to ensure the compatibility of the variable over time as much as possible. However, as one can see in the variable reports, some harmonized variables show a clear discontinuity in 2010.

We also produce a [report](./Auxiliary Files/technical_reports/CONTAS_MG_checks.pdf) checking whether the sum of disaggregated variables corresponds to the aggregated variables.

- **Type 3**: covers the Economic and Financial Indicators files containing information affected by the change in the accounting system. The information on this file is calculated using the variables available in the Economic and Financial Information File. We provide a Stata ado file to compute all the economic and financial indicators that are possible to harmonize over time given the information available in the panel dataset. By adopting this procedure, the size of the dataset is minimized. All indicators variables calculated by this ado are denominated Rxxx.

[^3]: A Micro-Entity is defined as a firm that falls below in at least two of the following criteria at the balance sheet date: i) total assets equal to 500.000 euros; ii) net turnover equal to 500.000 euros; or iii) average number of employees equal to 5. Small-sized Entities are firms satisfying at least two of the following conditions: i) total assets below 500.000 euros; ii) total gross sales and other income lower than 1.000.000 euros or; iii) average number of employees less than 20. For more details please check the manual on [*Central Balance Sheet Database - Annual Data*](../../CB/Jun2018/Pack_CB_Empresas_Jun18/manual_CB_Jun2018.html).

[^4]: The relative changes are defined as the difference between the value of the variable observed in year t minus the value observed in the previous year. Relative changes are computed with respect to the average of year t and t-1 and are measured in percentage.

[^5]: In 2010 some declarations were reported according to *Plano Oficial de Contas*. This situation occurs mostly for declarations sent in the cessation period and before or after the firms adopts a special fiscal period - a fiscal period different from calendar year.

# Description of Files
Similarly to the annual data files, the panel data of *Central de Balanços* is organized in four files. Each file provides a different type of information, namely:

| Type of Information | File Name |
| :------ | :----------- |
| **A.	General Information (Cover sheet)** | CB_A_FRM_PanelyyYYeeee_ROSTO_V01.dta |
| **B.	Economic and Financial Information** | CB_A_FRM_PanelyyYYeeee_CONTAS_V01.dta |
| **C.	Employment Information** | CB_A_FRM_PanelyyYYeeee_PESSOAL_V01.dta |
| **D.	Trade Information per Market** | CB_A_FRM_PanelyyYYeeee_MG_V01.dta |


Where *A* stands for Anonymized and *yy* corresponds to the first year available and *YY* corresponds to most recent year available. *eee* reports the extraction date.

All files contain a unique firm identifier (*tina*) and a reference year (*ano*) allowing the matching of the different types of information by firm. Whenever possible, labels and value labels were attributed to all categorical variables. All data sets are anonymized.


# Description of Variables
## A.	General Information File (Cover Sheet)

The information reported in this file was not affected by the change in the accounting system. Therefore, the panel dataset includes all the variables available in the annual data files.

### A1. Identifiers

`Firm identifier` (*tina*) – Unique identifier that enables tracking the legal entity firm over time. *tina* is the anonymized tax identification number. The first digit of the tax identification number contains information on the type of corporation and legal form. Therefore, this first digit is preserved in *tina*.

`Reference year of the data` (*ano*) – Reference year of the data.


### A2. Other variables

All the variables available in the annual datasets are also available in the panel data of Central Balance Sheet Database. For a full description of these variables please check the manual on [*Central Balance Sheet Database - Annual Data*](../../CB/Jun2018/Pack_CB_Empresas_Jun18/manual_CB_Jun2018.html) or the auxiliary file [var_rosto.html](./Auxiliary Files/variables_description/var_rosto.html).

The variables reporting the accounting system (*planocont*) and the accounting standards (*regime*) under which the firm is reporting information are kept in the panel dataset. These variables do not have any interpretation given that all the economic and financial variables included in the panel dataset are harmonized over time. They are kept in the dataset because they may be useful in case one wants to calculate additional variables not provided by BPLIM.

## B.	Economic and Financial Information File

This file provides a set of balance sheet and profit and loss statement variables harmonized over time. For a full account of the SNC items included in the definition of the harmonized variable see the auxiliary file [contas_snc_items.html](./Auxiliary Files/variables_description/contas_snc_items.html).

### B1. Identifiers

`Firm identifier` (*tina*) – Unique identifier that enables tracking the legal entity firm over time. *tina* is the anonymized tax identification number.

`Reference year of the data` (*ano*) – Reference year of the data.

### B2. Balance Sheet Variables

### Assets

| Variable | Variable description | Definition | SNC Variable | Formula in POC | Variable Report |
| :----: | :-------------- | :----------- | :-----: | :---------: | :----------: |
| B001 | **Total Assets (QS)** | Total non-current assets; Total current assets | VF15991 | [Formula in POC](#b001---formula-in-poc) | [Report - B001](./Auxiliary Files/technical_reports/variable_report/B001(!).pdf) |
| B004 | > Total non-current assets (QS) | Fixed tangible assets and intangible assets; Financial investments; Remaining non-current assets | VF15994 | [Formula in POC](#b004---formula-in-poc) | [Report - B004](./Auxiliary Files/technical_reports/variable_report/B004(!).pdf) |
| B005 | > > Fixed tangible assets and intangible assets | Intangible assets (including Goodwill); Land and buildings; Basic equipment; Other fixed assets; Payments on account of fixed assets | VF15995 | [Formula in POC](#b005---formula-in-poc) | [Report - B005](./Auxiliary Files/technical_reports/variable_report/B005.pdf) |
| B012 | > > > Fixed tangible assets | Land and buildings; Basic equipment; Other fixed assets; Payments on account of fixed assets [^6] | VF16002 | [Formula in POC](#b012---formula-in-poc) | [Report - B012](./Auxiliary Files/technical_reports/variable_report/B012.pdf) |
| B025 | > > Financial investments | Investments in subsidiary and associated companies; Financial investments (excepting investments in subsidiary and associated companies | VF16015 | [Formula in POC](#b025---formula-in-poc) | [Report - B025](./Auxiliary Files/technical_reports/variable_report/B025(!).pdf) |
| B158 | > > Non-current assets - Remaining non-current assets | Shareholders / partners; Deferred tax assets | VF18510 | [Formula in POC](#b158---formula-in-poc) | [Report - B158](./Auxiliary Files/technical_reports/variable_report/B158.pdf) |
| B029 | > Total Current assets (QS) | Inventories and biological assets; Customers; Remaining current assets; Cash and bank deposits; Non-current assets held for sale [^7] | VF16019 | [Formula in POC](#b029---formula-in-poc) | [Report - B029](./Auxiliary Files/technical_reports/variable_report/B029(!).pdf) |
| B032 | > > Current assets - Inventories and biological assets | Raw and subsidiary materials and consumables; Advances from customers; Inventories (excepting Raw and subsidiary materials and consumables) | VF16022 | [Formula in POC](#b032---formula-in-poc) | [Report - B032](./Auxiliary Files/technical_reports/variable_report/B032(!).pdf) |
| B041 | > > Current assets - Customers | | VF16031 | [Formula in POC](#b041---formula-in-poc) | [Report - B041](./Auxiliary Files/technical_reports/variable_report/B041(!).pdf) |
| B049 | > > Current assets - Cash and bank deposits | | VF16039 | [Formula in POC](#b049---formula-in-poc) | [Report - B049](./Auxiliary Files/technical_reports/variable_report/B049(!).pdf) |
| B159 | > > Current assets - Remaining current assets | Current assets - State and other public entities; Other current assets; Shareholders; Deferred expense | VF18511 | [Formula in POC](#b159---formula-in-poc) | [Report - B159](./Auxiliary Files/technical_reports/variable_report/B159.pdf) |
| B042 | > > Current assets - State and other public entities | | VF16032 | [Formula in POC](#b042---formula-in-poc) | [Report - B042](./Auxiliary Files/technical_reports/variable_report/B042(!).pdf) |


[^6]: With the introduction of SNC some components that were previously classified as fixed tangible assets were reallocated to intangible assets to accommodate international standards. An example is highway concessions which were considered as tangible assets in POC and were reclassified as intangible assets in SNC.
[^7]: This variable has no match in *Plano Oficial de Contas*.

### Equity

| Variable | Variable description | Definition | SNC Variable | Formula in POC | Variable Report |
| :----: | :-------------- | :----------- | :-----: | :---------: |  :----------: |
| B060 | **Equity and Liabilities (QS)** | Equity; Liabilities | VF16050 | [Formula in POC](#b060---formula-in-poc) | [Report - B060](./Auxiliary Files/technical_reports/variable_report/B060(!).pdf) |
| B061 | > **Equity (QS)** | Paid-up capital;	Other equity instruments; Reserves and retained earnings; Other items of equity; Net income; Interim dividends | VF16051 | [Formula in POC](#b061---formula-in-poc) | [Report - B061](./Auxiliary Files/technical_reports/variable_report/B061.pdf) |
| BL005 |	> > Legal reserves | | VF13024 | [Formula in POC](#bl005---formula-in-poc) | [Report - BL005](./Auxiliary Files/technical_reports/variable_report/BL005(!).pdf) |
| BL007 | > > Retained earnings | | VF13026 | [Formula in POC](#bl007---formula-in-poc) | [Report - BL007](./Auxiliary Files/technical_reports/variable_report/BL007.pdf) |
| B074 | > > Interim dividends | | VF16064 | [Formula in POC](#b074---formula-in-poc) | [Report - B074](./Auxiliary Files/technical_reports/variable_report/B074(!).pdf) |
| B143 | > > Subscribed capital | |VF16425 | [Formula in POC](#b143---formula-in-poc) | [Report - B143](./Auxiliary Files/technical_reports/variable_report/B143.pdf) |


### Liabilities

| Variable | Variable description | Definition | SNC Variable | Formula in POC | Variable Report |
| :----: | :-------------- | :----------- | :-----: | :---------: |  :----------: |
| B080 | > **Liabilities (QS)** | Non-current liabilities; Current liabilities | VF16070 | [Formula in POC](#b080---formula-in-poc) | [Report - B080](./Auxiliary Files/technical_reports/variable_report/B080(!).pdf) |
| B081 | > > Non-current liabilities | Obtained funding; Post-employment benefits; Remaining non-current liabilities | VF16071 | [Formula in POC](#b081---formula-in-poc) | [Report - B081](./Auxiliary Files/technical_reports/variable_report/B081(!).pdf) |
| B085 | > > > Non-current liabilities - Obtained funding | | VF16075 | [Formula in POC](#b085---formula-in-poc) | [Report - B085](./Auxiliary Files/technical_reports/variable_report/B085(!).pdf) |
| B160 | > > > Non-current liabilities - Remaining non-current liabilities | Provisions; Other accounts payable; Deferred tax liabilities | VF18512 | [Formula in POC](#b160---formula-in-poc) | [Report - B160](./Auxiliary Files/technical_reports/variable_report/B160(!).pdf) |
| B089 | > > Current liabilities (QS) | Suppliers; Obtained funding; Remaining current liabilities | VF16079 | [Formula in POC](#b089---formula-in-poc) | [Report - B089](./Auxiliary Files/technical_reports/variable_report/B089(!).pdf) |
| B093 | > > > Current liabilities - Suppliers | | VF16083 | [Formula in POC](#b093---formula-in-poc) | [Report - B093](./Auxiliary Files/technical_reports/variable_report/B093(!).pdf) |
| B161 | > > > Current liabilities - Remaining current liabilities | State and other public sector institutions; Other current liabilities; Deferred income | VF18513 | [Formula in POC](#b161---formula-in-poc) | [Report - B161](./Auxiliary Files/technical_reports/variable_report/B161(!).pdf) |
| B094 | > > > > Current liabilities - State and other public entities | | VF16084 | [Formula in POC](#b094---formula-in-poc) | [Report - B094](./Auxiliary Files/technical_reports/variable_report/B094(!).pdf) |


### B3. Profit and Loss Statement Variables

| Variable | Variable description | Definition | SNC Variable | Formula in POC | Variable Report |
| :----: | :-------------- | :----------- | :-----: | :---------: |  :----------: |
| D021 | **Total income** | Turnover; Remaining income | VF16152 | [Formula in POC](#d021---formula-in-poc) | [Report - D021](./Auxiliary Files/technical_reports/variable_report/D021(!).pdf) |
| D001 | > Turnover | Sales; Services | VF16132 | [Formula in POC](#d001---formula-in-poc) | [Report - D001](./Auxiliary Files/technical_reports/variable_report/D001(!).pdf) |
| D002 | > > Sales | Sales of good and products | VF16133 | [Formula in POC](#d002---formula-in-poc) | [Report - D002](./Auxiliary Files/technical_reports/variable_report/D002.pdf) |
| DL017 | > > Services | | VF15599 | [Formula in POC](#dl017---formula-in-poc) | [Report - DL017](./Auxiliary Files/technical_reports/variable_report/DL017.pdf) |
| D111 | > Remaining Income | Operating subsidies; Variation in production; Capitalized production; Other incomes; Obtained interest and similar income[^9] | VF18514 | [Formula in POC](#d111---formula-in-poc) | [Report - D111](./Auxiliary Files/technical_reports/variable_report/D111(!).pdf) |
| D005 | > > Operating subsidies | | VF16136 | [Formula in POC](#d005---formula-in-poc) | [Report - D005](./Auxiliary Files/technical_reports/variable_report/D005.pdf) |
| D006 | > > Variation in production | | VF16137 | [Formula in POC](#d006---formula-in-poc) | [Report - D006](./Auxiliary Files/technical_reports/variable_report/D006(!).pdf) |
| D007 | > > Capitalized production | | VF16138 | [Formula in POC](#d007---formula-in-poc) | [Report - D007](./Auxiliary Files/technical_reports/variable_report/D007.pdf) |
| DL043 |	Supplementary income | | VF15650 | [Formula in POC](#dl043---formula-in-poc) | [Report - DL043](./Auxiliary Files/technical_reports/variable_report/DL043.pdf) |
| D013 | Other incomes - Income from financial assets | | VF16144 | [Formula in POC](#d013---formula-in-poc) | [Report - D013](./Auxiliary Files/technical_reports/variable_report/D013(!).pdf) |
| D062 | **Total Expenses (QS)** | Costs of goods sold and material consumed; Supplies and external services; Employee expenses; Remaining expenses; Expenses/reversals of depreciations and amortizations; Interest expenses; Income tax | VF16193 | [Formula in POC](#d062---formula-in-poc) | [Report - D062](./Auxiliary Files/technical_reports/variable_report/D062(!).pdf) |
| D025 | > Costs of goods sold and material consumed | |VF16156 | [Formula in POC](#d025---formula-in-poc) | [Report - D025](./Auxiliary Files/technical_reports/variable_report/D025.pdf) |
| D026 | > Supplies and external services | | VF16157 | [Formula in POC](#d026---formula-in-poc) | [Report - D026](./Auxiliary Files/technical_reports/variable_report/D026(!).pdf) |
| D029 | > Employee expenses | Salaries; Social security expenses; Other employee expenses | VF16160 | [Formula in POC](#d029---formula-in-poc) | [Report - D029](./Auxiliary Files/technical_reports/variable_report/D029(!).pdf) |
| D030 | > > Salaries | Salaries of Corporate Bodies; Salaries of employees | VF16161 | [Formula in POC](#d030---formula-in-poc) | [Report - D030](./Auxiliary Files/technical_reports/variable_report/D030(!).pdf) |
| DL011 | > > > Salaries of corporate bodies | | VF15555 | [Formula in POC](#dl011---formula-in-poc) | [Report - DL011](./Auxiliary Files/technical_reports/variable_report/DL011(!).pdf) |
| DL012 | > > > Salaries of employees | | VF15557 | [Formula in POC](#dl012---formula-in-poc) | [Report - DL012](./Auxiliary Files/technical_reports/variable_report/DL012.pdf) |
| DL045 | > > Employee expenses - Other, except salaries | Social security expenses; Insurance schemes for accidents at work and occupational diseases; Expenses with social actions; Post-employment benefits; Indemnities; Other employee expenses | VF15554 - VF16161 | [Formula in POC](#dl045---formula-in-poc) | [Report - DL045](./Auxiliary Files/technical_reports/variable_report/DL045(!).pdf) |
| DL013 | > > > Social security expenses | | VF15565 | [Formula in POC](#dl013---formula-in-poc) | [Report - DL013](./Auxiliary Files/technical_reports/variable_report/DL013.pdf) |
| DL014	| > > > Insurance schemes for accidents at work and occupational diseases | | VF15566 | [Formula in POC](#dl014---formula-in-poc) | [Report - DL014](./Auxiliary Files/technical_reports/variable_report/DL014(!).pdf) |
| D108 | > Remaining expenses | Impairment (losses/reversals) and changes (gains/losses) in fair value; Provisions (increases/decreases); Other expenses | VF16572 | [Formula in POC](#d108---formula-in-poc) | [Report - D108](./Auxiliary Files/technical_reports/variable_report/D108(!).pdf) |
| D041 | > Expenses/reversals of depreciations and amortizations | | VF16172 | [Formula in POC](#d041---formula-in-poc) | [Report - D041](./Auxiliary Files/technical_reports/variable_report/D041(!).pdf) |
| D053 | > Interest expenses | | VF16184 | [Formula in POC](#d053---formula-in-poc) | [Report - D053](./Auxiliary Files/technical_reports/variable_report/D053(!).pdf) |
| D060 | > Income tax | | VF16191 | [Formula in POC](#d060---formula-in-poc) | [Report - D060](./Auxiliary Files/technical_reports/variable_report/D060.pdf) |
| D112 | Impairment losses, changes in fair value and other expenses and losses in fin. invest. and fin. instrum. | Impairment (losses/reversals) and changes (gains/losses) in fair value in financial instruments and investments; Other expenses - expenses in financial investments and other financing expenses | VF18515 | [Formula in POC](#d112---formula-in-poc) | [Report - D112](./Auxiliary Files/technical_reports/variable_report/D112(!).pdf) |
| D082 | **Operating net income** | (Turnover; Remaining income (excepting Obtained interest and similar income) [^8; Impairment losses, changes in fair value and other expenses and losses in fin. invest. and fin. instrum.) - (Income from financial assets; Costs of goods sold and material consumed, Supplies and external services, Employee expenses and Remaining expenses) | VF16213 | [Formula in POC](#d082---formula-in-poc) | [Report - D082](./Auxiliary Files/technical_reports/variable_report/D082(!).pdf) |
| D084 | **Earnings before Interest, Taxes, Depreciation and Amortization - EBITDA** | (Turnover; Remaining income (excepting Obtained interest and similar income) [^9]) - (Costs of goods sold and material consumed; Supplies and external services; Employee expenses; Remaining expenses) | VF16215 |  [Formula in POC](#d084---formula-in-poc) | [Report - D084](./Auxiliary Files/technical_reports/variable_report/D084(!).pdf) |
| D085 | **Earning before Interest and Tax - EBIT** | (Turnover; Remaining income (excepting Obtained interest and similar income) [^9]) - (Costs of goods sold and material consumed; Supplies and external services; Employee expenses; Remaining expenses; Expenses/reversals of depreciations and amortizations) | VF16216 | [Formula in POC](#d085---formula-in-poc) | [Report - D085](./Auxiliary Files/technical_reports/variable_report/D085(!).pdf) |
| D086 | **Earnings before Tax - EBT** | (Turnover; Operating subsidies; Variation in production; Capitalized production; Other income; Interest, dividends and other similar income) - (Costs of goods sold and material consumed; Supplies and external services; Employee expenses; Impairment, provisions, Losses/reversals of depreciations and amortizations; Other expenses; Financial expenses and losses)[^10] | VF16217 | [Formula in POC](#d086---formula-in-poc) | [Report - D086](./Auxiliary Files/technical_reports/variable_report/D086(!).pdf) |
| D087 | **Net income** | Total Income - Total Expenses [^11] | VF16218 | [Formula in POC](#d087---formula-in-poc) | [Report - D087](./Auxiliary Files/technical_reports/variable_report/D087(!).pdf) |
| DL002 | Other expenses - Cash discounts granted | | VF15843 | [Formula in POC](#dl002---formula-in-poc) | [Report - DL002](./Auxiliary Files/technical_reports/variable_report/DL002(!).pdf) |
| DL005 | Other expenses - Other - Donations | | VF15859 | [Formula in POC](#dl005---formula-in-poc) | [Report - DL005](./Auxiliary Files/technical_reports/variable_report/DL005(!).pdf) |
| DL047 | Indirect taxes | | VF15841 + VF15842 | [Formula in POC](#dl047---formula-in-poc) | [Report - DL047](./Auxiliary Files/technical_reports/variable_report/DL047(!).pdf) |


[^8]: The item "Obtained interest and similar income" has no correspondence in the POC accounting system.
[^9]: Obtained interest and similar income has to be subtracted to Remaining Income to make it compatible with the POC formula.
[^10]: In SNC, some components of EBT are different from the ones used to compute EBIT.
[^11]: This variable is not computed using the total income and total expenses as given by D021 and D062, respectively. This formula corresponds to the difference between D020 - Total income and D061 - Total expenses.


## C. Employment Information File

This file contains information on the number of employees and number of hours worked. Although the change in the accounting system did not have a direct impact on the report of this information, the denomination of the variables is different under both accounting regimes. Also, some variables are no longer required after 2010, such as the number of paid apprentices and home workers. The number of employees by gender only started being reported after 2010.
These variables are reported on Tables Q05-0507-Nota7 in the forms written according to POC and Q05A-05291-A in the forms written according to SNC.

### C1. Identifiers

`Firm identifier` (*tina*) – Unique identifier that enables tracking the legal entity firm over time. *tina* is the anonymized tax identification number.

`Reference year of the data` (*ano*) – Reference year of the data.

### C2. Number of employees

| Variable | Variable description | SNC Variable | Formula in POC | Variable Report |
| :----: | :-------------- | :-----: | :---------: |  :----------: |
| E001 | Number of (paid and unpaid) employees | VF15532	| VF03319 | [Report - E001](./Auxiliary Files/technical_reports/variable_report/E001.pdf)
| E002 | Number of paid employees | VF15534 | VF03321 | [Report - E002](./Auxiliary Files/technical_reports/variable_report/E002.pdf)
| E003 | Number of unpaid employees | VF15536 | VF04902 | [Report - E003](./Auxiliary Files/technical_reports/variable_report/E003.pdf)
| E004 | Number of (paid and unpaid) full-time employees| VF15538 | VF03320 | [Report - E004](./Auxiliary Files/technical_reports/variable_report/E004.pdf)
| E005 | Number of paid full-time employees | VF15540 | VF04903 | [Report - E005](./Auxiliary Files/technical_reports/variable_report/E005.pdf)
| E006 | Number of (paid and unpaid) part-time employees | VF15542 | VF04904 | [Report - E006](./Auxiliary Files/technical_reports/variable_report/E006.pdf)
| E007 | Number of paid part-time employees | VF15544 |	VF03324 | [Report - E007](./Auxiliary Files/technical_reports/variable_report/E007.pdf)
| E008 | Number of employees allocated to research and development | VF15550	| VF03326 | [Report - E008](./Auxiliary Files/technical_reports/variable_report/E008.pdf)
| E009 | Service providers | VF15551 | VF03325 | [Report - E009](./Auxiliary Files/technical_reports/variable_report/E009.pdf)
| E010 | Temporary Agency Employment | VF15553 | VF03327 | [Report - E010](./Auxiliary Files/technical_reports/variable_report/E010.pdf)

### C3. Number of hours of work

| Variable | Variable description | SNC Variable | Formula in POC | Variable Report |
| :----: | :-------------- | :-----: | :---------: |  :----------: |
| E011 | Number of hours worked by paid and unpaid employees | VF15533 | VF03328 | [Report - E011](./Auxiliary Files/technical_reports/variable_report/E011.pdf)
| E012 | Number of hours worked by paid employees | VF15535	| VF03330 | [Report - E012](./Auxiliary Files/technical_reports/variable_report/E012.pdf)
| E013 | Number of hours worked by unpaid employees | VF15537 | VF04905 | [Report - E013](./Auxiliary Files/technical_reports/variable_report/E013.pdf)
| E014 | Number of hours worked by paid and unpaid full-time employees | VF15539 | VF03329 | [Report - E014](./Auxiliary Files/technical_reports/variable_report/E014.pdf)
| E015 | Number of hours worked by paid full-time employees | VF15541 | VF04906 | [Report - E015](./Auxiliary Files/technical_reports/variable_report/E015.pdf)
| E016 | Number of hours worked by paid and unpaid part-time employees | VF15543 | VF04907 | [Report - E016](./Auxiliary Files/technical_reports/variable_report/E016.pdf)
| E017 | Number of hours worked by paid part-time employees | VF15545 | VF03331 | [Report - E017](./Auxiliary Files/technical_reports/variable_report/E017.pdf)
| E018 | Number of hours worked by service providers | VF15552 | VF03332 | [Report - E018](./Auxiliary Files/technical_reports/variable_report/E018.pdf)


## D. Trade information per market file

According to the forms written according to POC and respective filling instructions (Q0544-Nota44), some variables are reported in net terms. These variables were reported in a different table and have new denominations in the new accounting system (Q05-A-05301-A). However, there is a direct correspondence between the POC and SNC variables.

### D1. Identifiers

`Firm identifier` (*tina*) – Unique identifier that enables tracking the legal entity firm over time. *tina* is the anonymized tax identification number.

`Reference year of the data` (*ano*) – Reference year of the data.

### D2. Variables available

| Variable | Variable description | SNC Variable | Formula in POC | Variable Report |
| :----: | :-------------- | :-----: | :---------: |  :----------: |
| MG001 | Total Sales - Internal Market	| VF15619 | VF03949 | [Report - MG001](./Auxiliary Files/technical_reports/variable_report/MG001(!).pdf) |
| MG002	| Total Services - Internal Market | VF15623 | VF03950 | [Report - MG002](./Auxiliary Files/technical_reports/variable_report/MG002(!).pdf) |
| MG003	| Total Purchases - Internal Market	| VF15627 |	VF03951 | [Report - MG003](./Auxiliary Files/technical_reports/variable_report/MG003.pdf) |
| MG004	| Total Sales - EU-Market | VF15620 | VF03953 | [Report - MG004](./Auxiliary Files/technical_reports/variable_report/MG004(!).pdf) |
| MG005	| Total Services - EU-Market | VF15624 | VF03954 | [Report - MG005](./Auxiliary Files/technical_reports/variable_report/MG005.pdf) |
| MG006	| Total Purchases - EU-Market | VF15628 | VF03955 | [Report - MG006](./Auxiliary Files/technical_reports/variable_report/MG006.pdf) |
| MG007	| Total Sales - Extra EU-Market | VF15621 |	VF03957 | [Report - MG007](./Auxiliary Files/technical_reports/variable_report/MG007(!).pdf) |
| MG008	| Total Services - Extra EU-Market | VF15625 | VF03958 | [Report - MG008](./Auxiliary Files/technical_reports/variable_report/MG008(!).pdf) |
| MG009 | Total Purchases - Extra EU-Market | VF15629 | VF03959 | [Report - MG009](./Auxiliary Files/technical_reports/variable_report/MG009.pdf) |
| MG010	| Total Sales | VF15622 | VF03961 | [Report - MG010](./Auxiliary Files/technical_reports/variable_report/MG010.pdf) |
| MG011	| Total Services | VF15626 | VF05195 | [Report - MG011](./Auxiliary Files/technical_reports/variable_report/MG011.pdf) |
| MG012	| Total Purchases | VF15630 | VF03962 | [Report - MG012](./Auxiliary Files/technical_reports/variable_report/MG012.pdf) |


## E. Economic and Financial indicators

The Economic and Financial Indicators are calculated based on the information available in the Economic and Financial Information file. For an overview of the formulas used to compute these variables check the auxiliary file [indicadores_formula.html](./Auxiliary Files/variables_description/indicadores_formula.html).
A Stata ado file (cbhp_addindic.ado) is provided by BPLIM upon request to create the variables listed below. These variables follow the naming convention Rxxx.


| Variable Name | Variable Description |
| ------ | ------- |
| R001 | Current ratio (%) |
| R002 | Quick ratio (%) |
| R003 | Capital ratio (%) (QS) |
| R006 | Assets to equity ratio (%) |
| R007 | Solvency ratio (%) QS |
| R009 |	Non-current assets coverage ratio (%) |
| R023 |	Financial Cost Effect (%) |
| R034 |	Return on sales (%) |
| R036 |	Return on assets (%) |
| R040 | EBITDA over Turnover (%) |
| R041 | Degree of combined leverage |
| R050 | Asset turnover (times) - QS |
| R056 | Coefficient Fixed non-financial assets over employee expenses |
| R150 | Asset turnover ratio (%) |
| R152 | Profit or loss of the year before taxes (EBT) / Equity (%) |
| R155 | Profit or loss of the year before taxes (EBT) / Net turnover (%) |
| R156 | Equity / Total assets (%) |
| R157 | Trade payables / Total assets (%) |
| R158 | Total income / Net turnover (%) |
| R159 | Total expenses / Net turnover (%) |
| R160 | Financial fixed assets / Total assets (%) |
| R161 | Trade receivables / Total assets (%) |


# Basic Descriptive Statistics

Table 1- Firm flows (as of June 2018 extraction)
```s/
use "S:\data\Projects\CB\Jun2018\CB_Painel\Output\Dados\Empresas\Panel\CB_A_FRM_JUN18_ROSTO0616_V01.dta", clear
panelstat tina ano, gaps pattern demog
```


# Citation of this dataset
Banco de Portugal (2018), Central Balance-Sheet Database: Harmonized Panel Data. Extraction: June 2018. Microdata Research Laboratory (BPLIM) Dataset.


# Auxiliary Files
For summary statistics, a codebook and description of each dataset please check the following auxiliary files:

| File | Summary Statistics | Codebook | Dataset description |
| :---- | :----: | :----: | :----: |
| Summary of all variables (Portuguese and English labels) | [variables_pt_en.html](./Auxiliary Files/variables_description/variables_pt_en.html) | |
| General Information File | [stat_Rosto.html](./Auxiliary Files/descriptive_statistics/stat_Rosto.html) | 	[cdbk_Rosto.html](./Auxiliary Files/codebook/cdbk_Rosto.html) | [dscr_Rosto.html](./Auxiliary Files/describe_dataset/dscr_Rosto.html) |
| Economic and Financial Information File | [stat_Contas.html](./Auxiliary Files/descriptive_statistics/stat_Contas.html) | 	[cdbk_Contas.html](./Auxiliary Files/codebook/cdbk_Contas.html) | [dscr_Contas.html](./Auxiliary Files/describe_dataset/dscr_Contas.html) |
| Employment Information File | [stat_Pessoal.html](./Auxiliary Files/descriptive_statistics/stat_Pessoal.html) | 	[cdbk_Pessoal.html](./Auxiliary Files/codebook/cdbk_Pessoal.html) | [dscr_Pessoal.html](./Auxiliary Files/describe_dataset/dscr_Pessoal.html) |
| Trade Information per Market File | [stat_MG.html](./Auxiliary Files/descriptive_statistics/stat_MG.html) | 	[cdbk_MG.html](./Auxiliary Files/codebook/cdbk_MG.html) | [dscr_MG.html](./Auxiliary Files/describe_dataset/dscr_MG.html) |


## References
Banco de Portugal (2014). Quadros do Setor e Quadros da Empresa e do Setor- Notas Metodológicas Série Longa 1995-2013. Estudos da Central de Balanços. Lisboa.


# Appendix
## Balance Sheet Variables

## B001 - Formula in POC
**Total Assets**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [B004](#b004---formula-in-poc) | Total non-current assets (QS) | 1 |
| [B029](#b029---formula-in-poc) | Total current assets (QS) | 1 |

[return](#assets)

------------------------------------------------------

## B004 - Formula in POC
**Total non-current assets (QS)**

| Variable name	| Variable description | Coefficient |
| :----: | :------------- | :---: |
| [B005](#b005---formula-in-poc) | Fixed tangible assets and intangible assets | 1 |
| [B025](#b025---formula-in-poc) | Financial investments	| 1 |
| [B158](#b158---formula-in-poc) | Non-current assets - Remaining non-current assets | 1 |

[return](#assets)

-----------------------------------------------------

## B005 - Formula in POC
**Fixed Tangible Assets and Intangible Assets**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03088	| Intangible assets | Q04-A0207-3-soma |	1 |
| VF03117	| Tangible fixed assets | Q04-A0218-3-soma |	1 |
| VF03587	| Investment in properties | Q05-0510-Nota10-A1489-9-soma | 1 |
| VF03642 | Amortizations and adjustments - Financial investments - Investment in properties | Q05-0510-Nota10-A1506-4-soma | -1 |

[return](#assets)

------------------------------------------------------

## B012 - Formula in POC
**Fixed Tangible Assets**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03117	| Tangible fixed assets | Q04-A0218-3-soma |	1 |
| VF03587	| Investment in properties | Q05-0510-Nota10-A1489-9-soma | 1 |
| VF03642 | Amortizations and adjustments - Financial investments - Investment in properties | Q05-0510-Nota10-A1506-4-soma | -1 |

[return](#assets)

------------------------------------------------------

## B025 - Formula in POC
**Financial Investments**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03140	| Financial investments	| Q04-A0227-3-soma | 1 |
| VF03587 |	Investment in properties | Q05-0510-Nota10-A1489-9-soma | -1 |
| VF03642 | Amortizations and adjustments - Financial investments - Investment in properties | Q05-0510-Nota10-A1506-4-soma | 1 |

[return](#assets)

-----------------------------------------------------

## B029 - Formula in POC
**Total current assets**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [B032](#b032---formula-in-poc) | Current assets - Inventories and biological assets | 1 |
| [B041](#b041---formula-in-poc) | Current assets - Customers	| 1 |
| [B159](#b159---formula-in-poc) | Current assets - Remaining current assets | 1 |
| [B049](#b049---formula-in-poc) | Current assets - Cash and bank deposits | 1 |

[return](#assets)

-----------------------------------------------------

## B032 - Formula in POC
**Current Assets - Inventories and Biological Assets**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03159 | Current assets - Inventories | Q04-A0234-3-soma | 1 |

[return](#assets)

-----------------------------------------------------

## B041 - Formula in POC
**Current Assets - Customers**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03162	| Assets - Medium and long term debt - Customers (current account) | Q04-A0235-3 | 1 |
| VF03165	| Assets - Medium and long term debt - Customers - Notes receivable | Q04-A0236-3 |	1 |
| VF03168	| Assets - Medium and long term debt - Customers - Doubtful debtors	| Q04-A0237-3 | 1 |
| VF03194	| Assets - Short term debt - Customers (current account)	| Q04-A0247-3 | 1 |
| VF03197	| Assets - Short term debt - Customers - Notes receivable | Q04-A0248-3 | 1 |
| VF03200	| Assets - Short term debt - Customers - Doubtful debtors | Q04-A0249-3 | 1 |
| VF03289	| Liabilities - Medium and long term debt - Advances from customers | Q04-A0308-1 | -1 |
| VF03307	| Liabilities - Short term debt - Advances from customers	| Q04-A0326-1 | -1 |

[return](#assets)

------------------------------------------------------

## B042 - Formula in POC
**Current assets - State and other public entities**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03182 |	Assets - Medium and long term debt - State and other public entities (Net Assets) | Q04-A0243-3 | 1 |
| VF03214 | Assets - Short term debt - State and other public entities (Net Assets) | Q04-A0255-3 | 1 |

[return](#assets)

------------------------------------------------------

## B049 - Formula in POC
**Current Assets - Cash and Bank Deposits**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF05131 | Assets - Cash and bank deposits |Q04-A0268-3-soma | 1 |

[return](#assets)

------------------------------------------------------

## B060 - Formula in POC
**Equity and Liabilities**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [B061](#b061---formula-in-poc) | Equity (QS) | 1 |
| [B080](#b080---formula-in-poc) | Liabilities (QS) |	1 |

[return](#equity)

---------------------------------------------------

## B061 - Formula in POC
**Equity**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03258	| Equity - Capital	| Q04-A0277-1 | 1 |
| VF03188	| Assets - Medium and long term debt - Subscribed capital	| Q04-A0245-3 | -1 |
| VF03220	| Assets - Short term debt - Subscribed capital | Q04-A0257-3 | -1 |
| VF03261	| Equity - Supplementary capital	| Q04-A0280-1 | 1 |
| VF03265	| Equity - Reserves- Legal reserves | Q04-A0284-1 | 1 |
| VF03266	| Equity - Reserves- Statutory reserves | Q04-A0285-1 | 1 |
| VF03267	| Equity - Reserves- Contractual reserves | Q04-A0286-1 | 1 |
| VF03268	| Equity - Reserves- Other reserves | Q04-A0287-1 | 1 |
| VF03269	| Equity - Retained earnings | Q04-A0288-1 | 1 |
| VF03259	| Equity - Own shares- Nominal value |	Q04-A0278-1 | 1 |
| VF03260	| Equity - Own shares- Discounts and Premiums | Q04-A0279-1 | 1 |
| VF03262	| Equity - Share Premiums | Q04-A0281-1 | 1 |
| VF03263	| Equity - Adjustments to investments in group and associated companies | Q04-A0282-1 | 1 |
| VF03264	| Equity - Revaluation reserves |	Q04-A0283-1 | 1 |
| VF04061	| Split of account Accruals and deferrals - Investment subsidies | Q06-A0666 | 1 |
| VF03270	| Equity - Net income | Q04-A0289-1 | 1 |
| VF03271	| Equity - Interim dividends |	Q04-A0290-1 | 1 |

[return](#equity)

---------------------------

## B074 - Formula in POC
**Interim dividends**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03271 | Equity - Interim dividends | Q04-A0290-1 | 1 |


[return](#equity)

------------------------------------------------------

## B080 - Formula in POC
**Liabilities - Total**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [B081](#b081---formula-in-poc) | Non-current liabilities	| 1 |
| [B089](#b089---formula-in-poc) | Current liabilities (QS)	| 1 |

[return](#liabilities)

-----------------------------------

## B081 - Formula in POC
**Non-current liabilities- Total**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [B085](#b085---formula-in-poc) | Non-current liabilities - Obtained funding	| 1 |
| [B160](#b160---formula-in-poc) | Non-current liabilities - Remaining non-current liabilities | 1 |
| VF03273	| Provisions- Provisions for pension liabilities (Q04-A0292-1) |	1 |

[return](#liabilities)

-----------------------------------------------------

## B085 - Formula in POC
**Non-current liabilities - Obtained Funding**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03277	| Liabilities - Medium and long term debt - Bond loans: convertible	| Q04-A0296-1 | 1 |
| VF03278	| Liabilities - Medium and long term debt - Bond loans: non-convertible	| Q04-A0297-1 | 1 |
| VF03279	| Liabilities - Medium and long term debt - Participating loans	| Q04-A0298-1 | 1 |
| VF03280	| Liabilities - Medium and long term debt - Loans from credit institutions	| Q04-A0299-1 | 1 |
| VF03286	| Liabilities - Medium and long term debt - Group companies	| Q04-A0305-1 | 1 |
| VF03287	| Liabilities - Medium and long term debt - Affiliate and participating companies	| Q04-A0306-1 | 1 |
| VF03288	| Liabilities - Medium and long term debt - Other shareholders (partners)	| Q04-A0307-1 | 1 |
| VF03290	| Liabilities - Medium and long term debt - Other loans	| Q04-A0309-1 | 1 |

[return](#liabilities)

----------------------------------------------------

## B089 - Formula in POC
**Current liabilities - Total**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [B093](#b093---formula-in-poc) | Current liabilities - Suppliers	| 1 |
| [B161](#b161---formula-in-poc) | Current liabilities - Remaining current liabilities | 1 |
| VF03295	| Liabilities - Short term debt - Bond loans: convertible	(Q04-A0314-1) | 1 |
| VF03296	| Liabilities - Short term debt - Bond loans: non-convertible	(Q04-A0315-1) | 1 |
| VF03297	| Liabilities - Short term debt - Participating loans	(Q04-A0316-1) | 1 |
| VF03298	| Liabilities- Short term debt - Loans from credit institutions (Q04-A0317-1) | 1 |
| VF03304	| Liabilities - Short term debt - Group companies	(Q04-A0323-1) | 1 |
| VF03305	| Liabilities - Short term debt - Affiliate and participating companies	(Q04-A0324-1) | 1 |
| VF03306	| Liabilities - Short term debt - Other shareholders (partners) (Q04-A0325-1) | 1 |
| VF03308	| Liabilities - Short term debt - Other loans	(Q04-A0327-1) | 1 |

[return](#liabilities)

------------------------------------------------------

## B093 - Formula in POC
**Current liabilities - Suppliers**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF05125	| Assets - Medium and long term debt - Advances to suppliers | Q04-A0241-3 | -1 |
| VF05127	| Assets - Short term debt - Advances to suppliers | Q04-A0253-3 | -1 |
| VF03282	| Liabilities - Medium and long term debt - Suppliers (current account)	| Q04-A0301-1 | 1 |
| VF03283	| Liabilities - Medium and long term debt - Suppliers - Trade accounts payable: unchecked invoices | Q04-A0302-1 | 1 |
| VF03284	| Liabilities - Medium and long term debt - Suppliers - Notes payable |	Q04-A0303-1 | 1 |
| VF03300	| Liabilities - Short term debt - Suppliers (current account) | Q04-A0319-1 | 1 |
| VF03301	| Liabilities - Short term debt - Suppliers - Trade accounts payable: unchecked invoices | Q04-A0320-1 | 1 |
| VF03302	| Liabilities - Short term debt - Suppliers - Notes payable	| Q04-A0321-1 | 1 |

[return](#liabilities)

------------------------------------------------------

## B094 - Formula in POC
**Current liabilities - State and other public entities**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03310 | Liabilities - Short term debt - State and other public sector institutions | Q04-A0329-1 | 1 |
| VF03292 | Liabilities - Medium and long term debt - State and other public sector institutions | Q04-A0311-1 | 1 |

[return](#liabilities)

------------------------------------------------------

## B143 - Formula in POC
**Subscribed capital**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03258 | Equity - Capital | Q04-A0277-1 | 1 |


[return](#equity)

------------------------------------------------------

## B158 - Formula in POC
**Non-current assets - Remaining non-current assets**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03171	| Assets - Medium and long term debt - Group companies | Q04-A0238-3 | 1 |
| VF03174	| Assets - Medium and long term debt - Affiliate and participating companies | Q04-A0239-3 | 1 |
| VF03177	| Assets - Medium and long term debt - Other shareholders (partners) | Q04-A0240-3 | 1 |
| VF05135	| Accruals and deferrals - Deferred tax assets | Q04-A0272-3 | 1 |

[return](#assets)

-----------------------------------------------------

## B159 - Formula in POC
**Current assets - Remaining current assets**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03182	| Current assets - Medium and long term debt - State and other public sector institutions | Q04-A0243-3 | 1 |
| VF03214	| Assets - Short term debt - State and other public sector institutions | Q04-A0255-3 | 1 |
| VF05126	| Assets - Medium and long term debt - Advances to fixed assets suppliers | Q04-A0242-3 | 1 |
| VF03185	| Assets - Medium and long term debt - Other debtors | Q04-A0244-3 | 1 |
| VF05128	| Assets - Short term debt - Advances to fixed assets suppliers | Q04-A0254-3 | 1 |
| VF03217	| Assets - Short term debt - Other debtors | Q04-A0256-3 | 1 |
| VF03244	| Assets - negotiable securities | Q04-A0265-3-soma | 1 |
| VF05132	| Accruals and deferrals - Accrued profits | Q04-A0269-3 | 1 |
| VF05134	| Accruals and Deferrals- Deferred daily adjustments in futures contracts | Q04-A0271-3 | 1 |
| VF03203	| Assets - Short term debt - Group companies | Q04-A0250-3 | 1 |
| VF03206	| Assets - Short term debt - Affiliate and participating companies | Q04-A0251-3 |	1 |
| VF03209	| Assets - Short term debt - Other shareholders (partners) | Q04-A0252-3 | 1 |
| VF05133	| Accruals and deferrals - Deferred costs | Q04-A0270-3 |	1 |

[return](#assets)

------------------------------------------------------

## B160 - Formula in POC
**Non-current liabilities - Remaining non-current liabilities**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03273 | Liabilities - Provisions- Provisions for pension liabilities | Q04-A0292-1 | -1 |
| VF03276	| Liabilities - Provisions - Total | Q04-A0295-1-soma | 1 |
| VF03285	| Liabilities - Medium and long term debt - Fixed assets suppliers - notes payable | Q04-A0304-1 | 1 |
| VF03291	| Liabilities - Medium and long term debt - Fixed assets suppliers (current account) | Q04-A0310-1 | 1 |
| VF03293	| Liabilities - Medium and long term debt - Other creditors	| Q04-A0312-1 | 1 |
| VF03315	| Accruals and deferrals - Deferred tax liabilities	| Q04-A0334-1 | 1 |

[return](#liabilities)

-----------------------------------------------------

## B161 - Formula in POC
**Current liabilities - Remaining current liabilities**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03292	| Liabilities - Medium and long term debt - State and other public sector institutions | Q04-A0311-1 | 1 |
| VF03310	| Liabilities - Short term debt - State and other public sector institutions | Q04-A0329-1 | 1 |
| VF03303	| Liabilities - Short term debt - Fixed assets suppliers - Notes payable	| Q04-A0322-1 | 1 |
| VF03309	| Liabilities - Short term debt - Fixed assets suppliers (current account)	| Q04-A0328-1 | 1 |
| VF03311	| Liabilities - Short term debt - Other creditors	| Q04-A0330-1 | 1 |
| VF03313	| Accruals and deferrals - Accrued costs | Q04-A0332-1 | 1 |
| VF03281	| Liabilities - Medium and long term debt - Advances on sales | Q04-A0300-1 | 1 |
| VF03299	| Liabilities - Short Term advances on sales | Q04-A0318-1 | 1 |
| VF03314	| Accruals and deferrals - Deferred profits	| Q04-A0333-1 | 1 |
| VF04061 | Accruals and deferrals - Investment subsidies | Q06-A0666 | -1 |

[return](#liabilities)

-----------------------------------------------------

## BL005 - Formula in POC
**Legal reserves**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03265 | Equity - Reserves - Legal Reserves | Q04-A0284-1 | 1 |

[return](#equity)

-----------------------------------------------------

## BL007 - Formula in POC
**Retained earnings**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03269 | Equity - Retained earnings | Q04-A0288-1 | 1 |

[return](#equity)

------------------------------------------------------


## Profit and Loss Statement Variables
## D001 - Formula in POC
**Turnover**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03045	| Sales - goods	| Q03-A0124-1 | 1 |
| VF03046	| Sales - products | Q03-A0125-1 | 1 |
| VF03047	| Services	| Q03-A0126-1 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------

## D002 - Formula in POC
**Sales**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF05908 | Sales | [Q03-A0124-1]+[Q03-A0125-1] | 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D005 - Formula in POC
**Operating subsidies**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03052 | Operating subsidies | Q03-A0130-1 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D006 - Formula in POC
**Variation in production**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03049 | Variation in production | Q03-A0127-2 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

------------------------------------------------------

## D007 - Formula in POC
**Capitalized production**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03050	| Capitalized production | Q03-A0128-2 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

------------------------------------------------------

## D013 - Formula in POC
**Other incomes - Income from financial assets**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03972	| Revenues - Interests income | Q05-0545-Nota45-A1439-1 | 1 |
| VF05206	| Revenues - Gains in group and associated companies | Q05-0545-Nota45-A1440-1 | 1 |
| VF05207	| Revenues - Income from equity holdings | Q05-0545-Nota45-A1442-1 | 1 |
| VF03977	| Revenues - Reversals and other financial revenues | Q05-0545-Nota45-A1446-1 | 1 |
| VF04054	| Extraordinary revenues – Disposal of financial investments | Q06-A0659 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

------------------------------------------------------

## D021 - Formula in POC
**Total income**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [D001](#d001---formula-in-poc) | Turnover | 1 |
| [D111](#d111---formula-in-poc) | Remaining Income	| 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D025 - Formula in POC
**Costs of goods sold and material consumed**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03019 | Cost of goods sold and material consumed - Total | Q03-A0102-2 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D026 - Formula in POC
**Supplies and external services**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03020	| Supplies and external services | Q03-A0103-2 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D029 - Formula in POC
**Employee expenses**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03021	| Employee expenses - Salaries | Q03-A0104-1 | 1 |
| VF03022	| Employee expenses - Pensions | Q03-A0105-1 | 1 |
| VF03023	| Employee expenses - Others | Q03-A0106-1 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D030 - Formula in POC
**Employee expenses - Salaries**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03021	| Salaries | Q03-A0104-1 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

------------------------------------------------------

## D041 - Formula in POC
**Expenses/reversals of depreciations and amortizations**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03025	| Depreciation of intangible and tangible fixed assets | Q03-A0107-1 | 1 |
| VF03965	| Costs - Amortizations of investment in properties | Q05-0545-Nota45-A1431-1 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D053 - Formula in POC
**Interest expenses**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03964 | Interests paid | Q05-0545-Nota45-A1429-1 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

------------------------------------------------------

## D060 - Formula in POC
**Income tax**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03041 | Income tax | Q03-A0120-2 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D062 - Formula in POC
**Total expenses (QS)**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [D025](#d025---formula-in-poc) | Costs of goods sold and material consumed | 1 |
| [D026](#d026---formula-in-poc) | Supplies and external services	| 1 |
| [D029](#d029---formula-in-poc) | Employee expenses | 1 |
| [D108](#d108---formula-in-poc) | Remaining expenses | 1 |
| [D041](#d041---formula-in-poc) | Expenses/reversals of depreciations and amortizations | 1 |
| [D053](#d053---formula-in-poc) | Interest expenses (QS) | 1 |
| [D060](#d060---formula-in-poc) | Income tax	| 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D082 - Formula in POC
**Operating net income**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [D001](#d001---formula-in-poc) | Turnover	| 1 |
| [D111](#d111---formula-in-poc) | Remaining income	| 1 |
| [D112](#d112---formula-in-poc) | (Remaining expenses) of which: Impairment losses, changes in fair value and other expenses and losses in fin. invest. and fin. instrum. | 1 |
| [D013](#d013---formula-in-poc) | (Remaining income) of which: income from financial assets | -1 |
| [D025](#d025---formula-in-poc) | Costs of goods sold and material consumed | -1 |
| [D026](#d026---formula-in-poc) | Supplies and external services	| -1 |
| [D029](#d029---formula-in-poc) | Employee expenses | -1 |
| [D108](#d108---formula-in-poc) | Remaining expenses	| -1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D084 - Formula in POC
**Earnings before interest, taxes, depreciation and amortization - EBITDA**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [D001](#d001---formula-in-poc) | Turnover	| 1 |
| [D111](#d111---formula-in-poc) | Remaining Income | 1 |
| [D025](#d025---formula-in-poc) | Costs of goods sold and material consumed | -1 |
| [D026](#d026---formula-in-poc) | Supplies and external services	| -1 |
| [D029](#d029---formula-in-poc) | Employee expenses | -1 |
| [D108](#d108---formula-in-poc) | Remaining expenses | -1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D085 - Formula in POC
**Earnings before interest and taxes - EBIT**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [D084](#d084---formula-in-poc) | Earnings before Interest, Taxes, Depreciation and Amortization - EBITDA | 1 |
| [D041](#d041---formula-in-poc) | Expenses/reversals of depreciations and amortizations	| -1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D086 - Formula in POC
**Earnings before taxes - EBT**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [D085](#d085---formula-in-poc) | Earnings before Interest and Tax - EBIT | 1 |
| [D053](#d053---formula-in-poc) | Interest expenses | -1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D087 - Formula in POC
**Net income**

| Variable name	| Variable description | Coefficient |
| :----: | :---------- | :---: |
| [D086](#d086---formula-in-poc) | Earnings before Tax - EBT | 1 |
| [D060](#d060---formula-in-poc) | Income tax	| -1 |

[return](#b3.-profit-and-loss-statement-variables)

------------------------------------------------------

## D108 - Formula in POC
**Remaining expenses**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03026 | Adjustments | Q03-A0108-1 | 1 |
| VF03034	| Depreciation and adjustments of financial fixed assets | Q03-A0114-1 | 1 |
| VF03055	| Reversals of amortizations and adjustments | Q03-A0132-1 | -1 |
| VF03965	| Costs - Amortizations of investment in properties | Q05-0545-Nota45-A1431-1 | -1 |
| VF03027	| Provisions | Q03-A0109-1 | 1 |
| VF03993	| Revenues - Provisions decreases | Q05-0546-Nota46-A1463-1 | -1 |
| VF03029	| Taxes |	Q03-A0110-1 | 1 |
| VF03030	| Other operating costs | Q03-A0111-1 | 1 |
| VF03033	| Losses in group and associated companies | Q03-A0113-2 | 1 |
| VF03035	| Interest expenses - relative to group companies | Q03-A0115-1 | 1 |
| VF03036	| Interest expenses - others |	Q03-A0116-1 | 1 |
| VF03039	| Extraordinary costs |	Q03-A0118-2 | 1 |
| VF03964	| Interests paid |	Q05-0545-Nota45-A1429-1 | -1 |

[return](#b3.-profit-and-loss-statement-variables)

----------------------------------------------------

## D111 - Formula in POC
**Remaining income**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03052 | Operating subsidies | Q03-A0130-1 | 1 |
| VF03049 | Variation in production | Q03-A0127-2 | 1 |
| VF03050	| Capitalized production | Q03-A0128-2 | 1 |
| VF03051	| Supplementary income | Q03-A0129-1 | 1 |
| VF03053	| Operating revenues | Q03-A0131-1 | 1 |
| VF03057	| Gains in group and associated companies | Q03-A0134-1 | 1 |
| VF03058	| Income from equity holdings | Q03-A0135-1 | 1 |
| VF03059	| Income from negotiable securities and other financial applications - relative to group companies | Q03-A0136-1 | 1 |
| VF03060	| Income from negotiable securities and other financial applications | Q03-A0137-1 | 1 |
| VF03061	| Interest Income and similar earnings- relative to group companies | Q03-A0138-1 | 1 |
| VF03062	| Interest Income and similar earnings - Others | Q03-A0139-1 | 1 |
| VF03065	| Extraordinary revenues | Q03-A0141-2 | 1 |
| VF03993	| Revenues - Decreases in Provisions | Q05-0546-Nota46-A1463-1 | -1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## D112 - Formula in POC
**(Remaining expenses) of which: Impairment losses, changes in fair value and other expenses and losses in financial investments and financial instruments**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF05204	| Costs - Losses in group and associated companies | Q05-0545-Nota45-A1430-1 | 1 |
| VF03970	| Costs - Other financial costs | Q05-0545-Nota45-A1436-1 | 1 |
| VF04046	| Extraordinary costs – Disposal of financial investments | Q06-A0651 | 1 |
| VF03966	| Costs - Adjustments of financial fixed assets | Q05-0545-Nota45-A1432-1 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## DL002 - Formula in POC
**Other expenses - Cash discounts granted**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03968 |	Costs  - Cash discounts granted | Q05-0545-Nota45-A1434-1 |	1 |

[return](#b3.-profit-and-loss-statement-variables)

------------------------------------------------------

## DL005 - Formula in POC
**Other expenses - Other - Donations**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03978 | Costs - Donations | Q05-0546-Nota46-A1448-1 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

------------------------------------------------------

## DL011 - Formula in POC
**Salaries of corporate bodies**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF04036 |	Employee expenses - Salaries of corporate bodies | Q06-A0641 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## DL012 - Formula in POC
**Employee Salaries**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF04037 | Employee expenses - Salaries of employees | Q06-A0642 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## DL013 - Formula in POC
**Social security expenses**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF04040 |	Employee expenses - Social security expenses | Q06-A0645 | 1 |


[return](#b3.-profit-and-loss-statement-variables)

------------------------------------------------------

## DL014 - Formula in POC
**Insurance schemes for accidents at work and occupational diseases**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF04041 |	Employee expenses - Insurance schemes for accidents at work and occupational diseases | Q06-A0646 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

-----------------------------------------------------

## DL017 - Formula in POC
**Services**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03047	| Services | Q03-A0126-1 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

----------------------------------------------------

## DL043 - Formula in POC
**Supplementary income**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03051	| Supplementary income | Q03-A0129-1 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

------------------------------------------------------

## DL045 - Formula in POC
**Employee expenses - Other, except salaries**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF03022	| Employee expenses - Pensions | Q03-A0105-1 | 1 |
| VF03023	| Employee expenses - Others | Q03-A0106-1 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

------------------------------------------------------

## DL047 - Formula in POC
**Indirect taxes**

| Variable name	| Variable description | Item in IES| Coefficient |
| :----: | :------------- | :-------------- | :---: |
| VF04032 | Indirect Taxes | Q06-A0637 | 1 |

[return](#b3.-profit-and-loss-statement-variables)

------------------------------------------------------


Footnotes