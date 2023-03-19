Case scheme:

```mermaid
flowchart TD;
    dist([Distributions])-->synth([Synthesised data]);
    logic([Business logic])-->synth[Synthesised data];
    synth[Synthesised data]-->feat[Feature engineering];
    feat[Feature engineering]-->prop[Propensity models];
    hyper[Hyperparametric optimization]-->prop[Propensity models];
    prop[Propensity models]-->expl[Explainability models];
```

```python
data = {
    'features': ['age_sim', 'ind_risk_sim', 'income_sim', 'pers_exp_sim', 'house_exp_sim', 'taxes_sim', 'transp_telecom_sim', 'hobby_sim'],
    'age_sim': [1, -0.00665947056405372, 0.00291644965339247, 0.0107779942638097, 0.00698674581731255, 0.00729153655132963, 0.0099866509330216, 0.00931630696561133],
    'ind_risk_sim': [-0.00665947056405372, 1, 0.0039918072709289, 0.00806259039194059, 0.00457023635440603, 0.0061985340641631, 0.00768699810849585, -0.00332322616613201],
    'income_sim': [0.00291644965339247, 0.0039918072709289, 1, 0.560949334881676, 0.58892666343229, 0.581907424628933, 0.562946509689962, 0.352350802339294],
    'pers_exp_sim': [0.0107779942638097, 0.00806259039194059, 0.560949334881676, 1, 0.928449923861951, 0.929598634668897, 0.934775947642248, 0.714298364869941],
    'house_exp_sim': [0.00698674581731255, 0.00457023635440603, 0.58892666343229, 0.928449923861951, 1, 0.93031279279417, 0.927846735467478, 0.679286362990223],
    'taxes_sim': [0.00729153655132963, 0.0061985340641631, 0.581907424628933, 0.929598634668897, 0.93031279279417, 1, 0.92920510128812, 0.689442053350162],
    'transp_telecom_sim': [0.0099866509330216, 0.00768699810849585, 0.562946509689962, 0.934775947642248, 0.927846735467478, 0.92920510128812, 1, 0.714114127908189],
    'hobby_sim': [0.00931630696561133, -0.00332322616613201, 0.352350802339294, 0.714298364869941, 0.679286362990223, 0.689442053350162, 0.714114127908189, 1]
}
```


| Number | Factor | Code | Variable type | Possible values | 
| --- | --- | --- | --- | --- | 
| 1 | gender | sex | Binary	 | M; F | 
| 2 | Age - completed years | age | Proportional | 20 - 24; 25 - 34; 35-44; 45-54; 55-64; 65-74; 75+ | 
| 3 | Level of education | lv_educ | Ordinal | Incomplete; Primary; Basic; Secondary; Higher | 
| 4 | Employment status | empl_stat | Ordinal | Employers; Self-employed; Employed in private sector; Employed in public sector; Unpaid family workers | 
| 5 | Marital status | marit_stat | Ordinal | Single; Married; Divorced; Widowed | 
| 6 | Number of household members | house_memb | Interval | 1; 2; 3; 4; 5; 6; 7+ | 
| 7 | Number of children under 18 years | chil_u_18_y | Interval | No children under 18; One child under 18; Two children under 18; Three children under 18; Four children under 18; Five children under 18; Six or more children under 18 | 
| 8 | Nationality | nation | Nominal | Bulgaria; EU; Other | 
| 9 | Religion | religion | Nominal | Protestant; Catholic; Orthodox; Muslim; Other; No religion; I do not identify myself | 
| 10 | Socio-economic status | soc_econ_stat | Nominal | Economically active; Economically inactive | 
| 11 | Profession - Industry | prof_ind | Nominal | Agriculture, forestry and fisheries; Mining and processing industry; Utilities (electricity distribution and water supply); Construction; Trade, automobile and motorcycle repair; Transportation, warehousing and mail; Hospitality and restaurant services; Creation and distribution of information and creative products; Telecommunications; Financial and administrative activities; Public administration; Education and research; Human health and social work; Other activities | 
| 12 | Professional status | prof_stat | Nominal | Management contract; Employment contract; Civil contract; Self-employed; Unemployed; Pensioner | 
| 13 | No. apartment/house | count_house | Interval | 0; 1; 2+ | 
| 14 | Land ownership | own_field | Nominal | YES; NO | 
| 15 | Cars per household | num_car_house | Interval | 0; 1; 2; 3+ | 
| 16 | The apartment I live in is | own_rent_house | Binary | own; rented | 
| 17 | Education | edu | Nominal | Educational Sciences; Humanities; Social, Economic and Legal Sciences; Natural Sciences, Mathematics and Informatics; Technical Sciences; Agricultural Sciences and Veterinary Medicine; Health and Sports; Arts; Security and Defense | 
| 18 | Temperament | temp | Nominal | Choleric; Phlegmatic; Sanguine; Melancholic | 
| 19 | Individual risk preference | ind_risk | Interval | 0; 0.1; 0.2; 0.3; 0.4; 0.5; 0.6; 0.7; 0.8; 0.9; 1 | 
| 20 | Previous investment experience in years | invest_exp | Proportional | 0; 1-5; 6-10; 11-15; 16-25 | 
| 21 | Investment experience with shares | shares | Binary | YES; NO | 
| 22 | Investment experience with bonds | corp_oblig | Binary | YES; NO | 
| 23 | Investment experience with others | oth | Binary | YES; NO | 
| 24 | Investment experience with investment funds | inv_fund | Binary | YES; NO |
| 25 | Investment experience with currencies | cash | Binary | YES; NO |
| 26 | Investment experience with cryptocurrencies | crypto | Binary | YES; NO |
| 27 | Investment experience with government securities | gov_bond | Binary | YES; NO |
| 28 | Investment experience with bank deposits | deposits | Binary | YES; NO |
| 29 | Income | income | Proportional | Up to 6121; Up to 12001; Up to 27601; Up to 43201; Up to 58801; Up to 74401; Over 90001+ |
| 30 | Personal expenses | pers_exp | Proportional | Group 1; Group 2; Group 3; Group 4 |
| 31 | Housing costs | house_exp | Proportional | Group 1; Group 2; Group 3; Group 4 |
| 32 | Taxes and insurance | taxes | Proportional | Group 1; Group 2; Group 3; Group 4 |
| 33 | Transport and communications | transp_telecom | Proportional | Group 1; Group 2; Group 3; Group 4 |
| 34 | Leisure and hobby | hobby | Proportional | Group 1; Group 2; Group 3; Group 4 |
| 35 | Preferred method of banking | banking | Binary | Online; Offline |
| 36 | Average number of bank transactions | bk_oprat | Proportional | Until 7; From 8 to 10; From 11 to 13; From 14 to 18 From 19 |
| 37 | Debit card | bk_dc | Proportional | Under one; One; Two; Three |
| 38 | Credit card | bk_cc | Binary | YES; NO |
| 39 | Current account in BGN | bk_acc | Binary | YES; NO |
| 40 | Property insurance | ins_prop | Binary | YES; NO |
| 41 | Insurance - life | ins_life | Binary | YES; NO |
| 42 | Insurance - Motor Vehicle (Casco) | ins_casco | Binary | YES; NO |
| 43 | Additional health insurance | health_ins | Binary | YES; NO |
| 44 | Overdraft | overdraft | Binary | YES; NO |
| 45 | Consumer credit | cons_cred | Binary | YES; NO |
| 46 | Mortgage | mortgage | Binary | YES; NO |
| 47 | Car lease/loan | car_leas | Binary | YES; NO |
| 48 | Additional pension insurance - 3rd pillar | pens_ins | Binary | YES; NO |
