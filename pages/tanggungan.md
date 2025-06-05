---
title: Tanggungan - FMM
---
<LastRefreshed/>

> The objective of this dashboard is to recreate  <Link 
    url="https://docs.google.com/document/d/1tJlVIYRTI0wTyuWCU6J9j23EyO7rNSQ4XmaO95kHQMA/edit?usp=sharing"
    label="JBI’s original Data Health Dashboard (KK only)"
/> originally powered by data <Link 
    url="https://docs.google.com/document/d/1ft5_HxxNEDMxu28PU3FC829K0QZipxed9P-MuO3Blp0/edit?usp=sharing"
    label="queried from CRM"
/>—by using data directly from PPA. 
>
> The SQL scripts used for PPA in this dashboard were carefully adapted from the original CRM-based scripts to maintain alignment with JBI’s data health metrics, while ensuring consistency and reliability across data sources.

---

## Summary

```sql tanggungan_total
  select
      *
  from sample.tanggungan_total
```

<Grid cols=5>
  <BigValue 
    data={tanggungan_total} 
    value=total_asnaf
    fmt=num1k
    title="Total KK FMM"
  />
  <BigValue 
    data={tanggungan_total} 
    value=cleaned_data
    fmt=num1k
  />
    <BigValue 
    data={tanggungan_total} 
    value=cleaned_data_pct
    title="Cleaned Data (%)"
  />
  <BigValue 
    data={tanggungan_total} 
    value=dirty_data
    fmt=num1k
  />
  <BigValue 
    data={tanggungan_total} 
    value=dirty_data_pct
    title="Dirty Data (%)"
  />
</Grid>

```sql tanggungan_metrics
  select
      *
  from sample.tanggungan_metrics
```

```sql pie_data
select 
  "Field Name" as field,
  'Valid' as name,
  Valid as value
from tanggungan_metrics
union all
select 
  "Field Name",
  'Missing',
  Missing
from tanggungan_metrics
union all
select 
  "Field Name",
  'Invalid',
  Invalid
from tanggungan_metrics
```

<DataTable data={tanggungan_metrics}>     
  <Column id="Field Name"/> 
  <Column id="Total"/> 
  <Column id="Valid" contentType=colorscale colorScale=#5C947D/> 
  <Column id="Invalid" contentType=colorscale colorScale=#DE6B64/> 
  <Column id="Missing" contentType=colorscale colorScale=#EBA776/> 
</DataTable>

---

## Dashboard
<Grid cols=2>

<Group>  
<Details title="IC No. Valid Criteria" open="true">
Numeric, 12 digits, and must be Mykad or Mykid format.
</Details>
<ECharts config={{
  title: {
    text: 'IC No.',
    left: 'center',
    top: 'middle',
    textStyle: { fontSize: 14, fontWeight: 'bold', color: '#333' }
  },
  tooltip: {
    formatter: function (params) {
      const name = params.name;
      const value = params.value.toLocaleString(); // Adds commas
      const percent = params.percent.toFixed(2); // Ensures two decimal places
      return `${name}: ${value} (${percent}%)`;
    }
  },
  legend: { top: 'bottom' },
  series: [{
    type: 'pie', radius: ['40%', '70%'],
    label: { show: true, position: 'outside', formatter: '{b}\n{d}%' },
    data: [
      { value: 127645, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 1006, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 2821, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
    ]
  }]
}} />
</Group>

<Group>  
<Details title="Gender Valid Criteria" open="true">
Gender column is 0 or 1
</Details>
<ECharts config={{
  title: {
    text: 'Gender',
    left: 'center',
    top: 'middle',
    textStyle: { fontSize: 14, fontWeight: 'bold', color: '#333' }
  },
  tooltip: {
    formatter: function (params) {
      const name = params.name;
      const value = params.value.toLocaleString(); // Adds commas
      const percent = params.percent.toFixed(2); // Ensures two decimal places
      return `${name}: ${value} (${percent}%)`;
    }
  },
  legend: { top: 'bottom' },
  series: [{
    type: 'pie', radius: ['40%', '70%'],
    label: { show: true, position: 'outside', formatter: '{b}\n{d}%' },
    data: [
      { value: 131457, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 15, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 0, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
    ]
  }]
}} />
</Group>

<Group>  
<Details title="Postcode Valid Criteria" open="true">
Must be numeric and 5-digit postcode format.
</Details>
<ECharts config={{
  title: {
    text: 'Postcode',
    left: 'center',
    top: 'middle',
    textStyle: { fontSize: 14, fontWeight: 'bold', color: '#333' }
  },
  tooltip: {
    formatter: function (params) {
      const name = params.name;
      const value = params.value.toLocaleString(); // Adds commas
      const percent = params.percent.toFixed(2); // Ensures two decimal places
      return `${name}: ${value} (${percent}%)`;
    }
  },
  legend: { top: 'bottom' },
  series: [{
    type: 'pie', radius: ['40%', '70%'],
    label: { show: true, position: 'outside', formatter: '{b}\n{d}%' },
    data: [
      { value: 131329, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 129, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 100, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
    ]
  }]
}} />
</Group>

<Group>  
<Details title="Mobile No. Valid Criteria" open="true">
Must follow numeric mobile phone format.
</Details>
<ECharts config={{
  title: {
    text: 'Mobile No.',
    left: 'center',
    top: 'middle',
    textStyle: { fontSize: 14, fontWeight: 'bold', color: '#333' }
  },
  tooltip: {
    formatter: function (params) {
      const name = params.name;
      const value = params.value.toLocaleString(); // Adds commas
      const percent = params.percent.toFixed(2); // Ensures two decimal places
      return `${name}: ${value} (${percent}%)`;
    }
  },
  legend: { top: 'bottom' },
  series: [{
    type: 'pie', radius: ['40%', '70%'],
    label: { show: true, position: 'outside', formatter: '{b}\n{d}%' },
    data: [
      { value: 15258, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 109863, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 6351, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
    ]
  }]
}} />
</Group>

<Group>  
<Details title="Education Valid Criteria" open="true">
Age between 4–8, schooling = yes, max edu ≤ current edu.
</Details>
<ECharts config={{
  title: {
    text: 'Education',
    left: 'center',
    top: 'middle',
    textStyle: { fontSize: 14, fontWeight: 'bold', color: '#333' }
  },
  tooltip: {
    formatter: function (params) {
      const name = params.name;
      const value = params.value.toLocaleString(); // Adds commas
      const percent = params.percent.toFixed(2); // Ensures two decimal places
      return `${name}: ${value} (${percent}%)`;
    }
  },
  legend: { top: 'bottom' },
  series: [{
    type: 'pie', radius: ['40%', '70%'],
    label: { show: true, position: 'outside', formatter: '{b}\n{d}%' },
    data: [
      { value: 29608, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 0, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 283, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
    ]
  }]
}} />
</Group>

<Group>  
<Details title="District Valid Criteria" open="true">
Daerah must not be null.
</Details>
<ECharts config={{
  title: {
    text: 'District',
    left: 'center',
    top: 'middle',
    textStyle: { fontSize: 14, fontWeight: 'bold', color: '#333' }
  },
  tooltip: {
    formatter: function (params) {
      const name = params.name;
      const value = params.value.toLocaleString(); // Adds commas
      const percent = params.percent.toFixed(2); // Ensures two decimal places
      return `${name}: ${value} (${percent}%)`;
    }
  },
  legend: { top: 'bottom' },
  series: [{
    type: 'pie', radius: ['40%', '70%'],
    label: { show: true, position: 'outside', formatter: '{b}\n{d}%' },
    data: [
      { value: 131368, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 0, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 104, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
    ]
  }]
}} />
</Group>

<Group>  
<Details title="Age Valid Criteria" open="true">
DOB year must match IC year and calculated age must match DOB.
</Details>
<ECharts config={{
  title: {
    text: 'Age',
    left: 'center',
    top: 'middle',
    textStyle: { fontSize: 14, fontWeight: 'bold', color: '#333' }
  },
  tooltip: {
    formatter: function (params) {
      const name = params.name;
      const value = params.value.toLocaleString(); // Adds commas
      const percent = params.percent.toFixed(2); // Ensures two decimal places
      return `${name}: ${value} (${percent}%)`;
    }
  },
  legend: { top: 'bottom' },
  series: [{
    type: 'pie', radius: ['40%', '70%'],
    label: { show: true, position: 'outside', formatter: '{b}\n{d}%' },
    data: [
      { value: 124921, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 470, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 6107, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
    ]
  }]
}} />
</Group>

<Group>  
<Details title="Health Valid Criteria" open="true">
Person must be healthy and not bedridden.
</Details>
<ECharts config={{
  title: {
    text: 'Health',
    left: 'center',
    top: 'middle',
    textStyle: { fontSize: 14, fontWeight: 'bold', color: '#333' }
  },
  tooltip: {
    formatter: function (params) {
      const name = params.name;
      const value = params.value.toLocaleString(); // Adds commas
      const percent = params.percent.toFixed(2); // Ensures two decimal places
      return `${name}: ${value} (${percent}%)`;
    }
  },
  legend: { top: 'bottom' },
  series: [{
    type: 'pie', radius: ['40%', '70%'],
    label: { show: true, position: 'outside', formatter: '{b}\n{d}%' },
    data: [
      { value: 117127, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 6318, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 8027, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
    ]
  }]
}} />
</Group>

</Grid>

---
## References
      <BigLink url='https://www.notion.so/SQL-DQ-Agihan-NFM-Tanggungan-JBI-Criteria-2082b8e44fc6801dbc3cc67f98ca9d1b?source=copy_link'>SQL scripts that query data from PPA — powering this dashboard. Adapted from the original CRM version below.</BigLink> 

      <BigLink url='https://docs.google.com/document/d/1ft5_HxxNEDMxu28PU3FC829K0QZipxed9P-MuO3Blp0/edit?usp=sharing'>Original SQL scripts for extracting data from CRM, based on JBI’s data health metrics.</BigLink> 


      <BigLink url='https://docs.google.com/document/d/1tJlVIYRTI0wTyuWCU6J9j23EyO7rNSQ4XmaO95kHQMA/edit?usp=sharing'>Initial JBI dashboard used to define and monitor data health metrics.</BigLink> 

      <BigLink url='https://dbdocs.io/1zaak/ppa_core?table=asnaf&schema=dbo&view=table_structure'>PPA Data Structure & ERD</BigLink> 

---
## Changelog
### June 4
- Created dashboard Tanggungan by FMM. 

      