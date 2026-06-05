# Data Jobs Dashboard w/ Power BI
![aa](/Images/1_Exec_Dash.png)

## Introduction
AdventureWorks is a global company that makes and sells bicycles, bike parts, and cycling accessories. As a Data Analyst before making a dashboard I wyznaczyłem cele dashboardu i odpowiedziałem na kluczowe pytania.


Goals:
- Track KPIs (measurement used to define whether an organization is meeting a predefined goal)
- compare regional performance
- Analyze product-level trends
- identify high-value customers

 3 key questions:

 Q1: Jakiego typu dane będą używane? Typ danych wyznacza jakie rodzaje wizualizacji będą najlepiej do tych danych przystosowane
 A1:
   - Time series - profit, revenue, orders in time
   - Categorical - Product Cutegories and subcutegories
   - Geospatial - TerritoryLookup Table
   - hierarchic - 

 Q2: Co chcę zakomunikować/przedaswić pokazać w raporcie?
 A2: Porównanie wartości w czasie lub w różnych kategoriach, np. Total Customers,  Monthly revenue, Orders by Country, Orders by Category 
     Kompozycje - rozbicie całości na części składowe np.: Orders by Customer Occupation, Orders by Customers Income Level

 Q3: Kim są adbiorcy dashboardu i czego potrzebują?
 A3: Menadżerowie: posumowanie, szybkie wnioski, pomaga w podejmowaniu decyzji, powszechne wykresy





Data Model:

2 fact tables: sales table and returns table - Contains details for every order and every return (date, quantity, and price).
7  dimension tables - contains calendar table, information about customers, territory and product

star schema? what is it? 



