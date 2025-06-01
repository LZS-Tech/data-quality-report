---
title: Agihan - Data Quality Dashboard
---

<!-- <Details title='How to edit this page'>

  This page can be found in your project at `/pages/index.md`. Make a change to the markdown file and save it to see the change take effect in your browser.
</Details> -->

```sql kk_total
  select
      *
  from sample.kk_total
```

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
    label="Cleaned Data (%)"
  />
  <BigValue 
    data={kk_total} 
    value=dirty_data
  />
  <BigValue 
    data={kk_total} 
    value=dirty_data_pct
  />
</Grid>


```sql kk_metrics
  select
      *
  from sample.kk_metrics
```

<Grid cols=3>

</Grid>

<!-- 
```sql asnaf
  select
      *
  from ppa_core.asnaf
```
 -->



<!-- <Dropdown data={categories} name=category value=category>
    <DropdownOption value="%" valueLabel="All Categories"/>
</Dropdown>

<Dropdown name=year>
    <DropdownOption value=% valueLabel="All Years"/>
    <DropdownOption value=2019/>
    <DropdownOption value=2020/>
    <DropdownOption value=2021/>
</Dropdown>

```sql orders_by_category
  select 
      date_trunc('month', order_datetime) as month,
      sum(sales) as sales_usd,
      category
  from needful_things.orders
  where category like '${inputs.category.value}'
  and date_part('year', order_datetime) like '${inputs.year.value}'
  group by all
  order by sales_usd desc
```

<BarChart
    data={orders_by_category}
    title="Sales by Month, {inputs.category.label}"
    x=month
    y=sales_usd
    series=category
/>

## What's Next?
- [Connect your data sources](settings)
- Edit/add markdown files in the `pages` folder
- Deploy your project with [Evidence Cloud](https://evidence.dev/cloud)

## Get Support
- Message us on [Slack](https://slack.evidence.dev/)
- Read the [Docs](https://docs.evidence.dev/)
- Open an issue on [Github](https://github.com/evidence-dev/evidence) -->
