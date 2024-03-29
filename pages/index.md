---
title: Espalhamento da Dengue no Brasil no século 21
---



## A dengue no ínicio do século 21

```sql casos_por_ano
select year, sum(total) as total from dengue group by year order by year asc
```

No ano 2000, o Brasil registrou <Value data={casos_por_ano} column=total row=0/>  casos de dengue. Em <Value data={casos_por_ano} column=year row=24/>, o número de casos subiu para <Value data={casos_por_ano} column=total row=24/>.



## Onde estava a dengue am 2000?

```sql incidence_map
select
  estado,
  nome_estado,
  total
  from dengue
  where year = 2000
```

<DataTable data={incidence_map} rows=6/>

```sql evolucao
select year as ano, nome_estado as nome, total from dengue where estado != '"s' and estado not like ' %' order by All;
```

## Espalhamento ao longo dos anos

<Heatmap 
data={evolucao} 
x=ano 
y=nome
value=total
title="Evolução da dengue por ano e estados"
/>