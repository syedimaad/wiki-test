# **Objective**

The aim of the document is to capture the broken down steps to build the
Inhouse Shoppable ML platform.

**Link to existing recommendation flow**

Project Notebook:
<http://perf.ads.jupyter1-n3.dailyhunt.in/groot/tree/gautham/shoppable_v2>

# **Top View**

## **Group Frames Model**

Find the group of similar frames in the Video in the increasing order of
time

**Input** → Shoppable Video

**Output 1**

frame group 1 → \[timestamps\]

frame group 2 → \[timestamps\]

frame group 3 → \[timestamps\]

**Jupiter Notebook**: Link to be added

**Detailed Work**: Group Frames Model

**KPIs to track efficiency**

Below are the KPI we would be established in the first iteration. This
can act as a baseline to iterate on top of it and improvise.

Link:
<http://perf.ads.jupyter1-n3.dailyhunt.in/groot/tree/gautham/shoppable_v2/kpi>

**Excel with KPIs:**
[https://docs.google.com/spreadsheets/d/1q00x59C8NwYoutyrvy03NKaUP_0zOv_9vGF8kfEwWm8/edit#gid=1726612002](https://docs.google.com/spreadsheets/d/1q00x59C8NwYoutyrvy03NKaUP_0zOv_9vGF8kfEwWm8/edit#gid=1726612002){card-appearance="inline"}

## **Prominent Frame extraction**

**Input →** Frame group

**Output** → Most prominent frame based on **Area**

**Jupiter Notebook**: Link to be added

**Detailed Work**:

**KPIs to track efficiency**

TBD

## **Key Frame Entities Extraction**

**Input** → Most prominent frame

**Output** → Objects to search in the catalog

**Jupiter Notebook**: Link to be added

**Detailed Work**:

**KPIs to track efficiency**

TBD

## **Catalog Matching**

**Input** → Objects detected from the most prominent frame

**Output** → Related products in decreasing order of scores using the
entire **Accio** product catalog, along with product meta

**Jupiter Notebook**: Link to be added

**Detailed Work**:

**KPIs to track efficiency**

TBD

## **Backend**

Layout the recommendation into a persistent store and provide
recommendation APIs

**KPIs to track efficiency**

TBD

**Action item**

To make way to access the entire Accio product catalog
