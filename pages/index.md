---
title: PPA - Data Quality Dashboard (KK)
---
<LastRefreshed/>

> The objective of this dashboard is to recreate  <Link 
    url="https://docs.google.com/document/d/1tJlVIYRTI0wTyuWCU6J9j23EyO7rNSQ4XmaO95kHQMA/edit?usp=sharing"
    label="this JBI data health dashboard"
/> that's <Link 
    url="https://docs.google.com/document/d/1ft5_HxxNEDMxu28PU3FC829K0QZipxed9P-MuO3Blp0/edit?usp=sharing"
    label="queried from CRM"
/>, with data queried from PPA. 


```sql kk_total
  select
      *
  from sample.kk_total
```

## Summary
<Grid cols=5>
  <BigValue 
    data={kk_total} 
    value=total_asnaf
  />
  <BigValue 
    data={kk_total} 
    value=cleaned_data
  />
    <BigValue 
    data={kk_total} 
    value=cleaned_data_pct
    title="Cleaned Data (%)"
  />
  <BigValue 
    data={kk_total} 
    value=dirty_data
  />
  <BigValue 
    data={kk_total} 
    value=dirty_data_pct
    title="Dirty Data (%)"
  />
</Grid>

```sql kk_metrics
  select
      *
  from sample.kk_metrics
```


<DataTable data={kk_metrics}>     
  <Column id="Field Name"/> 
  <Column id="Total"/> 
  <Column id="Valid" contentType=colorscale colorScale=#5C947D/> 
  <Column id="Invalid" contentType=colorscale colorScale=#DE6B64/> 
  <Column id="Missing" contentType=colorscale colorScale=#EBA776/> 
</DataTable>

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
      { value: 441844, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 145, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 6016, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
    ]
  }]
}} />
</Group>

<Group>  
<Details title="Gender Valid Criteria" open="true">
Last digit of IC must be odd or even (gender format).
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
      { value: 448002, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 3, name: 'Missing', itemStyle: { color: '#EBA776' }},
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
      { value: 441623, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 547, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 5835, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
    ]
  }]
}} />
</Group>

<Group>  
<Details title="Bank Info Valid Criteria" open="true">
Must include valid MOP, Bank Name, and Account Number.
</Details>
<ECharts config={{
  title: {
    text: 'Bank Info',
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
      { value: 312470, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 116680, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 18855, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
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
      { value: 361976, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 81264, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 4765, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
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
      { value: 1571, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 0, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 97, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
    ]
  }]
}} />
</Group>

<Group>  
<Details title="District Valid Criteria" open="true">
Daerah must match Daerah Kariah field.
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
      { value: 447862, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 0, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 143, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
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
      { value: 438541, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 131, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 9337, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
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
      { value: 325477, name: 'Valid', itemStyle: { color: '#5C947D' }},
      { value: 77727, name: 'Missing', itemStyle: { color: '#EBA776' }},
      { value: 44801, name: 'Invalid', itemStyle: { color: '#DE6B64' }}
    ]
  }]
}} />
</Group>

</Grid>

## References
      <BigLink url='https://www.notion.so/SQL-DQ-Agihan-KK-JBI-Criteria-2042b8e44fc680cebccadb18e0c9f688'>PPA SQL Queries that powers this dashboard</BigLink> 

      <BigLink url='https://docs.google.com/document/d/1ft5_HxxNEDMxu28PU3FC829K0QZipxed9P-MuO3Blp0/edit?usp=sharing'>The original CRM SQL Queries that's based on JBI's Data Health Criterias</BigLink> 


      <BigLink url='https://docs.google.com/document/d/1tJlVIYRTI0wTyuWCU6J9j23EyO7rNSQ4XmaO95kHQMA/edit?usp=sharing'>Original JBI Data Health Dashboard</BigLink> 