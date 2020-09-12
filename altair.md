# Overview

## Bar Chart

```python
trend_bar = alt.Chart(trends).mark_bar().encode(
    x="search_term",
    y="value",
    color="search_term"
)
```

# Overview

## Line Chart

```python
alt.Chart(lifecountries).mark_circle().encode(
    x='Country GDP',
    y='Life Expectancy'
).properties(
    width=700,
    height=300,
    title="Relación PIB/esperanza de vida",
    tooltip='country'
    color='Continent',
    size='size'
).interactive()
```
# Overview

## Scatter Chart

```python
alt.Chart(temp).mark_circle().encode(
    x='lat',
    y='lon'
)
```
# Overview

## Map Chart

```python
points = alt.Chart(temp).mark_circle().encode(
    latitude="lat",
    longitude="lon",
    color=alt.Color("mean(temp)",scale=alt.Scale(domain=[-30,10,40],range=["lightblue","orange","red"]))
)

# remote geojson data object
url = "https://raw.githubusercontent.com/datasets/geo-countries/master/data/countries.geojson"
data_geojson_remote = alt.Data(url=url, format=alt.DataFormat(property='features',type='json'))

# chart object
background = alt.Chart(data_geojson_remote).mark_geoshape(
    fill="lightgrey",
    stroke="white"
).encode(
    color="properties.name:N"
).properties(
    projection={'type': 'identity', 'reflectY': True}
)

(background+points)
```
# Overview

## Histograma Chart

```python
hist_brain = alt.Chart(brain).mark_bar().encode(
    x=alt.X('Brain Weight',bin=alt.Bin(maxbins=100)),
    y="count()"
).properties(
    width=300,
    height=150,
    title="Relación peso del cerebro y del cuerpo"
).interactive()
```
# Overview

## Comp Horizontal

```python
con |
```
# Overview

## Comp layer

```python
con +
```
# Overview

## Selection Single

```python
select_type= alt.selection(type='single',encodings=['x'])

scat_snake=alt.Chart(snake).mark_circle().encode(
    x='evidence',
    y='popularity',
    color='type'
).transform_filter(select_type)

bar_snake=alt.Chart(snake).mark_bar().encode(
    x='type',
    y='count()',
    color='type'
).add_selection(select_type)

scat_snake|bar_snake
```
# Overview

## Selection interval

```python


trends_line2= alt.Chart(trends).mark_line().encode(
    x='yearmonth(date):T',
    y='mean(value)',
    color='search_term',
    tooltip='search_term').properties(high=100)
select_date= alt.selection(type='interval',encodings=['x'])
```
