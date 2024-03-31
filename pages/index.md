---
title: Espalhamento da Dengue no Brasil no século 21
---



## A dengue no ínicio do século 21

```sql casos_por_ano
select year, sum(total) as total from dengue group by year order by year asc
```

No ano 2000, o Brasil registrou <Value data={casos_por_ano} column=total row=0/>  casos de dengue. Em <Value data={casos_por_ano} column=year row=24/>, o número de casos subiu para <Value data={casos_por_ano} column=total row=24/>.



## Onde estava a dengue am 2000?
Na tabela a baixo é possível ver o total de casos e a incidência (por 100 mil habitantes) de dengue por estado no ano 2000.

```sql incidence_map
select
  estado,
  nome_estado,
  total,
  incidencia
  from dengue
  where year = 2000
  order by incidencia desc
```

<DataTable data={incidence_map} rows=10/>

## E em 2019?
```sql incidence_map2
select
  estado,
  nome_estado,
  total,
  incidencia
  from dengue
  where year = 2019
  order by incidencia desc
```

<DataTable data={incidence_map2} rows=10/>

```sql evolucao
select year as ano, nome_estado as nome, total, incidencia from dengue where estado != '"s' and estado not like ' %' order by All;
```

## Espalhamento ao longo dos anos

<Heatmap 
data={evolucao} 
x=ano 
y=nome
value=incidencia
title="Evolução da dengue por ano e estados"
/>