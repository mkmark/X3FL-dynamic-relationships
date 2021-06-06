# X3FL dynamic relationships

## The relationship


```python
import numpy as np
import pandas as pd
```


```python
all_races = ["Goner", "Teladi", "NMMC", "Strong Arms", "TerraCorp", "Argon", "Boron", "Split", "Arteus", "OTAS", "Duke's", "Paranid", "Pirates", "Terran", "Yaki"]
# https://imgur.com/nqI0nbO, by blazenclaw, forum.egosoft.com
relationship_df = pd.read_csv("relationship.csv", index_col=0)
relationship_df = pd.DataFrame(relationship_df, columns=all_races)
relationship_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Goner</th>
      <th>Teladi</th>
      <th>NMMC</th>
      <th>Strong Arms</th>
      <th>TerraCorp</th>
      <th>Argon</th>
      <th>Boron</th>
      <th>Split</th>
      <th>Arteus</th>
      <th>OTAS</th>
      <th>Duke's</th>
      <th>Paranid</th>
      <th>Pirates</th>
      <th>Terran</th>
      <th>Yaki</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Goner</th>
      <td>1.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.05</td>
      <td>0.05</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Teladi</th>
      <td>0.00</td>
      <td>1.00</td>
      <td>0.15</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>-0.3</td>
    </tr>
    <tr>
      <th>NMMC</th>
      <td>0.00</td>
      <td>0.15</td>
      <td>1.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>-0.30</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Strong Arms</th>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>1.00</td>
      <td>-0.15</td>
      <td>-0.15</td>
      <td>-0.30</td>
      <td>0.15</td>
      <td>-0.30</td>
      <td>-0.15</td>
      <td>0.00</td>
      <td>0.05</td>
      <td>0.00</td>
      <td>-0.3</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>TerraCorp</th>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>-0.15</td>
      <td>1.00</td>
      <td>0.15</td>
      <td>0.05</td>
      <td>-0.15</td>
      <td>0.05</td>
      <td>-0.30</td>
      <td>0.00</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>0.0</td>
      <td>-0.3</td>
    </tr>
    <tr>
      <th>Argon</th>
      <td>0.05</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>-0.15</td>
      <td>0.15</td>
      <td>1.00</td>
      <td>0.15</td>
      <td>-0.15</td>
      <td>0.05</td>
      <td>0.15</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.3</td>
      <td>-0.3</td>
    </tr>
    <tr>
      <th>Boron</th>
      <td>0.05</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>-0.30</td>
      <td>0.05</td>
      <td>0.15</td>
      <td>1.00</td>
      <td>-0.30</td>
      <td>0.15</td>
      <td>0.05</td>
      <td>-0.30</td>
      <td>-0.15</td>
      <td>-0.30</td>
      <td>-0.3</td>
      <td>-0.3</td>
    </tr>
    <tr>
      <th>Split</th>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.15</td>
      <td>-0.15</td>
      <td>-0.15</td>
      <td>-0.30</td>
      <td>1.00</td>
      <td>-0.30</td>
      <td>0.15</td>
      <td>-0.30</td>
      <td>0.15</td>
      <td>0.00</td>
      <td>-0.3</td>
      <td>-0.3</td>
    </tr>
    <tr>
      <th>Arteus</th>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>-0.30</td>
      <td>0.05</td>
      <td>0.05</td>
      <td>0.15</td>
      <td>-0.30</td>
      <td>1.00</td>
      <td>-0.30</td>
      <td>0.00</td>
      <td>-0.15</td>
      <td>-0.30</td>
      <td>-0.3</td>
      <td>-0.3</td>
    </tr>
    <tr>
      <th>OTAS</th>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>-0.15</td>
      <td>-0.30</td>
      <td>0.15</td>
      <td>0.05</td>
      <td>0.15</td>
      <td>-0.30</td>
      <td>1.00</td>
      <td>0.00</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.3</td>
      <td>-0.3</td>
    </tr>
    <tr>
      <th>Duke's</th>
      <td>0.00</td>
      <td>0.00</td>
      <td>-0.30</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>1.00</td>
      <td>-0.30</td>
      <td>0.15</td>
      <td>-0.3</td>
      <td>-0.3</td>
    </tr>
    <tr>
      <th>Paranid</th>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.05</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.15</td>
      <td>0.15</td>
      <td>-0.15</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>1.00</td>
      <td>-0.30</td>
      <td>-0.3</td>
      <td>-0.3</td>
    </tr>
    <tr>
      <th>Pirates</th>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>0.00</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>0.15</td>
      <td>-0.30</td>
      <td>1.00</td>
      <td>-0.3</td>
      <td>-0.3</td>
    </tr>
    <tr>
      <th>Terran</th>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>-0.30</td>
      <td>0.00</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Yaki</th>
      <td>0.00</td>
      <td>-0.30</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>-0.30</td>
      <td>0.0</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div>



The problem is simple: given the relationship $\mathbf{R}$, target notority $\mathbf{N}$, find tactics $\mathbf{X}$, which is a vector that represents how much notority point one should get from a race.

$$
\mathbf{R}\mathbf{X}=\mathbf{N}
$$

$$
\mathbf{X}=\mathbf{R}^{-1}\mathbf{N}
$$

Let's first define $\mathbf{N}$ as vectors of 1, since we don't want to lose effort by hitting the notoriety ceiling.


```python
def get_X(races):
    R = np.array(relationship_df.loc[races, races])
    invR = np.linalg.inv(R) 
    N = np.ones(len(races))
    X = invR@N
    return X

def get_X_df(races):
    X = get_X(races)
    return pd.DataFrame(list(X)+[sum(X)]+[len(races)/sum(X)], index=races+['sum', 'efficiency']).transpose()
```

## Example solutions

Let's see if there is a solution for all the races

The number for each race represents how much effort you will have to put with that race to get 1 notoriety point for each race assuming you're to be friend with all these selected race.

The sum is the total workload of current tactic.

The efficiency is the sum of actual gained notoriety points (equal the number of races selected) divided by total workload.


```python
get_X_df(all_races)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Goner</th>
      <th>Teladi</th>
      <th>NMMC</th>
      <th>Strong Arms</th>
      <th>TerraCorp</th>
      <th>Argon</th>
      <th>Boron</th>
      <th>Split</th>
      <th>Arteus</th>
      <th>OTAS</th>
      <th>Duke's</th>
      <th>Paranid</th>
      <th>Pirates</th>
      <th>Terran</th>
      <th>Yaki</th>
      <th>sum</th>
      <th>efficiency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.071172</td>
      <td>0.415461</td>
      <td>0.807539</td>
      <td>-0.302713</td>
      <td>-0.796793</td>
      <td>-0.741422</td>
      <td>-0.68202</td>
      <td>-0.320156</td>
      <td>-1.119438</td>
      <td>-1.375322</td>
      <td>-0.433805</td>
      <td>-1.661266</td>
      <td>-1.767547</td>
      <td>-1.521107</td>
      <td>-1.544692</td>
      <td>-9.972109</td>
      <td>-1.504195</td>
    </tr>
  </tbody>
</table>
</div>



Unfortunately there is not a solution as one would have to get negative points from races. The problem is, when actively losing points of a race, the notoriety points of enemy races does not increase accordingly. However if that is true, we can see a path that you do some missions for some races but keep robbing other races and one day you will find yourself master of diplomacy with all races - too good to be true for those races you robbed.

Let's get results of some interesting races combo.


```python
commonwealth_races = ["Teladi", "Argon", "Boron", "Split", "Paranid"]
major_races = ["Goner", "Teladi", "NMMC", "Argon", "Boron", "Split", "Paranid", "Terran"]
all_but_yaki_races = ["Goner", "Teladi", "NMMC", "Strong Arms", "TerraCorp", "Argon", "Boron", "Split", "Arteus", "OTAS", "Duke's", "Paranid", "Pirates", "Terran"]
all_but_yaki_terran_races = ["Goner", "Teladi", "NMMC", "Strong Arms", "TerraCorp", "Argon", "Boron", "Split", "Arteus", "OTAS", "Duke's", "Paranid", "Pirates"]
all_but_yaki_terran_pirates_races = ["Goner", "Teladi", "NMMC", "Strong Arms", "TerraCorp", "Argon", "Boron", "Split", "Arteus", "OTAS", "Duke's", "Paranid"]
all_but_yaki_pirates_races = ["Goner", "Teladi", "NMMC", "Strong Arms", "TerraCorp", "Argon", "Boron", "Split", "Arteus", "OTAS", "Duke's", "Paranid", "Terran"]
all_but_terran_pirates_races = ["Goner", "Teladi", "NMMC", "Strong Arms", "TerraCorp", "Argon", "Boron", "Split", "Arteus", "OTAS", "Duke's", "Paranid", "Yaki"]
```

All commonwealth races, no problem


```python
get_X_df(commonwealth_races)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Teladi</th>
      <th>Argon</th>
      <th>Boron</th>
      <th>Split</th>
      <th>Paranid</th>
      <th>sum</th>
      <th>efficiency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>1.428571</td>
      <td>1.428571</td>
      <td>1.428571</td>
      <td>1.428571</td>
      <td>6.714286</td>
      <td>0.744681</td>
    </tr>
  </tbody>
</table>
</div>



All major races, no problem


```python
get_X_df(major_races)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Goner</th>
      <th>Teladi</th>
      <th>NMMC</th>
      <th>Argon</th>
      <th>Boron</th>
      <th>Split</th>
      <th>Paranid</th>
      <th>Terran</th>
      <th>sum</th>
      <th>efficiency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.623203</td>
      <td>0.869565</td>
      <td>0.869565</td>
      <td>3.767968</td>
      <td>3.767968</td>
      <td>3.787443</td>
      <td>3.787443</td>
      <td>5.533247</td>
      <td>23.006403</td>
      <td>0.347729</td>
    </tr>
  </tbody>
</table>
</div>



All but Yaki, not an option


```python
get_X_df(all_but_yaki_races)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Goner</th>
      <th>Teladi</th>
      <th>NMMC</th>
      <th>Strong Arms</th>
      <th>TerraCorp</th>
      <th>Argon</th>
      <th>Boron</th>
      <th>Split</th>
      <th>Arteus</th>
      <th>OTAS</th>
      <th>Duke's</th>
      <th>Paranid</th>
      <th>Pirates</th>
      <th>Terran</th>
      <th>sum</th>
      <th>efficiency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.10937</td>
      <td>0.904362</td>
      <td>0.637588</td>
      <td>-1.091562</td>
      <td>-0.909377</td>
      <td>-1.094362</td>
      <td>-1.093043</td>
      <td>-0.413423</td>
      <td>-1.679534</td>
      <td>-1.918018</td>
      <td>-0.755858</td>
      <td>-2.2777</td>
      <td>-2.425656</td>
      <td>-2.824747</td>
      <td>-13.83196</td>
      <td>-1.012149</td>
    </tr>
  </tbody>
</table>
</div>



Later we will learn that one of the best options, that if we want to have good relationship with as many races as possible, is as following


```python
get_X_df(all_but_yaki_terran_pirates_races)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Goner</th>
      <th>Teladi</th>
      <th>NMMC</th>
      <th>Strong Arms</th>
      <th>TerraCorp</th>
      <th>Argon</th>
      <th>Boron</th>
      <th>Split</th>
      <th>Arteus</th>
      <th>OTAS</th>
      <th>Duke's</th>
      <th>Paranid</th>
      <th>sum</th>
      <th>efficiency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.219569</td>
      <td>0.254951</td>
      <td>4.966994</td>
      <td>7.478574</td>
      <td>7.592467</td>
      <td>7.11746</td>
      <td>8.491154</td>
      <td>7.915631</td>
      <td>7.876733</td>
      <td>7.886442</td>
      <td>13.350788</td>
      <td>12.678057</td>
      <td>85.828819</td>
      <td>0.139813</td>
    </tr>
  </tbody>
</table>
</div>



Before that, let's consider another problem - the infinite notoriety we can get from Goner as a peaceful race. With Goner, the notoriety with Goner, Argon, Boron is actually infinite, thus not limited by 1. We should remove their possible influence, that is, to remove Goner, Argon, Boron.


```python
infinite_races = ["Goner", "Argon", "Boron"]
all_races_without_infinite = ["Teladi", "NMMC", "Strong Arms", "TerraCorp", "Split", "Arteus", "OTAS", "Duke's", "Paranid", "Pirates", "Terran", "Yaki"]
major_races_without_infinite = ["Teladi", "NMMC", "Split", "Paranid", "Terran"]
all_but_yaki_races_without_infinite = ["Teladi", "NMMC", "Strong Arms", "TerraCorp", "Split", "Arteus", "OTAS", "Duke's", "Paranid", "Pirates", "Terran"]
all_but_yaki_terran_races_without_infinite = ["Teladi", "NMMC", "Strong Arms", "TerraCorp", "Split", "Arteus", "OTAS", "Duke's", "Paranid", "Pirates"]
all_but_yaki_terran_pirates_races_without_infinite = ["Teladi", "NMMC", "Strong Arms", "TerraCorp", "Split", "Arteus", "OTAS", "Duke's", "Paranid"]
all_but_terran_pirates_races_without_infinite = ["Teladi", "NMMC", "Strong Arms", "TerraCorp", "Split", "Arteus", "OTAS", "Duke's", "Paranid", "Yaki"]
```

redo all above gives us the following, which does not change too much, however. Note the efficiency in the following chart is higher than actual, due to that Goner workload is not included yet. This will be addressed later.


```python
get_X_df(all_races_without_infinite)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Teladi</th>
      <th>NMMC</th>
      <th>Strong Arms</th>
      <th>TerraCorp</th>
      <th>Split</th>
      <th>Arteus</th>
      <th>OTAS</th>
      <th>Duke's</th>
      <th>Paranid</th>
      <th>Pirates</th>
      <th>Terran</th>
      <th>Yaki</th>
      <th>sum</th>
      <th>efficiency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.328493</td>
      <td>0.959057</td>
      <td>-0.422597</td>
      <td>-1.436036</td>
      <td>-0.008105</td>
      <td>-1.681945</td>
      <td>-2.245461</td>
      <td>0.02777</td>
      <td>-1.979967</td>
      <td>-2.200839</td>
      <td>-1.553343</td>
      <td>-1.758827</td>
      <td>-11.971799</td>
      <td>-1.002356</td>
    </tr>
  </tbody>
</table>
</div>




```python
get_X_df(all_but_yaki_races_without_infinite)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Teladi</th>
      <th>NMMC</th>
      <th>Strong Arms</th>
      <th>TerraCorp</th>
      <th>Split</th>
      <th>Arteus</th>
      <th>OTAS</th>
      <th>Duke's</th>
      <th>Paranid</th>
      <th>Pirates</th>
      <th>Terran</th>
      <th>sum</th>
      <th>efficiency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.87254</td>
      <td>0.849735</td>
      <td>-1.465397</td>
      <td>-1.992687</td>
      <td>0.090597</td>
      <td>-2.746575</td>
      <td>-3.486809</td>
      <td>-0.064615</td>
      <td>-2.959362</td>
      <td>-3.299816</td>
      <td>-3.179593</td>
      <td>-17.381983</td>
      <td>-0.632839</td>
    </tr>
  </tbody>
</table>
</div>




```python
get_X_df(all_but_yaki_terran_races_without_infinite)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Teladi</th>
      <th>NMMC</th>
      <th>Strong Arms</th>
      <th>TerraCorp</th>
      <th>Split</th>
      <th>Arteus</th>
      <th>OTAS</th>
      <th>Duke's</th>
      <th>Paranid</th>
      <th>Pirates</th>
      <th>sum</th>
      <th>efficiency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.88775</td>
      <td>0.748335</td>
      <td>-6.288639</td>
      <td>-12.933661</td>
      <td>0.967362</td>
      <td>-11.554157</td>
      <td>-16.267633</td>
      <td>-0.395007</td>
      <td>-14.058134</td>
      <td>-15.384824</td>
      <td>-74.278608</td>
      <td>-0.134628</td>
    </tr>
  </tbody>
</table>
</div>




```python
get_X_df(all_but_yaki_terran_pirates_races_without_infinite)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Teladi</th>
      <th>NMMC</th>
      <th>Strong Arms</th>
      <th>TerraCorp</th>
      <th>Split</th>
      <th>Arteus</th>
      <th>OTAS</th>
      <th>Duke's</th>
      <th>Paranid</th>
      <th>sum</th>
      <th>efficiency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.682387</td>
      <td>2.11742</td>
      <td>3.632319</td>
      <td>5.212411</td>
      <td>2.221933</td>
      <td>5.208282</td>
      <td>6.101887</td>
      <td>4.065927</td>
      <td>5.880404</td>
      <td>35.122969</td>
      <td>0.256243</td>
    </tr>
  </tbody>
</table>
</div>




```python
get_X_df(all_but_terran_pirates_races_without_infinite)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Teladi</th>
      <th>NMMC</th>
      <th>Strong Arms</th>
      <th>TerraCorp</th>
      <th>Split</th>
      <th>Arteus</th>
      <th>OTAS</th>
      <th>Duke's</th>
      <th>Paranid</th>
      <th>Yaki</th>
      <th>sum</th>
      <th>efficiency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-1.184655</td>
      <td>0.118922</td>
      <td>-1.233279</td>
      <td>-4.783234</td>
      <td>-2.462803</td>
      <td>-4.493523</td>
      <td>-5.424689</td>
      <td>-3.529255</td>
      <td>-5.530914</td>
      <td>-7.222722</td>
      <td>-35.746151</td>
      <td>-0.27975</td>
    </tr>
  </tbody>
</table>
</div>



## Let's explore all possibilities


```python
# https://stackoverflow.com/questions/26332412/python-recursive-function-to-display-all-subsets-of-given-set
def subs(l):
    if l == []:
        return [[]]

    x = subs(l[1:])

    return x + [[l[0]] + y for y in x]
```

### The Goner approach

Turned out there are the following number of possible combos.


```python
least_enemy_set_list_without_infinite = []
for races in subs(all_races_without_infinite):
    if races != []:
        if min(get_X(races))>0:
            enemy_set = set(all_races_without_infinite) - set(races)
            is_duplicate = False
            for i, least_enemy_set in enumerate(least_enemy_set_list_without_infinite):
                if enemy_set.issubset(least_enemy_set):
                    least_enemy_set_list_without_infinite[i] = enemy_set
                    is_duplicate = True
                    break
                if least_enemy_set.issubset(enemy_set):
                    is_duplicate = True
                    break
            if not is_duplicate:
                least_enemy_set_list_without_infinite = least_enemy_set_list_without_infinite + [enemy_set]
                
len(least_enemy_set_list_without_infinite)
```




    824



which are parsed into races, workload, and efficiency. Note that to exploit Goner relationship bonus we can not gain points from argon and boron directly, and the 0.05 factor from Goner adds a lot of workloads.


```python
parsed_least_enemy_set_list_without_infinite = []

r1 = np.array(relationship_df.loc[[infinite_races[0]], [infinite_races[0]]])[0,0]
r2 = np.array(relationship_df.loc[[infinite_races[0]], [infinite_races[1]]])[0,0]
r3 = np.array(relationship_df.loc[[infinite_races[0]], [infinite_races[2]]])[0,0]

for least_enemy_set in least_enemy_set_list_without_infinite:
    friend_races = list(set(all_races_without_infinite) - least_enemy_set)
    X = get_X(friend_races)
    workload_without_infinite = sum(X)
    R_extra = np.array(relationship_df.loc[infinite_races, friend_races])
    N_extra = R_extra@X
    workload_extra = max((1-N_extra[0])/r1,(1-N_extra[1])/r2,(1-N_extra[2])/r3)
    efficiency = (len(all_races) - len(list(least_enemy_set)))/(workload_without_infinite+workload_extra)
    item = " - ".join(list(least_enemy_set)) + ", " + str(workload_without_infinite+workload_extra) + ", " + str(efficiency)
    print(item)
    parsed_least_enemy_set_list_without_infinite += [item]
```

    Split - OTAS - Arteus - TerraCorp, 1057.6083691205047, 0.010400825410588871
    Yaki - Strong Arms - Arteus - Teladi - TerraCorp, 1410.8633621392462, 0.00708785858953579
    Arteus - Terran - Teladi - TerraCorp, 1454.2439908459778, 0.007564067700634587
    Pirates - Split - Arteus - Strong Arms - Teladi - TerraCorp, 2431.643270024765, 0.003701200793284263
    Yaki - Pirates - Split - Strong Arms - TerraCorp, 396.11594526349927, 0.02524513370283018
    Terran - TerraCorp - Yaki, 171.2032461286091, 0.07009212892485411
    Arteus - Paranid - TerraCorp, 2023.7956074370447, 0.005929452537549937
    Paranid - Yaki - Strong Arms - Teladi - TerraCorp, 11081.001168964041, 0.0009024455324495645
    Paranid - Strong Arms - Terran - Teladi - TerraCorp, 11081.001168964132, 0.000902445532449557
    Split - TerraCorp - Pirates - Terran, 4497.323613667418, 0.0024458991491230196
    Arteus - Paranid - Duke's - TerraCorp, 276.50026848816077, 0.03978296317810266
    Arteus - Duke's - TerraCorp - Yaki, 433.6020668910826, 0.02536888276126025
    Arteus - Terran - Duke's - TerraCorp, 326.2400786389411, 0.03371750045516021
    Arteus - Pirates - Duke's - TerraCorp, 192.51007162251946, 0.05713986757830098
    Strong Arms - Pirates - Duke's - Yaki, 295.8863286643155, 0.03717643883600839
    Terran - Duke's - TerraCorp - Yaki, 135.72877842687274, 0.0810439770216198
    Split - Paranid - Pirates - Strong Arms, 586.9460397814119, 0.01874107542168029
    Teladi - Paranid - Pirates - Yaki, 1883.2152224164156, 0.005841074280339311
    Terran - Paranid - Yaki, 116.89992094755894, 0.10265190859609884
    Terran - Pirates - Yaki, 105.3461102176374, 0.11391023337462458
    Paranid - OTAS - Split - Teladi - NMMC, 20438.47148046224, 0.0004892733788610026
    Yaki - OTAS - Split - Strong Arms - Teladi, 1300.9468619844988, 0.0076867090364826545
    Split - OTAS - Terran - TerraCorp, 534.8383418935032, 0.020566962273228937
    OTAS - Pirates - Split - Strong Arms - Teladi - NMMC, 2410.8835450970782, 0.003733071229551073
    Teladi - OTAS - Pirates - Yaki, 1251.8362845922484, 0.008787091519385821
    Terran - OTAS - Yaki, 123.03150825209372, 0.0975359903368151
    Paranid - OTAS - Pirates - Strong Arms - Teladi - TerraCorp, 2431.643270024765, 0.003701200793284263
    Paranid - OTAS - Yaki, 816.7694861889692, 0.014692027803330131
    Terran - Paranid - Teladi - OTAS, 1532.0053547939397, 0.007180131561276129
    OTAS - Pirates - Terran - Teladi - NMMC, 2903.981713088131, 0.0034435478553223645
    Paranid - Pirates - Duke's - Strong Arms - TerraCorp, 332.16947467059333, 0.03010511429419222
    Paranid - Yaki - Duke's - Strong Arms - TerraCorp, 442.5554569653942, 0.022596038174673223
    Paranid - Duke's - Terran - Teladi - TerraCorp, 5494.503717472112, 0.001820000588624728
    Terran - Pirates - Duke's - TerraCorp, 258.2664091833172, 0.04259167901386747
    Terran - Paranid - Pirates - Teladi, 1753.2504571888478, 0.006274060819375082
    Arteus - OTAS - Duke's - TerraCorp, 252.46111812127492, 0.043571065841180034
    Arteus - OTAS - Yaki, 535.0506351864673, 0.022427783859779837
    OTAS - Arteus - Terran - Teladi - TerraCorp, 194.76232499322876, 0.051344632491667305
    Arteus - OTAS - Pirates - TerraCorp, 1030.788931037815, 0.010671437836381326
    Arteus - Pirates - Teladi - Yaki, 1095.126388947192, 0.010044502726826748
    Strong Arms - Terran - Arteus - Yaki, 173.72079712360858, 0.06331999496970478
    Arteus - Paranid - OTAS, 1324.7692323975446, 0.009058181384755296
    Arteus - Paranid - Yaki, 297.80939829876394, 0.04029422868636784
    Arteus - Paranid - Terran, 3824.2459278403912, 0.003137873511909988
    Arteus - TerraCorp - Pirates - Terran, 219.93982789746184, 0.05001367921924678
    Arteus - Paranid - Pirates, 2026.1585597183964, 0.005922537474889333
    Arteus - Paranid - Duke's - Yaki, 198.6811596211696, 0.05536508857193092
    Paranid - Duke's - Arteus - Terran - Teladi, 372.3225640732917, 0.02685843127689543
    Pirates - Duke's - Arteus - Terran - Teladi, 217.57559798112794, 0.045961036498529485
    Arteus - Pirates - Duke's - Yaki, 139.54348632588722, 0.0788284734001185
    Arteus - Terran - TerraCorp - Yaki, 79.17468394571607, 0.13893329852180838
    Arteus - Paranid - Pirates - Terran, 176.10908572604444, 0.06246128616618689
    Arteus - Paranid - Pirates - Yaki, 132.2864500533513, 0.08315288523929462
    Arteus - Paranid - Terran - Yaki, 69.4479683245564, 0.15839196257826973
    Arteus - Pirates - Terran - Yaki, 77.36791027790339, 0.14217780938490265
    Paranid - OTAS - Duke's - Strong Arms - Teladi - TerraCorp, 850.9999999999989, 0.010575793184488851
    Strong Arms - OTAS - Duke's - Yaki, 1563.3591271938062, 0.007036131243717973
    OTAS - Duke's - Terran - Teladi - TerraCorp, 298.3703435553207, 0.033515395266305696
    OTAS - Pirates - Duke's - Strong Arms - Teladi, 525.8277614121619, 0.01901763416435835
    OTAS - Pirates - Duke's - Yaki, 128.43790211643636, 0.08564450071776994
    Terran - OTAS - Duke's - Yaki, 88.96673057198294, 0.12364172460063491
    Terran - Paranid - Pirates - OTAS, 251.63126135098884, 0.04371475921132314
    Paranid - Pirates - OTAS - Yaki, 213.88102708965891, 0.051430461830486725
    Terran - Paranid - OTAS - Yaki, 74.78909640568672, 0.14708026341609332
    Terran - OTAS - Pirates - Yaki, 76.12798036380734, 0.1444935219275777
    Paranid - Pirates - Duke's - Terran - Teladi, 190.5687959622656, 0.05247448801628622
    Paranid - Pirates - Duke's - Yaki, 225.1484995307863, 0.048856643605994295
    Terran - Paranid - Duke's - Yaki, 109.52808992782926, 0.10043085757496702
    Terran - Pirates - Duke's - Yaki, 60.03207903289179, 0.18323536644421495
    Terran - Paranid - Pirates - Yaki, 62.12076978491299, 0.17707443159649197
    OTAS - Duke's - Split - Strong Arms - Arteus - Teladi, 8523.499999999985, 0.0010559042646800041
    Split - OTAS - Arteus - Yaki, 280.13387621362347, 0.03926693961001582
    Split - OTAS - Terran - Arteus, 3097.5968700028434, 0.0035511399519169524
    Split - OTAS - Pirates - Arteus, 539.528965822449, 0.020388154662339182
    Yaki - Pirates - Split - Arteus - Teladi, 548.9383122356895, 0.018216983178442184
    Split - Terran - Arteus - Yaki, 238.16933583844525, 0.04618562654707786
    Split - Paranid - Arteus - OTAS, 180.27293821386039, 0.06101858719887586
    Split - Paranid - Strong Arms - Yaki, 1238.8161764990912, 0.008879444915779295
    Split - Paranid - Terran - Arteus, 499.9184994481015, 0.022003586608904745
    Pirates - Split - Arteus - Terran - Strong Arms - Teladi - NMMC, 5764.999999999969, 0.001387684301821343
    Paranid - Duke's - Split - Strong Arms - Arteus - Teladi, 6530.99999999994, 0.0013780431786862783
    Paranid - Yaki - Duke's - Split - Strong Arms, 822.6915113871632, 0.012155224481578422
    Paranid - Duke's - Split - Terran - Arteus - Teladi, 249.1218274111674, 0.036126902622409696
    Pirates - Duke's - Split - Strong Arms - Arteus - Teladi, 5398.499999999991, 0.001667129758266188
    Yaki - Pirates - Duke's - Split - Strong Arms, 160.75238905441626, 0.06220747361095145
    Yaki - Duke's - Split - Terran - Arteus, 188.10063278220042, 0.053163032213607096
    Split - Paranid - Pirates - Arteus, 220.4761735208537, 0.04989201247616703
    Split - Paranid - Pirates - Yaki, 201.66728255596405, 0.054545287964335144
    Strong Arms - Paranid - Terran - Yaki, 74.62837403727593, 0.14739702079675002
    Split - Pirates - Terran - Yaki, 86.22664083983406, 0.1275707819864222
    Paranid - OTAS - Duke's - Split - Teladi, 775.9700011203693, 0.012887096132017595
    Yaki - OTAS - Duke's - Split - Strong Arms, 296.3931202688199, 0.03373897474722184
    Split - Paranid - Terran - OTAS, 169.88740515841215, 0.06474876692444038
    Split - OTAS - Pirates - Duke's, 278.9246649694425, 0.03943717204502191
    Split - OTAS - Pirates - Yaki, 202.8673253986203, 0.05422263037374678
    Split - OTAS - Terran - Yaki, 99.48063310991552, 0.11057428623163436
    Split - Paranid - Pirates - OTAS, 168.3588446726157, 0.06533663272274283
    Split - Paranid - OTAS - Yaki, 154.61464552459722, 0.0711446186917011
    Split - Paranid - Terran - Yaki, 93.00721055570571, 0.11827040005045268
    Split - OTAS - Pirates - Terran, 265.91895025699546, 0.041365987604001626
    Paranid - Pirates - Duke's - Split - Strong Arms, 129.21013066030594, 0.07739331234243582
    Paranid - Yaki - Pirates - Duke's - Split, 118.72222908046423, 0.08423022442766366
    Paranid - Yaki - Duke's - Split - Terran, 91.8442105145514, 0.10888002568671046
    Yaki - Pirates - Duke's - Split - Terran, 54.53250365153363, 0.18337687306456116
    Split - Paranid - Pirates - Terran, 195.78797541871438, 0.05618322563719899
    Arteus - Paranid - Duke's - OTAS, 226.8370476710913, 0.04849296053239838
    Arteus - OTAS - Duke's - Yaki, 171.60650628516808, 0.06410013371940973
    OTAS - Duke's - Arteus - Terran - Teladi, 336.97708925269467, 0.029675607983251147
    Arteus - OTAS - Pirates - Duke's, 157.5671335357666, 0.06981151305581808
    Arteus - OTAS - Pirates - Yaki, 191.81497205850326, 0.05734693116992462
    Arteus - OTAS - Terran - Yaki, 88.82853336736402, 0.12383408329514813
    Arteus - Paranid - Pirates - OTAS, 313.87190588793885, 0.03504614396398801
    Arteus - Paranid - OTAS - Yaki, 139.74483694436472, 0.07871489380591087
    Arteus - Paranid - Terran - OTAS, 199.60787014398295, 0.05510804755376319
    Arteus - OTAS - Pirates - Terran, 369.41728926215853, 0.02977662475400225
    Arteus - Paranid - Pirates - Duke's, 165.66374323749335, 0.06639956205885403
    Paranid - Yaki - Pirates - Duke's - Arteus, 70.49353840167753, 0.14185697337278266
    Paranid - Yaki - Duke's - Arteus - Terran, 59.251847441573624, 0.16877110894914601
    Yaki - Pirates - Duke's - Arteus - Terran, 46.54237194014475, 0.2148579795817106
    Paranid - Yaki - Pirates - Arteus - Terran, 54.181067679830655, 0.18456631491820125
    Paranid - Pirates - Duke's - OTAS, 284.80947269537717, 0.03862231089401032
    Paranid - Duke's - OTAS - Yaki, 280.57457834637336, 0.03920526251818988
    Paranid - OTAS - Duke's - Terran - Teladi, 320.24608085140375, 0.031225987132813857
    Terran - OTAS - Pirates - Duke's, 164.70324252474194, 0.06678678471279985
    Paranid - Yaki - OTAS - Pirates - Terran, 59.33896932010084, 0.1685233180585855
    Paranid - Yaki - Pirates - Duke's - Terran, 42.6381087279123, 0.23453197851277285
    OTAS - Duke's - Split - Arteus - TerraCorp, 185.79414709252325, 0.053823008724920275
    Yaki - OTAS - Split - Teladi - TerraCorp, 1553.4160711344357, 0.006437425352949487
    Split - Terran - Arteus - TerraCorp, 3097.59687000284, 0.0035511399519169563
    Split - OTAS - Pirates - TerraCorp, 6266.63399428815, 0.0017553283006517012
    Arteus - Pirates - TerraCorp - Yaki, 244.36002528313054, 0.04501554616903777
    Split - Terran - TerraCorp - Yaki, 163.94865050319805, 0.0670941783676678
    Split - Paranid - Arteus - TerraCorp, 342.9911065180377, 0.03207080239388515
    Arteus - Paranid - TerraCorp - Yaki, 157.50217926192076, 0.06984030349007028
    Split - Paranid - Terran - TerraCorp, 1191.4566043972136, 0.009232396681006408
    Pirates - Split - Arteus - Terran - TerraCorp, 152.5497246665671, 0.06555239625543295
    Paranid - Duke's - Split - Arteus - TerraCorp, 194.83241667794294, 0.05132616106964352
    Yaki - Duke's - Split - Arteus - TerraCorp, 432.94480419364777, 0.023097632546081312
    Duke's - Split - Terran - Arteus - TerraCorp, 320.43828355134804, 0.03120725741372775
    Pirates - Duke's - Split - Arteus - TerraCorp, 160.40827799858226, 0.06234092233125514
    Pirates - Duke's - TerraCorp - Yaki, 1401.767315254792, 0.007847236756266205
    Yaki - Duke's - Split - Terran - TerraCorp, 134.8059045586797, 0.07418072696991619
    Paranid - Pirates - Split - Teladi - TerraCorp - NMMC, 5045.472445275504, 0.0017837774554546324
    Paranid - Pirates - TerraCorp - Yaki, 539.0174920455864, 0.02040750098527358
    Terran - Paranid - TerraCorp - Yaki, 75.40773840612667, 0.1458736229530825
    Terran - Pirates - TerraCorp - Yaki, 74.38219623173842, 0.1478848509088035
    Split - Paranid - TerraCorp - OTAS, 516.0044587449564, 0.021317645252047965
    OTAS - Duke's - TerraCorp - Yaki, 945.3148496279766, 0.011636334713591972
    OTAS - Duke's - Split - Terran - TerraCorp, 221.30580746627942, 0.04518634243940349
    OTAS - Pirates - Duke's - TerraCorp, 444.3049577900574, 0.024757770101673522
    Yaki - OTAS - Pirates - Teladi - TerraCorp, 553.1922518475523, 0.018076898160814772
    Terran - OTAS - TerraCorp - Yaki, 88.7580732328566, 0.12393238833769549
    Paranid - OTAS - Pirates - Split - TerraCorp, 140.61311964219155, 0.07111711926629824
    Paranid - TerraCorp - OTAS - Yaki, 437.0729480473949, 0.025167423536830727
    Terran - Paranid - TerraCorp - OTAS, 288.82423959462847, 0.038085446067264835
    Terran - OTAS - Pirates - TerraCorp, 384.77912262198214, 0.028587829622987913
    Paranid - Pirates - Duke's - Split - TerraCorp, 335.5696488335274, 0.02980007290516579
    Paranid - Yaki - Pirates - Duke's - TerraCorp, 148.8053764915649, 0.06720187291463124
    Paranid - Duke's - Split - Terran - Teladi - TerraCorp, 375.2241379310344, 0.02398566374121215
    Pirates - Duke's - Split - Terran - TerraCorp, 177.53868485308624, 0.05632575237489806
    Terran - Paranid - Pirates - TerraCorp, 255.93690461756006, 0.042979342961254524
    Arteus - Paranid - TerraCorp - OTAS, 307.33477120557416, 0.0357915895973976
    Arteus - OTAS - TerraCorp - Yaki, 225.75422249399557, 0.04872555595407554
    OTAS - Duke's - Arteus - Terran - TerraCorp, 98.77126758911992, 0.10124401806403002
    OTAS - Pirates - Duke's - Arteus - TerraCorp, 95.3407653621142, 0.10488692808389942
    Yaki - OTAS - Pirates - Arteus - TerraCorp, 150.5606075085813, 0.06641843550896966
    Yaki - OTAS - Arteus - Terran - TerraCorp, 67.42090266209917, 0.14832195365461232
    Arteus - Paranid - Pirates - TerraCorp, 305.34651047869477, 0.036024646172491674
    Paranid - Yaki - OTAS - Arteus - TerraCorp, 117.85007053312393, 0.08485357670778242
    Arteus - Paranid - Terran - TerraCorp, 142.9135492389856, 0.07696960895992704
    OTAS - Pirates - Arteus - Terran - TerraCorp, 148.87298922453454, 0.0671713522519368
    Paranid - Pirates - Duke's - Arteus - TerraCorp, 94.19760674430471, 0.10615980963449065
    Paranid - Yaki - Duke's - Arteus - TerraCorp, 101.52941884003158, 0.09849362001919727
    Paranid - Duke's - Arteus - Terran - TerraCorp, 91.3356065391403, 0.10948632607716545
    Pirates - Duke's - Arteus - Terran - TerraCorp, 74.34278592162093, 0.13451204277632167
    Yaki - Pirates - Duke's - Arteus - TerraCorp, 82.14068589520296, 0.12174234839916284
    Paranid - Pirates - Arteus - Terran - TerraCorp, 104.9067683700724, 0.09532273422743981
    Paranid - Yaki - Pirates - Arteus - TerraCorp, 112.56096064662025, 0.08884074853798131
    Paranid - Yaki - Arteus - Terran - TerraCorp, 56.29158422193729, 0.17764644818972633
    Yaki - Pirates - Arteus - Terran - TerraCorp, 61.136289763462635, 0.16356897087949193
    Paranid - OTAS - Pirates - Duke's - TerraCorp, 181.47763444463055, 0.055103208891843
    Paranid - Yaki - OTAS - Duke's - TerraCorp, 186.1929119473876, 0.05370773728929967
    Paranid - OTAS - Duke's - Terran - TerraCorp, 141.81693968671135, 0.07051343811318352
    OTAS - Pirates - Duke's - Terran - TerraCorp, 90.56547516505596, 0.1104173525482526
    Yaki - OTAS - Pirates - Duke's - TerraCorp, 105.9284859618046, 0.09440331285019757
    Yaki - OTAS - Duke's - Terran - TerraCorp, 63.594465671573076, 0.15724638762819312
    Paranid - OTAS - Pirates - Terran - TerraCorp, 158.0877586581771, 0.0632560046703069
    Paranid - Yaki - OTAS - Pirates - TerraCorp, 194.93466242251628, 0.05129923983619309
    Paranid - Yaki - OTAS - Terran - TerraCorp, 65.02676318178604, 0.15378283510812968
    Yaki - OTAS - Pirates - Terran - TerraCorp, 66.4850652730632, 0.15040971921932603
    Paranid - Pirates - Duke's - Terran - TerraCorp, 99.95573941667172, 0.10004428018199513
    Paranid - Yaki - Duke's - Terran - TerraCorp, 63.8223623142606, 0.15668489283991263
    Yaki - Pirates - Duke's - Terran - TerraCorp, 44.467304873772974, 0.22488432857324003
    Paranid - Yaki - Pirates - Terran - TerraCorp, 56.430532887885136, 0.17720903008071476
    Paranid - OTAS - Duke's - Split - Arteus, 120.51393405534138, 0.08297795668514053
    Yaki - OTAS - Duke's - Split - Arteus, 143.1713982557543, 0.06984635284581418
    OTAS - Duke's - Split - Terran - Arteus, 320.43828355134804, 0.03120725741372775
    OTAS - Pirates - Duke's - Split - Arteus, 102.65850618957765, 0.09741034007969274
    Yaki - OTAS - Pirates - Split - Arteus, 115.8106032420725, 0.08634787938283642
    Yaki - OTAS - Split - Terran - Arteus, 75.59987236920867, 0.13227535558741146
    Paranid - OTAS - Pirates - Split - Arteus, 101.42611063841383, 0.0985939413140883
    Split - Paranid - Arteus - Yaki, 204.91736033461723, 0.05368017615509827
    Paranid - OTAS - Split - Terran - Arteus, 98.99184017126501, 0.10101842720267729
    OTAS - Pirates - Split - Arteus - Terran, 152.5497246665671, 0.06555239625543295
    Paranid - Pirates - Duke's - Split - Arteus, 107.3022171782586, 0.0931947192049838
    Paranid - Yaki - Duke's - Split - Arteus, 167.81449841754306, 0.059589606942773043
    Paranid - Yaki - Split - Terran - Arteus, 60.323726797068474, 0.16577225133388088
    Pirates - Duke's - Split - Terran - Arteus - Teladi, 187.36150234741785, 0.0480354816076977
    Yaki - Pirates - Duke's - Split - Arteus, 130.38132747346856, 0.07669809928906354
    Paranid - Pirates - Split - Arteus - Terran, 95.01237920325536, 0.1052494431131704
    Paranid - Yaki - Pirates - Split - Arteus, 86.612845422967, 0.11545631541332915
    Yaki - Pirates - Split - Arteus - Terran, 68.75961783147136, 0.1454341998309215
    Paranid - OTAS - Pirates - Duke's - Split, 86.35233819777861, 0.11580462334553493
    Paranid - Yaki - OTAS - Duke's - Split, 122.14133360357195, 0.08187236625773632
    Paranid - OTAS - Duke's - Split - Terran, 135.3182048680474, 0.07389988663943098
    OTAS - Pirates - Duke's - Split - Terran, 93.50106409788492, 0.10695065448165535
    Yaki - OTAS - Pirates - Duke's - Split, 83.79111791225154, 0.11934439173460232
    Yaki - OTAS - Duke's - Split - Terran, 79.14734597410525, 0.12634662447521253
    Paranid - OTAS - Pirates - Split - Terran, 78.61607734936788, 0.1272004447075151
    Paranid - Yaki - OTAS - Pirates - Split, 82.14772256000184, 0.12173192011130754
    Yaki - OTAS - Pirates - Split - Terran, 57.40764327424609, 0.17419283269003566
    Paranid - Pirates - Duke's - Split - Terran, 114.84646275242879, 0.08707277316460944
    Paranid - Yaki - Pirates - Split - Terran, 44.089133655415154, 0.22681325693891857
    Paranid - OTAS - Pirates - Duke's - Arteus, 92.57571438058937, 0.1080196903357273
    Paranid - Yaki - OTAS - Duke's - Arteus, 87.74009989673124, 0.11397297258345783
    Paranid - OTAS - Duke's - Arteus - Terran, 114.0394134279495, 0.08768898137412848
    OTAS - Pirates - Duke's - Arteus - Terran, 88.7813000313418, 0.11263633216082412
    Yaki - OTAS - Pirates - Duke's - Arteus, 71.57224629759202, 0.13971896254898514
    Yaki - OTAS - Duke's - Arteus - Terran, 63.7401058183402, 0.1568870944221536
    Paranid - OTAS - Pirates - Arteus - Terran, 129.94244978219476, 0.0769571453882982
    Paranid - Yaki - OTAS - Pirates - Arteus, 108.13696029784975, 0.09247531993183689
    Paranid - Yaki - OTAS - Arteus - Terran, 61.69467996475963, 0.1620885302543438
    Yaki - OTAS - Pirates - Arteus - Terran, 67.25886370258512, 0.14867928849079926
    Paranid - Pirates - Duke's - Arteus - Terran, 83.31128105091945, 0.12003176369221893
    Paranid - OTAS - Pirates - Duke's - Terran, 94.05472321792554, 0.10632108264068696
    Paranid - Yaki - OTAS - Pirates - Duke's, 88.86321035066064, 0.1125325087912003
    Paranid - Yaki - OTAS - Duke's - Terran, 59.76814096252372, 0.1673132180281511
    Yaki - OTAS - Pirates - Duke's - Terran, 44.953387479014765, 0.22245264619197433
    OTAS - Split - Arteus - Strong Arms - TerraCorp, 779.6105905154787, 0.012826916567908598
    Yaki - Split - Strong Arms - Arteus - Teladi - TerraCorp, 806.3941018766756, 0.011160795917349602
    Strong Arms - Terran - Arteus - Teladi - TerraCorp, 1410.8633621392455, 0.007087858589535793
    OTAS - Pirates - Split - Strong Arms - TerraCorp, 587.7581838254713, 0.01701379968019194
    Strong Arms - Pirates - Arteus - Yaki, 368.92031379025576, 0.029816737080663683
    Strong Arms - Terran - TerraCorp - Yaki, 127.97972352641226, 0.08595111551190246
    Strong Arms - Paranid - Arteus - TerraCorp, 935.6370033647505, 0.011756696197822072
    Paranid - Yaki - Split - Strong Arms - TerraCorp, 185.5934879320924, 0.053881200851502636
    Paranid - Split - Terran - Strong Arms - TerraCorp, 266.8542621590498, 0.03747363792915485
    Pirates - Split - Terran - Strong Arms - TerraCorp, 699.2233841747376, 0.014301581191828356
    Paranid - Duke's - Strong Arms - Arteus - TerraCorp, 195.69365716011794, 0.05110027655018951
    Yaki - Duke's - Strong Arms - Arteus - TerraCorp, 217.3614480313491, 0.046006318464338454
    Duke's - Strong Arms - Terran - Arteus - TerraCorp, 307.0520063774798, 0.03256777286029625
    Pirates - Duke's - Strong Arms - Arteus - TerraCorp, 143.00612907102507, 0.06992707281121793
    Yaki - Pirates - Duke's - Strong Arms - TerraCorp, 128.21033693047957, 0.07799683114024085
    Yaki - Duke's - Strong Arms - Terran - TerraCorp, 94.34713772289165, 0.1059915567271489
    Paranid - Pirates - Split - Strong Arms - TerraCorp, 195.398508181923, 0.051177463395419794
    Strong Arms - Paranid - Pirates - Yaki, 190.82782290467065, 0.0576435858910109
    Paranid - Yaki - Strong Arms - Terran - TerraCorp, 58.766773338038824, 0.17016418346601914
    Strong Arms - Pirates - Terran - Yaki, 77.85796182794802, 0.14128291753010444
    Split - Paranid - OTAS - Strong Arms, 400.5719587027374, 0.027460733985533545
    Yaki - OTAS - Split - Strong Arms - TerraCorp, 314.1120590843982, 0.031835772332806614
    OTAS - Split - Terran - Strong Arms - TerraCorp, 436.65329430113445, 0.022901464687229818
    OTAS - Pirates - Duke's - Strong Arms - TerraCorp, 234.10857314462106, 0.04271522339261997
    Strong Arms - OTAS - Pirates - Yaki, 366.616082231343, 0.030004139297573836
    Strong Arms - OTAS - Terran - Yaki, 107.68655804917002, 0.10214831079453171
    Paranid - OTAS - Pirates - Split - Strong Arms, 97.37211905808198, 0.10269880225195727
    Strong Arms - Paranid - OTAS - Yaki, 251.40006393601783, 0.04375496102817037
    Strong Arms - Paranid - Terran - OTAS, 5110.34512522506, 0.00215249650081423
    OTAS - Pirates - Strong Arms - Terran - TerraCorp, 367.1760564812699, 0.027234891337502322
    Paranid - Pirates - Duke's - Split - Strong Arms - TerraCorp, 76.16074242689545, 0.11817111694570002
    Paranid - Yaki - Duke's - Split - Strong Arms - TerraCorp, 141.73913043478257, 0.06349693251533745
    Paranid - Duke's - Strong Arms - Terran - Teladi - TerraCorp, 441.81632653061223, 0.020370455910203707
    Pirates - Duke's - Strong Arms - Terran - TerraCorp, 174.05672181085507, 0.05745253556404938
    Strong Arms - Paranid - Pirates - Terran, 1318.4973529314104, 0.00834283055293493
    OTAS - Duke's - Strong Arms - Arteus - TerraCorp, 229.29430741570553, 0.04361207267945916
    Strong Arms - OTAS - Arteus - Yaki, 372.3239802639132, 0.029544162028464847
    OTAS - Strong Arms - Terran - Arteus - TerraCorp, 234.2380407436375, 0.04269161391656503
    OTAS - Pirates - Strong Arms - Arteus - TerraCorp, 918.5660578377282, 0.010886533325147725
    Yaki - OTAS - Pirates - Strong Arms - Arteus, 156.426606574522, 0.06392774361717024
    Yaki - Strong Arms - Terran - Arteus - TerraCorp, 73.69254734624205, 0.13569893239020933
    Strong Arms - Paranid - Arteus - OTAS, 940.7864696527125, 0.01169234502709271
    Strong Arms - Paranid - Arteus - Yaki, 168.66557091294405, 0.06521781499602904
    Strong Arms - Paranid - Terran - Arteus, 1565.5825820308105, 0.007026138465165628
    Pirates - Strong Arms - Arteus - Terran - TerraCorp, 216.27015342004267, 0.04623846537241721
    Strong Arms - Paranid - Pirates - Arteus, 783.1182257851985, 0.014046410411366405
    Paranid - Yaki - Duke's - Strong Arms - Arteus, 108.41280950835349, 0.09224002260756349
    Paranid - Duke's - Strong Arms - Terran - Arteus - Teladi, 267.3687150837988, 0.033661380304644904
    Pirates - Duke's - Strong Arms - Terran - Arteus, 250.00232246598756, 0.03999962840889402
    Yaki - Pirates - Duke's - Strong Arms - Arteus, 80.23315632260204, 0.12463675191577818
    Yaki - Duke's - Arteus - Terran - TerraCorp, 58.90658098953417, 0.16976031933981506
    Paranid - Pirates - Strong Arms - Arteus - Terran, 161.97218363542527, 0.06173899601494833
    Paranid - Yaki - Pirates - Strong Arms - Arteus, 97.45844948984427, 0.10260782982230861
    Paranid - Yaki - Strong Arms - Terran - Arteus, 58.7288143717182, 0.1702741679187663
    Yaki - Pirates - Strong Arms - Arteus - Terran, 67.18353795380125, 0.148845986748666
    Paranid - OTAS - Pirates - Duke's - Strong Arms, 152.06843038869545, 0.0657598685962592
    Yaki - OTAS - Duke's - Strong Arms - TerraCorp, 258.3540567833822, 0.03870657238560234
    OTAS - Duke's - Strong Arms - Terran - TerraCorp, 381.03799724273136, 0.026244101828064494
    OTAS - Pirates - Duke's - Strong Arms - Terran, 134.05481359625387, 0.07459635153511152
    Yaki - OTAS - Pirates - Duke's - Strong Arms, 75.63345872704424, 0.13221661640636173
    Yaki - OTAS - Duke's - Strong Arms - Terran, 73.72115160340664, 0.13564628037549406
    Paranid - OTAS - Pirates - Strong Arms - Terran, 219.88473680429075, 0.04547837264803213
    Paranid - Yaki - OTAS - Pirates - Strong Arms, 129.2795181224945, 0.07735177346905667
    Paranid - Yaki - OTAS - Strong Arms - Terran, 62.30516709695474, 0.16050033192975363
    Yaki - OTAS - Pirates - Strong Arms - Terran, 66.24627045065682, 0.15095189407603626
    Paranid - Pirates - Duke's - Strong Arms - Terran, 144.2590199510967, 0.0693197555576765
    Paranid - Yaki - Pirates - Duke's - Strong Arms, 69.2720587711683, 0.14435834847977835
    Paranid - Yaki - Duke's - Strong Arms - Terran, 62.47112514254196, 0.16007395380158027
    Yaki - Pirates - Duke's - Strong Arms - Terran, 37.98045620718212, 0.26329330920751276
    Paranid - Yaki - Pirates - Strong Arms - Terran, 48.94594796925489, 0.20430700425460024
    Paranid - OTAS - Split - Arteus - Strong Arms, 134.2882225748207, 0.07446669416171883
    Yaki - OTAS - Split - Strong Arms - Arteus, 201.30237497095104, 0.049676512765649446
    OTAS - Split - Terran - Arteus - Strong Arms, 2538.252082251008, 0.003939719017636602
    OTAS - Pirates - Split - Arteus - Strong Arms, 391.4940633245381, 0.02554317149813398
    Yaki - Pirates - Split - Strong Arms - Arteus, 202.2798589280888, 0.04943645923519768
    Yaki - Split - Strong Arms - Terran - Arteus, 171.86745755778276, 0.05818437150405827
    Paranid - Pirates - Split - Arteus - Strong Arms, 127.36134112305983, 0.07851676114448057
    Paranid - Yaki - Split - Strong Arms - Arteus, 101.35497875088687, 0.0986631354792968
    Paranid - Split - Terran - Arteus - Strong Arms, 298.89134048726515, 0.03345697464402141
    OTAS - Pirates - Split - Terran - Strong Arms, 219.88473680429067, 0.045478372648032145
    Paranid - Pirates - Duke's - Strong Arms - Arteus, 113.89533381605449, 0.08779990948663796
    Paranid - Yaki - Duke's - Split - Strong Arms - Arteus, 81.44501278772377, 0.11050400376825249
    Paranid - Duke's - Split - Strong Arms - Arteus - Terran, 227.81224265715062, 0.0395062174667438
    Pirates - Duke's - Split - Strong Arms - Arteus - Terran, 186.39857260499585, 0.04828363154406893
    Yaki - Pirates - Duke's - Split - Strong Arms - Arteus, 67.32736572890025, 0.1336752136752137
    Yaki - Duke's - Split - Strong Arms - Arteus - Terran, 131.73913043478257, 0.06831683168316834
    Paranid - Pirates - Split - Terran - Strong Arms, 100.33149545068373, 0.09966959981091214
    Paranid - Yaki - Pirates - Split - Strong Arms, 61.73709585366364, 0.16197716885975896
    Paranid - Yaki - Split - Terran - Strong Arms, 49.502093829117484, 0.20201165701233287
    Yaki - Pirates - Split - Strong Arms - Terran, 59.87694644757991, 0.16700918455744293
    Paranid - OTAS - Duke's - Split - Strong Arms, 211.98602446253838, 0.047172921070403745
    Paranid - Yaki - OTAS - Split - Strong Arms, 78.17894702085069, 0.1279116741919401
    Paranid - OTAS - Split - Terran - Strong Arms, 120.7170750590789, 0.08283832254141349
    OTAS - Pirates - Duke's - Split - Strong Arms, 140.57162019964403, 0.0711381144060067
    Yaki - OTAS - Pirates - Split - Strong Arms, 119.3116934859714, 0.08381408148544797
    Yaki - OTAS - Split - Terran - Strong Arms, 84.49344392246415, 0.11835237783864688
    Paranid - OTAS - Pirates - Split - Strong Arms - Terran, 60.89292645010782, 0.1478004182862534
    Paranid - Yaki - OTAS - Pirates - Split - Strong Arms, 49.718852795739295, 0.1810178532673478
    Paranid - Yaki - OTAS - Split - Terran, 52.48877107936717, 0.19051693903976546
    Yaki - OTAS - Pirates - Split - Strong Arms - Terran, 50.43385040767113, 0.17845157423536862
    Paranid - Pirates - Duke's - Split - Strong Arms - Terran, 55.805044179732256, 0.16127574365882674
    Paranid - Yaki - Pirates - Duke's - Split - Strong Arms, 35.69174217414718, 0.2521591676889066
    Paranid - Yaki - Duke's - Split - Strong Arms - Terran, 45.60579710144927, 0.1973433329096225
    Yaki - Pirates - Duke's - Split - Strong Arms - Terran, 31.96213512961829, 0.28158319096961665
    Paranid - Yaki - Pirates - Split - Strong Arms - Terran, 28.834029464141164, 0.31213119245760157
    Paranid - OTAS - Duke's - Strong Arms - Arteus, 185.94821639968671, 0.05377841311747504
    Yaki - OTAS - Duke's - Strong Arms - Arteus, 128.3524016896297, 0.07791050162178582
    OTAS - Duke's - Strong Arms - Terran - Arteus - Teladi, 320.77653631284903, 0.028056914958463238
    OTAS - Pirates - Duke's - Strong Arms - Arteus, 132.23591488667455, 0.07562242079672489
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus, 55.03489346698082, 0.16353261418412143
    Yaki - OTAS - Strong Arms - Terran - Arteus, 82.31915841655547, 0.12147840420570757
    Paranid - OTAS - Pirates - Strong Arms - Arteus, 274.10873978770263, 0.0364818721495163
    Paranid - Yaki - OTAS - Strong Arms - Arteus, 112.83858093123297, 0.08862217086985774
    Paranid - OTAS - Strong Arms - Terran - Arteus, 193.65958448001592, 0.05163700018695392
    OTAS - Pirates - Strong Arms - Arteus - Terran, 367.17605648126994, 0.027234891337502315
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Terran, 70.09483457664747, 0.1283974782786406
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus, 47.347185140806445, 0.19008521780618587
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Terran, 46.49012645071886, 0.1935894928042476
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran, 35.8779479155024, 0.2508504672897196
    Paranid - Yaki - Pirates - Strong Arms - Arteus - Terran, 47.1932797702725, 0.19070511826705436
    Paranid - OTAS - Duke's - Strong Arms - Terran - Teladi, 226.64643057897686, 0.03970942748583845
    Paranid - Yaki - OTAS - Duke's - Strong Arms, 122.14133360357195, 0.08187236625773632
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Terran, 46.24383186776549, 0.19462055016841062
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran, 34.972961280553754, 0.2573416625432954
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Terran, 50.433850407671116, 0.17845157423536867
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Terran, 28.762185361001748, 0.31291085454872897
    Paranid - OTAS - Split - Arteus - TerraCorp, 120.70747702071208, 0.08284490941919125
    Yaki - OTAS - Split - Arteus - TerraCorp, 158.18175009046425, 0.06321841801776117
    OTAS - Split - Terran - Arteus - TerraCorp, 153.2518546765796, 0.06525206511271169
    OTAS - Pirates - Split - Arteus - TerraCorp, 217.54942144914222, 0.045966566738665206
    Yaki - Pirates - Split - Arteus - TerraCorp, 178.2988529921536, 0.056085610379333566
    Yaki - Split - Terran - Arteus - TerraCorp, 75.5998723692087, 0.1322753555874114
    Paranid - Pirates - Split - Arteus - TerraCorp, 129.10209634697577, 0.07745807607278447
    Paranid - Yaki - Split - Arteus - TerraCorp, 115.94875200264238, 0.08624499899552268
    Paranid - Split - Terran - Arteus - TerraCorp, 98.99184017126503, 0.10101842720267727
    OTAS - Pirates - Split - Terran - TerraCorp, 138.18461702366722, 0.07236695527612365
    Paranid - Pirates - Duke's - Split - Arteus - TerraCorp, 70.82881651115547, 0.12706692619355725
    Paranid - Yaki - Duke's - Split - Arteus - TerraCorp, 89.41565427304452, 0.10065351613395467
    Paranid - Duke's - Split - Terran - Arteus - TerraCorp, 77.41542704028151, 0.11625589813406359
    Pirates - Duke's - Split - Terran - Arteus - TerraCorp, 66.62204495536056, 0.1350904194854775
    Yaki - Pirates - Duke's - Split - TerraCorp, 515.4778691735205, 0.01939947492999703
    Yaki - Duke's - Split - Terran - Arteus - TerraCorp, 58.82986021782008, 0.15298353534543707
    Paranid - Pirates - Split - Terran - TerraCorp, 97.6455313474668, 0.10241124055555081
    Paranid - Yaki - Pirates - Split - TerraCorp, 151.28364940524432, 0.06610099663323792
    Paranid - Yaki - Split - Terran - TerraCorp, 60.176816613849596, 0.1661769525657912
    Yaki - Pirates - Split - Terran - TerraCorp, 62.803024271017236, 0.15922800081802538
    Paranid - OTAS - Duke's - Split - TerraCorp, 252.73734807510152, 0.03956676793581167
    Yaki - OTAS - Duke's - Split - TerraCorp, 331.64374798637743, 0.030152837376601953
    Paranid - OTAS - Split - Terran - TerraCorp, 101.6046619565746, 0.09842068077815128
    OTAS - Pirates - Duke's - Split - TerraCorp, 150.47710911701154, 0.06645529050019139
    Yaki - OTAS - Pirates - Split - TerraCorp, 169.1143093970459, 0.059131601788480474
    Yaki - OTAS - Split - Terran - TerraCorp, 75.1520121271029, 0.13306363618165307
    Paranid - OTAS - Pirates - Split - Terran - TerraCorp, 66.78558432548611, 0.13475962052136303
    Paranid - Yaki - OTAS - Split - TerraCorp, 129.21132620571163, 0.07739259625026558
    Paranid - Yaki - OTAS - Split - Terran - TerraCorp, 47.08831978322415, 0.19113020047078366
    Yaki - OTAS - Pirates - Split - Terran - TerraCorp, 54.18572043801999, 0.16609542010786024
    Paranid - Pirates - Duke's - Split - Terran - TerraCorp, 63.12998161769481, 0.14256300682142722
    Paranid - Yaki - Pirates - Duke's - Split - TerraCorp, 91.31359851988897, 0.09856144260966469
    Paranid - Yaki - Duke's - Split - Terran - TerraCorp, 55.14287213665346, 0.1632123908543694
    Yaki - Pirates - Duke's - Split - Terran - TerraCorp, 39.86119616248214, 0.22578349037279805
    Paranid - Yaki - Pirates - Split - Terran - TerraCorp, 41.07626655455118, 0.2191046254909166
    Paranid - OTAS - Duke's - Arteus - TerraCorp, 117.18709555686108, 0.0853336278408559
    Yaki - OTAS - Duke's - Arteus - TerraCorp, 99.75496497994335, 0.10024563691652431
    Paranid - OTAS - Arteus - Terran - TerraCorp, 114.41576379186537, 0.08740054402111129
    OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp, 59.06409886885717, 0.15237682741902367
    Yaki - OTAS - Pirates - Duke's - Arteus - TerraCorp, 61.458697037714416, 0.1464398113496794
    Yaki - OTAS - Duke's - Arteus - Terran - TerraCorp, 47.11365092741334, 0.19102743733161423
    Paranid - OTAS - Pirates - Arteus - TerraCorp, 207.38418901104905, 0.048219683707262845
    Paranid - Yaki - OTAS - Pirates - Arteus - TerraCorp, 100.41865655351937, 0.08962477998501542
    Paranid - Yaki - OTAS - Arteus - Terran - TerraCorp, 54.80919721794633, 0.16420601754504635
    Yaki - OTAS - Pirates - Arteus - Terran - TerraCorp, 59.064098868857165, 0.15237682741902367
    Paranid - Pirates - Duke's - Arteus - Terran - TerraCorp, 55.47059519933702, 0.16224812385116733
    Paranid - Yaki - Pirates - Duke's - Arteus - TerraCorp, 60.0793793974382, 0.1498018137048826
    Paranid - Yaki - Duke's - Arteus - Terran - TerraCorp, 44.098355763779054, 0.20408924197106473
    Yaki - Pirates - Duke's - Arteus - Terran - TerraCorp, 37.627160723706666, 0.2391889216963859
    Paranid - Yaki - Pirates - Arteus - Terran - TerraCorp, 50.29888983774551, 0.17893039049235995
    Paranid - OTAS - Pirates - Duke's - Terran - TerraCorp, 70.41510688777956, 0.127813482046449
    Paranid - Yaki - OTAS - Pirates - Duke's - TerraCorp, 82.3009281875916, 0.10935478126669437
    Paranid - Yaki - OTAS - Duke's - Terran - TerraCorp, 49.98494693795628, 0.18005420734308736
    Yaki - OTAS - Pirates - Duke's - Terran - TerraCorp, 39.98259544934841, 0.22509794321385587
    Paranid - Yaki - OTAS - Pirates - Terran - TerraCorp, 55.896972700830844, 0.1610105085327139
    Paranid - Yaki - Pirates - Duke's - Terran - TerraCorp, 37.971495580010824, 0.2370198977555636
    Paranid - OTAS - Pirates - Duke's - Split - Arteus, 59.08061628125534, 0.15233422679877248
    Paranid - Yaki - OTAS - Split - Arteus, 86.71700852432173, 0.11531763111034067
    Paranid - OTAS - Duke's - Split - Arteus - Terran, 77.41542704028151, 0.11625589813406359
    OTAS - Pirates - Duke's - Split - Arteus - Terran, 66.62204495536056, 0.1350904194854775
    Yaki - OTAS - Pirates - Duke's - Split - Arteus, 58.5386863141761, 0.15374448192597215
    Yaki - OTAS - Duke's - Split - Arteus - Terran, 58.82986021782008, 0.15298353534543707
    Paranid - OTAS - Pirates - Split - Arteus - Terran, 67.4192498882335, 0.1334930307726658
    Paranid - Yaki - OTAS - Pirates - Split - Arteus, 65.32235711153476, 0.13777824925443116
    Paranid - Yaki - OTAS - Split - Arteus - Terran, 47.993321215364716, 0.18752609263304568
    Yaki - OTAS - Pirates - Split - Arteus - Terran, 53.48330973042933, 0.16827679598294287
    Paranid - Pirates - Duke's - Split - Arteus - Terran, 62.48342532918067, 0.14403819817152164
    Paranid - Yaki - Pirates - Duke's - Split - Arteus, 57.84755624971629, 0.15558133451910752
    Paranid - Yaki - Duke's - Split - Arteus - Terran, 54.97070938215102, 0.1637235557109674
    Yaki - Pirates - Duke's - Split - Arteus - Terran, 44.74586967791376, 0.20113588281517603
    Paranid - Yaki - Pirates - Split - Arteus - Terran, 42.50955811203096, 0.21171709139580164
    Paranid - OTAS - Pirates - Duke's - Split - Terran, 51.72536383433497, 0.17399587615903547
    Paranid - Yaki - OTAS - Pirates - Duke's - Split, 53.760826687248084, 0.1674081399893126
    Paranid - Yaki - OTAS - Duke's - Split - Terran, 46.24383186776549, 0.19462055016841062
    Yaki - OTAS - Pirates - Duke's - Split - Terran, 36.7391304347826, 0.24497041420118348
    Paranid - Yaki - OTAS - Pirates - Split - Terran, 40.19240592515181, 0.2239228976926692
    Paranid - Yaki - Pirates - Duke's - Split - Terran, 34.00572887893016, 0.26466128786836185
    Paranid - OTAS - Pirates - Duke's - Arteus - Terran, 63.801885757411526, 0.1410616613154654
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus, 57.26886016451234, 0.15715346829230256
    Paranid - Yaki - OTAS - Duke's - Arteus - Terran, 47.94981440882155, 0.1876962426437302
    Yaki - OTAS - Pirates - Duke's - Arteus - Terran, 40.66691907289646, 0.22131010180208824
    Paranid - Yaki - OTAS - Pirates - Arteus - Terran, 54.00815505114316, 0.16664150055630353
    Paranid - Yaki - Pirates - Duke's - Arteus - Terran, 37.24034682802071, 0.24167336683417084
    Paranid - Yaki - OTAS - Pirates - Duke's - Terran, 39.464999678976454, 0.22805017289267643
    OTAS - Split - Arteus - TerraCorp - NMMC, 809.7825445111578, 0.012348994267389043
    Yaki - Strong Arms - Arteus - TerraCorp - NMMC, 940.0170324271209, 0.010638105114095681
    Arteus - Terran - TerraCorp - NMMC, 20114.06683905385, 0.0005468809509294358
    Pirates - Split - Arteus - Strong Arms - TerraCorp - NMMC, 2417.2625928984235, 0.0037232198216448353
    Yaki - Pirates - Split - Strong Arms - TerraCorp - NMMC, 309.3882914322339, 0.029089659334995525
    Terran - TerraCorp - Yaki - NMMC, 162.2928274940361, 0.06777871930541247
    Arteus - Paranid - TerraCorp - NMMC, 1452.9740385266407, 0.007570678971769055
    Paranid - Yaki - Strong Arms - TerraCorp - NMMC, 3613.9731154454453, 0.002767037739506658
    Paranid - Split - Terran - TerraCorp - NMMC, 1183.3040620672941, 0.008450913269518806
    Pirates - Split - Terran - TerraCorp - NMMC, 2252.731245663543, 0.004439055932326492
    Paranid - Duke's - Arteus - TerraCorp - NMMC, 277.09037901092586, 0.036089307884651214
    Yaki - Duke's - Arteus - TerraCorp - NMMC, 432.86293645629996, 0.02310200102107739
    Duke's - Arteus - Terran - TerraCorp - NMMC, 326.54872220773575, 0.03062330157776102
    Pirates - Duke's - Arteus - TerraCorp - NMMC, 192.85762346711152, 0.05185172263467886
    Yaki - Pirates - Duke's - Strong Arms - NMMC, 295.14719822953293, 0.033881399044225734
    Yaki - Duke's - Terran - TerraCorp - NMMC, 134.98964799209014, 0.07407975462374686
    Paranid - Pirates - Split - Strong Arms - NMMC, 502.4910304148585, 0.019900852741080693
    Paranid - Pirates - Yaki - NMMC, 1181.7489104741023, 0.00930823790274276
    Terran - Paranid - Yaki - NMMC, 113.122578202054, 0.0972396507826434
    Terran - Pirates - Yaki - NMMC, 94.69338877294456, 0.11616439270513126
    Paranid - OTAS - Split - Strong Arms - NMMC, 378.4588158447106, 0.02642295431189851
    Yaki - OTAS - Split - Strong Arms - NMMC, 989.942895898562, 0.010101592770079017
    OTAS - Split - Terran - TerraCorp - NMMC, 492.01570435099114, 0.02032455450419172
    OTAS - Pirates - Split - TerraCorp - NMMC, 1956.3940752452963, 0.005111444635072401
    OTAS - Pirates - Yaki - NMMC, 738.6073155403925, 0.014892893379957917
    Terran - OTAS - Yaki - NMMC, 114.29716386509662, 0.09624035827330894
    Paranid - OTAS - Pirates - Strong Arms - TerraCorp - NMMC, 2417.262592898423, 0.0037232198216448358
    Paranid - OTAS - Yaki - NMMC, 679.8765824885459, 0.0161794070914118
    Paranid - OTAS - Strong Arms - Terran - NMMC, 3320.0944660963883, 0.003011962491464146
    OTAS - Pirates - Terran - TerraCorp - NMMC, 319.13417947690374, 0.031334782179681
    Paranid - Pirates - Duke's - Strong Arms - TerraCorp - NMMC, 332.23959684292424, 0.02708888430374242
    Paranid - Yaki - Duke's - Strong Arms - TerraCorp - NMMC, 441.81632653061166, 0.02037045591020373
    Paranid - Duke's - Strong Arms - Terran - TerraCorp - NMMC, 1337.316479183578, 0.006729895383846937
    Pirates - Duke's - Terran - TerraCorp - NMMC, 258.34145092665153, 0.038708461085632
    Paranid - Pirates - Strong Arms - Terran - NMMC, 995.2769537808152, 0.010047454592425184
    OTAS - Duke's - Arteus - TerraCorp - NMMC, 253.10185895723603, 0.03950978487949231
    Arteus - OTAS - Yaki - NMMC, 436.0411596359644, 0.025226976300089462
    OTAS - Arteus - Terran - TerraCorp - NMMC, 209.09184825327907, 0.047825872139628835
    OTAS - Pirates - Arteus - TerraCorp - NMMC, 636.1987504417658, 0.01571835844232037
    Arteus - Pirates - Yaki - NMMC, 703.201153874598, 0.01564275021363465
    Yaki - Strong Arms - Terran - Arteus - NMMC, 163.46641587807395, 0.06117464524002767
    Arteus - Paranid - OTAS - NMMC, 1015.0807385608553, 0.010836576424054112
    Arteus - Paranid - Yaki - NMMC, 276.1368700272337, 0.03983531789476406
    Arteus - Paranid - Terran - NMMC, 3361.998979687546, 0.0032718629798698827
    Pirates - Arteus - Terran - TerraCorp - NMMC, 191.0184898899485, 0.052350953071408426
    Arteus - Paranid - Pirates - NMMC, 1254.6272662791762, 0.008767544190732031
    Paranid - Yaki - Duke's - Arteus - NMMC, 197.942029186387, 0.05051984179966024
    Paranid - Duke's - Arteus - Terran - NMMC, 695.3884446060831, 0.014380451785713384
    Pirates - Duke's - Arteus - Terran - NMMC, 336.576770890106, 0.029710903618078415
    Yaki - Pirates - Duke's - Arteus - NMMC, 138.8043558911046, 0.07204384859395367
    Yaki - Arteus - Terran - TerraCorp - NMMC, 72.89843849626402, 0.13717714955598798
    Paranid - Pirates - Arteus - Terran - NMMC, 160.7037601357411, 0.062226297577314515
    Paranid - Yaki - Pirates - Arteus - NMMC, 117.3736912921891, 0.08519796804469651
    Paranid - Yaki - Arteus - Terran - NMMC, 65.15904869364687, 0.15347062611389872
    Yaki - Pirates - Arteus - Terran - NMMC, 69.23826511341969, 0.14442880657998766
    Paranid - OTAS - Duke's - Strong Arms - TerraCorp - NMMC, 2241.9075144508593, 0.004014438571612751
    Yaki - OTAS - Duke's - Strong Arms - NMMC, 1562.6199967590237, 0.006399508531018837
    OTAS - Duke's - Terran - TerraCorp - NMMC, 451.0509480968327, 0.022170444474607722
    OTAS - Pirates - Duke's - Strong Arms - NMMC, 1077.6646711136962, 0.00927932432791515
    Yaki - OTAS - Pirates - Duke's - NMMC, 127.69877168165374, 0.07830928887029133
    Yaki - OTAS - Duke's - Terran - NMMC, 88.22760013720033, 0.11334321668558675
    Paranid - OTAS - Pirates - Terran - NMMC, 224.86173638086998, 0.04447177256988729
    Paranid - Yaki - OTAS - Pirates - NMMC, 184.40878821572204, 0.05422735053332689
    Paranid - Yaki - OTAS - Terran - NMMC, 69.7145691819487, 0.14344203969619188
    Yaki - OTAS - Pirates - Terran - NMMC, 67.89661240999102, 0.14728275307191166
    Paranid - Pirates - Duke's - Terran - NMMC, 285.8080888970434, 0.03498851288146117
    Paranid - Yaki - Pirates - Duke's - NMMC, 224.4093690960037, 0.04456141933950155
    Paranid - Yaki - Duke's - Terran - NMMC, 108.78895949304663, 0.09192109242150773
    Yaki - Pirates - Duke's - Terran - NMMC, 59.29294859810918, 0.16865411885282586
    Paranid - Yaki - Pirates - Terran - NMMC, 56.270359320854006, 0.17771345555090426
    Paranid - OTAS - Split - Arteus - NMMC, 170.42278601951247, 0.058677599595485165
    Yaki - OTAS - Split - Arteus - NMMC, 249.22859149842884, 0.04012380738452731
    OTAS - Split - Terran - Arteus - NMMC, 2252.4134045882706, 0.004439682333460428
    OTAS - Pirates - Split - Arteus - NMMC, 423.9572212468571, 0.02358728545910841
    Yaki - Pirates - Split - Arteus - NMMC, 426.85700961400454, 0.023427048812066444
    Yaki - Split - Terran - Arteus - NMMC, 227.3932772399076, 0.04397667389898102
    Paranid - Pirates - Split - Arteus - NMMC, 202.38820419197793, 0.04940999422335094
    Paranid - Yaki - Split - Strong Arms - NMMC, 1170.5333268964614, 0.008543114296893951
    Paranid - Split - Terran - Arteus - NMMC, 494.3282686440881, 0.020229472264310076
    OTAS - Pirates - Split - Terran - NMMC, 236.6213902309284, 0.04226160614744337
    Paranid - Pirates - Duke's - Split - Strong Arms - NMMC, 129.33678198003548, 0.06958577337566081
    Paranid - Yaki - Duke's - Split - Strong Arms - NMMC, 821.9523809523807, 0.010949539424135337
    Paranid - Duke's - Split - Terran - Arteus - NMMC, 377.2895662368111, 0.02385435698571909
    Pirates - Duke's - Split - Terran - Arteus - NMMC, 276.2324101107341, 0.03258126009323867
    Yaki - Pirates - Duke's - Split - Strong Arms - NMMC, 160.01325861963363, 0.05624533915276256
    Yaki - Duke's - Split - Terran - Arteus - NMMC, 187.3615023474178, 0.048035481607697716
    Paranid - Pirates - Split - Terran - NMMC, 186.38955173147238, 0.05365107597021745
    Paranid - Yaki - Pirates - Split - NMMC, 184.78323182848453, 0.054117464561297325
    Paranid - Yaki - Split - Terran - Strong Arms - NMMC, 46.76748410535876, 0.1924413975257812
    Yaki - Pirates - Split - Terran - NMMC, 78.4811892945176, 0.1274190680581157
    Paranid - OTAS - Duke's - Split - NMMC, 1527.8716152889212, 0.006545052542329609
    Yaki - OTAS - Duke's - Split - Strong Arms - NMMC, 295.6539898340373, 0.0304409894994215
    Paranid - OTAS - Split - Terran - NMMC, 165.33512904453286, 0.06048321405009161
    OTAS - Pirates - Duke's - Split - NMMC, 279.33969326475244, 0.03579870759907438
    Yaki - OTAS - Pirates - Split - NMMC, 175.0970282737627, 0.0571111919978738
    Yaki - OTAS - Split - Terran - NMMC, 93.4990897337801, 0.10695291289437142
    Paranid - OTAS - Pirates - Split - NMMC, 154.18306528192625, 0.06485796596218163
    Paranid - Yaki - OTAS - Split - NMMC, 146.42614045328634, 0.0682938167259162
    Paranid - Yaki - OTAS - Split - Terran - NMMC, 49.39533269451418, 0.18220344937568433
    Yaki - OTAS - Pirates - Split - Terran - NMMC, 51.367865495227846, 0.17520681292151635
    Paranid - Pirates - Duke's - Split - Terran - NMMC, 114.9379198870862, 0.0783031397196113
    Paranid - Yaki - Pirates - Duke's - Split - NMMC, 117.98309864568162, 0.07628211246619446
    Paranid - Yaki - Duke's - Split - Terran - NMMC, 91.1050800797688, 0.09878702693768424
    Yaki - Pirates - Duke's - Split - Terran - NMMC, 53.79337321675102, 0.16730685327607303
    Paranid - Yaki - Pirates - Split - Terran - NMMC, 40.26659844414755, 0.22351031246117298
    Paranid - OTAS - Duke's - Arteus - NMMC, 227.3598863238295, 0.043983132476398956
    Yaki - OTAS - Duke's - Arteus - NMMC, 170.86737585038546, 0.058524922913056145
    OTAS - Duke's - Arteus - Terran - NMMC, 558.3085635700331, 0.017911242371165276
    OTAS - Pirates - Duke's - Arteus - NMMC, 157.83021329744074, 0.06335922502464332
    Yaki - OTAS - Pirates - Arteus - NMMC, 161.05830975112585, 0.062089314208328805
    Yaki - OTAS - Arteus - Terran - NMMC, 81.67054829937206, 0.1224431598444024
    Paranid - OTAS - Pirates - Arteus - NMMC, 265.48039651163947, 0.037667564654106464
    Paranid - Yaki - OTAS - Arteus - NMMC, 126.65746937209136, 0.07895310122312829
    Paranid - OTAS - Arteus - Terran - NMMC, 186.07296333804246, 0.0537423590219972
    OTAS - Pirates - Arteus - Terran - NMMC, 306.3454921743059, 0.032642882808636704
    Paranid - Pirates - Duke's - Arteus - NMMC, 165.91556860906564, 0.06027161937745726
    Paranid - Yaki - Pirates - Duke's - Arteus - NMMC, 69.75440796689492, 0.12902410417233207
    Paranid - Yaki - Duke's - Arteus - Terran - NMMC, 58.512717006791014, 0.1538127173099047
    Yaki - Pirates - Duke's - Arteus - Terran - NMMC, 45.80324150536214, 0.1964926434070475
    Paranid - Yaki - Pirates - Arteus - Terran - NMMC, 48.72325031210555, 0.18471674082391631
    Paranid - OTAS - Pirates - Duke's - NMMC, 285.25578842798984, 0.03505625619416451
    Paranid - Yaki - OTAS - Duke's - NMMC, 279.83544791159073, 0.03573528684314266
    Paranid - OTAS - Duke's - Terran - NMMC, 530.2681281480275, 0.01885838403097167
    OTAS - Pirates - Duke's - Terran - NMMC, 165.0233699056201, 0.06059747783431634
    Paranid - Yaki - OTAS - Pirates - Terran - NMMC, 53.43511485255331, 0.16842857032934683
    Paranid - Yaki - Pirates - Duke's - Terran - NMMC, 41.89897829312969, 0.21480237386780765
    OTAS - Duke's - Split - Arteus - TerraCorp - NMMC, 186.19915287922248, 0.04833534342574492
    Yaki - OTAS - Split - TerraCorp - NMMC, 1156.9613975019288, 0.008643330729609178
    Split - Terran - Arteus - TerraCorp - NMMC, 2252.4134045882693, 0.004439682333460431
    OTAS - Pirates - Split - Arteus - TerraCorp - NMMC, 186.19915287922248, 0.04833534342574492
    Yaki - Pirates - Arteus - TerraCorp - NMMC, 202.02486186711326, 0.04949885824734652
    Yaki - Split - Terran - TerraCorp - NMMC, 156.52525708956225, 0.0638874529640804
    Paranid - Split - Arteus - TerraCorp - NMMC, 322.324864678274, 0.031024600010245627
    Paranid - Yaki - Arteus - TerraCorp - NMMC, 143.67775964414605, 0.06960019438476424
    Paranid - Arteus - Terran - TerraCorp - NMMC, 133.66330599726624, 0.07481484858832181
    Pirates - Split - Arteus - Terran - TerraCorp - NMMC, 136.74202527390287, 0.06581736654823149
    Paranid - Duke's - Split - Arteus - TerraCorp - NMMC, 195.1786138096009, 0.046111609383493256
    Yaki - Duke's - Split - Arteus - TerraCorp - NMMC, 432.20567375886515, 0.020823419372836025
    Duke's - Split - Terran - Arteus - TerraCorp - NMMC, 320.7726725176389, 0.02805725291173331
    Pirates - Duke's - Split - Arteus - TerraCorp - NMMC, 160.61735874929568, 0.05603379404369309
    Yaki - Pirates - Duke's - TerraCorp - NMMC, 1401.0281848200093, 0.00713761515174993
    Yaki - Duke's - Split - Terran - TerraCorp - NMMC, 134.06677412389712, 0.06713072689943816
    Paranid - Pirates - Arteus - TerraCorp - NMMC, 259.52515279683774, 0.03853191065387111
    Paranid - Yaki - Pirates - TerraCorp - NMMC, 434.0482967802143, 0.023038910817483573
    Paranid - Yaki - Terran - TerraCorp - NMMC, 70.87547591382938, 0.14109252701397068
    Yaki - Pirates - Terran - TerraCorp - NMMC, 66.44024600327378, 0.15051118262727772
    Paranid - OTAS - Split - TerraCorp - NMMC, 480.6296654249812, 0.02080603990841436
    Yaki - OTAS - Duke's - TerraCorp - NMMC, 944.5757191931941, 0.010586763767907842
    OTAS - Duke's - Split - Terran - TerraCorp - NMMC, 221.8739940482392, 0.04056356419149892
    OTAS - Pirates - Duke's - TerraCorp - NMMC, 444.56742438209193, 0.022493775862905577
    Yaki - OTAS - Pirates - TerraCorp - NMMC, 403.74445282130574, 0.02476814215061408
    Yaki - OTAS - Terran - TerraCorp - NMMC, 81.58227722697544, 0.12257564191519613
    Paranid - OTAS - Pirates - Split - TerraCorp - NMMC, 128.31902340939024, 0.07013769089627743
    Paranid - Yaki - OTAS - TerraCorp - NMMC, 378.5475602227781, 0.02641675987586586
    Paranid - OTAS - Terran - TerraCorp - NMMC, 267.12519487994524, 0.03743563015272418
    OTAS - Pirates - Split - Terran - TerraCorp - NMMC, 125.0852258887947, 0.0719509433352371
    Paranid - Pirates - Duke's - Split - TerraCorp - NMMC, 335.7940587779749, 0.026802141862643104
    Paranid - Yaki - Pirates - Duke's - TerraCorp - NMMC, 148.0662460567823, 0.06078360355369966
    Paranid - Duke's - Split - Terran - TerraCorp - NMMC, 749.3985702105329, 0.01200963059947069
    Pirates - Duke's - Split - Terran - TerraCorp - NMMC, 177.80266504216007, 0.050617913954585245
    Paranid - Pirates - Terran - TerraCorp - NMMC, 230.82939614990227, 0.04332203855658804
    Paranid - OTAS - Arteus - TerraCorp - NMMC, 268.3838522725825, 0.03726006581738591
    Yaki - OTAS - Arteus - TerraCorp - NMMC, 194.2286402883306, 0.05148571284417732
    OTAS - Duke's - Arteus - Terran - TerraCorp - NMMC, 98.9044234256987, 0.090996941170798
    OTAS - Pirates - Duke's - Arteus - TerraCorp - NMMC, 95.26085202879764, 0.0944774249686458
    Yaki - OTAS - Pirates - Arteus - TerraCorp - NMMC, 127.59706678057807, 0.07053453678113795
    Yaki - OTAS - Arteus - Terran - TerraCorp - NMMC, 61.137997014180485, 0.1472079629614382
    Paranid - OTAS - Pirates - Arteus - TerraCorp - NMMC, 178.40479440623452, 0.050447074754654056
    Paranid - Yaki - OTAS - Arteus - TerraCorp - NMMC, 105.84723854289071, 0.08502819841023136
    Paranid - OTAS - Arteus - Terran - TerraCorp - NMMC, 105.30896603908202, 0.08546280851964629
    OTAS - Pirates - Arteus - Terran - TerraCorp - NMMC, 130.30830865268592, 0.06906696965876467
    Paranid - Pirates - Duke's - Arteus - TerraCorp - NMMC, 94.09448097539729, 0.09564854289757137
    Paranid - Yaki - Duke's - Arteus - TerraCorp - NMMC, 100.79028840524897, 0.08929431736333138
    Paranid - Duke's - Arteus - Terran - TerraCorp - NMMC, 91.37755488181095, 0.09849245814949557
    Pirates - Duke's - Arteus - Terran - TerraCorp - NMMC, 74.26507689856362, 0.12118751337580681
    Yaki - Pirates - Duke's - Arteus - TerraCorp - NMMC, 81.40155546042035, 0.1105629978333282
    Paranid - Pirates - Arteus - Terran - TerraCorp - NMMC, 94.97941759796626, 0.09475737194026247
    Paranid - Yaki - Pirates - Arteus - TerraCorp - NMMC, 99.37518463810929, 0.09056586946504751
    Paranid - Yaki - Arteus - Terran - TerraCorp - NMMC, 51.654557153109444, 0.17423438503834368
    Yaki - Pirates - Arteus - Terran - TerraCorp - NMMC, 54.28542967291706, 0.16579034290098085
    Paranid - OTAS - Pirates - Duke's - TerraCorp - NMMC, 181.75954161098844, 0.04951596994705392
    Paranid - Yaki - OTAS - Duke's - TerraCorp - NMMC, 185.45378151260502, 0.048529611672481765
    Paranid - OTAS - Duke's - Terran - TerraCorp - NMMC, 142.12119069833923, 0.06332623555837666
    OTAS - Pirates - Duke's - Terran - TerraCorp - NMMC, 90.60998604532641, 0.09932680042018628
    Yaki - OTAS - Pirates - Duke's - TerraCorp - NMMC, 105.18935552702197, 0.08555998803213506
    Yaki - OTAS - Duke's - Terran - TerraCorp - NMMC, 62.85533523679047, 0.14318593586518846
    Paranid - OTAS - Pirates - Terran - TerraCorp - NMMC, 142.3059073769699, 0.06324403649778854
    Paranid - Yaki - OTAS - Pirates - TerraCorp - NMMC, 168.19874751691856, 0.05350812733664809
    Paranid - Yaki - OTAS - Terran - TerraCorp - NMMC, 59.94863558780217, 0.15012852105396776
    Yaki - OTAS - Pirates - Terran - TerraCorp - NMMC, 59.09945681148531, 0.15228566361799373
    Paranid - Pirates - Duke's - Terran - TerraCorp - NMMC, 100.02030360459241, 0.08998173046524092
    Paranid - Yaki - Duke's - Terran - TerraCorp - NMMC, 63.08323187947799, 0.14266865745234347
    Yaki - Pirates - Duke's - Terran - TerraCorp - NMMC, 43.728174438990365, 0.2058169616149153
    Paranid - Yaki - Pirates - Terran - TerraCorp - NMMC, 50.73625968277388, 0.17738792840213458
    Paranid - OTAS - Duke's - Split - Arteus - NMMC, 120.57516329481159, 0.07464223770524452
    Yaki - OTAS - Duke's - Split - Arteus - NMMC, 142.4322678209717, 0.06318792881478534
    OTAS - Duke's - Split - Terran - Arteus - NMMC, 320.77267251763885, 0.028057252911733315
    OTAS - Pirates - Duke's - Split - Arteus - NMMC, 102.62490227400292, 0.08769801286602436
    Yaki - OTAS - Pirates - Split - Arteus - NMMC, 101.67154778774993, 0.08852034021148619
    Yaki - OTAS - Split - Terran - Arteus - NMMC, 70.342482429481, 0.12794544191730203
    Paranid - OTAS - Pirates - Split - Arteus - NMMC, 92.7047213488543, 0.09708243408803717
    Paranid - Yaki - Split - Arteus - NMMC, 195.97954915834163, 0.0510257322406661
    Paranid - OTAS - Split - Terran - Arteus - NMMC, 94.65202927462141, 0.09508512462936837
    OTAS - Pirates - Split - Arteus - Terran - NMMC, 136.74202527390293, 0.06581736654823146
    Paranid - Pirates - Duke's - Split - Arteus - NMMC, 107.2697949336078, 0.0839005985382031
    Paranid - Yaki - Duke's - Split - Arteus - NMMC, 167.07536798276047, 0.05386790469872649
    Paranid - Yaki - Split - Terran - Arteus - NMMC, 57.4096575323864, 0.15676804891098414
    Yaki - Pirates - Duke's - Split - Arteus - NMMC, 129.64219703868594, 0.06942184107936979
    Paranid - Pirates - Split - Arteus - Terran - NMMC, 89.11789414729766, 0.1009898190045249
    Paranid - Yaki - Pirates - Split - Arteus - NMMC, 79.05501938970676, 0.11384476367824194
    Yaki - Pirates - Split - Arteus - Terran - NMMC, 62.25147649421214, 0.1445748841127773
    Paranid - OTAS - Pirates - Duke's - Split - NMMC, 86.18283171967437, 0.10442915161193783
    Paranid - Yaki - OTAS - Duke's - Split - NMMC, 121.40220316878934, 0.07413374522937623
    Paranid - OTAS - Duke's - Split - Terran - NMMC, 135.54875267290225, 0.06639677475836488
    OTAS - Pirates - Duke's - Split - Terran - NMMC, 93.5473931003684, 0.09620791880692779
    Yaki - OTAS - Pirates - Duke's - Split - NMMC, 83.05198747746893, 0.10836585942559893
    Yaki - OTAS - Duke's - Split - Terran - NMMC, 78.40821553932264, 0.1147838901586326
    Paranid - OTAS - Pirates - Split - Terran - NMMC, 73.17345181695707, 0.12299542766567093
    Paranid - Yaki - OTAS - Pirates - Split - NMMC, 74.64669412567243, 0.12056796493690573
    Paranid - Yaki - Pirates - Duke's - Split - Terran - NMMC, 33.26659844414755, 0.24048145509771549
    Paranid - OTAS - Pirates - Duke's - Arteus - NMMC, 92.4902290338606, 0.09730757609763413
    Paranid - Yaki - OTAS - Duke's - Arteus - NMMC, 87.00096946194861, 0.10344712312586708
    Paranid - OTAS - Duke's - Arteus - Terran - NMMC, 114.2286130518568, 0.07878936598761149
    OTAS - Pirates - Duke's - Arteus - Terran - NMMC, 88.80804411177834, 0.10134217108387321
    Yaki - OTAS - Pirates - Duke's - Arteus - NMMC, 70.83311586280941, 0.1270592136230648
    Yaki - OTAS - Duke's - Arteus - Terran - NMMC, 63.00097538355759, 0.14285493113728648
    Paranid - OTAS - Pirates - Arteus - Terran - NMMC, 117.53660659911033, 0.07657188905152655
    Paranid - Yaki - OTAS - Pirates - Arteus - NMMC, 95.2578469204825, 0.09448040545691574
    Paranid - Yaki - OTAS - Arteus - Terran - NMMC, 56.84181568658343, 0.15833413995120324
    Yaki - OTAS - Pirates - Arteus - Terran - NMMC, 59.832081224093514, 0.15042097510015798
    Paranid - Pirates - Duke's - Arteus - Terran - NMMC, 83.28851820936791, 0.10805811165202987
    Paranid - OTAS - Pirates - Duke's - Terran - NMMC, 94.0955044844464, 0.0956475024955912
    Paranid - Yaki - OTAS - Pirates - Duke's - NMMC, 88.12407991587803, 0.10212872586688303
    Paranid - Yaki - OTAS - Duke's - Terran - NMMC, 59.02901052774111, 0.15246740407024756
    Yaki - OTAS - Pirates - Duke's - Terran - NMMC, 44.214257044232156, 0.20355425153918918
    OTAS - Duke's - Split - Strong Arms - Arteus - TerraCorp, 161.52582735072664, 0.05571864356068573
    Yaki - OTAS - Strong Arms - Arteus - TerraCorp, 194.4188751461133, 0.05143533513649132
    Split - Terran - Arteus - Strong Arms - TerraCorp, 2538.252082251005, 0.003939719017636606
    OTAS - Pirates - Split - Arteus - Strong Arms - TerraCorp, 189.3094863565439, 0.047541199192994876
    Yaki - Pirates - Strong Arms - Arteus - TerraCorp, 177.81257154747232, 0.0562389931880053
    Yaki - Split - Strong Arms - Terran - TerraCorp, 116.24160193128415, 0.08602772014370094
    Paranid - Split - Arteus - Strong Arms - TerraCorp, 205.19064398718413, 0.048735165530376635
    Paranid - Yaki - Strong Arms - Arteus - TerraCorp, 117.94649845747625, 0.08478420411611746
    Paranid - Strong Arms - Terran - Arteus - TerraCorp, 137.32367144338482, 0.07282065717360867
    Pirates - Split - Arteus - Terran - Strong Arms - TerraCorp, 145.21572010300775, 0.06197676114966006
    Paranid - Duke's - Split - Strong Arms - Arteus - TerraCorp, 124.1786026965505, 0.07247625439942244
    Yaki - Duke's - Split - Strong Arms - Arteus - TerraCorp, 211.7391304347826, 0.04250513347022587
    Duke's - Split - Terran - Strong Arms - Arteus - TerraCorp, 296.83502607740866, 0.030319872014204212
    Pirates - Duke's - Split - Strong Arms - Arteus - TerraCorp, 113.5079670810716, 0.07928958848828528
    Yaki - Pirates - Duke's - Split - Strong Arms - TerraCorp, 91.31359851988896, 0.0985614426096647
    Yaki - Duke's - Split - Strong Arms - Terran - TerraCorp, 91.31359851988896, 0.0985614426096647
    Paranid - Pirates - Strong Arms - Arteus - TerraCorp, 251.98569592049202, 0.03968479227946041
    Paranid - Yaki - Pirates - Strong Arms - TerraCorp, 162.61434076059632, 0.06149519134183974
    Paranid - Yaki - Split - Terran - Strong Arms - TerraCorp, 40.31606952969246, 0.22323604718886528
    Yaki - Pirates - Strong Arms - Terran - TerraCorp, 64.71196506081807, 0.1545309277905829
    Paranid - OTAS - Split - Strong Arms - TerraCorp, 205.19064398718416, 0.04873516553037663
    Yaki - OTAS - Duke's - Split - Strong Arms - TerraCorp, 146.84551341350593, 0.06128890008819457
    OTAS - Duke's - Split - Terran - Strong Arms - TerraCorp, 184.63083693046812, 0.04874591996454739
    OTAS - Pirates - Duke's - Split - Strong Arms - TerraCorp, 97.03815608765746, 0.09274702202574864
    Yaki - OTAS - Pirates - Strong Arms - TerraCorp, 276.951354932495, 0.036107424000281316
    Yaki - OTAS - Strong Arms - Terran - TerraCorp, 81.99725850055546, 0.1219552968338845
    Paranid - OTAS - Pirates - Split - Strong Arms - TerraCorp, 91.76322418136019, 0.09807850672522647
    Paranid - Yaki - OTAS - Strong Arms - TerraCorp, 201.74604684462324, 0.049567266156652884
    Paranid - OTAS - Strong Arms - Terran - TerraCorp, 257.13109017952377, 0.03889066854194178
    OTAS - Pirates - Split - Terran - Strong Arms - TerraCorp, 125.56626456180715, 0.0716753025297647
    Paranid - Duke's - Split - Terran - Strong Arms - TerraCorp, 200.20312928904744, 0.04495434228206325
    Paranid - Yaki - Pirates - Duke's - Strong Arms - TerraCorp, 61.85148998534441, 0.1455098333464971
    Paranid - Yaki - Duke's - Strong Arms - Terran - TerraCorp, 44.883818101627234, 0.20051770060251872
    Pirates - Duke's - Split - Terran - Strong Arms - TerraCorp, 115.78775942641647, 0.07772842349298184
    Paranid - Pirates - Strong Arms - Terran - TerraCorp, 204.44834169589498, 0.048912111084150625
    Paranid - OTAS - Strong Arms - Arteus - TerraCorp, 278.2196692472231, 0.03594282182513165
    Yaki - OTAS - Duke's - Strong Arms - Arteus - TerraCorp, 84.35525430023908, 0.10669163497471067
    OTAS - Duke's - Strong Arms - Terran - Arteus - TerraCorp, 97.64100494767396, 0.09217438928269041
    OTAS - Pirates - Duke's - Strong Arms - Arteus - TerraCorp, 83.3053984012848, 0.10803621581216992
    Yaki - OTAS - Pirates - Strong Arms - Arteus - TerraCorp, 129.0676962569305, 0.06973084870194024
    Yaki - OTAS - Strong Arms - Terran - Arteus - TerraCorp, 65.0170961736176, 0.13842513015295177
    Paranid - OTAS - Pirates - Strong Arms - Arteus - TerraCorp, 189.30948635654386, 0.04754119919299489
    Paranid - Yaki - OTAS - Strong Arms - Arteus - TerraCorp, 99.32982631544047, 0.09060722578351052
    Paranid - OTAS - Strong Arms - Terran - Arteus - TerraCorp, 112.39514902594566, 0.08007463024869882
    OTAS - Pirates - Strong Arms - Arteus - Terran - TerraCorp, 148.30373545621552, 0.06068626641341152
    Paranid - Pirates - Duke's - Strong Arms - Arteus - TerraCorp, 74.40807387670182, 0.12095461595892784
    Paranid - Yaki - Duke's - Strong Arms - Arteus - TerraCorp, 71.74446946307944, 0.12544520946846652
    Paranid - Duke's - Strong Arms - Terran - Arteus - TerraCorp, 83.22965270436892, 0.10813453748230731
    Pirates - Duke's - Strong Arms - Terran - Arteus - TerraCorp, 67.45164727093919, 0.13342891336439686
    Yaki - Pirates - Duke's - Strong Arms - Arteus - TerraCorp, 58.337842881134534, 0.15427378791392451
    Yaki - Duke's - Strong Arms - Terran - Arteus - TerraCorp, 52.107551487414185, 0.17271968732159326
    Paranid - Pirates - Strong Arms - Arteus - Terran - TerraCorp, 100.9745021347541, 0.08913141248262038
    Paranid - Yaki - Pirates - Strong Arms - Arteus - TerraCorp, 89.3431690354905, 0.10073517759846708
    Paranid - Yaki - Strong Arms - Terran - Arteus - TerraCorp, 50.60409342007826, 0.177851224905633
    Yaki - Pirates - Strong Arms - Arteus - Terran - TerraCorp, 55.97198114193142, 0.16079473723072574
    Paranid - OTAS - Pirates - Duke's - Strong Arms - TerraCorp, 113.5079670810716, 0.07928958848828528
    Paranid - Yaki - OTAS - Duke's - Strong Arms - TerraCorp, 98.79795396419436, 0.0910950038829925
    Paranid - OTAS - Duke's - Strong Arms - Terran - TerraCorp, 119.82512456211357, 0.07510945665935598
    OTAS - Pirates - Duke's - Strong Arms - Terran - TerraCorp, 82.17382257619008, 0.10952393010140624
    Yaki - OTAS - Pirates - Duke's - Strong Arms - TerraCorp, 70.08764979696937, 0.1284106404776204
    Yaki - OTAS - Duke's - Strong Arms - Terran - TerraCorp, 56.072379193345796, 0.16050683294473164
    Paranid - OTAS - Pirates - Strong Arms - Terran - TerraCorp, 145.21572010300775, 0.06197676114966006
    Paranid - Yaki - OTAS - Pirates - Strong Arms - TerraCorp, 123.71511118893363, 0.07274778249405198
    Paranid - Yaki - OTAS - Strong Arms - Terran - TerraCorp, 55.96735014242042, 0.16080804213702543
    Yaki - OTAS - Pirates - Strong Arms - Terran - TerraCorp, 61.9191292863336, 0.14535088112077868
    Paranid - Pirates - Duke's - Strong Arms - Terran - TerraCorp, 73.98554948803675, 0.1216453761887012
    Yaki - Pirates - Duke's - Strong Arms - Terran - TerraCorp, 34.469529900576, 0.26110016660974555
    Paranid - Yaki - Pirates - Strong Arms - Terran - TerraCorp, 46.82981387522989, 0.192185260953182
    Paranid - OTAS - Duke's - Split - Strong Arms - Arteus, 89.04100198694994, 0.10107702967357737
    Yaki - OTAS - Duke's - Split - Strong Arms - Arteus, 106.7391304347826, 0.08431771894093687
    OTAS - Duke's - Split - Strong Arms - Arteus - Terran, 296.83502607740866, 0.030319872014204212
    OTAS - Pirates - Duke's - Split - Strong Arms - Arteus, 82.61987413517869, 0.10893262782359883
    Yaki - OTAS - Pirates - Split - Strong Arms - Arteus, 92.5322392368613, 0.09726339786246894
    Yaki - OTAS - Split - Strong Arms - Arteus - Terran, 70.16779651478484, 0.12826396790304848
    Paranid - OTAS - Pirates - Split - Strong Arms - Arteus, 77.5306623058054, 0.1160831048302046
    Paranid - Yaki - OTAS - Split - Strong Arms - Arteus, 61.92638226383873, 0.14533385725094192
    Paranid - OTAS - Split - Arteus - Strong Arms - Terran, 86.17342273717415, 0.10444055387529026
    OTAS - Pirates - Split - Arteus - Strong Arms - Terran, 145.21572010300775, 0.06197676114966006
    Paranid - Pirates - Duke's - Split - Strong Arms - Arteus, 63.15990138731419, 0.1424954726387155
    Paranid - Yaki - Pirates - Split - Strong Arms - Arteus, 53.448270804328125, 0.16838711270844706
    Paranid - Yaki - Duke's - Split - Strong Arms - Arteus - Terran, 39.23913043478261, 0.2038781163434903
    Yaki - Pirates - Split - Strong Arms - Arteus - Terran, 54.4254127413779, 0.16536392737647698
    Paranid - Pirates - Split - Arteus - Strong Arms - Terran, 74.67405583512198, 0.12052378700136128
    Paranid - OTAS - Pirates - Duke's - Split - Strong Arms, 49.48486199097298, 0.1818738021668481
    Paranid - Yaki - OTAS - Duke's - Split - Strong Arms, 59.71435929854135, 0.1507175176242717
    Paranid - OTAS - Duke's - Split - Strong Arms - Terran, 92.26937865875668, 0.09754048559582307
    OTAS - Pirates - Duke's - Split - Strong Arms - Terran, 76.5046462649406, 0.11763991390578306
    Yaki - OTAS - Pirates - Duke's - Split - Strong Arms, 52.375733296972136, 0.17183530298219793
    Yaki - OTAS - Duke's - Split - Strong Arms - Terran, 64.60298020004083, 0.1393124585294954
    Paranid - Yaki - OTAS - Pirates - Split - Strong Arms - Terran, 29.9177733065057, 0.267399579441976
    Paranid - Yaki - Pirates - Duke's - Split - Strong Arms - Terran, 18.75062468765617, 0.4266524520255864
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus, 77.15583629662281, 0.11664704100153651
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus, 67.48170469220835, 0.13336948201071702
    Paranid - OTAS - Duke's - Strong Arms - Arteus - Terran, 105.85884503825372, 0.0850188758128592
    OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran, 82.17382257619008, 0.10952393010140624
    Yaki - OTAS - Duke's - Strong Arms - Arteus - Terran, 56.012038801316464, 0.16067974300889884
    Paranid - OTAS - Pirates - Strong Arms - Arteus - Terran, 125.56626456180717, 0.07167530252976469
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Arteus, 89.02550373500833, 0.10109462594886555
    Paranid - Yaki - OTAS - Strong Arms - Arteus - Terran, 55.62678915015756, 0.16179254883300248
    Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran, 61.91912928633362, 0.14535088112077862
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran, 28.99012645071886, 0.2759560229445507
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Terran, 76.5046462649406, 0.11763991390578306
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms, 53.760826687248084, 0.1674081399893126
    Paranid - OTAS - Duke's - Split - Arteus - TerraCorp, 80.35072185075408, 0.11200895017118674
    Yaki - OTAS - Duke's - Split - Arteus - TerraCorp, 89.48280302498183, 0.10057798477197208
    OTAS - Duke's - Split - Terran - Arteus - TerraCorp, 87.53728145656584, 0.10281333678914407
    OTAS - Pirates - Duke's - Split - Arteus - TerraCorp, 73.33336776535418, 0.12272721510346324
    Yaki - OTAS - Pirates - Split - Arteus - TerraCorp, 101.52895191412357, 0.08864466568720701
    Yaki - OTAS - Split - Terran - Arteus - TerraCorp, 60.65037498723772, 0.1483914980227874
    Paranid - OTAS - Pirates - Split - Arteus - TerraCorp, 88.25666336080656, 0.10197530313611157
    Paranid - Yaki - OTAS - Split - Arteus - TerraCorp, 76.93434151789276, 0.1169828690599354
    Paranid - OTAS - Split - Terran - Arteus - TerraCorp, 70.91181095408056, 0.12691820839024986
    OTAS - Pirates - Split - Arteus - Terran - TerraCorp, 97.44474899375263, 0.0923600306115726
    Paranid - Pirates - Split - Arteus - Terran - TerraCorp, 67.4192498882335, 0.1334930307726658
    Yaki - Pirates - Duke's - Split - Arteus - TerraCorp, 76.09359052867931, 0.11827540187642929
    Paranid - Yaki - Split - Terran - Arteus - TerraCorp, 47.993321215364716, 0.18752609263304568
    Yaki - Pirates - Split - Arteus - Terran - TerraCorp, 53.48330973042933, 0.16827679598294287
    Paranid - Yaki - Pirates - Split - Arteus - TerraCorp, 76.61746141286966, 0.11746669537250216
    Paranid - OTAS - Pirates - Duke's - Split - TerraCorp, 74.4254127413779, 0.12092643720061384
    Paranid - Yaki - OTAS - Duke's - Split - TerraCorp, 98.79795396419436, 0.0910950038829925
    Paranid - OTAS - Duke's - Split - Terran - TerraCorp, 79.3062787914176, 0.1134840789046575
    OTAS - Pirates - Duke's - Split - Terran - TerraCorp, 66.39231783978236, 0.13555785206533622
    Yaki - OTAS - Pirates - Duke's - Split - TerraCorp, 76.09359052867931, 0.11827540187642929
    Yaki - OTAS - Duke's - Split - Terran - TerraCorp, 58.76014625973484, 0.15316503740847928
    Paranid - Yaki - OTAS - Pirates - Split - TerraCorp, 79.73369507460914, 0.1128757420758995
    Paranid - Yaki - Pirates - Duke's - Split - Terran - TerraCorp, 30.992861778066185, 0.2581239530988275
    Paranid - OTAS - Pirates - Duke's - Arteus - TerraCorp, 73.85142626093987, 0.12186629907728827
    Paranid - Yaki - OTAS - Duke's - Arteus - TerraCorp, 71.7449007752327, 0.12544445532367257
    Paranid - OTAS - Duke's - Arteus - Terran - TerraCorp, 68.9898171311793, 0.13045403472931566
    Yaki - OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp, 36.266493618862214, 0.2205892878444471
    Paranid - OTAS - Pirates - Arteus - Terran - TerraCorp, 97.11279953243715, 0.0926757342320655
    Paranid - Yaki - Pirates - Duke's - Arteus - Terran - TerraCorp, 33.91304347826087, 0.23589743589743592
    Paranid - Yaki - OTAS - Pirates - Duke's - Terran - TerraCorp, 36.893769610040344, 0.21683878022111527
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - Terran, 44.974264204796, 0.17787950823544302
    Paranid - Yaki - OTAS - Duke's - Split - Arteus, 67.48170469220835, 0.13336948201071702
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - Terran, 40.88560930802205, 0.1956678678732652
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - Terran, 35.612092773174965, 0.224642793417242
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - Terran, 40.05782932891466, 0.19971127078085124
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Terran, 32.42615333554596, 0.24671443193449338
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Terran, 30.10900114866681, 0.2657012751933895
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - Terran, 36.30926618138894, 0.22032943216298223


with least enemies, which is 3, the results are


```python
parsed_least_enemy_set_list_without_infinite = []
for least_enemy_set in least_enemy_set_list_without_infinite:
    if len(list(least_enemy_set)) == 3:
        friend_races = list(set(all_races_without_infinite) - least_enemy_set)
        X = get_X(friend_races)
        workload_without_infinite = sum(X)
        R_extra = np.array(relationship_df.loc[infinite_races, friend_races])
        N_extra = R_extra@X
        workload_extra = max((1-N_extra[0])/r1,(1-N_extra[1])/r2,(1-N_extra[2])/r3)
        efficiency = (len(all_races) - len(list(least_enemy_set)))/(workload_without_infinite+workload_extra)
        item = " - ".join(list(least_enemy_set)) + ", " + str(workload_without_infinite+workload_extra) + ", " + str(efficiency)
        print(item)
        parsed_least_enemy_set_list_without_infinite += [item]
```

    Terran - TerraCorp - Yaki, 171.2032461286091, 0.07009212892485411
    Arteus - Paranid - TerraCorp, 2023.7956074370447, 0.005929452537549937
    Terran - Paranid - Yaki, 116.89992094755894, 0.10265190859609884
    Terran - Pirates - Yaki, 105.3461102176374, 0.11391023337462458
    Terran - OTAS - Yaki, 123.03150825209372, 0.0975359903368151
    Paranid - OTAS - Yaki, 816.7694861889692, 0.014692027803330131
    Arteus - OTAS - Yaki, 535.0506351864673, 0.022427783859779837
    Arteus - Paranid - OTAS, 1324.7692323975446, 0.009058181384755296
    Arteus - Paranid - Yaki, 297.80939829876394, 0.04029422868636784
    Arteus - Paranid - Terran, 3824.2459278403912, 0.003137873511909988
    Arteus - Paranid - Pirates, 2026.1585597183964, 0.005922537474889333


The same has been done with normal approach, that is to ignore Goner's peaceful nature and get Argon and Boron points directly.

### The normal approach

Turned out there are the following number of possible combos.


```python
least_enemy_set_list = []
for races in subs(all_races):
    if races != []:
        if min(get_X(races))>0:
            enemy_set = set(all_races) - set(races)
            is_duplicate = False
            for i, least_enemy_set in enumerate(least_enemy_set_list):
                if enemy_set.issubset(least_enemy_set):
                    least_enemy_set_list[i] = enemy_set
                    is_duplicate = True
                    break
                if least_enemy_set.issubset(enemy_set):
                    is_duplicate = True
                    break
            if not is_duplicate:
                least_enemy_set_list = least_enemy_set_list + [enemy_set]
                
len(least_enemy_set_list)
```




    4744



which is the following


```python
parsed_least_enemy_set_list = []
for least_enemy_set in least_enemy_set_list:
    workload = sum(get_X(list(set(all_races) - least_enemy_set)))
    efficiency = (len(all_races) - len(list(least_enemy_set)))/workload
    item = " - ".join(list(least_enemy_set)) + ", " + str(workload) + ", " + str(efficiency)
    print(item)
    parsed_least_enemy_set_list += [item]
```

    OTAS - Boron - Split - Arteus - TerraCorp - Argon, 166.54797513966005, 0.054038483460714444
    Yaki - Boron - Strong Arms - Arteus - Teladi - TerraCorp - Argon, 278.3952388716777, 0.028736123622026044
    Boron - Arteus - Terran - Teladi - TerraCorp - Argon, 288.4090947263057, 0.03120567334584513
    Pirates - Boron - Split - Arteus - Strong Arms - Teladi - TerraCorp - Argon, 476.3674649050357, 0.014694538388333168
    Yaki - Pirates - Boron - Strong Arms - Split - TerraCorp - Argon, 100.16244463951448, 0.07987025505210132
    Yaki - Strong Arms - Terran - Goner - Teladi - TerraCorp, 772.5786876184618, 0.01164929882772621
    Paranid - Boron - Arteus - TerraCorp - Argon, 362.2912386041893, 0.027602102768279218
    Paranid - Yaki - Boron - Strong Arms - Teladi - TerraCorp - Argon, 2838.3315961229455, 0.0028185572154175715
    Paranid - Boron - Strong Arms - Terran - Teladi - TerraCorp - Argon, 2838.3315961229687, 0.002818557215417548
    Pirates - Boron - Split - Terran - TerraCorp - Argon, 1257.4655385968397, 0.007157253796428309
    Paranid - Boron - Duke's - Strong Arms - Arteus - Goner - Teladi - TerraCorp, 5214.858823529308, 0.001342318217401434
    Yaki - Boron - Duke's - Arteus - TerraCorp - Argon, 88.86361536213022, 0.10127879631414823
    Boron - Duke's - Arteus - Terran - TerraCorp - Argon, 70.25849786913693, 0.12809838344058178
    Pirates - Duke's - Strong Arms - Arteus - Goner - Teladi - TerraCorp - Argon, 175.87737478411026, 0.03980045761197261
    Yaki - Pirates - Duke's - Strong Arms - Goner - TerraCorp, 217.37508432770215, 0.041403089171121926
    Yaki - Duke's - Terran - Goner - TerraCorp, 209.28476387541915, 0.047781786952979986
    Paranid - Pirates - Strong Arms - Split - Goner - TerraCorp - Argon, 616.600293635307, 0.012974369429560572
    Paranid - Yaki - Pirates - Strong Arms - Goner - Argon - NMMC, 697.2642382004123, 0.011473412175343183
    Terran - Paranid - Yaki, 82.5459352322271, 0.14537360278541045
    Terran - Pirates - Yaki, 85.82881902339327, 0.1398131785633601
    Paranid - OTAS - Boron - Split - Teladi - Argon - NMMC, 4477.450280948551, 0.001786731174668721
    Yaki - OTAS - Boron - Strong Arms - Split - Teladi - Argon, 271.8582041673784, 0.02942710529741651
    OTAS - Boron - Split - Terran - TerraCorp - Argon, 102.83845349614998, 0.08751590182496218
    OTAS - Pirates - Boron - Split - Strong Arms - Teladi - Argon - NMMC, 480.8724363445209, 0.014556875110605948
    Yaki - OTAS - Pirates - Boron - Teladi - Argon, 277.89450423202965, 0.03238639074519227
    Yaki - OTAS - Strong Arms - Terran - Goner - Teladi, 532.3804342191361, 0.016905204289110784
    Paranid - OTAS - Pirates - Boron - Strong Arms - Teladi - TerraCorp - Argon, 476.3674649050356, 0.014694538388333171
    Paranid - Yaki - OTAS - Boron - Argon, 173.7756727887986, 0.0575454540875447
    Paranid - OTAS - Boron - Terran - Teladi - Argon, 346.2239575759454, 0.02599473491959556
    OTAS - Pirates - Boron - Terran - Teladi - Argon - NMMC, 668.294945466013, 0.011970762392077451
    Paranid - Pirates - Boron - Duke's - Strong Arms - Goner - Teladi - TerraCorp, 395.4698535151764, 0.017700464239637347
    Paranid - Yaki - Boron - Duke's - Strong Arms - TerraCorp - Argon, 122.99423247559874, 0.06504370033438071
    Paranid - Boron - Duke's - Terran - Teladi - TerraCorp - Argon, 1525.8243494423755, 0.005243067462466216
    Pirates - Duke's - Strong Arms - Terran - Goner - Teladi - TerraCorp, 216.63595389291947, 0.036928311557897275
    Paranid - Pirates - Strong Arms - Terran - Goner - Teladi - TerraCorp - Argon - NMMC, 317.42141916054993, 0.018902316094066843
    OTAS - Boron - Duke's - Arteus - TerraCorp - Argon, 40.04932550653259, 0.22472288574577812
    Yaki - OTAS - Boron - Arteus - Argon, 99.23980523490638, 0.10076601799378203
    OTAS - Boron - Arteus - Terran - Teladi - TerraCorp - Argon, 30.211238516028715, 0.26480211977259926
    OTAS - Pirates - Boron - Arteus - TerraCorp - Argon, 173.15841855222558, 0.051975526660781715
    Yaki - Pirates - Boron - Arteus - Teladi - Argon, 257.45039658146754, 0.034958190468943565
    Yaki - Arteus - Terran - Goner - Teladi - TerraCorp, 119.56415119063742, 0.07527339850930798
    Paranid - OTAS - Boron - Arteus - Argon, 234.93801966591195, 0.04256441768863236
    Paranid - Yaki - Strong Arms - Arteus - Goner - Teladi - TerraCorp - Argon, 92579.07196952126, 7.56110409305521e-05
    Paranid - Arteus - Terran - Goner - Teladi - TerraCorp - Argon - NMMC, 6396.16069283495, 0.001094406525439781
    Pirates - Boron - Arteus - Terran - TerraCorp - Argon, 43.95991199804972, 0.20473198400395534
    Paranid - Pirates - Boron - Arteus - Argon, 423.7500694380173, 0.023598816191964585
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Goner, 188.0701240608723, 0.04785449068501166
    Paranid - Duke's - Arteus - Terran - Goner - Teladi - TerraCorp, 105.12738271129649, 0.07609815629073355
    Pirates - Duke's - Strong Arms - Terran - Arteus - Goner - Teladi, 1100.565813425448, 0.007268988280764836
    Yaki - Pirates - Duke's - Arteus - Goner, 1640.6848273277199, 0.006095015833289316
    Yaki - Duke's - Strong Arms - Terran - Arteus - Goner, 130.83526677293096, 0.06878879236452205
    Paranid - Pirates - Arteus - Terran - Goner - Teladi - Argon - NMMC, 376.3590344544348, 0.018599261235078653
    Paranid - Yaki - Pirates - Arteus - Goner - Argon - NMMC, 498.583955235548, 0.016045442128639155
    Arteus - Paranid - Terran - Yaki, 35.236630370332534, 0.3121751394611627
    Arteus - Pirates - Terran - Yaki, 51.070866881961976, 0.2153869842355301
    Paranid - OTAS - Boron - Duke's - Strong Arms - Teladi - TerraCorp - Argon, 171.99999999999977, 0.0406976744186047
    Yaki - OTAS - Boron - Duke's - Strong Arms - Argon, 362.01996012202704, 0.02486050768296407
    OTAS - Boron - Duke's - Terran - Teladi - TerraCorp - Argon, 58.870165621561405, 0.13589226249891798
    OTAS - Pirates - Boron - Duke's - Strong Arms - Teladi - Argon, 127.14106779931939, 0.06292223384994117
    Yaki - OTAS - Pirates - Duke's - Strong Arms, 55.07160810648667, 0.18158176860686476
    Terran - OTAS - Duke's - Yaki, 74.95096743102711, 0.14676261530743606
    Paranid - OTAS - Pirates - Terran - Goner - Teladi - TerraCorp - Argon, 3432.742769847534, 0.0020391857093069944
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Goner - Teladi - Argon, 318.7005404978946, 0.02196419243300983
    Terran - Paranid - OTAS - Yaki, 45.85731953596932, 0.23987446521752934
    Terran - OTAS - Pirates - Yaki, 55.976158239538634, 0.19651223567233264
    Paranid - Pirates - Duke's - Terran - Goner - Teladi, 243.1580128123961, 0.037012969039781456
    Paranid - Yaki - Pirates - Duke's - Strong Arms, 33.928908278004215, 0.2947339159298239
    Terran - Paranid - Duke's - Yaki, 62.50956326037024, 0.1759730739788062
    Terran - Pirates - Duke's - Yaki, 29.970950403601996, 0.3670220614251188
    Terran - Paranid - Pirates - Yaki, 29.044273921030808, 0.3787321394195693
    Paranid - OTAS - Strong Arms - Split - Arteus - Goner - Teladi - Argon, 693.376751718244, 0.010095521637628361
    Yaki - OTAS - Strong Arms - Split - Arteus - Goner - Teladi - TerraCorp - Argon, 1231.6195372750467, 0.004871634314339456
    OTAS - Split - Terran - Arteus - Goner - Teladi - TerraCorp - Argon - NMMC, 1261.2301731444145, 0.004757260116161986
    Pirates - Duke's - Strong Arms - Split - Arteus - Goner - Teladi - TerraCorp, 2639.118232367569, 0.002652401061137855
    Yaki - Pirates - Strong Arms - Split - Arteus - Goner - Teladi - Argon, 2635.837577258648, 0.0026557023317348013
    Yaki - Strong Arms - Split - Terran - Goner - TerraCorp, 151.32608155961768, 0.05947421559616797
    Paranid - Pirates - Strong Arms - Split - Arteus - Goner - Teladi - NMMC, 335.8674937770554, 0.020841552486310304
    Paranid - Yaki - Strong Arms - Split - Goner - Teladi - TerraCorp - Argon, 297.6908892800259, 0.023514323924825865
    Paranid - Strong Arms - Split - Terran - Goner - Teladi - TerraCorp - Argon, 297.6908892800266, 0.023514323924825806
    Pirates - Split - Arteus - Terran - Goner - TerraCorp - Argon, 394.8732120631686, 0.020259667547972905
    Paranid - Duke's - Strong Arms - Split - Arteus - Teladi - TerraCorp - Argon, 106.61913933803015, 0.06565425348076467
    Paranid - Yaki - Duke's - Strong Arms - Split - Goner - TerraCorp, 523.2206119162627, 0.015289917518158357
    Paranid - Duke's - Strong Arms - Split - Terran - Goner - Teladi - TerraCorp, 522.4814814814815, 0.013397604026369886
    Pirates - Duke's - Split - Terran - Goner - Teladi - TerraCorp, 183.39089796168452, 0.04362266660405045
    Yaki - Pirates - Duke's - Strong Arms - Split, 148.17935813664124, 0.06748578294406336
    Yaki - Duke's - Split - Terran - Goner - TerraCorp, 184.13002839646708, 0.04887850221052094
    Paranid - Pirates - Split - Terran - Goner, 457.3552169614727, 0.0218648429691847
    Paranid - Yaki - Pirates - Strong Arms - Split, 33.198513566407165, 0.3012183054520482
    Split - Paranid - Terran - Yaki, 50.401375412268266, 0.21824801228187268
    Split - Pirates - Terran - Yaki, 53.26729548048723, 0.20650569736602262
    Paranid - OTAS - Duke's - Strong Arms - Split - Goner - Teladi - Argon, 754.0427301405186, 0.00928329353257676
    Yaki - OTAS - Duke's - Strong Arms - Split - TerraCorp - Argon, 96.56931428625627, 0.08284205038762048
    OTAS - Duke's - Split - Terran - Goner - Teladi - TerraCorp - Argon, 490.5631358467924, 0.014269315177784103
    OTAS - Pirates - Duke's - Strong Arms - Split - Goner - Teladi, 8127.759905083091, 0.0009842810434147803
    Yaki - OTAS - Pirates - Strong Arms - Split - Argon, 60.96908076517785, 0.14761580602901758
    Yaki - OTAS - Split - Terran - Goner - Teladi, 164.0932678437565, 0.05484685702383272
    Paranid - OTAS - Pirates - Strong Arms - Split - Goner - Teladi, 534.3895770838527, 0.014970351861381263
    Paranid - Yaki - OTAS - Strong Arms - Split - Goner, 105.27686191177384, 0.08548887036110893
    Paranid - OTAS - Strong Arms - Split - Terran - Goner - Teladi, 670.282790522552, 0.011935260927351582
    OTAS - Pirates - Split - Terran - Goner - Teladi - Argon - NMMC, 602.7254161729193, 0.011613912093582148
    Paranid - Pirates - Duke's - Strong Arms - Split, 91.18748201649653, 0.10966417515718793
    Paranid - Yaki - Pirates - Duke's - Split, 76.81574884109857, 0.1301816378915481
    Paranid - Yaki - Duke's - Split - Terran, 47.55612856250648, 0.21027784014958814
    Yaki - Pirates - Duke's - Split - Terran, 27.63996232163363, 0.3617949939162204
    Paranid - Yaki - Pirates - Split - Terran, 17.953012589578723, 0.5570095798743411
    Paranid - OTAS - Duke's - Strong Arms - Arteus - Goner - Teladi - TerraCorp - Argon, 170.99999999999972, 0.035087719298245675
    Yaki - OTAS - Duke's - Strong Arms - Arteus - Goner - Argon, 361.019960122027, 0.0221594395980099
    OTAS - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 57.999407660615006, 0.13793244315204392
    OTAS - Pirates - Duke's - Strong Arms - Arteus - Goner - Teladi - Argon, 126.1410677993193, 0.0554934259089709
    Yaki - OTAS - Pirates - Duke's - Arteus, 60.54902726197111, 0.1651554195368664
    Yaki - OTAS - Arteus - Terran - Goner - Teladi, 224.05901344974038, 0.04016798905534246
    Paranid - OTAS - Arteus - Terran - Goner - Teladi - TerraCorp - Argon, 413.04255228721576, 0.016947406414272875
    Paranid - Yaki - OTAS - Strong Arms - Arteus - Goner - Teladi - Argon, 823.7088387551263, 0.008498148460539917
    Paranid - Yaki - OTAS - Arteus - Terran, 30.772867754972943, 0.3249615888783711
    Yaki - OTAS - Pirates - Arteus - Terran, 43.22861047339676, 0.23132827751088786
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Goner - Teladi, 101.27747822238167, 0.0789909083481904
    Paranid - Yaki - Pirates - Duke's - Arteus, 35.45919231659144, 0.28201431974864744
    Paranid - Yaki - Duke's - Arteus - Terran, 23.13225312949753, 0.43229684302772525
    Yaki - Pirates - Duke's - Arteus - Terran, 17.90242128022806, 0.5585836599122087
    Paranid - Yaki - Pirates - Arteus - Terran, 22.17108147532488, 0.4510379888833757
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Goner - Teladi - TerraCorp, 2639.11823236757, 0.0026524010611378543
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Argon, 108.99962884236942, 0.08256908849676373
    Paranid - OTAS - Duke's - Terran - Goner - Teladi - TerraCorp - Argon, 128.78624768659324, 0.054353629566371055
    OTAS - Pirates - Duke's - Terran - Goner - Teladi, 1782.6872916492916, 0.005048557894679025
    Paranid - Yaki - OTAS - Pirates - Terran, 26.667041069698108, 0.3749947350312911
    Paranid - Yaki - Pirates - Duke's - Terran, 16.962700637456543, 0.5895287674840108
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - Goner, 468.8548267521469, 0.01706285089441786
    Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - Goner, 531.0935398867756, 0.015063259857586534
    OTAS - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp, 67.20762095019293, 0.11903411974556785
    Pirates - Boron - Duke's - Strong Arms - Arteus - Goner - Teladi - TerraCorp, 149.0454030776085, 0.04696555449184215
    Yaki - Pirates - Boron - Strong Arms - Split - Arteus - Goner - NMMC, 1455.3698696281983, 0.004809773890528792
    Yaki - Boron - Terran - Goner - TerraCorp, 202.43207750872492, 0.04939928554341391
    Paranid - Pirates - Boron - Split - Strong Arms - Goner - Teladi - NMMC, 1871.627827901483, 0.00374005980016261
    Paranid - Yaki - Boron - Strong Arms - Split - Goner - Teladi - TerraCorp, 297.69088928002634, 0.023514323924825827
    Paranid - Boron - Strong Arms - Split - Terran - Goner - Teladi - TerraCorp, 297.6908892800268, 0.023514323924825793
    Pirates - Boron - Split - Arteus - Terran - Goner - Teladi - TerraCorp, 422.4745299943169, 0.016569046186273438
    Paranid - Boron - Duke's - Split - Arteus - Goner - Teladi - TerraCorp, 491.07724088377825, 0.014254376740005894
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - TerraCorp, 94.80819459497872, 0.0843808916958714
    Paranid - Boron - Duke's - Strong Arms - Split - Terran - Teladi - TerraCorp, 94.06906416019618, 0.07441341170439685
    Pirates - Boron - Duke's - Terran - Teladi - TerraCorp, 175.0467562068749, 0.051414834499209805
    Yaki - Pirates - Boron - Duke's - Strong Arms - Goner, 460.88060155747655, 0.019527834258126413
    Yaki - Boron - Duke's - Terran - TerraCorp, 85.48450431944002, 0.11698026536636186
    Paranid - Pirates - Boron - Terran - Goner - TerraCorp, 5419.062279368924, 0.0016608039428268196
    Paranid - Yaki - Pirates - Boron - Strong Arms - Goner - Teladi, 178.66284659282627, 0.04477707678212499
    Terran - Paranid - Boron - Yaki, 45.732148368752426, 0.24053101357285045
    Pirates - Boron - Terran - Yaki, 48.89364099591666, 0.22497813163308214
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Teladi - TerraCorp, 106.61913933803017, 0.06565425348076466
    Paranid - Yaki - OTAS - Boron - Split - Goner - Teladi, 242.7917906504138, 0.032950043238977884
    Paranid - OTAS - Boron - Split - Terran - Goner, 205.54401289261477, 0.043786242534351975
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Teladi, 100.19062694242137, 0.07984778860199693
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Goner - Teladi, 200.04678993185559, 0.034991813677112724
    Terran - OTAS - Boron - Yaki, 88.81007384601443, 0.12385982269390548
    Paranid - OTAS - Pirates - Boron - Split - Goner, 533.5335247342081, 0.016868668195655665
    Paranid - Yaki - OTAS - Pirates - Boron - Goner - NMMC, 653.8807284240169, 0.012234647164600794
    Paranid - Yaki - OTAS - Boron - Terran, 23.97685773264607, 0.41706882993196986
    OTAS - Pirates - Boron - Split - Terran - Goner - TerraCorp, 2843.7374818143585, 0.0028131991968878395
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split, 62.92270870050274, 0.1430326218605413
    Paranid - Yaki - Pirates - Boron - Duke's, 101.77922397373626, 0.09825187901393767
    Paranid - Yaki - Boron - Duke's - Terran, 42.57647995430956, 0.23487145979966825
    Yaki - Pirates - Boron - Duke's - Terran, 26.454341490444257, 0.37800978730134577
    Paranid - Yaki - Pirates - Boron - Terran, 20.193577084425524, 0.49520696398621666
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - Goner - Teladi, 347.73073883691654, 0.02013051829531514
    Paranid - Yaki - Boron - Strong Arms - Arteus - Goner - Teladi, 144.22595793580825, 0.05546851700274801
    Paranid - Boron - Arteus - Terran - Goner - TerraCorp, 151.77939388891346, 0.0592965867724248
    OTAS - Pirates - Boron - Duke's - Arteus - Goner - Teladi, 172.4861180866566, 0.046380544061991234
    Yaki - Pirates - Boron - Duke's - Arteus, 65.03227424289932, 0.15376980301579826
    Yaki - Boron - Arteus - Terran - Goner - Teladi, 274.36403581005055, 0.032803133156384015
    Paranid - Pirates - Boron - Arteus - Terran, 97.97421399512332, 0.10206767262759313
    Paranid - Yaki - Pirates - Boron - Arteus, 62.18193980934839, 0.1608183988897787
    Paranid - Yaki - Boron - Arteus - Terran, 19.432218946343944, 0.5146092696676536
    Yaki - Pirates - Boron - Arteus - Terran, 28.037292533573186, 0.3566678197627508
    Paranid - Pirates - Boron - Duke's - Arteus, 65.31766773897365, 0.1530979342367611
    Paranid - Yaki - Boron - Duke's - Arteus, 99.42537741275243, 0.10057794358160904
    Paranid - Boron - Duke's - Arteus - Terran - Goner - Teladi, 487.41280756754213, 0.016413192012586616
    Pirates - Boron - Duke's - Terran - Arteus - Teladi, 142.28901837683551, 0.06325154325096664
    Yaki - Boron - Arteus - Terran - TerraCorp, 34.45780389734442, 0.29021002121295014
    Paranid - Yaki - Pirates - Boron - Arteus - Terran, 13.783457566490785, 0.6529566298285028
    Paranid - OTAS - Pirates - Boron - Duke's - Goner - Teladi, 669.4907968707928, 0.011949380092141798
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms, 71.01039402238317, 0.12674200902424387
    Paranid - OTAS - Boron - Duke's - Strong Arms - Terran - Goner - Teladi, 874.2684948979552, 0.008006693642571486
    OTAS - Pirates - Boron - Duke's - Terran - Teladi, 76.74399286182678, 0.11727302247882763
    Yaki - OTAS - Pirates - Boron - Duke's, 82.20978039771907, 0.12164002812830105
    Yaki - OTAS - Boron - Duke's - Terran, 39.93077589051236, 0.2504334007287853
    Paranid - OTAS - Pirates - Boron - Terran - Goner - Teladi, 346.2041785727188, 0.023107751133973193
    Yaki - OTAS - Pirates - Boron - Terran, 29.296538879370928, 0.3413372494674267
    Paranid - Pirates - Boron - Duke's - Terran - Teladi, 77.57905776588971, 0.11601068972968576
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - Goner - Teladi, 221.65607037693678, 0.03158045700303251
    Paranid - Yaki - Strong Arms - Split - Arteus - Goner - Teladi, 176.88827104977153, 0.045226288620057904
    Paranid - Split - Terran - Arteus - Goner - Teladi - TerraCorp, 359.50804829924476, 0.022252631165967714
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Teladi, 70.23395430359594, 0.11390502043240935
    Yaki - Pirates - Duke's - Split - Arteus - Goner, 236.00307206715442, 0.03813509680687148
    Yaki - Split - Terran - Arteus - Goner - TerraCorp, 78.63401116334249, 0.11445429104849746
    Paranid - OTAS - Pirates - Strong Arms - Split - Arteus - Goner, 180.2616155750283, 0.04437994175565485
    Paranid - Yaki - Pirates - Split - Arteus - Goner, 87.39867884416473, 0.10297638498686407
    Paranid - Yaki - Split - Terran - Arteus, 24.767437167162846, 0.4037559450542665
    Yaki - Pirates - Split - Arteus - Terran, 35.92519912858433, 0.278356146731651
    Paranid - Pirates - Duke's - Split - Arteus, 90.5683111708841, 0.11041389500055954
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus, 48.02062540820497, 0.18741946660407777
    Paranid - Duke's - Strong Arms - Split - Arteus - Terran - Goner - Teladi, 844.1316725978642, 0.008292545141040726
    Pirates - Duke's - Split - Terran - Arteus - Goner - Teladi, 1455.4346403060574, 0.0054966398204715754
    Yaki - Duke's - Split - Terran - Arteus - Goner, 1456.1737707408395, 0.006180581041108289
    Paranid - Pirates - Split - Arteus - Terran, 71.31684353727496, 0.14021932974043264
    Paranid - OTAS - Pirates - Duke's - Split, 73.36893176329212, 0.13629747305388998
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split, 31.84040555068092, 0.2826597163052633
    Paranid - OTAS - Duke's - Split - Terran - Goner - Teladi, 288.37771438153794, 0.027741394709216695
    OTAS - Pirates - Duke's - Split - Terran, 75.62331854186633, 0.1322343450778854
    Yaki - OTAS - Pirates - Duke's - Split, 77.26324891431679, 0.12942764044377392
    Yaki - OTAS - Duke's - Split - Terran, 51.98824532213995, 0.1923511735784888
    Paranid - OTAS - Pirates - Split - Terran, 58.70478820760149, 0.17034385618829526
    Paranid - Yaki - OTAS - Pirates - Split - Goner - Teladi, 112.69518889176318, 0.07098794614633913
    Paranid - Yaki - OTAS - Split - Terran, 22.14964436373034, 0.4514745174136894
    Yaki - OTAS - Pirates - Split - Terran, 28.239648098601855, 0.3541120613501944
    Paranid - Pirates - Duke's - Split - Terran, 65.66896427362819, 0.15227893588106842
    Paranid - OTAS - Pirates - Duke's - Arteus - Goner - Teladi, 172.4861180866564, 0.04638054406199129
    Paranid - Yaki - OTAS - Duke's - Arteus - Goner, 1012.3058429777323, 0.008890593749341792
    Paranid - OTAS - Duke's - Arteus - Terran - Goner - Teladi, 1159.796756188346, 0.006897760281975503
    OTAS - Pirates - Duke's - Arteus - Terran - Teladi, 59.83809919068021, 0.15040584713963892
    Yaki - OTAS - Duke's - Arteus - Terran, 34.641907221802995, 0.2886677091989375
    Paranid - Yaki - OTAS - Pirates - Arteus - Terran, 21.731889034289637, 0.4141379511831374
    Paranid - Pirates - Duke's - Arteus - Terran, 43.534001548941674, 0.22970550935359865
    Paranid - OTAS - Pirates - Duke's - Terran, 66.57826797716129, 0.1501991611351373
    Paranid - Yaki - OTAS - Pirates - Duke's, 77.90170660427117, 0.12836689253546754
    Paranid - Yaki - OTAS - Duke's - Terran, 25.498916438473643, 0.3921735272214021
    Yaki - OTAS - Pirates - Duke's - Terran, 16.88589441639568, 0.592210264579785
    OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Teladi - Argon, 1634.4999999999973, 0.004282655246252684
    Yaki - OTAS - Boron - Split - Arteus - Argon, 52.71428595923331, 0.17073170652373376
    OTAS - Boron - Split - Arteus - Terran - Argon, 648.0091286380559, 0.013888693233250623
    OTAS - Pirates - Boron - Split - Arteus - Argon, 105.49944754359063, 0.08530850359459322
    Yaki - Pirates - Boron - Split - Arteus - Teladi - Argon, 136.9148590130381, 0.058430473198224434
    Yaki - Arteus - Terran - Goner - Teladi - Argon, 2311.241378262243, 0.003894011280970941
    Paranid - OTAS - Boron - Split - Arteus - Argon, 32.23620525946051, 0.2791891889123248
    Paranid - Yaki - Boron - Strong Arms - Split - Argon, 435.9241874341268, 0.020645791767083362
    Paranid - Boron - Arteus - Terran - Argon, 924.983317080018, 0.010811005793669818
    Pirates - Boron - Split - Arteus - Strong Arms - Terran - Teladi - Argon - NMMC, 1633.4999999999914, 0.0036730945821855107
    Paranid - Boron - Duke's - Strong Arms - Split - Arteus - Teladi - Argon, 1634.4999999999852, 0.004282655246252715
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Argon, 304.2867494824016, 0.026290990368815517
    Paranid - Boron - Arteus - Terran - Teladi - Argon, 187.167134719339, 0.04808536505885869
    Pirates - Boron - Duke's - Split - Strong Arms - Arteus - Teladi - Argon, 1634.4999999999973, 0.004282655246252684
    Yaki - Pirates - Duke's - Strong Arms - Goner - Argon, 451.31672511818493, 0.01994164962010481
    Yaki - Split - Terran - Arteus - Goner - Teladi - Argon, 1330.6861608885883, 0.006011935973436339
    Paranid - Pirates - Boron - Split - Strong Arms - Argon, 193.07567554288727, 0.04661384700425849
    Paranid - Yaki - Pirates - Boron - Teladi - Argon, 507.8536081752675, 0.01772164232983843
    Terran - Paranid - Argon - Yaki, 67.54098818275885, 0.1628640666351394
    Terran - Argon - Pirates - Yaki, 56.98896447693796, 0.19301982587262892
    Paranid - OTAS - Boron - Duke's - Split - Teladi - Argon, 177.42023543228885, 0.04509068529025339
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Argon, 64.7142973157918, 0.12362028688902743
    Paranid - OTAS - Split - Terran - Goner - Argon, 625.4102228996402, 0.01439055466390135
    OTAS - Pirates - Duke's - Strong Arms - Split - Argon, 70.74471823109549, 0.1272179778934238
    Yaki - OTAS - Pirates - Boron - Split - Argon, 43.9231303820508, 0.20490342836943726
    Terran - OTAS - Argon - Yaki, 92.05261490380018, 0.11949687699252844
    Paranid - OTAS - Pirates - Split - Goner - Teladi - Argon - NMMC, 533.0672232175413, 0.013131552072829933
    Paranid - Yaki - OTAS - Split - Goner - Argon - NMMC, 1581.620410690794, 0.005058103667558193
    Paranid - Yaki - OTAS - Terran - Argon, 31.319893040669175, 0.31928589242035105
    OTAS - Pirates - Boron - Split - Terran - Argon, 63.097765431086195, 0.14263579603036142
    Paranid - Pirates - Duke's - Strong Arms - Split - Argon, 72.96101225705445, 0.12335355173378654
    Paranid - Yaki - Pirates - Duke's - Goner - Argon, 660.3875084884455, 0.013628361960691854
    Paranid - Yaki - Duke's - Terran - Argon, 57.869871855984606, 0.17280148856880267
    Yaki - Pirates - Duke's - Terran - Argon, 28.50185899430977, 0.3508543075031155
    Paranid - Pirates - Boron - Terran - Teladi - Argon, 508.2192131463915, 0.01770889365689441
    Paranid - OTAS - Boron - Duke's - Arteus - Argon, 40.51435290337985, 0.22214349619413984
    Yaki - OTAS - Boron - Duke's - Arteus - Argon, 32.16655840628907, 0.27979368778974995
    OTAS - Boron - Duke's - Arteus - Terran - Teladi - Argon, 68.14891985748432, 0.11738997502425443
    OTAS - Pirates - Boron - Duke's - Arteus - Argon, 30.80989446650882, 0.2921139509186973
    Yaki - OTAS - Pirates - Boron - Arteus - Argon, 34.62184243864099, 0.25995150361943814
    Yaki - OTAS - Arteus - Terran - Argon, 46.34731689016408, 0.21576222036107165
    Paranid - OTAS - Pirates - Boron - Arteus - Argon, 54.893470041194604, 0.16395392736596873
    Paranid - Yaki - Boron - Arteus - Argon, 62.676932630041144, 0.15954833110653832
    Paranid - OTAS - Boron - Arteus - Terran - Goner - Teladi, 308.7905452517181, 0.025907528980456986
    OTAS - Pirates - Boron - Arteus - Terran - Argon, 75.82704580175371, 0.11869115966261011
    Paranid - Pirates - Duke's - Arteus - Goner - Teladi - Argon, 406.92902801826085, 0.019659447837771363
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Argon, 73.20073989641652, 0.12294957691323263
    Paranid - Yaki - Arteus - Terran - Argon, 27.846614350086345, 0.35911008334013117
    Pirates - Duke's - Arteus - Terran - Goner - Teladi - Argon, 631.5443492732461, 0.012667360588699833
    Yaki - Pirates - Duke's - Arteus - Argon, 126.37655645665667, 0.07912860011682386
    Paranid - Pirates - Boron - Arteus - Terran - Argon, 39.04154285072881, 0.23052367664901316
    Paranid - Yaki - Pirates - Boron - Arteus - Argon, 25.825110383579094, 0.3484980263907276
    Yaki - Pirates - Arteus - Terran - Argon, 33.645472360471985, 0.29721681101283604
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Teladi - Argon, 122.92017358628598, 0.06508288889117342
    Paranid - Yaki - OTAS - Boron - Duke's - Argon, 62.373606181803225, 0.1442918014675516
    Paranid - OTAS - Boron - Duke's - Terran - Teladi - Argon, 75.20064701855316, 0.10638206341530913
    OTAS - Pirates - Duke's - Terran - Teladi - Argon, 94.72771255287239, 0.09500915579457953
    Yaki - OTAS - Pirates - Duke's - Argon, 114.63648859098303, 0.08723226018968074
    Yaki - OTAS - Duke's - Terran - Argon, 40.950107758401906, 0.24419960159807536
    Paranid - OTAS - Pirates - Boron - Terran - Argon, 57.415504636568755, 0.1567520839008314
    Paranid - Yaki - OTAS - Pirates - Boron - Argon, 44.067757909384284, 0.2042309485884563
    Yaki - OTAS - Pirates - Terran - Argon, 32.129928799334216, 0.3112362950585566
    Paranid - Pirates - Duke's - Terran - Teladi - Argon, 176.48392294856654, 0.050996146559043276
    Paranid - Yaki - Pirates - Terran - Argon, 25.23893963889831, 0.39621315883603836
    Paranid - OTAS - Duke's - Split - Arteus - Goner - Teladi - Argon, 176.4202354322888, 0.039677988088201166
    Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - Argon, 63.916982887228826, 0.12516235339385004
    Paranid - OTAS - Split - Terran - Arteus - Goner - Teladi, 359.5080482992453, 0.022252631165967682
    OTAS - Pirates - Duke's - Split - Arteus - Argon, 67.66890966764709, 0.13300051743412314
    Yaki - OTAS - Pirates - Split - Arteus - Goner - Teladi - Argon, 169.6109685724232, 0.041270915784028604
    Yaki - OTAS - Split - Terran - Argon, 46.10307835862345, 0.21690525570142385
    Paranid - Pirates - Strong Arms - Split - Arteus - Argon, 110.39916476121888, 0.0815223558934164
    Paranid - Yaki - Strong Arms - Split - Arteus - Argon, 58.18060997802723, 0.1546907123077428
    Paranid - Yaki - Split - Terran - Argon, 46.66196162024679, 0.21430732126917193
    OTAS - Pirates - Split - Arteus - Terran - Goner - Argon, 394.87321206316864, 0.0202596675479729
    Paranid - Pirates - Duke's - Split - Arteus - Argon, 62.12886909685055, 0.14486019351117127
    Paranid - Yaki - Duke's - Split - Arteus - Goner - Argon, 1687.914354006902, 0.004739576970246731
    Paranid - Duke's - Strong Arms - Split - Arteus - Terran - Goner - Teladi - Argon, 169.21917808219177, 0.035456974014409455
    Pirates - Duke's - Split - Terran - Arteus - Teladi - Argon, 182.83317695427033, 0.04375573478111653
    Yaki - Pirates - Duke's - Strong Arms - Split - Argon, 86.98707867027596, 0.10346364238893974
    Paranid - Pirates - Split - Terran - Argon, 185.27106544629487, 0.05397496892410722
    Paranid - Yaki - Pirates - Split - Goner - Teladi - Argon, 416.66290458674683, 0.019200173358207957
    Yaki - Pirates - Split - Terran - Argon, 42.311838109262936, 0.23634047696478572
    Paranid - OTAS - Pirates - Duke's - Split - Argon, 40.129396446842634, 0.22427449194063612
    Paranid - Yaki - OTAS - Duke's - Split - Argon, 108.99962884236945, 0.0825690884967637
    Paranid - OTAS - Duke's - Split - Terran - Teladi - Argon, 69.26928391517565, 0.11549130506093401
    OTAS - Pirates - Duke's - Split - Terran - Argon, 40.148523829305, 0.22416764407738368
    Yaki - OTAS - Pirates - Duke's - Split - Argon, 35.79851859728236, 0.25140705125946844
    Yaki - OTAS - Duke's - Split - Terran - Argon, 31.01489948570955, 0.29018311035142474
    Paranid - OTAS - Pirates - Split - Terran - Argon, 33.83835850318842, 0.2659703483888551
    Paranid - Yaki - OTAS - Pirates - Split - Argon, 39.60031866297289, 0.22727089841363285
    Paranid - Yaki - OTAS - Split - Terran - Argon, 17.425960795376465, 0.516470805006512
    Yaki - OTAS - Pirates - Split - Terran - Argon, 19.273913306097853, 0.4669523960737435
    Paranid - Pirates - Duke's - Split - Terran - Argon, 61.784229657689494, 0.14566824009725085
    Paranid - Yaki - Pirates - Duke's - Split - Argon, 65.657725643946, 0.13707450131315735
    Paranid - Yaki - Duke's - Split - Terran - Argon, 45.310734227771015, 0.19862842996006644
    Yaki - Pirates - Duke's - Split - Terran - Argon, 26.48568589279969, 0.3398061895178901
    Paranid - Yaki - Pirates - Split - Terran - Argon, 16.958983124400206, 0.5306921962231923
    Paranid - OTAS - Pirates - Duke's - Arteus - Argon, 65.30711281770172, 0.13781041010222883
    Paranid - Yaki - OTAS - Duke's - Arteus - Argon, 61.50094431231478, 0.14633921642399667
    Paranid - OTAS - Duke's - Arteus - Terran - Teladi - Argon, 74.2776963807951, 0.10770393253698754
    OTAS - Pirates - Duke's - Arteus - Terran - Argon, 43.32479687245827, 0.20773323015211487
    Yaki - OTAS - Pirates - Duke's - Arteus - Argon, 29.79614693142014, 0.30205247748021635
    Yaki - Strong Arms - Terran - Arteus - Goner - Argon, 174.18456698403617, 0.05166933073252604
    Paranid - OTAS - Pirates - Arteus - Terran - Goner - Argon, 1247.6678318355716, 0.006411963020822924
    Paranid - Yaki - OTAS - Pirates - Arteus - Goner - Teladi - Argon, 422.4745299943169, 0.016569046186273438
    Paranid - Yaki - OTAS - Arteus - Terran - Argon, 21.564882287474212, 0.4173451948415029
    Yaki - OTAS - Pirates - Arteus - Terran - Argon, 25.172259486848883, 0.3575364382645906
    Paranid - Pirates - Duke's - Arteus - Terran - Argon, 37.12606860485278, 0.24241726469318656
    Paranid - Yaki - Pirates - Duke's - Arteus - Argon, 28.6293990048528, 0.3143621701061368
    Paranid - Yaki - Duke's - Arteus - Terran - Argon, 21.178396333770547, 0.4249613548712762
    Yaki - Pirates - Duke's - Arteus - Terran - Argon, 16.566136619478687, 0.5432769393811275
    Paranid - Yaki - Pirates - Arteus - Terran - Argon, 18.209101884242067, 0.4942583141779491
    Paranid - OTAS - Pirates - Duke's - Terran - Argon, 46.202770516063836, 0.19479351345112236
    Paranid - Yaki - OTAS - Pirates - Duke's - Argon, 44.78641704641534, 0.20095378450731305
    Paranid - Yaki - OTAS - Duke's - Terran - Argon, 21.217698348774817, 0.4241741894930696
    Yaki - OTAS - Pirates - Duke's - Terran - Argon, 14.62083778456603, 0.6155598011969281
    Paranid - Yaki - OTAS - Pirates - Terran - Argon, 20.916131594146727, 0.4302898917751409
    Paranid - Yaki - Pirates - Duke's - Terran - Argon, 16.63954823076892, 0.5408800692892434
    Paranid - OTAS - Boron - Duke's - Split - Arteus, 76.18089474672648, 0.11813985684890808
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Goner, 121.99423247559889, 0.05737976179652698
    Paranid - Boron - Split - Arteus - Terran - Goner - Teladi, 430.66734820450836, 0.018575821996612313
    OTAS - Pirates - Boron - Duke's - Split - Arteus, 66.23684914952507, 0.13587602845786229
    Yaki - OTAS - Pirates - Boron - Split - Arteus - Goner - Teladi, 249.0010386038825, 0.028112332539848506
    Yaki - Boron - Split - Arteus - Terran - Goner - Teladi, 273.63050009774935, 0.02923650688480323
    Paranid - Pirates - Boron - Split - Arteus - Goner, 246.29514425975637, 0.03654152430430421
    Paranid - Yaki - Boron - Split - Arteus, 146.83386100976205, 0.06810418204105635
    Paranid - Yaki - Boron - Split - Terran, 37.355214460713505, 0.26770024330919057
    OTAS - Pirates - Boron - Split - Arteus - Terran - Goner - Teladi, 422.47452999431704, 0.016569046186273435
    Paranid - Pirates - Boron - Duke's - Split - Arteus, 34.753492022708805, 0.2589667822191558
    Paranid - Yaki - Boron - Duke's - Split - Arteus, 70.24812020405244, 0.12811730725117412
    Paranid - Boron - Duke's - Split - Arteus - Terran - Teladi, 129.89648411625996, 0.06158750219012733
    Pirates - Boron - Duke's - Split - Arteus - Terran - Teladi, 107.32113473855348, 0.07454263337309014
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split, 104.81042516895388, 0.0858693205899322
    Yaki - Boron - Duke's - Split - Arteus - Terran, 108.06026517333606, 0.08328685836152062
    Paranid - Pirates - Boron - Split - Terran, 95.80326389855144, 0.10438057737353562
    Paranid - Yaki - Pirates - Boron - Split, 111.20502089151213, 0.08992399731443478
    Yaki - Pirates - Boron - Split - Terran, 40.18198356228048, 0.24886775398980485
    Paranid - OTAS - Pirates - Boron - Duke's - Split, 33.42298529716118, 0.26927576696042244
    Paranid - Yaki - OTAS - Boron - Duke's - Split, 71.01039402238317, 0.12674200902424387
    Paranid - OTAS - Boron - Duke's - Split - Terran, 79.18441155168613, 0.11365873438518162
    OTAS - Pirates - Boron - Duke's - Split - Terran, 44.42554407389051, 0.20258615144995876
    Yaki - OTAS - Pirates - Boron - Duke's - Split, 37.941571608298936, 0.2372068319392293
    Yaki - OTAS - Boron - Split - Terran, 54.93815656468408, 0.18202285306435464
    Paranid - OTAS - Pirates - Boron - Split - Terran, 29.46670172869527, 0.3054295008265421
    Paranid - Yaki - OTAS - Pirates - Boron - Split, 32.46776083360487, 0.27719805027899536
    Paranid - Yaki - OTAS - Boron - Split - Terran, 15.763160976605498, 0.5709514743494103
    Yaki - OTAS - Pirates - Boron - Split - Terran, 20.194331234235154, 0.4456696235992421
    Paranid - Pirates - Boron - Duke's - Split - Terran, 48.43457872123177, 0.1858176583262974
    Paranid - Yaki - Pirates - Boron - Duke's - Split, 46.52706370572917, 0.19343580452277226
    Paranid - Yaki - Boron - Duke's - Split - Terran, 36.82816815764414, 0.24437816080004887
    Yaki - Pirates - Boron - Duke's - Split - Terran, 25.25427369822163, 0.356375325125021
    Paranid - Yaki - Pirates - Boron - Split - Terran, 15.149910321453168, 0.5940629224224164
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus, 29.9148209838657, 0.3008542155359737
    Paranid - Yaki - OTAS - Boron - Arteus - Goner - Teladi, 155.92313708497326, 0.051307330968079795
    Paranid - OTAS - Boron - Duke's - Arteus - Terran, 45.69473842383126, 0.1969592191670412
    OTAS - Pirates - Boron - Duke's - Arteus - Terran, 34.41372642620009, 0.26152355279805034
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus, 23.29299881189067, 0.38638219461058215
    Yaki - OTAS - Boron - Arteus - Terran, 40.38760559612792, 0.24760071443697396
    Paranid - OTAS - Pirates - Boron - Arteus - Terran, 68.88018080122488, 0.1306616779356647
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus, 51.02081538089388, 0.17639859208071954
    Paranid - Yaki - OTAS - Boron - Arteus - Terran, 15.770262804933465, 0.5706943575591207
    Yaki - OTAS - Pirates - Boron - Arteus - Terran, 21.917311648668104, 0.4106343033428975
    Paranid - Pirates - Boron - Duke's - Arteus - Terran, 24.13010870786965, 0.37297801302754985
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus, 18.469510331339762, 0.48728958367285247
    Paranid - Yaki - Boron - Duke's - Arteus - Terran, 16.00622566598231, 0.5622812140608207
    Yaki - Pirates - Boron - Duke's - Arteus - Terran, 14.774230390010276, 0.6091687866249486
    Paranid - OTAS - Pirates - Boron - Duke's - Terran, 32.78423409258243, 0.27452219791330396
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates, 30.103998269837444, 0.29896361006031236
    Paranid - Yaki - OTAS - Boron - Duke's - Terran, 17.662466449295835, 0.5095551080499752
    Yaki - OTAS - Pirates - Boron - Duke's - Terran, 13.719638505671227, 0.6559939605026553
    Paranid - Yaki - OTAS - Pirates - Boron - Terran, 16.848335657712003, 0.5341773919301295
    Paranid - Yaki - Pirates - Boron - Duke's - Terran, 14.694495366449221, 0.6124742480472646
    Paranid - OTAS - Pirates - Duke's - Split - Arteus, 28.933162758617907, 0.3110617416797719
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus, 51.5209325733036, 0.17468627896428054
    Paranid - OTAS - Duke's - Split - Arteus - Terran, 61.34177920059709, 0.14671892659925317
    OTAS - Pirates - Duke's - Split - Arteus - Terran, 38.623649015515205, 0.2330178589906065
    Yaki - OTAS - Pirates - Duke's - Split - Arteus, 32.252055026528865, 0.2790519857601963
    Yaki - OTAS - Split - Terran - Arteus - Goner, 78.6340111633425, 0.11445429104849744
    Paranid - OTAS - Pirates - Split - Arteus - Terran, 41.80233848811216, 0.21529895995075585
    Paranid - Yaki - OTAS - Pirates - Split - Arteus, 53.64762422946728, 0.16776138979620514
    Paranid - Yaki - OTAS - Split - Arteus - Terran, 17.653142643714833, 0.5098242381904918
    Yaki - OTAS - Pirates - Split - Arteus - Terran, 25.0089601179431, 0.3598710205284704
    Paranid - Pirates - Duke's - Split - Arteus - Terran, 25.053886858370152, 0.35922569822706873
    Paranid - Yaki - Pirates - Duke's - Split - Arteus, 22.671060154231498, 0.39698187639981947
    Paranid - Yaki - Duke's - Split - Arteus - Terran, 20.41537203826441, 0.44084428062987796
    Yaki - Pirates - Duke's - Split - Arteus - Terran, 17.08068054085469, 0.5269110898990945
    Paranid - Yaki - Pirates - Split - Arteus - Terran, 14.268018217940131, 0.6307813644843612
    Paranid - OTAS - Pirates - Duke's - Split - Terran, 20.760150872130023, 0.4335228609577338
    Paranid - Yaki - OTAS - Pirates - Duke's - Split, 22.89693108047647, 0.3930657767352076
    Paranid - Yaki - OTAS - Duke's - Split - Terran, 17.238586078782877, 0.5220845815816143
    Yaki - OTAS - Pirates - Duke's - Split - Terran, 13.329356547109377, 0.6752013848674303
    Paranid - Yaki - OTAS - Pirates - Split - Terran, 13.908062962383038, 0.6471066477296074
    Paranid - Yaki - Pirates - Duke's - Split - Terran, 13.859412015827973, 0.6493781979871628
    Paranid - OTAS - Pirates - Duke's - Arteus - Terran, 29.22465587712865, 0.3079591437394286
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus, 26.147404514746952, 0.34420242341545076
    Paranid - Yaki - OTAS - Duke's - Arteus - Terran, 16.300236381464288, 0.5521392321791293
    Yaki - OTAS - Pirates - Duke's - Arteus - Terran, 12.89783229545913, 0.6977916748978494
    Paranid - Yaki - Pirates - Duke's - Arteus - Terran, 11.363750432431905, 0.7919920499410291
    Paranid - Yaki - OTAS - Pirates - Duke's - Terran, 12.80002059677728, 0.703123868587053
    OTAS - Boron - Duke's - Split - Arteus - TerraCorp - Argon, 28.30973519110228, 0.28258830208042324
    Yaki - OTAS - Boron - Split - Teladi - TerraCorp - Argon, 297.26648700348613, 0.026911879911663845
    Boron - Split - Arteus - Terran - TerraCorp - Argon, 648.0091286380552, 0.013888693233250638
    OTAS - Pirates - Boron - Split - TerraCorp - Argon, 1217.9779286631835, 0.007389296462767706
    Yaki - Pirates - Boron - Arteus - TerraCorp - Argon, 46.306405299046396, 0.19435756115980224
    Terran - Argon - TerraCorp - Yaki, 157.97854747268636, 0.06962970717211994
    Paranid - Boron - Split - Arteus - TerraCorp - Argon, 64.15031270840363, 0.14029549693560586
    Paranid - Yaki - Boron - Arteus - Goner - Teladi - TerraCorp, 301.55239010812363, 0.026529386807816534
    Paranid - Boron - Split - Terran - TerraCorp - Argon, 352.20536978762067, 0.02555327309582755
    Pirates - Boron - Split - Arteus - Terran - TerraCorp - Argon, 31.535950501638784, 0.25367873403987856
    Paranid - Boron - Duke's - Arteus - TerraCorp - Argon, 50.30556339374862, 0.17890665351575039
    Yaki - Boron - Duke's - Split - Arteus - TerraCorp - Argon, 88.83842121492441, 0.09005112754813387
    Boron - Duke's - Split - Terran - Arteus - TerraCorp - Argon, 69.11703402185366, 0.11574570745426566
    Pirates - Boron - Duke's - Arteus - TerraCorp - Argon, 39.108931122213654, 0.23012646323356176
    Yaki - Pirates - Boron - Duke's - TerraCorp - Argon, 425.0419853760438, 0.021174378789985904
    Yaki - Duke's - Terran - TerraCorp - Argon, 76.60902515260116, 0.13053292324344976
    Paranid - Pirates - Boron - Split - Teladi - TerraCorp - Argon - NMMC, 1320.7954020459683, 0.00529983674167604
    Paranid - Yaki - Pirates - Boron - TerraCorp - Argon, 130.39966404482655, 0.06901858272354242
    Terran - Paranid - TerraCorp - Yaki, 45.81087467240295, 0.24011765936934923
    Terran - Pirates - TerraCorp - Yaki, 53.27692036839961, 0.20646839051388718
    Paranid - OTAS - Boron - Split - TerraCorp - Argon, 105.34024774236256, 0.08543742959492444
    Yaki - OTAS - Boron - Duke's - TerraCorp - Argon, 194.77657826554628, 0.04620678769564357
    OTAS - Boron - Duke's - Split - Terran - TerraCorp - Argon, 43.50844791610121, 0.18387233705570621
    OTAS - Pirates - Boron - Duke's - TerraCorp - Argon, 97.27606641017744, 0.09252018849169236
    Yaki - OTAS - Pirates - Boron - Teladi - TerraCorp - Argon, 113.58932087968562, 0.07042915599850835
    Yaki - OTAS - Terran - Goner - Teladi - TerraCorp, 233.68358058482656, 0.03851361733450084
    Paranid - OTAS - Pirates - Split - Goner - TerraCorp - Argon, 1242.9624162643738, 0.006436236442324115
    Paranid - Yaki - OTAS - Boron - TerraCorp - Argon, 86.24384153096139, 0.10435527731877546
    Paranid - OTAS - Boron - Terran - TerraCorp - Argon, 59.46626634995479, 0.15134631031038057
    OTAS - Pirates - Boron - Terran - TerraCorp - Argon, 80.18274612777459, 0.1122435989615287
    Paranid - Pirates - Boron - Duke's - Split - Goner - Teladi - TerraCorp, 276.8374340355207, 0.025285597753018613
    Paranid - Yaki - Pirates - Duke's - Goner - TerraCorp, 575.6798058640685, 0.01563369065289935
    Paranid - Boron - Split - Terran - Teladi - TerraCorp - Argon, 140.870164845453, 0.05678988172390304
    Pirates - Duke's - Terran - Goner - Teladi - TerraCorp - Argon, 186.1409993909504, 0.04297817260128525
    Paranid - Pirates - Boron - Terran - TerraCorp - Argon, 63.674327492958255, 0.14134424899886552
    Paranid - OTAS - Boron - Arteus - TerraCorp - Argon, 47.34120745133759, 0.19010921952616383
    Yaki - OTAS - Boron - Arteus - TerraCorp - Argon, 35.912367730989395, 0.250610042407027
    OTAS - Boron - Duke's - Arteus - Terran - TerraCorp - Argon, 15.567180562670742, 0.5139016643247247
    OTAS - Pirates - Duke's - Arteus - Goner - TerraCorp - Argon, 96.27606641017742, 0.08309437950982088
    Yaki - OTAS - Pirates - Boron - Arteus - TerraCorp - Argon, 23.92477908154936, 0.33438135302028976
    Yaki - Arteus - Terran - TerraCorp - Argon, 35.951894206478784, 0.2781494611262494
    Paranid - Pirates - Boron - Arteus - TerraCorp - Argon, 53.31421545600065, 0.16881051184983772
    Paranid - Yaki - OTAS - Boron - Arteus - Goner - Teladi - TerraCorp, 116.82127426545519, 0.05992059275174287
    Paranid - Boron - Arteus - Terran - TerraCorp - Argon, 25.550252959426686, 0.3522470017925783
    OTAS - Pirates - Boron - Arteus - Terran - TerraCorp - Argon, 25.118225897924148, 0.31849383123276814
    Paranid - Pirates - Duke's - Arteus - Goner - Teladi - TerraCorp, 215.97676501846755, 0.037041021515976234
    Paranid - Yaki - Duke's - Arteus - Goner - TerraCorp - Argon, 107.7390820187394, 0.07425346355381546
    Paranid - Duke's - Arteus - Terran - TerraCorp - Argon, 56.0114707463656, 0.1606813725844537
    Pirates - Duke's - Arteus - Terran - TerraCorp, 56.304663102078564, 0.17760518310659842
    Yaki - Pirates - Duke's - Arteus - Goner - TerraCorp, 100.11301025716666, 0.08989840558066456
    Yaki - Duke's - Arteus - Terran - TerraCorp, 30.347321491214018, 0.32951837291126806
    Paranid - Pirates - Arteus - Terran - Goner - TerraCorp - Argon, 127.87717260047798, 0.06256003192214854
    Paranid - Yaki - Pirates - Arteus - Goner - Teladi - TerraCorp - Argon, 761.877458625042, 0.009187829250957076
    Paranid - Yaki - Arteus - Terran - TerraCorp, 26.746418104732104, 0.3738818394613652
    Yaki - Pirates - Arteus - Terran - TerraCorp, 37.01394880191841, 0.2701684182229621
    Paranid - OTAS - Pirates - Boron - Duke's - Goner - Teladi - TerraCorp, 171.90147159519046, 0.04072100101902705
    Paranid - Yaki - OTAS - Boron - Duke's - TerraCorp - Argon, 37.550054804530504, 0.21304895669645682
    Paranid - OTAS - Boron - Duke's - Terran - Teladi - TerraCorp, 74.3681226261695, 0.1075729723636303
    OTAS - Pirates - Duke's - Terran - Teladi - TerraCorp, 71.03733232122815, 0.1266939467729776
    Yaki - OTAS - Pirates - Duke's - TerraCorp - Argon, 72.00639492698224, 0.12498889868221301
    Yaki - OTAS - Duke's - Terran - TerraCorp, 35.48019860230642, 0.2818473513096384
    Paranid - OTAS - Pirates - Boron - Terran - Goner - TerraCorp, 214.31415055617265, 0.03732837976045434
    Paranid - Yaki - OTAS - Pirates - Boron - Goner - TerraCorp - NMMC, 580.9691504432174, 0.012048832532088405
    Paranid - Yaki - OTAS - Terran - TerraCorp, 37.72309143055006, 0.26508962072767706
    Yaki - OTAS - Pirates - Terran - TerraCorp, 45.865216548750816, 0.21803014904270326
    Paranid - Pirates - Duke's - Terran - TerraCorp, 70.91294860763149, 0.1410179691628818
    Paranid - Yaki - Duke's - Terran - TerraCorp, 29.256218930488135, 0.3418076691236037
    Yaki - Pirates - Duke's - Terran - TerraCorp, 18.436161459910483, 0.5424122598267023
    Paranid - Yaki - Pirates - Terran - TerraCorp, 25.698876921044207, 0.3891220628326849
    Paranid - OTAS - Duke's - Split - Arteus - TerraCorp - Argon, 51.79329933780341, 0.15446013484915952
    Yaki - OTAS - Duke's - Arteus - Goner - TerraCorp - Argon, 193.77657826554616, 0.04128465922768549
    OTAS - Duke's - Split - Terran - Arteus - TerraCorp - Argon, 42.82964485251255, 0.18678651264909307
    Pirates - Duke's - Split - Arteus - Goner - Teladi - TerraCorp - Argon, 402.6222154097677, 0.01738602524174124
    Yaki - OTAS - Pirates - Split - Goner - TerraCorp - Argon - NMMC, 580.9691504432147, 0.012048832532088459
    Yaki - Split - Terran - TerraCorp - Argon, 114.33660970968555, 0.08746105053657972
    Paranid - Pirates - Split - Arteus - Goner - TerraCorp - Argon, 775.0099358044475, 0.010322448307318967
    Paranid - Yaki - Split - Arteus - Goner - Teladi - TerraCorp - Argon, 236.07209008447452, 0.02965195927013297
    Paranid - Split - Terran - Arteus - TerraCorp - Argon, 67.33144500954062, 0.13366711495237824
    OTAS - Pirates - Split - Terran - TerraCorp - Argon, 110.83865372807796, 0.08119910967233351
    Paranid - Pirates - Duke's - Split - Arteus - TerraCorp, 43.069019496754265, 0.20896691183504307
    Paranid - Yaki - Duke's - Split - Arteus - Goner - TerraCorp, 200.6558434498713, 0.03986926003477489
    Paranid - Duke's - Split - Terran - Arteus - TerraCorp, 61.34177920059709, 0.14671892659925317
    Pirates - Duke's - Split - Terran - Teladi - TerraCorp - Argon, 71.6975699596816, 0.11157979279491227
    Yaki - Pirates - Duke's - Split - Arteus - TerraCorp, 61.90009446264128, 0.14539557779563314
    Yaki - Duke's - Split - Terran - TerraCorp - Argon, 72.4367003944642, 0.12424641032776534
    Paranid - Pirates - Split - Terran - TerraCorp, 88.03751809216017, 0.11358793633336774
    Paranid - Yaki - Pirates - Split - Goner - Teladi - TerraCorp - Argon, 167.70958019567473, 0.041738820118879125
    Paranid - Yaki - Split - Terran - TerraCorp, 28.05718977798867, 0.35641488257121057
    Yaki - Pirates - Split - Terran - TerraCorp, 33.19478610355756, 0.3012521294399387
    OTAS - Pirates - Duke's - Split - Teladi - TerraCorp - Argon, 109.74863585071493, 0.07289384453836822
    Paranid - Yaki - OTAS - Split - Goner - Teladi - TerraCorp - Argon, 345.9349020721801, 0.02023502097669068
    Paranid - OTAS - Split - Terran - Goner - Teladi - TerraCorp, 2458.9869981132847, 0.003253372224472186
    OTAS - Pirates - Duke's - Split - Terran - TerraCorp, 35.17040373080261, 0.2558969771540525
    Yaki - OTAS - Pirates - Duke's - Split - TerraCorp, 61.90009446264127, 0.14539557779563317
    Yaki - OTAS - Split - Terran - TerraCorp, 65.72241857997028, 0.15215508217842158
    Paranid - OTAS - Pirates - Split - Terran - TerraCorp, 46.129275797997224, 0.1951038650468202
    Paranid - Yaki - OTAS - Pirates - Split - Goner - Teladi - TerraCorp, 112.58932087968574, 0.06217285924906041
    Paranid - Yaki - OTAS - Split - Terran - TerraCorp, 18.98977022139546, 0.47393938394577567
    Yaki - OTAS - Pirates - Split - Terran - TerraCorp, 24.160200515363872, 0.3725134646244658
    Paranid - Pirates - Duke's - Split - Terran - TerraCorp, 29.0560624301172, 0.30974603051070393
    Paranid - Yaki - Pirates - Duke's - Split - TerraCorp, 54.63133071686247, 0.16474063292809496
    Paranid - Yaki - Duke's - Split - Terran - TerraCorp, 23.53473971890316, 0.38241340705251897
    Yaki - Pirates - Duke's - Split - Terran - TerraCorp, 16.56887622465858, 0.5431871104574839
    Paranid - Yaki - Pirates - Split - Terran - TerraCorp, 15.293650739583743, 0.5884795038967235
    Paranid - OTAS - Pirates - Duke's - Arteus - Goner - Teladi - TerraCorp, 88.7548406698554, 0.07886893770716297
    Paranid - Yaki - OTAS - Duke's - Arteus - Goner - TerraCorp, 190.9763086336096, 0.041890012731097964
    Paranid - OTAS - Duke's - Arteus - Terran - Goner - TerraCorp, 78.76342750062122, 0.10156998309827112
    OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp, 35.572418186046825, 0.2530050094691123
    Yaki - OTAS - Pirates - Duke's - Arteus - TerraCorp, 46.51016489307401, 0.1935060866950446
    Yaki - OTAS - Arteus - Terran - Goner - TerraCorp, 80.15358516586633, 0.1122844347058936
    Paranid - OTAS - Pirates - Arteus - Terran - Goner - TerraCorp - Argon, 105.04008687724561, 0.06664122439445906
    Paranid - Yaki - OTAS - Pirates - Arteus - Goner - Teladi - TerraCorp - Argon, 277.1187726544716, 0.021651366100271963
    Paranid - Yaki - OTAS - Arteus - Terran - TerraCorp, 26.0087113034173, 0.34603790610792334
    Yaki - OTAS - Pirates - Arteus - Terran - TerraCorp, 35.572418186046825, 0.2530050094691123
    Paranid - Pirates - Duke's - Arteus - Terran - TerraCorp, 22.92625263103994, 0.3925630649212539
    Paranid - Yaki - Pirates - Duke's - Arteus - TerraCorp, 28.726942735151002, 0.3132947380783189
    Paranid - Yaki - Duke's - Arteus - Terran - TerraCorp, 14.413128829780419, 0.6244306913710639
    Yaki - Pirates - Duke's - Arteus - Terran - TerraCorp, 11.753485989552455, 0.7657302699811784
    Paranid - Yaki - Pirates - Arteus - Terran - TerraCorp, 20.11071595179616, 0.44752260543942385
    Paranid - OTAS - Pirates - Duke's - Terran - TerraCorp, 40.293755011545045, 0.22335967440664944
    Paranid - Yaki - OTAS - Pirates - Duke's - TerraCorp, 71.85350298293729, 0.12525485364488337
    Paranid - Yaki - OTAS - Duke's - Terran - TerraCorp, 19.557237551599254, 0.46018769144950344
    Yaki - OTAS - Pirates - Duke's - Terran - TerraCorp, 13.765899862012487, 0.6537894427690728
    Paranid - Yaki - OTAS - Pirates - Terran - TerraCorp, 24.828962065404525, 0.3624799126234989
    Paranid - Yaki - Pirates - Duke's - Terran - TerraCorp, 13.253454692441553, 0.6790682285376282
    Paranid - OTAS - Boron - Split - Arteus - Goner - TerraCorp, 1304.838423523144, 0.006131027302521877
    Yaki - OTAS - Boron - Duke's - Arteus - Goner - TerraCorp, 148.28119500958928, 0.0539515479321747
    OTAS - Boron - Duke's - Split - Arteus - Terran - TerraCorp, 68.18419729634546, 0.11732923928443438
    Pirates - Boron - Duke's - Split - Arteus - Goner - Teladi - TerraCorp, 237.45866809498358, 0.029478814381288437
    Yaki - OTAS - Pirates - Boron - Split - Arteus - Goner - Teladi - TerraCorp, 159.9287188144814, 0.037516713974055205
    Yaki - Boron - Split - Terran - Goner - TerraCorp, 164.35888577732416, 0.05475821983968261
    Paranid - Pirates - Boron - Split - Arteus - TerraCorp, 90.98448592873113, 0.0989179628607208
    Paranid - Yaki - Boron - Split - Arteus - TerraCorp, 61.50680081363495, 0.14632528242315704
    Paranid - Boron - Split - Arteus - Terran - TerraCorp, 43.300752835911915, 0.20784858023382355
    OTAS - Pirates - Boron - Split - Arteus - Terran - TerraCorp, 96.5972443984074, 0.08281809745011626
    Paranid - Pirates - Boron - Duke's - Arteus - TerraCorp, 31.396285805911873, 0.2866581115880055
    Paranid - Yaki - Boron - Duke's - Arteus - TerraCorp, 37.83350315403676, 0.23788439477457474
    Paranid - Boron - Duke's - Arteus - Terran - TerraCorp, 32.10550951389541, 0.2803257178056856
    Pirates - Boron - Duke's - Split - Terran - Teladi - TerraCorp, 83.4817350536814, 0.09582934512388544
    Yaki - Pirates - Boron - Duke's - Arteus - TerraCorp, 30.531591746402714, 0.29477663905486995
    Yaki - Boron - Duke's - Split - Terran - TerraCorp, 84.22086548846401, 0.10686187974680404
    Paranid - Pirates - Boron - Split - Terran - TerraCorp, 41.60313216444501, 0.21632986584821629
    Paranid - Yaki - Pirates - Boron - Split - TerraCorp, 83.48520420436253, 0.10780353340178694
    Paranid - Yaki - Boron - Terran - TerraCorp, 26.219111536220638, 0.38140117700729126
    Yaki - Pirates - Boron - Terran - TerraCorp, 30.633464164056242, 0.32644039036673805
    OTAS - Pirates - Boron - Duke's - Split - Goner - Teladi - TerraCorp, 402.62221540976856, 0.017386025241741203
    Paranid - Yaki - OTAS - Boron - Split - Goner - Teladi - TerraCorp, 171.20962028079143, 0.04088555297605174
    Paranid - OTAS - Boron - Split - Terran - TerraCorp, 63.21639818998944, 0.14236812374143112
    OTAS - Pirates - Boron - Duke's - Terran - TerraCorp, 43.35277100196088, 0.20759918667235647
    Yaki - OTAS - Pirates - Boron - Duke's - TerraCorp, 62.12188525943843, 0.14487647891581967
    Yaki - OTAS - Boron - Terran - TerraCorp, 46.02410113982884, 0.2172774644662444
    Paranid - OTAS - Pirates - Boron - Split - Goner - TerraCorp, 309.2876622179953, 0.025865887900699245
    Paranid - Yaki - OTAS - Pirates - Boron - Split - TerraCorp, 31.851571178620993, 0.2511650039219936
    Paranid - Yaki - OTAS - Boron - Terran - TerraCorp, 20.015433557100874, 0.4496530127276244
    Yaki - OTAS - Pirates - Boron - Terran - TerraCorp, 24.347161149480165, 0.36965295233987305
    Paranid - Pirates - Boron - Duke's - Terran - TerraCorp, 38.03632461486069, 0.23661592152054892
    Paranid - Yaki - Pirates - Boron - Duke's - TerraCorp, 64.34162302960887, 0.1398783489788307
    Paranid - Yaki - Boron - Duke's - Terran - TerraCorp, 21.37768927524567, 0.42099966390762183
    Yaki - Pirates - Boron - Duke's - Terran - TerraCorp, 15.763378546074048, 0.5709435939569882
    Paranid - Yaki - Pirates - Boron - Terran - TerraCorp, 16.95290718767852, 0.5308823967691664
    Paranid - OTAS - Boron - Duke's - Arteus - Teladi - TerraCorp, 89.02789410563415, 0.08985947696918194
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus, 28.711924362929466, 0.31345861344006876
    Paranid - OTAS - Boron - Arteus - Terran - TerraCorp, 94.70863790668979, 0.09502829096610078
    OTAS - Pirates - Boron - Duke's - Arteus - TerraCorp, 66.06655258590867, 0.13622626953778136
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - TerraCorp, 18.513299689944397, 0.4321217791523812
    Yaki - OTAS - Boron - Arteus - Terran - TerraCorp, 25.641020746401875, 0.3510000670025175
    Paranid - Pirates - Boron - Arteus - Terran - TerraCorp, 47.759271371234206, 0.18844508598221146
    Paranid - Yaki - Pirates - Boron - Arteus - TerraCorp, 54.943870411888035, 0.16380353135902667
    Paranid - Yaki - Boron - Arteus - Terran - TerraCorp, 14.139120380305544, 0.6365318179577951
    Yaki - Pirates - Boron - Arteus - Terran - TerraCorp, 19.625529727620876, 0.4585863477271364
    Pirates - Boron - Duke's - Terran - Arteus - TerraCorp, 27.046553523089074, 0.3327595877351578
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - TerraCorp, 14.461496904155782, 0.5531930790443311
    Yaki - Boron - Duke's - Arteus - Terran - TerraCorp, 19.14724440973225, 0.4700415269899328
    Yaki - Pirates - Boron - Duke's - Arteus - Terran - TerraCorp, 9.165109091629207, 0.8728755893704158
    Paranid - Yaki - Pirates - Boron - Arteus - Terran - TerraCorp, 11.764319968227088, 0.68002230656819
    Paranid - OTAS - Pirates - Boron - Duke's - Terran - TerraCorp, 22.65461094010965, 0.35312899529146713
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - TerraCorp, 27.760443336799618, 0.2881798357087148
    Yaki - OTAS - Boron - Duke's - Terran - TerraCorp, 22.526040445358646, 0.39953759391630655
    Yaki - OTAS - Pirates - Boron - Duke's - Terran - TerraCorp, 11.000763267866008, 0.7272222667829381
    Paranid - Yaki - OTAS - Pirates - Boron - Terran - TerraCorp, 15.391578798459186, 0.519764743094507
    Paranid - Yaki - Pirates - Boron - Duke's - Terran - TerraCorp, 11.131997975725374, 0.71864907067401
    OTAS - Pirates - Duke's - Split - Arteus - Goner - Teladi - TerraCorp, 126.14106779931934, 0.05549342590897088
    Paranid - Yaki - OTAS - Split - Arteus - Goner - TerraCorp - NMMC, 10334.015564202233, 0.0006773746329789263
    Paranid - OTAS - Split - Terran - Arteus - Goner - TerraCorp, 121.76154635302761, 0.0657021879206865
    Pirates - Duke's - Split - Terran - Arteus - TerraCorp, 38.62364901551519, 0.2330178589906066
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - TerraCorp, 26.500793147987167, 0.301877757217528
    Yaki - OTAS - Split - Terran - Arteus - TerraCorp, 42.74250205648109, 0.21056324658081924
    Paranid - Pirates - Split - Arteus - Terran - TerraCorp, 41.80233848811217, 0.2152989599507558
    Paranid - Yaki - Pirates - Split - Arteus - Goner - TerraCorp, 79.03893674481684, 0.10121593646721998
    Paranid - Yaki - Split - Terran - Arteus - TerraCorp, 17.653142643714826, 0.509824238190492
    Yaki - Pirates - Split - Arteus - Terran - TerraCorp, 25.008960117943097, 0.3598710205284705
    Paranid - Pirates - Duke's - Split - Arteus - Terran - TerraCorp, 14.907391445034145, 0.5366465373568029
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - TerraCorp, 18.418867119202794, 0.4343372449687479
    Yaki - Duke's - Split - Terran - Arteus - TerraCorp, 29.66530818912322, 0.30338467891932597
    Yaki - Pirates - Duke's - Split - Arteus - Terran - TerraCorp, 10.900461693377615, 0.7339138675988615
    Paranid - Yaki - Pirates - Split - Arteus - Terran - TerraCorp, 12.41091600819121, 0.6445938393846189
    Paranid - OTAS - Pirates - Duke's - Split - TerraCorp, 58.7378801862051, 0.15322309847527826
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - TerraCorp, 21.821184159694187, 0.3666162175917458
    Paranid - OTAS - Duke's - Split - Terran - Goner - TerraCorp, 80.24363884399297, 0.09969637612712623
    Yaki - OTAS - Duke's - Split - Terran - TerraCorp, 27.548141524211225, 0.32670080455664036
    Paranid - Yaki - OTAS - Pirates - Split - Terran - TerraCorp, 13.035172302368231, 0.6137241468259349
    Paranid - Yaki - Pirates - Duke's - Split - Terran - TerraCorp, 10.700837644093166, 0.7476050255202198
    Paranid - OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp, 20.075925012269867, 0.3984872425609587
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - TerraCorp, 23.803599643262444, 0.33608362264084635
    Yaki - OTAS - Duke's - Arteus - Terran - TerraCorp, 19.763092431831218, 0.4553943180220239
    Yaki - OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp, 10.200751130733561, 0.784255972670191
    Paranid - Yaki - OTAS - Pirates - Arteus - Terran - TerraCorp, 20.07592501226987, 0.39848724256095863
    Paranid - Yaki - Pirates - Duke's - Arteus - Terran - TerraCorp, 8.903456559720151, 0.8985274366578649
    Paranid - Yaki - OTAS - Pirates - Duke's - Terran - TerraCorp, 11.206460677795173, 0.7138739188057338
    Paranid - OTAS - Boron - Duke's - Split - Arteus - Argon, 21.666752976072207, 0.3692292984017883
    Yaki - OTAS - Boron - Duke's - Split - Arteus - Argon, 27.373346145540395, 0.29225509944838596
    OTAS - Boron - Duke's - Split - Arteus - Terran - Argon, 69.11703402185364, 0.11574570745426568
    OTAS - Pirates - Boron - Duke's - Split - Argon, 68.48801124548599, 0.13140986044609648
    Yaki - OTAS - Pirates - Boron - Split - Arteus - Argon, 21.536285874313148, 0.3714660943251034
    Yaki - Boron - Split - Arteus - Terran - Argon, 70.14215962460077, 0.12831084825685143
    Paranid - Pirates - Boron - Split - Arteus - Argon, 50.20596394904899, 0.1792615715761091
    Paranid - Yaki - Boron - Split - Arteus - Argon, 45.78143026834367, 0.1965862566382772
    Paranid - Boron - Split - Arteus - Terran - Argon, 129.93046386977025, 0.06926782012431458
    OTAS - Pirates - Boron - Split - Arteus - Terran - Argon, 31.535950501638784, 0.25367873403987856
    Paranid - Pirates - Boron - Duke's - Arteus - Argon, 37.65552343900061, 0.23900876094789622
    Paranid - Yaki - Boron - Duke's - Arteus - Argon, 44.24720749605653, 0.20340266672878987
    Paranid - Boron - Split - Arteus - Terran - Teladi - Argon, 77.92001897435368, 0.1026693795163614
    Pirates - Boron - Duke's - Terran - Arteus - Teladi - Argon, 63.12464340574939, 0.1267333891865021
    Yaki - Pirates - Boron - Duke's - Arteus - Argon, 36.23622561496175, 0.2483702385461456
    Yaki - Duke's - Split - Terran - Arteus - Argon, 183.57230738905284, 0.04902700264548021
    Paranid - Pirates - Boron - Split - Terran - Argon, 67.48988463444779, 0.13335331729706756
    Paranid - Yaki - Pirates - Boron - Split - Argon, 60.60753934105459, 0.14849637681798347
    Paranid - Yaki - Boron - Terran - Argon, 39.672859167067806, 0.2520614901459116
    Yaki - Pirates - Boron - Terran - Argon, 36.12296883391085, 0.2768321741764587
    Paranid - OTAS - Pirates - Boron - Split - Argon, 37.12309544928854, 0.24243667967544133
    Paranid - Yaki - OTAS - Boron - Split - Argon, 33.464559414394465, 0.26894123686352
    Paranid - OTAS - Boron - Split - Terran - Argon, 40.969100301710945, 0.2196777555211322
    OTAS - Pirates - Boron - Duke's - Terran - Argon, 43.91083154811542, 0.20496081906666297
    Yaki - OTAS - Pirates - Boron - Duke's - Argon, 30.291861055328315, 0.29710951016054876
    Yaki - OTAS - Boron - Terran - Argon, 29.984332111635922, 0.33350751194885986
    Paranid - OTAS - Pirates - Boron - Split - Terran - Argon, 18.13420970814092, 0.4411551497834831
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Argon, 17.09725763639197, 0.467911297246395
    Paranid - Yaki - OTAS - Boron - Terran - Argon, 16.54228109014394, 0.5440603959608866
    Yaki - OTAS - Pirates - Boron - Terran - Argon, 17.610075901795117, 0.5110710510386027
    Paranid - Pirates - Boron - Duke's - Terran - Teladi - Argon, 63.76668147742279, 0.12545736761967888
    Paranid - Yaki - Pirates - Boron - Duke's - Argon, 69.32495077033002, 0.129823388260549
    Paranid - Yaki - Boron - Duke's - Terran - Argon, 38.79883251983331, 0.2319657426650493
    Yaki - Pirates - Boron - Duke's - Terran - Argon, 24.734434547314976, 0.3638652010735773
    Paranid - Yaki - Pirates - Boron - Terran - Argon, 17.769997914162936, 0.5064716407663096
    Paranid - OTAS - Pirates - Boron - Duke's - Argon, 66.18071825652618, 0.13599127112997897
    Paranid - Yaki - OTAS - Boron - Arteus - Argon, 23.075892611734165, 0.3900174156393617
    Paranid - OTAS - Boron - Arteus - Terran - Argon, 37.073273128138226, 0.24276248738256387
    OTAS - Pirates - Boron - Duke's - Arteus - Terran - Argon, 18.308262113185833, 0.4369611900103999
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - Argon, 12.887402229835251, 0.6207612564058436
    Yaki - OTAS - Boron - Arteus - Terran - Argon, 17.327993008561766, 0.5193907912793535
    Paranid - OTAS - Pirates - Boron - Arteus - Terran - Argon, 23.798532517312346, 0.336155180752442
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - Argon, 17.64075432941385, 0.4534953466621865
    Paranid - Yaki - Boron - Arteus - Terran - Argon, 15.592957205508146, 0.577183652939212
    Yaki - Pirates - Boron - Arteus - Terran - Argon, 19.59933041990946, 0.459199360752528
    Paranid - Pirates - Boron - Duke's - Arteus - Terran - Argon, 20.1637282148957, 0.39675202495985346
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Argon, 14.910712321370593, 0.5365270167900764
    Paranid - Yaki - Boron - Duke's - Arteus - Terran - Argon, 14.131588883953315, 0.5661076093916199
    Yaki - Pirates - Boron - Duke's - Arteus - Terran - Argon, 13.209941471756029, 0.605604499997572
    Paranid - Yaki - Pirates - Boron - Arteus - Terran - Argon, 11.202973090052312, 0.7140961542702986
    Paranid - OTAS - Pirates - Boron - Duke's - Terran - Argon, 22.952500006305417, 0.34854590993583584
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Argon, 19.432085219220046, 0.4116902488718655
    Yaki - OTAS - Boron - Duke's - Terran - Argon, 22.87334540740605, 0.39347108346844334
    Yaki - OTAS - Pirates - Boron - Duke's - Terran - Argon, 11.171872400477934, 0.7160840827055776
    Paranid - Yaki - OTAS - Pirates - Boron - Terran - Argon, 12.683372821924793, 0.6307470506718056
    Paranid - Yaki - Pirates - Boron - Duke's - Terran - Argon, 14.232655286145969, 0.5620876666483435
    Paranid - OTAS - Pirates - Split - Arteus - Argon, 98.28873103232603, 0.09156695691838776
    Paranid - Yaki - OTAS - Split - Arteus - Argon, 57.504545009405625, 0.1565093680600017
    Paranid - OTAS - Split - Terran - Arteus - Argon, 67.33144500954063, 0.1336671149523782
    OTAS - Pirates - Duke's - Split - Arteus - Terran - Argon, 24.099624706059807, 0.3319553767983953
    Yaki - Pirates - Duke's - Split - Arteus - Argon, 89.11560673582622, 0.10099241120222126
    Yaki - OTAS - Split - Terran - Arteus - Argon, 30.90976193340452, 0.2911701493978056
    Paranid - Pirates - Split - Arteus - Terran - Argon, 47.56956212534023, 0.1891966122430569
    Paranid - Yaki - Pirates - Split - Arteus - Argon, 44.20053489146589, 0.20361744540194904
    Paranid - Yaki - Split - Terran - Arteus - Argon, 21.69513805138546, 0.41483948978260854
    Yaki - Pirates - Split - Arteus - Terran - Argon, 27.218373265583693, 0.33065899685416034
    Paranid - Pirates - Duke's - Split - Arteus - Terran - Argon, 23.184751451392444, 0.34505437838194
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Argon, 20.05686243230672, 0.39886597552336744
    Paranid - Yaki - Duke's - Split - Arteus - Terran - Argon, 19.030280255906682, 0.4203826686954299
    Yaki - Pirates - Duke's - Split - Arteus - Terran - Argon, 15.920171045295998, 0.5025071638513453
    Paranid - Yaki - Pirates - Split - Arteus - Terran - Argon, 12.892675276216536, 0.6205073678352712
    Paranid - OTAS - Pirates - Duke's - Split - Terran - Argon, 17.502071972667398, 0.4570887385501228
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Argon, 17.904147546256873, 0.4468238423153812
    Paranid - Yaki - OTAS - Duke's - Split - Terran - Argon, 14.714439993073897, 0.5436836198839785
    Yaki - OTAS - Pirates - Duke's - Split - Terran - Argon, 11.513765502158211, 0.6948204736756564
    Paranid - Yaki - OTAS - Pirates - Split - Terran - Argon, 11.769090242069588, 0.6797466784138793
    Paranid - Yaki - Pirates - Duke's - Split - Terran - Argon, 13.713147938124347, 0.5833817323416276
    Paranid - OTAS - Pirates - Duke's - Arteus - Terran - Argon, 22.57582979215228, 0.35436128255985205
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - Argon, 19.063365415614086, 0.41965307937954655
    Yaki - OTAS - Duke's - Arteus - Terran - Argon, 22.520065653478003, 0.399643595115809
    Yaki - OTAS - Pirates - Duke's - Arteus - Terran - Argon, 10.980174392763338, 0.7285858779504021
    Paranid - Yaki - OTAS - Pirates - Arteus - Terran - Argon, 16.748070060901902, 0.4776669772044882
    Paranid - Yaki - Pirates - Duke's - Arteus - Terran - Argon, 10.888188256369592, 0.7347411535909106
    Paranid - Yaki - OTAS - Pirates - Duke's - Terran - Argon, 11.775473209833336, 0.6793782175411385
    Paranid - OTAS - Pirates - Boron - Split - Arteus, 52.541542209223806, 0.1712930306491846
    Paranid - Yaki - OTAS - Boron - Split - Arteus, 35.04002572568708, 0.25684912649485575
    Paranid - OTAS - Boron - Split - Arteus - Terran, 43.300752835911915, 0.20784858023382355
    OTAS - Pirates - Boron - Duke's - Split - Arteus - Terran, 23.768292654651642, 0.3365828634070751
    Yaki - Pirates - Boron - Duke's - Split - Arteus, 59.01694616921981, 0.15249857175249668
    Yaki - OTAS - Boron - Split - Arteus - Terran, 32.29478541130335, 0.2786827621046818
    Paranid - Pirates - Boron - Split - Arteus - Terran, 31.892443297610814, 0.2821985106633152
    Paranid - Yaki - Pirates - Boron - Split - Arteus, 27.605205538743622, 0.3260254660074381
    Paranid - Yaki - Boron - Split - Arteus - Terran, 16.91065290731817, 0.5322089010593556
    Yaki - Pirates - Boron - Split - Arteus - Terran, 24.849788308003177, 0.3621761235326677
    Paranid - Pirates - Boron - Duke's - Split - Arteus - Terran, 18.24038006845502, 0.4385873523455374
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Arteus, 15.179600398242293, 0.5270230961367305
    Paranid - Yaki - Boron - Duke's - Split - Arteus - Terran, 15.151763274177908, 0.5279913535630432
    Yaki - Pirates - Boron - Duke's - Split - Arteus - Terran, 14.539176278640191, 0.550237499476017
    Paranid - Yaki - Pirates - Boron - Split - Arteus - Terran, 10.911168375522676, 0.7331937080126653
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Terran, 15.98494018614474, 0.500471062565136
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Split, 15.920913099028137, 0.5024837426245574
    Yaki - OTAS - Boron - Duke's - Split - Terran, 33.555600601660075, 0.26821156047359646
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Terran, 11.513765502158211, 0.6948204736756564
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Terran, 10.837534827758894, 0.7381752517656572
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Terran, 12.671204728228473, 0.6313527538686101
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - Terran, 16.171896949790035, 0.49468531891083234
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Arteus, 13.341640750557545, 0.5996263989993645
    Yaki - OTAS - Boron - Duke's - Arteus - Terran, 20.400871126732653, 0.44115763214673154
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - Terran, 9.87612035224877, 0.8100346810960457
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - Terran, 12.79825131036323, 0.6250853969027859
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Terran, 9.053100960596671, 0.8836751114142812
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Terran, 10.324358432058855, 0.7748665500762416
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - Terran, 14.907391445034142, 0.536646537356803
    Paranid - Yaki - OTAS - Duke's - Split - Arteus, 52.68017044383469, 0.17084227184867234
    Yaki - OTAS - Duke's - Split - Arteus - Terran, 29.665308189123216, 0.303384678919326
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - Terran, 10.900461693377615, 0.7339138675988615
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - Terran, 12.41091600819121, 0.6445938393846189
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Terran, 9.742097981553101, 0.8211783555398636
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Terran, 9.1177347734113, 0.8774109138740486
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - Terran, 9.773558722800223, 0.8185350113400577
    OTAS - Boron - Strong Arms - Split - Arteus - TerraCorp - Argon, 120.56313496934486, 0.06635527520111459
    Yaki - Boron - Strong Arms - Split - Arteus - Teladi - TerraCorp - Argon, 159.24396782841825, 0.0439577090137715
    Boron - Strong Arms - Arteus - Terran - Teladi - TerraCorp - Argon, 278.39523887167763, 0.028736123622026048
    OTAS - Pirates - Boron - Split - Strong Arms - TerraCorp - Argon, 108.15209690249021, 0.07396990191704549
    Yaki - Pirates - Boron - Strong Arms - Arteus - Argon, 87.19168042939714, 0.10322085726157885
    Yaki - Strong Arms - Terran - TerraCorp - Argon, 66.87751474296417, 0.14952708751863492
    Paranid - Boron - Strong Arms - Arteus - TerraCorp - Argon, 167.62107329364713, 0.05369253294443081
    Paranid - Yaki - Boron - Strong Arms - Split - TerraCorp - Argon, 52.64521118838207, 0.1519606402826145
    Paranid - Boron - Strong Arms - Split - Terran - TerraCorp - Argon, 79.56783299087787, 0.10054314286675581
    Pirates - Boron - Split - Terran - Strong Arms - TerraCorp - Argon, 185.62309783892957, 0.04309808473804175
    Paranid - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 35.74625792569027, 0.22379964964809718
    Yaki - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 43.85501026310879, 0.18241929375922797
    Boron - Duke's - Strong Arms - Terran - Arteus - TerraCorp - Argon, 65.30040636845735, 0.12251072305522916
    Pirates - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 29.491046749188797, 0.2712687707573504
    Yaki - Pirates - Duke's - Strong Arms - TerraCorp - Argon, 67.97255297359304, 0.1324063847285014
    Yaki - Duke's - Strong Arms - Terran - TerraCorp, 62.23166567573138, 0.16068989784246965
    Paranid - Pirates - Boron - Split - Strong Arms - Goner - TerraCorp, 616.6002936353068, 0.012974369429560578
    Paranid - Yaki - Pirates - Boron - Strong Arms - Goner - Teladi - TerraCorp, 158.14414324668957, 0.04426341599689011
    Strong Arms - Paranid - Terran - Yaki, 40.52498529967644, 0.271437482793802
    Strong Arms - Pirates - Terran - Yaki, 52.148737618505336, 0.21093511563924366
    Paranid - OTAS - Boron - Strong Arms - Split - Argon, 91.21586932119536, 0.09866704189715722
    Yaki - OTAS - Boron - Strong Arms - Split - TerraCorp - Argon, 55.65057419677589, 0.14375413219839658
    OTAS - Boron - Strong Arms - Split - Terran - TerraCorp - Argon, 81.50242391501979, 0.09815658989898715
    OTAS - Pirates - Boron - Duke's - Strong Arms - TerraCorp - Argon, 48.98857367958398, 0.16330338687394783
    Yaki - OTAS - Pirates - Boron - Strong Arms - Argon, 79.6790739165055, 0.11295312003037289
    Yaki - OTAS - Strong Arms - Terran - Goner - Teladi - TerraCorp, 113.54541732788952, 0.07045638818604266
    Paranid - OTAS - Pirates - Strong Arms - Split - Goner - TerraCorp, 3388.4251261137597, 0.002360978833011822
    Paranid - Yaki - OTAS - Boron - Strong Arms - Argon, 53.17952460621551, 0.16923806797152338
    Paranid - OTAS - Boron - Strong Arms - Terran - Argon, 1210.3156690210153, 0.00743607657932728
    OTAS - Pirates - Boron - Terran - Strong Arms - TerraCorp - Argon, 75.50686433814674, 0.10595063204019622
    Paranid - Pirates - Boron - Duke's - Strong Arms - TerraCorp - Argon, 92.51410376546632, 0.08647330163064544
    Paranid - Yaki - Duke's - Strong Arms - Split - TerraCorp - Argon, 94.80819459497872, 0.0843808916958714
    Paranid - Boron - Duke's - Strong Arms - Terran - Teladi - TerraCorp - Argon, 122.25510204081633, 0.0572573240964861
    Pirates - Duke's - Strong Arms - Terran - Teladi - TerraCorp - Argon, 67.23342253881044, 0.11898843905175295
    Paranid - Pirates - Boron - Terran - Strong Arms - Goner - TerraCorp, 420.09949682747424, 0.019043107788547117
    OTAS - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 35.74625792569028, 0.22379964964809712
    Yaki - OTAS - Boron - Strong Arms - Arteus - Argon, 69.8468256947587, 0.12885338611279737
    OTAS - Boron - Strong Arms - Arteus - Terran - TerraCorp - Argon, 38.75779670014945, 0.2064100821285631
    OTAS - Pirates - Boron - Arteus - Strong Arms - TerraCorp - Argon, 155.08427678347275, 0.05158485544714199
    Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - Argon, 28.57243787008961, 0.27999010922251805
    Yaki - Strong Arms - Terran - Arteus - Goner - TerraCorp, 81.90404938392737, 0.1098846768590435
    Paranid - OTAS - Boron - Strong Arms - Arteus - Argon, 167.88138903416151, 0.05360927766786958
    Paranid - Yaki - Boron - Strong Arms - Arteus - TerraCorp, 85.091502145731, 0.10576849359864693
    Paranid - Strong Arms - Terran - Arteus - Goner - Teladi - TerraCorp - Argon, 92579.0719697068, 7.561104093040057e-05
    Pirates - Boron - Arteus - Terran - Strong Arms - TerraCorp - Argon, 43.328202442399785, 0.1846372466209542
    Paranid - Pirates - Boron - Arteus - Strong Arms - Argon, 164.04634624323967, 0.054862544677802536
    Paranid - Yaki - Duke's - Strong Arms - Arteus - TerraCorp, 65.50783743410092, 0.13738814090838752
    Paranid - Duke's - Strong Arms - Terran - Arteus - Teladi - TerraCorp, 64.7687069993184, 0.12351643827140457
    Pirates - Duke's - Strong Arms - Terran - Arteus - TerraCorp, 43.99933092641141, 0.204548564955509
    Yaki - Pirates - Duke's - Strong Arms - Arteus, 51.8320209835895, 0.19293092976571555
    Yaki - Duke's - Strong Arms - Terran - Arteus - TerraCorp, 22.99762293542569, 0.391344793558483
    Paranid - Pirates - Strong Arms - Arteus - Terran - Goner - Teladi - Argon, 401.99484817734793, 0.017413158481354
    Paranid - Yaki - Pirates - Strong Arms - Arteus - Argon, 81.06627972334456, 0.11102026675843964
    Paranid - Yaki - Strong Arms - Terran - Arteus, 26.398377581210884, 0.3788111587250546
    Yaki - Pirates - Strong Arms - Arteus - Terran, 39.64897073960639, 0.2522133567016089
    Paranid - OTAS - Pirates - Duke's - Strong Arms - TerraCorp - Argon, 91.57339998164538, 0.08736161376123949
    Yaki - OTAS - Boron - Duke's - Strong Arms - TerraCorp - Argon, 50.07372899694635, 0.15976441459927748
    OTAS - Boron - Duke's - Strong Arms - Terran - TerraCorp - Argon, 77.87320882877293, 0.10273109481837771
    OTAS - Pirates - Duke's - Strong Arms - Terran - Goner - Teladi, 160.2110334859067, 0.04993413890375869
    Yaki - OTAS - Pirates - Duke's - Strong Arms - TerraCorp, 46.59709570869031, 0.1931450847551752
    Yaki - OTAS - Duke's - Strong Arms - Terran, 43.522461168046306, 0.22976641788221955
    Paranid - OTAS - Pirates - Strong Arms - Terran - Goner - TerraCorp - Argon, 6905.213018650576, 0.0010137268728847915
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Goner - Teladi - TerraCorp - Argon, 277.1187726544715, 0.021651366100271973
    Paranid - Yaki - OTAS - Strong Arms - Terran, 31.47747705642845, 0.31768746847383567
    Yaki - OTAS - Pirates - Strong Arms - Terran, 41.693105405861964, 0.23984780943167694
    Paranid - Pirates - Duke's - Strong Arms - Terran - Teladi, 62.41905129365092, 0.1441867476911725
    Paranid - Yaki - Pirates - Duke's - Strong Arms - TerraCorp, 29.265278181090537, 0.3075316743722347
    Paranid - Yaki - Duke's - Strong Arms - Terran, 29.216027227767203, 0.34227788473909626
    Yaki - Pirates - Duke's - Strong Arms - Terran, 18.787013941371452, 0.5322825666285741
    Paranid - Yaki - Pirates - Strong Arms - Terran, 20.982970617950155, 0.47657694337356454
    Paranid - OTAS - Strong Arms - Split - Arteus - Goner - TerraCorp - Argon, 119.56313496934482, 0.058546474227149974
    Yaki - OTAS - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 49.289461935749394, 0.16230649891103074
    OTAS - Strong Arms - Split - Terran - Arteus - Goner - Teladi - TerraCorp - Argon, 1231.6195372750349, 0.004871634314339503
    Pirates - Duke's - Strong Arms - Split - Arteus - TerraCorp - Argon, 64.47476349713095, 0.12407955556682251
    Yaki - Pirates - Strong Arms - Split - Arteus - Teladi - TerraCorp - Argon, 96.4475674940507, 0.07257829494177538
    Yaki - Strong Arms - Split - Terran - TerraCorp - Argon, 48.51211304107407, 0.1855206758852147
    Paranid - Pirates - Strong Arms - Split - Arteus - Goner - TerraCorp, 3388.425126113804, 0.002360978833011791
    Paranid - Yaki - Strong Arms - Split - Arteus - Goner - TerraCorp, 97.2796978980502, 0.0822370974916478
    Paranid - Strong Arms - Split - Terran - Arteus - Goner - TerraCorp, 179.25462670496924, 0.044629252516684
    Pirates - Strong Arms - Split - Arteus - Terran - Goner - TerraCorp - Argon, 164.16186454967624, 0.04264084121608989
    Paranid - Pirates - Duke's - Strong Arms - Split - TerraCorp, 44.323233011655624, 0.20305377989085954
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - TerraCorp, 27.497426430656095, 0.2909363179923278
    Paranid - Duke's - Strong Arms - Split - Terran - Teladi - TerraCorp - Argon, 94.06906416019615, 0.07441341170439687
    Pirates - Duke's - Strong Arms - Split - Terran - Teladi - TerraCorp, 53.89220028207984, 0.14844448655142678
    Yaki - Pirates - Duke's - Strong Arms - Split - TerraCorp, 54.63133071686246, 0.16474063292809502
    Yaki - Duke's - Strong Arms - Split - Terran - TerraCorp, 54.631330716862436, 0.16474063292809507
    Paranid - Pirates - Strong Arms - Split - Terran, 68.3677049816087, 0.14626789070497623
    Paranid - Yaki - Pirates - Strong Arms - Split - TerraCorp, 31.76072567007509, 0.28336884029321113
    Paranid - Yaki - Strong Arms - Split - Terran, 23.269150650353247, 0.42975354581101527
    Yaki - Pirates - Strong Arms - Split - Terran, 31.100315106737327, 0.32154015049942947
    Paranid - OTAS - Duke's - Strong Arms - Split - TerraCorp - Argon, 91.57339998164534, 0.08736161376123953
    Paranid - Yaki - OTAS - Strong Arms - Split - Goner - TerraCorp, 97.2796978980503, 0.08223709749164772
    OTAS - Duke's - Strong Arms - Split - Terran - Teladi - TerraCorp - Argon, 95.83018385147369, 0.07304587885221252
    OTAS - Pirates - Duke's - Strong Arms - Split - Goner - Teladi - TerraCorp, 120.92514310876248, 0.05788705160930891
    Yaki - OTAS - Pirates - Strong Arms - Split - TerraCorp - Argon, 48.72444591793778, 0.1641886295325694
    Yaki - OTAS - Strong Arms - Split - Terran, 70.91924007659895, 0.14100545901505895
    Paranid - OTAS - Strong Arms - Split - Terran - Goner - TerraCorp, 179.25462670496938, 0.04462925251668397
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split, 23.38980369002638, 0.3847830498824443
    Paranid - Yaki - OTAS - Strong Arms - Split - Terran, 14.252446814257421, 0.6314705199248215
    OTAS - Pirates - Strong Arms - Split - Terran - Goner - Argon, 957.9506538966936, 0.00835116085307535
    Paranid - Pirates - Duke's - Strong Arms - Split - Terran, 27.538792443078528, 0.3268117154592963
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split, 15.388638292238706, 0.5848470689274158
    Paranid - Yaki - Duke's - Strong Arms - Split - Terran, 21.26741147289407, 0.42318267135945337
    Yaki - Pirates - Duke's - Strong Arms - Split - Terran, 16.388046485663594, 0.5491807707449011
    Paranid - Yaki - Pirates - Strong Arms - Split - Terran, 11.205135857440165, 0.803203112796177
    OTAS - Pirates - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 48.236515330617955, 0.1658494595881811
    Paranid - Yaki - OTAS - Strong Arms - Arteus - Goner - Teladi - TerraCorp - Argon, 244.68126888217486, 0.024521697257051875
    OTAS - Duke's - Strong Arms - Terran - Arteus - TerraCorp - Argon, 76.92167761042226, 0.10400189190512486
    OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran, 71.43717144142761, 0.12598483140362343
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus, 27.373241754177403, 0.32878824075071483
    Yaki - OTAS - Strong Arms - Terran - Arteus - Goner - Teladi, 130.85048253961835, 0.06113848298249717
    Paranid - OTAS - Strong Arms - Terran - Arteus - Goner - TerraCorp - Argon, 2075.381414955135, 0.0033728739929721903
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Arteus - Argon, 68.19458160310636, 0.11731137301435675
    Paranid - Yaki - OTAS - Strong Arms - Arteus - Terran, 24.49125835921166, 0.3674780555575217
    Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran, 35.62167067495695, 0.25265519077203913
    Paranid - Pirates - Duke's - Strong Arms - Arteus - TerraCorp, 65.45170384276743, 0.13750596961723743
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus, 17.053042160399965, 0.5277650706159348
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Terran, 16.406877628729653, 0.5485504435189018
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran, 13.433872796600099, 0.6699482819487287
    Paranid - Yaki - Strong Arms - Terran - Argon, 34.05451966728139, 0.2936467786861112
    Paranid - OTAS - Duke's - Strong Arms - Terran - Teladi - TerraCorp - Argon, 62.74918432639616, 0.11155523494279702
    Paranid - Yaki - OTAS - Duke's - Strong Arms - TerraCorp - Argon, 63.488314761178735, 0.12600743979570503
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Terran, 17.238586078782877, 0.5220845815816143
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran, 12.416476031329726, 0.7248433434165102
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Terran, 20.335801814409862, 0.44256922260240744
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Terran, 11.051814703255834, 0.8143459008002211
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - Goner - TerraCorp, 119.56313496934479, 0.05854647422714999
    Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - TerraCorp, 65.05048717725494, 0.12298140024994647
    OTAS - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi - TerraCorp, 64.31135674247233, 0.10884547231728793
    Pirates - Boron - Duke's - Split - Strong Arms - Arteus - TerraCorp, 91.5733999816454, 0.08736161376123949
    Yaki - Pirates - Boron - Strong Arms - Split - Arteus - Goner - Teladi - TerraCorp, 277.11877265447214, 0.021651366100271924
    Yaki - Boron - Strong Arms - Terran - TerraCorp, 93.56260835699837, 0.1068803037410405
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus, 64.75344608664719, 0.13898874181857468
    Paranid - Yaki - Boron - Strong Arms - Split - Arteus, 39.98989752849885, 0.2250568407579974
    Paranid - Boron - Strong Arms - Arteus - Terran - Goner - TerraCorp, 141.57538564778417, 0.05650699776232755
    Pirates - Boron - Split - Arteus - Strong Arms - Terran - Goner - TerraCorp, 6905.213018650425, 0.0010137268728848136
    Paranid - Boron - Duke's - Strong Arms - Split - Arteus - TerraCorp, 91.57339998164538, 0.08736161376123949
    Paranid - Yaki - Boron - Duke's - Strong Arms - Arteus, 37.947610021274826, 0.23716908640502707
    Paranid - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi, 182.7167379354338, 0.043783618788263076
    Pirates - Boron - Duke's - Terran - Strong Arms - Teladi - TerraCorp, 79.6427223769052, 0.10044860046521766
    Yaki - Pirates - Boron - Duke's - Strong Arms - TerraCorp, 80.38185281168782, 0.11196557040162386
    Yaki - Boron - Duke's - Strong Arms - Terran - TerraCorp, 45.18006958912561, 0.19920288042597903
    Paranid - Pirates - Boron - Split - Strong Arms - Terran, 44.89752925011662, 0.200456464984131
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split, 24.007970656918506, 0.3748754998334864
    Paranid - Yaki - Boron - Strong Arms - Terran, 28.370622025303685, 0.3524772911598845
    Yaki - Pirates - Boron - Strong Arms - Terran, 35.60873715511378, 0.28082995351504336
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - TerraCorp, 64.37742994838072, 0.12426715397639485
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split, 35.41772782861217, 0.2541100333581919
    Paranid - OTAS - Boron - Strong Arms - Split - Terran, 85.68677944379723, 0.1050337059978218
    OTAS - Pirates - Boron - Split - Strong Arms - Terran - Goner - TerraCorp, 397.11861174422603, 0.01762697539975417
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Goner - Teladi - TerraCorp, 159.92871881448139, 0.03751671397405521
    Yaki - OTAS - Boron - Strong Arms - Terran, 66.78088166370232, 0.14974345577463888
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split, 57.9879917460554, 0.15520454716578833
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Teladi, 97.38123259589223, 0.08215135285048199
    Paranid - Yaki - OTAS - Boron - Strong Arms - Terran, 19.46855674705685, 0.4622838825153575
    Yaki - OTAS - Pirates - Boron - Strong Arms - Terran, 25.25306288267288, 0.3563924123507115
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - TerraCorp, 32.88145078504831, 0.24329826722967227
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms, 25.136139371763424, 0.3580502107698413
    Paranid - Yaki - Boron - Duke's - Strong Arms - Terran, 24.398584126104964, 0.36887386388829674
    Yaki - Pirates - Boron - Duke's - Strong Arms - Terran, 17.656979278697673, 0.5097134599267544
    Paranid - Yaki - Pirates - Boron - Strong Arms - Terran, 15.649840911061572, 0.575085718196576
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - TerraCorp, 78.64596260107223, 0.10172168710782531
    Paranid - Yaki - OTAS - Boron - Strong Arms - Arteus, 73.17078532587519, 0.12299990986726986
    Paranid - OTAS - Boron - Strong Arms - Arteus - Terran - Goner - Teladi, 272.6153914874775, 0.025677200255663273
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Teladi, 88.79750639908329, 0.09009261998918687
    Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus, 31.264120662258374, 0.2878699227534865
    Yaki - Boron - Strong Arms - Arteus - Terran, 142.33234408517993, 0.07025809955055205
    Paranid - Pirates - Boron - Arteus - Strong Arms - Terran, 88.45095185044356, 0.10175130749545311
    Paranid - Yaki - Pirates - Boron - Strong Arms - Arteus, 38.23780965654333, 0.2353691302101009
    Paranid - Yaki - Boron - Strong Arms - Arteus - Terran, 16.45135431086573, 0.5470674225316339
    Yaki - Pirates - Boron - Strong Arms - Arteus - Terran, 24.620554473826857, 0.365548225551441
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus, 39.186902551094725, 0.22966857327560267
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus, 12.037195968269007, 0.6646066094702311
    Yaki - Boron - Strong Arms - Arteus - Terran - TerraCorp, 31.21829776582427, 0.28829246448704854
    Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi, 94.61214374225526, 0.08455574182732607
    Paranid - Yaki - Pirates - Strong Arms - Arteus - Terran, 17.957328094160736, 0.5011881474130091
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Teladi, 65.8846609946018, 0.12142431757606634
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - TerraCorp, 53.41585268983821, 0.1497682728468718
    Paranid - OTAS - Boron - Duke's - Strong Arms - Terran - Teladi - TerraCorp, 52.67672225505562, 0.13288602062418906
    OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - Teladi, 55.63393587802206, 0.14379712443031314
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms, 31.507120161221884, 0.28564971834769454
    Yaki - OTAS - Boron - Duke's - Strong Arms - Terran, 29.867200347986113, 0.3013339012408256
    Paranid - OTAS - Pirates - Boron - Strong Arms - Terran - Goner, 957.9506538967025, 0.008351160853075272
    Paranid - Pirates - Boron - Duke's - Strong Arms - Terran, 61.30127951406315, 0.14681585884247828
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - Goner - TerraCorp, 91.51410376546625, 0.07649094196387157
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - TerraCorp, 48.235297876108895, 0.16585364561338028
    Paranid - OTAS - Strong Arms - Split - Arteus - Terran - Goner, 179.2546267049693, 0.04462925251668399
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - TerraCorp, 48.045503985419494, 0.16650881635933681
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus, 35.239699823451204, 0.25539377591436546
    Yaki - Strong Arms - Split - Terran - Arteus - TerraCorp, 51.98893936697471, 0.1731137451462826
    Paranid - OTAS - Pirates - Strong Arms - Split - Arteus - Goner - TerraCorp, 154.08427678347277, 0.0454296839763655
    Paranid - Yaki - Pirates - Strong Arms - Split - Arteus, 24.26163463555836, 0.37095604377824615
    Paranid - Yaki - Strong Arms - Split - Arteus - Terran, 16.48650784398053, 0.5459009321544123
    Yaki - Pirates - Strong Arms - Split - Arteus - Terran, 25.78181128669693, 0.3490833091561678
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus, 27.482102664338537, 0.3274858590670584
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Arteus, 10.36307978215402, 0.7719712834573158
    Paranid - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp, 37.10188845204575, 0.21562244763740296
    Pirates - Duke's - Strong Arms - Split - Arteus - Terran - Goner - Teladi, 128.07442019976847, 0.05465572273590238
    Yaki - Duke's - Strong Arms - Split - Arteus - Terran - Goner, 128.81355063455106, 0.062105267346416866
    Paranid - Pirates - Strong Arms - Split - Arteus - Terran, 41.214896614321134, 0.218367647120889
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split, 20.996913485262933, 0.42863442792755296
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - TerraCorp, 27.497426430656105, 0.29093631799232766
    Paranid - OTAS - Duke's - Strong Arms - Split - Terran - Teladi, 55.33159073935773, 0.1445828665523897
    OTAS - Pirates - Duke's - Strong Arms - Split - Terran, 41.72875185698415, 0.21567862923016398
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split, 20.90579444901686, 0.4305026542735976
    Yaki - OTAS - Duke's - Strong Arms - Split - Terran, 30.412299506952056, 0.295932900369558
    Paranid - OTAS - Pirates - Strong Arms - Split - Terran, 33.77700398972765, 0.2664534723901831
    Yaki - OTAS - Pirates - Strong Arms - Split - Terran, 20.335801814409866, 0.4425692226024074
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Terran, 8.048854793795302, 0.9939302180189705
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus, 70.61767898477443, 0.12744683950799984
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus, 52.6801704438347, 0.17084227184867232
    Paranid - OTAS - Duke's - Strong Arms - Arteus - Terran - Goner - Teladi, 199.91671301508927, 0.03501458129451966
    Yaki - OTAS - Duke's - Strong Arms - Arteus - Terran, 26.684852738096428, 0.33726998939556513
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran, 17.85351178241406, 0.44809111493012277
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Terran, 31.721417892006496, 0.2837199784271912
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Terran, 41.72875185698417, 0.21567862923016387
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms, 22.89693108047647, 0.3930657767352076
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - Argon, 24.444568486106125, 0.32727106655808075
    Yaki - OTAS - Boron - Strong Arms - Split - Arteus - Argon, 36.51785785736444, 0.21907090035914212
    OTAS - Boron - Strong Arms - Split - Arteus - Terran - Argon, 527.0508035729245, 0.01517880239583601
    OTAS - Pirates - Boron - Split - Strong Arms - Arteus - Argon, 74.92810026385223, 0.10676902219365973
    Yaki - Pirates - Boron - Strong Arms - Split - Arteus - Argon, 52.62225277657867, 0.15202693875471393
    Yaki - Boron - Strong Arms - Arteus - Terran - Argon, 52.72969326697945, 0.1706818197183788
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus - Argon, 29.9960377204798, 0.2667018915814337
    Paranid - Yaki - Boron - Strong Arms - Arteus - Argon, 35.283447192984475, 0.2550771173455382
    Paranid - Boron - Strong Arms - Arteus - Terran - Argon, 378.98016162688396, 0.02374794490921332
    OTAS - Pirates - Boron - Split - Strong Arms - Terran - Argon, 50.17758820052961, 0.15943372901919511
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Argon, 50.58902179321719, 0.15813707631469984
    Paranid - Yaki - Boron - Duke's - Strong Arms - Arteus - Argon, 24.53059156538484, 0.32612340304458104
    Paranid - Boron - Strong Arms - Arteus - Terran - Teladi - Argon, 134.19774381088047, 0.05961352085974025
    Pirates - Duke's - Strong Arms - Terran - Arteus - Teladi - Argon, 147.29465899753475, 0.05431289942518482
    Yaki - Pirates - Boron - Duke's - Strong Arms - Argon, 115.1694412179249, 0.07814572949928705
    Yaki - Strong Arms - Split - Terran - Arteus - Argon, 142.85533894545162, 0.06300079553510136
    Paranid - Pirates - Boron - Terran - Strong Arms - Argon, 392.9064505318782, 0.022906215939740068
    Paranid - Yaki - Pirates - Boron - Strong Arms - Argon, 49.55737924913583, 0.18160766643359053
    Paranid - Yaki - Boron - Strong Arms - Terran - Argon, 24.44163792202726, 0.3682240948299554
    Yaki - Pirates - Strong Arms - Terran - Argon, 36.489015928245244, 0.2740550750851915
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Argon, 50.58902179321719, 0.15813707631469984
    Paranid - Yaki - OTAS - Strong Arms - Split - Argon, 32.73845891858689, 0.27490603703677546
    Paranid - OTAS - Strong Arms - Split - Terran - Argon, 85.68677944379725, 0.10503370599782179
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Argon, 32.61937229010887, 0.2452530333462557
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Argon, 23.803916598041884, 0.33607914760792273
    Yaki - OTAS - Strong Arms - Terran - Argon, 58.255066063084215, 0.17165889039025437
    Paranid - OTAS - Pirates - Strong Arms - Split - Argon, 53.03005401617745, 0.16971508264454044
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Argon, 26.424160638563926, 0.3027532306295719
    Paranid - Yaki - OTAS - Strong Arms - Terran - Argon, 22.707064399234092, 0.3963524232706879
    Yaki - OTAS - Pirates - Strong Arms - Terran - Argon, 25.25306288267288, 0.3563924123507115
    Paranid - Pirates - Duke's - Strong Arms - Terran - Teladi - Argon, 54.61438658716809, 0.14648155000755128
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Argon, 29.597301369887305, 0.30408177717029033
    Paranid - Yaki - Duke's - Strong Arms - Terran - Argon, 27.573911230757332, 0.32639548030316956
    Yaki - Pirates - Duke's - Strong Arms - Terran - Argon, 17.867154165570756, 0.5037175991542411
    Paranid - Yaki - Pirates - Strong Arms - Terran - Argon, 17.948285093443648, 0.5014406642831644
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - Argon, 33.60535114996876, 0.2380573249866915
    Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - Argon, 24.53059156538484, 0.32612340304458104
    OTAS - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi - Argon, 65.24022346368713, 0.10729576982359997
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Argon, 26.405340975925967, 0.30296900946265704
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Argon, 35.05872347071434, 0.2567121420583948
    Yaki - OTAS - Strong Arms - Terran - Arteus - Argon, 37.73241236451939, 0.2385217227314863
    Paranid - OTAS - Pirates - Boron - Strong Arms - Arteus - Argon, 48.27695583363008, 0.16571053128472407
    Paranid - Yaki - OTAS - Boron - Strong Arms - Arteus - Argon, 18.716186420813603, 0.4274375035666179
    Paranid - OTAS - Boron - Strong Arms - Arteus - Terran - Argon, 36.09363443853318, 0.22164573128881931
    OTAS - Pirates - Boron - Arteus - Strong Arms - Terran - Argon, 75.50686433814676, 0.10595063204019621
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Argon, 80.88274451683043, 0.11127218857079264
    Paranid - Yaki - Pirates - Boron - Strong Arms - Arteus - Argon, 18.852922868697554, 0.4243373855458136
    Paranid - Yaki - Strong Arms - Terran - Arteus - Argon, 20.991216009231874, 0.42875076870448225
    Yaki - Pirates - Strong Arms - Arteus - Terran - Argon, 26.70426155848253, 0.3370248595075334
    Paranid - Pirates - Boron - Arteus - Strong Arms - Terran - Argon, 35.89404845615569, 0.22287817463031345
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Argon, 35.91520802882143, 0.22274686516029968
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Argon, 27.373346145540395, 0.29225509944838596
    Paranid - OTAS - Boron - Strong Arms - Terran - Teladi - Argon, 193.4702022744018, 0.041350036883992476
    OTAS - Pirates - Duke's - Strong Arms - Terran - Teladi - Argon, 55.63393587802205, 0.14379712443031314
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Argon, 30.04946580313226, 0.29950615624793797
    Yaki - OTAS - Duke's - Strong Arms - Terran - Argon, 27.560099143095137, 0.32655905747185404
    Paranid - OTAS - Pirates - Boron - Strong Arms - Terran - Argon, 50.17758820052963, 0.15943372901919506
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Terran - Argon, 10.799507357800916, 0.740774531184636
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - Argon, 49.877737098053636, 0.16039220031720688
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - Argon, 22.01821957014733, 0.3633354629112035
    Paranid - OTAS - Strong Arms - Split - Arteus - Terran - Argon, 42.7986269971388, 0.18692188421219263
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Argon, 32.17002288626228, 0.2486787164648328
    Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - Argon, 42.88756632667834, 0.1865342495552977
    Yaki - OTAS - Strong Arms - Split - Terran - Argon, 29.910061131258754, 0.3009020931285953
    Paranid - OTAS - Pirates - Strong Arms - Split - Arteus - Argon, 35.36529616562068, 0.22621046244133997
    Paranid - Yaki - Pirates - Strong Arms - Split - Argon, 25.238192515220877, 0.35660239910493585
    Paranid - Yaki - Strong Arms - Split - Terran - Argon, 21.719881572264995, 0.4143669002087225
    OTAS - Pirates - Strong Arms - Split - Arteus - Terran - Goner - Argon, 164.1618645496762, 0.042640841216089895
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus - Argon, 23.536318338726176, 0.3399002292910427
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - Argon, 35.058224862167805, 0.2281918160845901
    Paranid - Yaki - Duke's - Strong Arms - Split - Terran - Argon, 20.516858662438022, 0.3899232397913959
    Pirates - Duke's - Strong Arms - Split - Arteus - Terran - Teladi - Argon, 73.71327379119185, 0.09496254392158668
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Argon, 26.877792034113263, 0.29764349652852473
    Paranid - Pirates - Strong Arms - Split - Terran - Argon, 51.30950412208993, 0.17540609978581514
    Yaki - Pirates - Strong Arms - Split - Terran - Argon, 25.341240176697916, 0.35515231051224516
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Argon, 15.897587502325333, 0.5032210075163822
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Argon, 20.19761869792297, 0.3960862970852442
    Paranid - OTAS - Duke's - Strong Arms - Split - Terran - Argon, 43.47186757542052, 0.18402706039993758
    OTAS - Pirates - Duke's - Strong Arms - Split - Terran - Argon, 25.93119093827203, 0.30850877690282796
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Argon, 14.452927115513345, 0.553521092029381
    Yaki - OTAS - Duke's - Strong Arms - Split - Terran - Argon, 20.150236109225308, 0.39701768042000213
    Paranid - OTAS - Pirates - Strong Arms - Split - Terran - Argon, 21.93524275117603, 0.3647098913264176
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Argon, 15.104352759000278, 0.5296486468268569
    Paranid - Yaki - OTAS - Strong Arms - Split - Terran - Argon, 11.439654107155123, 0.6993218435683528
    Yaki - OTAS - Pirates - Strong Arms - Split - Terran - Argon, 14.126840529006627, 0.5662978911366352
    Paranid - Pirates - Duke's - Strong Arms - Split - Terran - Argon, 26.43406044546973, 0.30263984666688015
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Argon, 14.60035638347031, 0.5479318305584063
    Yaki - Pirates - Duke's - Strong Arms - Split - Terran - Argon, 15.720440827156484, 0.5088915818556623
    Paranid - Yaki - Pirates - Strong Arms - Split - Terran - Argon, 10.4756478741561, 0.7636759173374243
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - Argon, 35.34710790851484, 0.22632686161214513
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus - Argon, 26.891895603811683, 0.29748739612339087
    Paranid - OTAS - Duke's - Strong Arms - Arteus - Terran - Teladi - Argon, 52.60066621664775, 0.1330781623785698
    OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - Argon, 35.86538773226659, 0.22305628088338592
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Argon, 17.52699151223825, 0.4564388585693093
    Yaki - Duke's - Strong Arms - Terran - Arteus - Argon, 74.94877701699646, 0.12008201278533245
    Paranid - OTAS - Pirates - Strong Arms - Arteus - Terran - Goner - Argon, 397.1186117442264, 0.017626975399754153
    Paranid - Yaki - OTAS - Strong Arms - Arteus - Terran - Argon, 17.634787837499836, 0.4536487806781687
    Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran - Argon, 21.431013452892383, 0.37329079269092147
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Terran - Argon, 27.539833839443094, 0.29048831763618854
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - Argon, 14.815757191208508, 0.5399656525653042
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Terran - Argon, 15.11138347505634, 0.529402222715427
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran - Argon, 12.439591248952297, 0.6431079478333973
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Terran - Argon, 31.54854192045557, 0.2535774876750462
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Argon, 17.904147546256873, 0.4468238423153812
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Terran - Argon, 14.714439993073896, 0.5436836198839785
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran - Argon, 10.810279413250267, 0.7400363759510526
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Terran - Argon, 16.167866321228967, 0.4948086433332099
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Arteus, 40.11726421293545, 0.19941539277298156
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Arteus, 20.589628207909225, 0.3885451412341146
    Paranid - Boron - Strong Arms - Split - Arteus - Terran - Goner, 399.7573105560447, 0.020012141838938118
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Arteus, 40.11726421293545, 0.19941539277298156
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Arteus, 73.36390239778727, 0.10904545339781826
    Yaki - Boron - Strong Arms - Split - Arteus - Terran, 135.79369685854144, 0.06627700849307792
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Arteus, 32.355970274265786, 0.24724957812075793
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Arteus, 15.796807006769157, 0.5064314577352174
    Paranid - Yaki - Boron - Strong Arms - Split - Terran, 20.38263138247246, 0.44155240955489816
    OTAS - Pirates - Boron - Split - Strong Arms - Arteus - Terran - Goner, 6905.213018650579, 0.001013726872884791
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Arteus, 19.758463359907722, 0.4048897859250003
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Arteus, 26.678091616098275, 0.29987152436243175
    Paranid - Boron - Strong Arms - Split - Arteus - Terran - Teladi, 135.70049832526612, 0.05895335756855122
    Pirates - Boron - Duke's - Split - Strong Arms - Arteus - Terran - Teladi, 67.29872154661676, 0.10401386295505198
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Arteus, 26.67809161609828, 0.2998715243624317
    Yaki - Boron - Duke's - Strong Arms - Split - Arteus - Terran, 68.03785198139938, 0.11758160739976169
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus - Terran, 25.05376672034579, 0.3193132629235874
    Yaki - Pirates - Boron - Strong Arms - Split - Terran, 26.794789667860677, 0.3358861969644477
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Split, 16.260937916373056, 0.491976541644922
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Split, 21.12203721100181, 0.3787513448671064
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Terran, 43.47186757542052, 0.18402706039993758
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Terran, 31.54854192045556, 0.2535774876750463
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Split, 17.144566083866707, 0.46662015013189045
    Yaki - OTAS - Boron - Strong Arms - Split - Terran, 39.83148683041538, 0.22595189675740618
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Terran, 21.935242751176027, 0.3647098913264177
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Split, 15.694892588549298, 0.5097199585702582
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Terran, 11.439654107155125, 0.6993218435683527
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Terran, 16.167866321228967, 0.4948086433332099
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Terran, 24.84662092267583, 0.321975371415553
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Split, 14.113320363370494, 0.5668403886560305
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Terran, 19.41287788134448, 0.4120975802195663
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Terran, 15.917252452761346, 0.5025993037267025
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Terran, 10.121343166260651, 0.7904089278059342
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus, 23.212070707431316, 0.34464826946433563
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus, 19.47189500699278, 0.4108485587626179
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - Terran, 41.37274019568709, 0.19336403540498295
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran, 31.726841854798938, 0.25215242149258976
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus, 16.60067389102799, 0.48190814737488963
    Yaki - OTAS - Boron - Strong Arms - Arteus - Terran, 37.07213201515827, 0.2427699598264278
    Paranid - OTAS - Pirates - Boron - Strong Arms - Arteus - Terran, 66.06758627107561, 0.12108812280769518
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus, 35.24018725432561, 0.22701354968021709
    Paranid - Yaki - OTAS - Boron - Strong Arms - Arteus - Terran, 14.154603805150273, 0.5651871369998454
    Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - Terran, 20.281280238690588, 0.3944524165066466
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran, 20.420576909146654, 0.39176170367726937
    Paranid - Yaki - Boron - Duke's - Strong Arms - Arteus - Terran, 12.678865570265105, 0.6309712770172329
    Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran, 11.856501841446228, 0.6747352724253597
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Terran, 25.93119093827203, 0.30850877690282796
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Strong Arms, 15.920913099028137, 0.5024837426245574
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Terran, 13.448306581797267, 0.5948704360167003
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Terran, 10.810279413250269, 0.7400363759510525
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Terran, 14.126840529006627, 0.5662978911366352
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Terran, 10.125066541132982, 0.7901182641615321
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus, 14.965629001557216, 0.5345582199831078
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Arteus, 18.792435990035173, 0.4257031927229689
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - Terran, 37.10188845204575, 0.21562244763740296
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Terran, 28.43080008599718, 0.2813849760049554
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus, 15.737824425029697, 0.5083294732451499
    Yaki - OTAS - Strong Arms - Split - Arteus - Terran, 51.98893936697472, 0.17311374514628258
    Paranid - OTAS - Pirates - Strong Arms - Split - Arteus - Terran, 28.78437398849347, 0.2779285734405061
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Arteus, 20.240729899880076, 0.39524266365747013
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - Terran, 12.640476351465452, 0.6328875413838763
    Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - Terran, 19.246429375392346, 0.4156615153888469
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus - Terran, 16.597843016703262, 0.48199034006703095
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - Terran, 13.370726439968186, 0.5983220160788089
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Terran, 12.220161824604128, 0.6546558151049002
    Paranid - Yaki - Pirates - Strong Arms - Split - Arteus - Terran, 10.00199178441423, 0.7998406889781826
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Terran, 13.131034474326645, 0.6092436978702119
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Split, 9.229282289712815, 0.8668062964025921
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Terran, 10.711006738184862, 0.7468952448213769
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Terran, 9.1177347734113, 0.8774109138740486
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Terran, 9.439665219711559, 0.8474876824333448
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran, 23.53447178214451, 0.33992689846855034
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus, 14.554973669171563, 0.5496402935406576
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus - Terran, 12.561210396916065, 0.6368812994298783
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran, 10.252697945936177, 0.7802824234347926
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran, 8.394890587506595, 0.9529606034301058
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran, 9.1177347734113, 0.8774109138740486
    Paranid - OTAS - Boron - Split - Arteus - TerraCorp - Argon, 18.267850207078986, 0.43792783000267405
    Yaki - OTAS - Boron - Split - Arteus - TerraCorp - Argon, 24.202467049373013, 0.33054481527358376
    OTAS - Boron - Split - Arteus - Terran - TerraCorp - Argon, 24.00121922774963, 0.33331640047479727
    OTAS - Pirates - Boron - Split - Arteus - TerraCorp - Argon, 34.7618789605373, 0.23013715711632945
    Yaki - Pirates - Boron - Split - Arteus - TerraCorp - Argon, 35.50980871032351, 0.22528986470361406
    Yaki - Boron - Terran - TerraCorp - Argon, 49.309034917954385, 0.20280259016707716
    Paranid - Pirates - Boron - Split - Arteus - TerraCorp - Argon, 23.734656954311518, 0.33705985367303826
    Paranid - Yaki - Boron - Arteus - TerraCorp - Argon, 26.84470412685203, 0.3352616574752092
    Paranid - Boron - Split - Arteus - Terran - TerraCorp - Argon, 18.549988886838268, 0.4312671047299776
    OTAS - Pirates - Boron - Split - Terran - TerraCorp - Argon, 26.570881047984685, 0.30108147281803344
    Paranid - Boron - Duke's - Split - Arteus - TerraCorp - Argon, 36.60285887198815, 0.21856216280751586
    Paranid - Yaki - Boron - Duke's - Arteus - TerraCorp - Argon, 17.56104653978346, 0.45555371554175295
    Paranid - Boron - Duke's - Arteus - Terran - TerraCorp - Argon, 16.624000911254733, 0.48123192742270987
    Pirates - Boron - Duke's - Split - Arteus - TerraCorp - Argon, 33.90851460595156, 0.23592894271446072
    Yaki - Pirates - Boron - Duke's - Split - TerraCorp - Argon, 165.12651782216972, 0.0484477000151815
    Yaki - Boron - Duke's - Terran - TerraCorp - Argon, 41.83880334028768, 0.21511131489111363
    Paranid - Pirates - Split - Terran - TerraCorp - Argon, 49.537956488534014, 0.18167887086911078
    Paranid - Yaki - Pirates - Boron - Split - TerraCorp - Argon, 39.77250362885741, 0.20114398818472937
    Paranid - Yaki - Terran - TerraCorp - Argon, 32.65495295571697, 0.3062322586580018
    Yaki - Pirates - Terran - TerraCorp - Argon, 31.99128700772451, 0.31258511098929637
    Paranid - OTAS - Boron - Duke's - Split - TerraCorp - Argon, 52.62225277657867, 0.15202693875471393
    Yaki - OTAS - Boron - Duke's - Split - TerraCorp - Argon, 64.71429731579175, 0.12362028688902751
    Paranid - OTAS - Split - Terran - TerraCorp - Argon, 63.99155580724427, 0.1406435565828381
    OTAS - Pirates - Boron - Duke's - Split - TerraCorp - Argon, 30.403008775030667, 0.2631318518241598
    Yaki - OTAS - Pirates - Boron - Split - TerraCorp - Argon, 32.31841821315753, 0.24753686728216873
    Yaki - OTAS - Terran - TerraCorp - Argon, 41.95266163035122, 0.23836389900862368
    Paranid - OTAS - Pirates - Boron - Split - TerraCorp - Argon, 28.2642564293701, 0.2830430023868238
    Paranid - Yaki - OTAS - Boron - Split - TerraCorp - Argon, 25.404143665383476, 0.3149092567485777
    Paranid - Yaki - OTAS - Terran - TerraCorp - Argon, 24.123050186329177, 0.3730871482040197
    Yaki - OTAS - Pirates - Terran - TerraCorp - Argon, 24.9941963887448, 0.3600835914073562
    Paranid - Pirates - Boron - Duke's - Split - TerraCorp - Argon, 100.1624446395145, 0.0798702550521013
    Paranid - Yaki - Pirates - Duke's - TerraCorp - Argon, 142.9100129015059, 0.06297669293615439
    Paranid - Yaki - Duke's - Terran - TerraCorp - Argon, 24.927910095293576, 0.3610410967303357
    Pirates - Boron - Duke's - Terran - TerraCorp - Argon, 82.02061496544154, 0.10972851159177542
    Paranid - Yaki - Pirates - Terran - TerraCorp - Argon, 20.34581956340141, 0.4423513131016572
    Paranid - OTAS - Boron - Duke's - Arteus - TerraCorp - Argon, 17.09854582724033, 0.4678760451812752
    Yaki - OTAS - Boron - Duke's - Arteus - TerraCorp - Argon, 15.016719706070377, 0.5327395167911452
    Paranid - OTAS - Boron - Arteus - Terran - TerraCorp - Argon, 17.664920176356947, 0.45287495896569896
    OTAS - Pirates - Boron - Duke's - Arteus - TerraCorp - Argon, 14.870785195537966, 0.5379675581892226
    Yaki - Pirates - Duke's - Arteus - TerraCorp - Argon, 39.556032637539374, 0.2275253456904786
    Yaki - Boron - Arteus - Terran - TerraCorp - Argon, 15.452356739329916, 0.5824354272829376
    Paranid - OTAS - Pirates - Boron - Arteus - TerraCorp - Argon, 32.09273390981744, 0.24927760976925473
    Paranid - Yaki - OTAS - Boron - Arteus - TerraCorp - Argon, 17.223017753054215, 0.4644946730419141
    Paranid - Yaki - Arteus - Terran - TerraCorp - Argon, 18.374213056557544, 0.48981689568403064
    Yaki - Pirates - Arteus - Terran - TerraCorp - Argon, 21.450795758848212, 0.41956485443145397
    Paranid - Pirates - Duke's - Arteus - TerraCorp - Argon, 68.91368417239936, 0.13059815489598497
    Paranid - Yaki - Pirates - Boron - Arteus - TerraCorp - Argon, 18.730315080413547, 0.4271150787188663
    Yaki - Duke's - Arteus - Terran - TerraCorp - Argon, 19.89864480298115, 0.4522921077847296
    Pirates - Duke's - Arteus - Terran - TerraCorp - Argon, 30.34529521355793, 0.29658633856291844
    Paranid - Pirates - Boron - Arteus - Terran - TerraCorp - Argon, 18.300681187273828, 0.43714219804906207
    Paranid - OTAS - Pirates - Boron - Duke's - TerraCorp - Argon, 37.939185793265196, 0.2108637766659749
    Yaki - OTAS - Pirates - Boron - Duke's - TerraCorp - Argon, 22.316453758462433, 0.35847989499525157
    Paranid - OTAS - Boron - Duke's - Terran - TerraCorp - Argon, 29.9482981441334, 0.26712703211040817
    OTAS - Pirates - Duke's - Terran - TerraCorp - Argon, 42.55220193871749, 0.2115049184284647
    Yaki - OTAS - Duke's - Terran - TerraCorp - Argon, 21.288944031945398, 0.422754646096816
    Paranid - OTAS - Pirates - Boron - Terran - TerraCorp - Argon, 32.09273390981744, 0.24927760976925473
    Paranid - Yaki - OTAS - Pirates - Boron - TerraCorp - Argon, 37.93918579326518, 0.21086377666597497
    Paranid - Pirates - Duke's - Terran - TerraCorp - Argon, 50.87088418589297, 0.17691848970252014
    Yaki - Pirates - Duke's - Terran - TerraCorp - Argon, 16.28542557985526, 0.5526413759265104
    OTAS - Pirates - Duke's - Split - Arteus - TerraCorp - Argon, 29.876413450138962, 0.2677697580183538
    Yaki - OTAS - Duke's - Split - Arteus - TerraCorp - Argon, 63.81132748797822, 0.12536959055595837
    Paranid - OTAS - Split - Terran - Arteus - TerraCorp - Argon, 30.275346806510264, 0.26424139915317896
    OTAS - Pirates - Split - Arteus - Terran - TerraCorp - Argon, 54.50649961452244, 0.14677148700755166
    Yaki - OTAS - Pirates - Split - Arteus - Teladi - TerraCorp - Argon, 96.40286768847115, 0.07261194783770039
    Yaki - Split - Terran - Arteus - TerraCorp - Argon, 30.909761933404507, 0.2911701493978058
    Paranid - OTAS - Pirates - Split - Arteus - TerraCorp - Argon, 67.17239955276021, 0.11909653448834207
    Paranid - Yaki - OTAS - Split - Arteus - TerraCorp - Argon, 43.561648019631555, 0.18364778110310953
    Paranid - Yaki - Split - Terran - TerraCorp - Argon, 23.075415182125752, 0.3900254850873241
    Yaki - Pirates - Split - Terran - TerraCorp - Argon, 23.603980256688136, 0.3812916254854886
    Paranid - Pirates - Duke's - Split - Arteus - TerraCorp - Argon, 27.862518325489525, 0.28712408212869056
    Paranid - Yaki - Duke's - Split - Arteus - TerraCorp - Argon, 53.33979665143032, 0.14998182412053643
    Paranid - Duke's - Split - Terran - Arteus - TerraCorp - Argon, 33.31426482838556, 0.24013737181988076
    Pirates - Duke's - Split - Terran - Arteus - TerraCorp - Argon, 24.099624706059807, 0.3319553767983953
    Yaki - Pirates - Duke's - Split - Arteus - TerraCorp - Argon, 31.439814928727873, 0.25445442405228874
    Yaki - Duke's - Split - Terran - Arteus - TerraCorp - Argon, 19.538051943211098, 0.4094574025728172
    Paranid - Pirates - Split - Arteus - Terran - TerraCorp - Argon, 25.11834670107148, 0.31849229948158736
    Paranid - Yaki - Pirates - Split - Arteus - TerraCorp - Argon, 34.94181284311941, 0.22895205912521296
    Paranid - OTAS - Pirates - Duke's - Split - TerraCorp - Argon, 30.53382789473127, 0.262004489826198
    Paranid - Yaki - OTAS - Duke's - Split - TerraCorp - Argon, 63.48831476117874, 0.126007439795705
    Paranid - OTAS - Duke's - Split - Terran - TerraCorp - Argon, 33.5268308809817, 0.23861485830257967
    OTAS - Pirates - Duke's - Split - Terran - TerraCorp - Argon, 20.503412142496384, 0.3901789587216464
    Yaki - OTAS - Pirates - Duke's - Split - TerraCorp - Argon, 27.7222268023278, 0.288577106631573
    Yaki - OTAS - Split - Terran - TerraCorp - Argon, 25.400064564526446, 0.3543298079867615
    Paranid - OTAS - Pirates - Split - Terran - TerraCorp - Argon, 25.10275177083142, 0.3186901608649829
    Paranid - Yaki - OTAS - Pirates - Split - TerraCorp - Argon, 37.37022528456159, 0.21407417105684307
    Paranid - Yaki - OTAS - Split - Terran - TerraCorp - Argon, 13.911247327482506, 0.5750742411282933
    Yaki - OTAS - Pirates - Split - Terran - TerraCorp - Argon, 15.370811978471007, 0.5204669741068416
    Paranid - Pirates - Duke's - Split - Terran - TerraCorp - Argon, 25.21197482728354, 0.31730953464790357
    Paranid - Yaki - Pirates - Duke's - Split - TerraCorp - Argon, 42.816340208491326, 0.18684455422963595
    Paranid - Yaki - Duke's - Split - Terran - TerraCorp - Argon, 20.712794361734097, 0.3862347040329633
    Yaki - Pirates - Duke's - Split - Terran - TerraCorp - Argon, 14.772905602167244, 0.5415319244188745
    Paranid - Yaki - Pirates - Split - Terran - TerraCorp - Argon, 13.437110097139428, 0.5953661123683944
    Paranid - OTAS - Pirates - Duke's - Arteus - TerraCorp - Argon, 37.27188351475688, 0.21463900521240356
    Paranid - Yaki - OTAS - Duke's - Arteus - TerraCorp - Argon, 36.86572378593624, 0.21700374164502065
    Paranid - OTAS - Duke's - Arteus - Terran - TerraCorp - Argon, 29.397052143289454, 0.2721361298747154
    OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp - Argon, 19.344897334173414, 0.4135457460333858
    Yaki - OTAS - Pirates - Duke's - Arteus - TerraCorp - Argon, 21.883306314006877, 0.36557547041597777
    Yaki - OTAS - Arteus - Terran - TerraCorp - Argon, 26.123254069599003, 0.34452063192516935
    Paranid - Yaki - OTAS - Arteus - Terran - TerraCorp - Argon, 16.87298862642721, 0.47413058688785287
    Yaki - OTAS - Pirates - Arteus - Terran - TerraCorp - Argon, 19.34489733417341, 0.41354574603338584
    Paranid - Pirates - Duke's - Arteus - Terran - TerraCorp - Argon, 17.666781116572068, 0.4528272551300087
    Paranid - Yaki - Pirates - Duke's - Arteus - TerraCorp - Argon, 20.85985946355715, 0.383511692107814
    Paranid - Yaki - Duke's - Arteus - Terran - TerraCorp - Argon, 11.932408476296587, 0.6704430221184422
    Yaki - Pirates - Duke's - Arteus - Terran - TerraCorp - Argon, 9.891613994806765, 0.8087658903996974
    Paranid - Yaki - Pirates - Arteus - Terran - TerraCorp - Argon, 14.90084693837962, 0.5368822344852535
    Paranid - OTAS - Pirates - Duke's - Terran - TerraCorp - Argon, 27.31934943813031, 0.29283274179414376
    Paranid - Yaki - OTAS - Pirates - Duke's - TerraCorp - Argon, 38.753129536777344, 0.20643494075511684
    Paranid - Yaki - OTAS - Duke's - Terran - TerraCorp - Argon, 15.326054051061291, 0.5219869363207694
    Yaki - OTAS - Pirates - Duke's - Terran - TerraCorp - Argon, 11.291896672703148, 0.7084726536100063
    Paranid - Yaki - OTAS - Pirates - Terran - TerraCorp - Argon, 18.360791259135404, 0.43571106969693385
    Paranid - Yaki - Pirates - Duke's - Terran - TerraCorp - Argon, 12.37546594495287, 0.6464403066183272
    Paranid - OTAS - Boron - Duke's - Split - Arteus - TerraCorp, 35.98208902858446, 0.22233283880890672
    Yaki - OTAS - Boron - Duke's - Split - Arteus - TerraCorp, 87.83887971473955, 0.09107584279285365
    Paranid - OTAS - Boron - Split - Arteus - Terran - TerraCorp, 26.135454322643763, 0.3060976060044534
    OTAS - Pirates - Boron - Duke's - Split - Arteus - TerraCorp, 33.321325889287294, 0.24008648475095573
    Yaki - Pirates - Boron - Duke's - Split - Arteus - TerraCorp, 27.722226802327814, 0.2885771066315728
    Yaki - Boron - Split - Arteus - Terran - TerraCorp, 32.29478541130334, 0.2786827621046819
    Paranid - OTAS - Pirates - Boron - Split - Arteus - TerraCorp, 44.902821361911705, 0.17816252425478785
    Paranid - Yaki - OTAS - Boron - Split - Arteus - TerraCorp, 30.768883557331012, 0.26000293397366103
    Paranid - Yaki - Boron - Split - Terran - TerraCorp, 20.699158693521255, 0.43480028020737677
    Yaki - Pirates - Boron - Split - Terran - TerraCorp, 24.64475091779906, 0.36518932692884204
    Paranid - Pirates - Boron - Duke's - Split - Arteus - TerraCorp, 20.20459857721051, 0.3959494651392622
    Paranid - Yaki - Boron - Duke's - Split - Arteus - TerraCorp, 30.232283621436387, 0.26461778740152964
    Paranid - Boron - Duke's - Split - Arteus - Terran - TerraCorp, 24.773186783131496, 0.3229297897776859
    Pirates - Boron - Duke's - Split - Arteus - Terran - TerraCorp, 23.768292654651642, 0.3365828634070751
    Yaki - Boron - Duke's - Split - Arteus - Terran - TerraCorp, 19.13340414749341, 0.41811691941123025
    Paranid - Pirates - Boron - Split - Arteus - Terran - TerraCorp, 20.490011060425076, 0.39043414746863664
    Paranid - Yaki - Pirates - Boron - Split - Arteus - TerraCorp, 24.110202218005025, 0.3318097429322164
    Paranid - OTAS - Pirates - Boron - Duke's - Split - TerraCorp, 27.9202612472726, 0.2865302702273777
    Paranid - Yaki - OTAS - Boron - Duke's - Split - TerraCorp, 53.41585268983821, 0.1497682728468718
    Paranid - OTAS - Boron - Duke's - Split - Terran - TerraCorp, 33.3550426815484, 0.2398437944264872
    OTAS - Pirates - Boron - Duke's - Split - Terran - TerraCorp, 24.077371180949328, 0.3322621867594008
    Yaki - OTAS - Pirates - Boron - Duke's - Split - TerraCorp, 31.439814928727895, 0.2544544240522886
    Yaki - OTAS - Boron - Split - Terran - TerraCorp, 32.12726665094006, 0.28013587641252563
    Paranid - OTAS - Pirates - Boron - Split - Terran - TerraCorp, 24.030382367892592, 0.3329118895206985
    Paranid - Yaki - OTAS - Boron - Split - Terran - TerraCorp, 13.324112989428977, 0.6004152025990025
    Yaki - OTAS - Pirates - Boron - Split - Terran - TerraCorp, 17.033573678458676, 0.469660691937894
    Paranid - Pirates - Boron - Duke's - Split - Terran - TerraCorp, 22.799189731282684, 0.35088966293496077
    Paranid - Yaki - Pirates - Boron - Duke's - Split - TerraCorp, 33.92670836883025, 0.23580242188628894
    Paranid - Yaki - Boron - Duke's - Split - Terran - TerraCorp, 18.801944994743415, 0.42548789512130863
    Yaki - Pirates - Boron - Duke's - Split - Terran - TerraCorp, 14.772905602167244, 0.5415319244188745
    Paranid - Yaki - Pirates - Boron - Split - Terran - TerraCorp, 12.384760432339554, 0.6459551675388163
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - TerraCorp, 22.163795445724062, 0.36094900891820836
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - TerraCorp, 21.981892667215703, 0.36393590493376315
    Paranid - OTAS - Boron - Duke's - Arteus - Terran - TerraCorp, 20.946077935930102, 0.3819330771359876
    OTAS - Pirates - Boron - Duke's - Arteus - Terran - TerraCorp, 17.97367141222093, 0.445095485308612
    Yaki - OTAS - Boron - Duke's - Arteus - Terran - TerraCorp, 12.322351926032452, 0.6492267099675214
    Paranid - OTAS - Pirates - Boron - Arteus - Terran - TerraCorp, 44.506542984391274, 0.17974885182175687
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - TerraCorp, 48.65968534372154, 0.16440714615168023
    Paranid - Yaki - OTAS - Boron - Arteus - Terran - TerraCorp, 13.220744813562586, 0.6051096298139836
    Yaki - OTAS - Pirates - Boron - Arteus - Terran - TerraCorp, 17.973671412220934, 0.44509548530861187
    Paranid - Pirates - Boron - Duke's - Arteus - Terran - TerraCorp, 13.582789344641938, 0.5889806428571165
    Paranid - Yaki - OTAS - Boron - Duke's - Terran - TerraCorp, 13.681882524032583, 0.5847148582037444
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - TerraCorp, 23.905008525628762, 0.3346579019799609
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - TerraCorp, 40.23736001644877, 0.19882020084641866
    Paranid - OTAS - Duke's - Split - Arteus - Terran - TerraCorp, 27.86853844297656, 0.2870620580397234
    OTAS - Pirates - Duke's - Split - Arteus - Terran - TerraCorp, 21.22440741269986, 0.37692453996209624
    Yaki - OTAS - Duke's - Split - Arteus - Terran - TerraCorp, 17.33620879619923, 0.4614619086587092
    Paranid - OTAS - Pirates - Split - Arteus - Terran - TerraCorp, 33.62025656385976, 0.23795178316990104
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - TerraCorp, 53.202671007743874, 0.15036839031701182
    Paranid - Yaki - OTAS - Split - Arteus - Terran - TerraCorp, 15.182005763485531, 0.5269395970880817
    Yaki - OTAS - Pirates - Split - Arteus - Terran - TerraCorp, 21.224407412699865, 0.37692453996209613
    Paranid - Yaki - Duke's - Split - Arteus - Terran - TerraCorp, 12.561210396916065, 0.6368812994298783
    Paranid - OTAS - Pirates - Duke's - Split - Terran - TerraCorp, 16.333242854037515, 0.4897986316307316
    Paranid - Yaki - OTAS - Duke's - Split - Terran - TerraCorp, 13.763305085798462, 0.5812557340064143
    Yaki - OTAS - Pirates - Duke's - Split - Terran - TerraCorp, 10.900461693377615, 0.7339138675988615
    Paranid - Yaki - OTAS - Duke's - Arteus - Terran - TerraCorp, 12.462027225762661, 0.6419501301892244
    OTAS - Pirates - Boron - Duke's - Split - Arteus - Argon, 20.67838358066933, 0.3868774350176288
    Paranid - Yaki - OTAS - Boron - Split - Arteus - Argon, 14.439439256253216, 0.5540381352783821
    Paranid - OTAS - Boron - Split - Arteus - Terran - Argon, 18.549988886838268, 0.4312671047299776
    Pirates - Boron - Duke's - Split - Arteus - Terran - Teladi - Argon, 56.95305164319249, 0.12290825158684363
    Yaki - Pirates - Boron - Duke's - Split - Arteus - Argon, 34.97942521706869, 0.22870587353437388
    Yaki - OTAS - Boron - Split - Terran - Argon, 23.613190438961986, 0.38114290499050546
    Paranid - OTAS - Pirates - Boron - Split - Arteus - Argon, 17.823297415579113, 0.4488507268586173
    Paranid - Yaki - Pirates - Boron - Split - Arteus - Argon, 18.26342267324787, 0.4380339952225024
    Paranid - Yaki - Boron - Split - Terran - Argon, 34.4560070994808, 0.26120263947053857
    Yaki - Pirates - Boron - Split - Terran - Argon, 32.22871779982987, 0.27925405087159594
    Paranid - Pirates - Boron - Duke's - Split - Arteus - Argon, 26.05159012844896, 0.3070829826722864
    Paranid - Yaki - Boron - Duke's - Split - Arteus - Argon, 38.75185916848361, 0.2064417081311623
    Yaki - Boron - Duke's - Split - Arteus - Terran - Argon, 57.6921820779751, 0.138666968588351
    Yaki - Pirates - Boron - Duke's - Split - Terran - Argon, 23.81796786022678, 0.33588087980247316
    Paranid - Pirates - Boron - Split - Arteus - Terran - Argon, 23.07304423045161, 0.34672494535600407
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Argon, 20.19888944988625, 0.39606137851529516
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Argon, 27.373346145540395, 0.29225509944838596
    Paranid - OTAS - Boron - Duke's - Split - Terran - Argon, 33.823982431861616, 0.236518571286394
    OTAS - Pirates - Boron - Duke's - Split - Terran - Argon, 24.44460178063537, 0.32727062080174585
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Argon, 19.841239659081374, 0.40320061334163587
    Yaki - OTAS - Boron - Duke's - Split - Terran - Argon, 19.841239659081374, 0.40320061334163587
    Paranid - Yaki - OTAS - Boron - Split - Terran - Argon, 11.818874998582816, 0.6768833751908933
    Yaki - OTAS - Pirates - Boron - Split - Terran - Argon, 13.248724623111173, 0.6038317066417654
    Paranid - Pirates - Boron - Duke's - Split - Terran - Argon, 44.65939068666751, 0.17913365760246028
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Argon, 39.805294576815456, 0.20097828907060997
    Paranid - Yaki - Boron - Duke's - Split - Terran - Argon, 34.399246439542196, 0.2325632340249157
    Paranid - Yaki - Pirates - Boron - Split - Terran - Argon, 14.173569405670023, 0.5644308621933769
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - Argon, 16.195949481091045, 0.4939506639817623
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - Argon, 14.529172675624658, 0.550616348129819
    Paranid - OTAS - Boron - Duke's - Arteus - Terran - Argon, 21.325311824599293, 0.37514105612147697
    Yaki - OTAS - Boron - Duke's - Arteus - Terran - Argon, 12.580510682466073, 0.6359042332955448
    Yaki - OTAS - Pirates - Boron - Arteus - Terran - Argon, 12.745214747841883, 0.6276865598796302
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Terran - Argon, 8.408770507142412, 0.8324641508594149
    Paranid - Yaki - OTAS - Boron - Duke's - Terran - Argon, 13.884487734806305, 0.5761825825194266
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - Argon, 19.84544900812117, 0.40311509186444877
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - Argon, 26.891895603811676, 0.297487396123391
    Paranid - OTAS - Duke's - Split - Arteus - Terran - Argon, 33.31426482838556, 0.24013737181988076
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - Argon, 19.508061587841336, 0.4100868742892481
    Yaki - OTAS - Duke's - Split - Arteus - Terran - Argon, 19.538051943211094, 0.40945740257281726
    Paranid - OTAS - Pirates - Split - Arteus - Terran - Argon, 25.118346701071484, 0.3184922994815873
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - Argon, 25.251812780645764, 0.3168089384114076
    Paranid - Yaki - OTAS - Split - Arteus - Terran - Argon, 13.655293749309736, 0.5858533801518838
    Yaki - OTAS - Pirates - Split - Arteus - Terran - Argon, 16.694468402272694, 0.4792006434245563
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Terran - Argon, 9.451174852120513, 0.7406486610952335
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Terran - Argon, 8.418766049593184, 0.8314757719557081
    Paranid - Yaki - OTAS - Duke's - Arteus - Terran - Argon, 13.630244312269161, 0.5869300517818936
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Arteus, 15.690753461760389, 0.5098544196425389
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Arteus, 19.47189500699278, 0.4108485587626179
    Paranid - OTAS - Boron - Duke's - Split - Arteus - Terran, 24.77318678313149, 0.32292978977768594
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Arteus, 18.349498217476018, 0.435979224346354
    Yaki - OTAS - Boron - Duke's - Split - Arteus - Terran, 19.13340414749341, 0.41811691941123025
    Paranid - OTAS - Pirates - Boron - Split - Arteus - Terran, 20.490011060425072, 0.3904341474686367
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Arteus, 19.412160265430714, 0.4121128143706111
    Paranid - Yaki - OTAS - Boron - Split - Arteus - Terran, 11.654501870459724, 0.6864300241160313
    Yaki - OTAS - Pirates - Boron - Split - Arteus - Terran, 16.780376570290557, 0.4767473463118759
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Arteus - Terran, 8.237099046220255, 0.8498137464077331
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Terran, 13.448306581797267, 0.5948704360167003
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - Terran, 10.77746724125199, 0.7422894285754897
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Arteus, 14.554973669171563, 0.5496402935406576
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - Terran, 12.561210396916065, 0.6368812994298783
    OTAS - Boron - Split - Arteus - TerraCorp - Argon - NMMC, 123.1606273792324, 0.06495582370952567
    Yaki - Boron - Strong Arms - Arteus - TerraCorp - Argon - NMMC, 180.01801506714708, 0.044439996724861035
    Boron - Arteus - Terran - TerraCorp - Argon - NMMC, 4114.88387463056, 0.0021871820139293804
    Pirates - Boron - Split - Arteus - Strong Arms - TerraCorp - Argon - NMMC, 476.3674649050358, 0.014694538388333166
    Yaki - Pirates - Boron - Strong Arms - Split - TerraCorp - Argon - NMMC, 76.31237091375252, 0.09172824689081316
    Yaki - Strong Arms - Terran - Goner - TerraCorp - NMMC, 351.0086531291148, 0.025640393533801133
    Paranid - Boron - Arteus - TerraCorp - Argon - NMMC, 254.50124306611735, 0.035363285033786156
    Paranid - Yaki - Boron - Strong Arms - TerraCorp - Argon - NMMC, 914.6515550869808, 0.008746500189615074
    Paranid - Boron - Split - Terran - TerraCorp - Argon - NMMC, 349.30755474973733, 0.022902453414532155
    Pirates - Boron - Split - Terran - TerraCorp - Argon - NMMC, 624.0949080063336, 0.012818563166227294
    Paranid - Boron - Duke's - Arteus - TerraCorp - Argon - NMMC, 50.099753574429236, 0.15968142414343484
    Yaki - Boron - Duke's - Arteus - TerraCorp - Argon - NMMC, 88.12448492734765, 0.09078067243848777
    Boron - Duke's - Arteus - Terran - TerraCorp - Argon - NMMC, 70.24353273578075, 0.1138894883048066
    Pirates - Duke's - Strong Arms - Arteus - Goner - TerraCorp - Argon - NMMC, 509.68346179465004, 0.01373401439268257
    Yaki - Pirates - Duke's - Strong Arms - Goner - TerraCorp - NMMC, 216.63595389291953, 0.03692831155789727
    Yaki - Duke's - Terran - Goner - TerraCorp - NMMC, 208.54563344063652, 0.0431560222648435
    Paranid - Pirates - Strong Arms - Split - Goner - TerraCorp - Argon - NMMC, 304.79792447708877, 0.02296603565135556
    Paranid - Yaki - Pirates - Strong Arms - Goner - TerraCorp - Argon - NMMC, 318.4214191605481, 0.021983445769615768
    Terran - Paranid - Yaki - NMMC, 76.12231085408021, 0.14450428365326473
    Terran - Pirates - Yaki - NMMC, 67.18924030150454, 0.16371668961635338
    Paranid - OTAS - Boron - Strong Arms - Split - Argon - NMMC, 85.01022287626847, 0.09410632897226866
    Yaki - OTAS - Boron - Strong Arms - Split - Argon - NMMC, 202.6708113098482, 0.03947287696879744
    OTAS - Boron - Split - Terran - TerraCorp - Argon - NMMC, 92.73809465752821, 0.08626444213182445
    OTAS - Pirates - Boron - Split - TerraCorp - Argon - NMMC, 370.1789908381377, 0.021611167024597658
    Yaki - OTAS - Pirates - Boron - Argon - NMMC, 158.78235070303873, 0.05668136263350937
    Yaki - OTAS - Strong Arms - Terran - Goner - NMMC, 255.19714568977352, 0.03526685212592742
    Paranid - OTAS - Pirates - Boron - Strong Arms - TerraCorp - Argon - NMMC, 476.3674649050356, 0.014694538388333171
    Paranid - Yaki - OTAS - Boron - Argon - NMMC, 141.9261527609239, 0.06341325981801672
    Paranid - OTAS - Boron - Strong Arms - Terran - Argon - NMMC, 778.3977827860867, 0.01027752156662874
    OTAS - Pirates - Boron - Terran - TerraCorp - Argon - NMMC, 64.3057720686399, 0.1244056286496461
    Paranid - Pirates - Boron - Duke's - Strong Arms - TerraCorp - Argon - NMMC, 92.512950679957, 0.07566508200798913
    Paranid - Yaki - Boron - Duke's - Strong Arms - TerraCorp - Argon - NMMC, 122.25510204081614, 0.05725732409648619
    Paranid - Boron - Duke's - Strong Arms - Terran - TerraCorp - Argon - NMMC, 391.0939348254666, 0.01789851331528291
    Pirates - Duke's - Terran - Goner - TerraCorp - Argon - NMMC, 1077.5881970092262, 0.007423986289199774
    Paranid - Pirates - Boron - Terran - Goner - TerraCorp - NMMC, 611.3565585317951, 0.013085653352950723
    OTAS - Boron - Duke's - Arteus - TerraCorp - Argon - NMMC, 39.78131583024141, 0.20109943155571716
    Yaki - OTAS - Boron - Arteus - Argon - NMMC, 78.12119844711088, 0.11520560589061012
    OTAS - Boron - Arteus - Terran - TerraCorp - Argon - NMMC, 32.81969560171724, 0.24375606943720135
    OTAS - Pirates - Boron - Arteus - TerraCorp - Argon - NMMC, 101.70917112803662, 0.07865564050196809
    Yaki - Pirates - Boron - Arteus - Argon - NMMC, 161.2482702895777, 0.0558145522047297
    Yaki - Arteus - Terran - Goner - TerraCorp - NMMC, 87.5606911568681, 0.10278584923314708
    Paranid - OTAS - Boron - Arteus - Argon - NMMC, 175.58034574837626, 0.051258584562180305
    Paranid - Yaki - Strong Arms - Arteus - Goner - TerraCorp - Argon - NMMC, 357.23391599902595, 0.019595003963786817
    Paranid - Boron - Arteus - Terran - Goner - TerraCorp - NMMC, 118.29083335064531, 0.06762992341330358
    Pirates - Boron - Arteus - Terran - TerraCorp - Argon - NMMC, 36.55156389850204, 0.21886888402955193
    Paranid - Pirates - Boron - Arteus - Argon - NMMC, 257.28127622425325, 0.03498116976128243
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Goner - NMMC, 187.33099362608962, 0.042705159702338964
    Paranid - Duke's - Arteus - Terran - Goner - TerraCorp - NMMC, 232.79687534362102, 0.034364722413870716
    Pirates - Duke's - Arteus - Terran - TerraCorp - NMMC, 56.22653828611894, 0.16006676338852424
    Yaki - Pirates - Duke's - Arteus - Goner - NMMC, 1639.9456968929376, 0.005487986594343653
    Yaki - Duke's - Strong Arms - Terran - Arteus - Goner - NMMC, 130.09613633814837, 0.06149298684171717
    Paranid - Pirates - Strong Arms - Arteus - Terran - Goner - Argon - NMMC, 1089.3072995442255, 0.006426102168716627
    Paranid - Yaki - Pirates - Strong Arms - Arteus - Argon - NMMC, 54.213460190454, 0.14756482932274914
    Paranid - Yaki - Arteus - Terran - NMMC, 30.68040513712223, 0.32594093706736443
    Yaki - Pirates - Arteus - Terran - NMMC, 39.7087229458552, 0.25183383544304594
    Paranid - OTAS - Boron - Duke's - Strong Arms - TerraCorp - Argon - NMMC, 476.3674649050355, 0.014694538388333175
    Yaki - OTAS - Boron - Duke's - Strong Arms - Argon - NMMC, 361.2808296872444, 0.02214343896111367
    OTAS - Boron - Duke's - Terran - TerraCorp - Argon - NMMC, 94.29315101155296, 0.0848417930059398
    OTAS - Pirates - Boron - Duke's - Strong Arms - Argon - NMMC, 274.22259592565774, 0.029173380016316433
    Yaki - OTAS - Pirates - Duke's - Strong Arms - NMMC, 54.33247767170406, 0.16564678044651607
    Yaki - OTAS - Duke's - Terran - NMMC, 74.2118369962445, 0.13474939315282078
    Paranid - OTAS - Pirates - Strong Arms - Terran - Goner - TerraCorp - Argon - NMMC, 390.09393482546665, 0.015380910761108044
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Goner - Argon - NMMC, 133.44887455754295, 0.052454545032386994
    Paranid - Yaki - OTAS - Terran - NMMC, 39.3629209189021, 0.2540461877969527
    Yaki - OTAS - Pirates - Terran - NMMC, 42.59197701432992, 0.23478600198895522
    Paranid - Pirates - Duke's - Strong Arms - Terran - NMMC, 109.16085759737751, 0.08244713533852098
    Paranid - Yaki - Pirates - Duke's - Strong Arms - NMMC, 33.189777843221606, 0.2711678289174835
    Paranid - Yaki - Duke's - Terran - NMMC, 61.77043282558763, 0.16188975117327695
    Yaki - Pirates - Duke's - Terran - NMMC, 29.231819968819387, 0.3420929661809175
    Paranid - Yaki - Pirates - Terran - NMMC, 24.48744718828085, 0.4083724989016323
    Paranid - OTAS - Strong Arms - Split - Arteus - Goner - TerraCorp - Argon - NMMC, 91.51295067995702, 0.06556449065863318
    Yaki - OTAS - Strong Arms - Split - Arteus - Goner - TerraCorp - Argon - NMMC, 262.6265060240954, 0.02284613267272235
    OTAS - Duke's - Strong Arms - Split - Terran - Goner - TerraCorp - Argon - NMMC, 226.59601526070253, 0.026478841620833003
    Pirates - Duke's - Split - Arteus - Goner - TerraCorp - Argon - NMMC, 14308.868794324513, 0.0004892070855228254
    Yaki - Pirates - Strong Arms - Split - Arteus - Goner - Argon - NMMC, 305.0780593051548, 0.022944947322476046
    Yaki - Strong Arms - Split - Terran - Goner - TerraCorp - NMMC, 122.78628688936706, 0.06515385555398513
    Paranid - Pirates - Strong Arms - Split - Arteus - Goner - TerraCorp - NMMC, 311.4758350392808, 0.022473653531155047
    Paranid - Yaki - Strong Arms - Split - Goner - TerraCorp - Argon - NMMC, 238.64750865330373, 0.029331963444752664
    Paranid - Split - Terran - Arteus - Goner - TerraCorp - NMMC, 3320.611918718408, 0.002409194508669837
    Pirates - Split - Arteus - Terran - Goner - TerraCorp - Argon - NMMC, 211.32120992913448, 0.033124928644632574
    Paranid - Duke's - Strong Arms - Split - Arteus - Goner - TerraCorp - Argon - NMMC, 192.9112474437623, 0.031102385576295268
    Paranid - Yaki - Duke's - Strong Arms - Split - Goner - TerraCorp - NMMC, 522.4814814814802, 0.01339760402636992
    Paranid - Duke's - Strong Arms - Split - Terran - Goner - TerraCorp - Argon - NMMC, 217.69435569755046, 0.027561578162072272
    Pirates - Duke's - Split - Terran - Goner - TerraCorp - NMMC, 904.5534462080516, 0.00884414296749024
    Yaki - Pirates - Duke's - Strong Arms - Split - NMMC, 147.44022770185865, 0.06104168543607414
    Yaki - Duke's - Split - Terran - Goner - TerraCorp - NMMC, 183.39089796168452, 0.04362266660405045
    Paranid - Pirates - Split - Terran - Goner - NMMC, 339.63386021478215, 0.026499124658267172
    Paranid - Yaki - Pirates - Strong Arms - Split - NMMC, 27.01123477804522, 0.333194690059679
    Paranid - Yaki - Split - Terran - NMMC, 48.508887797191505, 0.20614778969595268
    Yaki - Pirates - Split - Terran - NMMC, 45.4126884973777, 0.22020277439811645
    Paranid - OTAS - Duke's - Strong Arms - Split - TerraCorp - Argon - NMMC, 91.57213461887594, 0.07644246832438781
    Yaki - OTAS - Duke's - Strong Arms - Split - TerraCorp - Argon - NMMC, 95.83018385147368, 0.07304587885221253
    Paranid - OTAS - Strong Arms - Split - Terran - Goner - TerraCorp - NMMC, 144.2012098337394, 0.048543282043686284
    OTAS - Pirates - Duke's - Strong Arms - Split - Goner - TerraCorp - NMMC, 237.15315476025648, 0.029516790561257594
    Yaki - OTAS - Pirates - Strong Arms - Split - Argon - NMMC, 44.26410259603033, 0.18073336023573766
    Yaki - OTAS - Split - Terran - Goner - NMMC, 129.5715462693063, 0.06945969434750794
    Paranid - OTAS - Pirates - Strong Arms - Split - Goner - NMMC, 414.2639822461459, 0.019311357836671858
    Paranid - Yaki - OTAS - Strong Arms - Split - Goner - NMMC, 81.2984524248763, 0.0984028571440814
    Paranid - Yaki - OTAS - Split - Terran - NMMC, 19.74562758480981, 0.45579711059291145
    OTAS - Pirates - Strong Arms - Split - Terran - Goner - Argon - NMMC, 335.7118774184465, 0.02085121340903552
    Paranid - Pirates - Duke's - Strong Arms - Split - NMMC, 91.18726168842174, 0.09869799611652064
    Paranid - Yaki - Pirates - Duke's - Split - NMMC, 76.07661840631597, 0.11830178823054534
    Paranid - Yaki - Duke's - Split - Terran - NMMC, 46.81699812772387, 0.1922378700028275
    Yaki - Pirates - Duke's - Split - Terran - NMMC, 26.90083188685102, 0.33456214431789194
    Paranid - Yaki - Pirates - Split - Terran - NMMC, 15.739886830174067, 0.5717957249061408
    Paranid - OTAS - Duke's - Strong Arms - Arteus - Goner - TerraCorp - Argon - NMMC, 475.367464905035, 0.012621814581270577
    Yaki - OTAS - Duke's - Strong Arms - Arteus - Goner - Argon - NMMC, 360.28082968724436, 0.0194292879975785
    OTAS - Duke's - Arteus - Terran - TerraCorp - Argon - NMMC, 93.29555214211213, 0.0857489967776173
    OTAS - Pirates - Duke's - Strong Arms - Arteus - Goner - Argon - NMMC, 273.22259592565746, 0.025620135758847216
    Yaki - OTAS - Pirates - Duke's - Arteus - NMMC, 59.8098968271885, 0.15047676851883085
    Yaki - OTAS - Arteus - Terran - Goner - NMMC, 142.67154189159567, 0.06308195650425057
    Paranid - OTAS - Arteus - Terran - Goner - TerraCorp - Argon - NMMC, 958.1104574628415, 0.0073060469651240415
    Paranid - Yaki - OTAS - Strong Arms - Arteus - Goner - Argon - NMMC, 229.8659094156305, 0.030452536514855695
    Paranid - Yaki - OTAS - Arteus - Terran - NMMC, 25.713945399224713, 0.35000463212741184
    Yaki - OTAS - Pirates - Arteus - Terran - NMMC, 32.68049661929549, 0.27539361181819205
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Goner - NMMC, 185.22980930819512, 0.04318959259245999
    Paranid - Yaki - Pirates - Duke's - Arteus - NMMC, 34.72006188180883, 0.25921612785821224
    Paranid - Yaki - Duke's - Arteus - Terran - NMMC, 22.393122694714922, 0.40190910944832725
    Yaki - Pirates - Duke's - Arteus - Terran - NMMC, 17.163290845445452, 0.5243749628812175
    Paranid - Yaki - Pirates - Arteus - Terran - NMMC, 17.930727621114602, 0.5019316666994547
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Goner - Argon - NMMC, 254.39606455975735, 0.027516148931445862
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Argon - NMMC, 108.26049840758684, 0.07389583567111459
    Paranid - OTAS - Duke's - Terran - Goner - TerraCorp - Argon - NMMC, 342.84972156337, 0.020417108603969416
    OTAS - Pirates - Duke's - Strong Arms - Terran - Goner - NMMC, 1148.8447796744572, 0.0069635168662792925
    Paranid - Yaki - OTAS - Pirates - Terran - NMMC, 21.739447701796305, 0.41399395805516903
    Paranid - Yaki - Pirates - Duke's - Terran - NMMC, 16.223570202673933, 0.5547484239021964
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - Goner - NMMC, 285.2860673670564, 0.024536774840089266
    Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - Goner - NMMC, 530.3544094519931, 0.013198721223479579
    OTAS - Boron - Duke's - Arteus - Terran - Goner - TerraCorp - NMMC, 119.25891646018077, 0.05869582088931038
    Pirates - Boron - Duke's - Strong Arms - Arteus - Goner - TerraCorp - NMMC, 350.17891710239894, 0.01998978138924642
    Yaki - Pirates - Boron - Strong Arms - Split - Arteus - Goner - TerraCorp - NMMC, 121.25510204081642, 0.04948245392577628
    Yaki - Boron - Terran - Goner - TerraCorp - NMMC, 169.9314530362969, 0.05296253188676981
    Paranid - Pirates - Boron - Split - Strong Arms - Goner - TerraCorp - NMMC, 304.79792447708866, 0.02296603565135557
    Paranid - Yaki - Boron - Strong Arms - Split - Goner - TerraCorp - NMMC, 238.647508653304, 0.029331963444752633
    Paranid - Boron - Strong Arms - Split - Arteus - Terran - Goner - NMMC, 366.41432275467895, 0.01910405670655682
    Pirates - Boron - Split - Arteus - Terran - Goner - TerraCorp - NMMC, 721.0125856946336, 0.009708568392403446
    Paranid - Boron - Duke's - Strong Arms - Split - Arteus - TerraCorp - NMMC, 91.57213461887596, 0.07644246832438778
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - TerraCorp - NMMC, 94.06906416019612, 0.07441341170439689
    Paranid - Boron - Duke's - Strong Arms - Split - Terran - Goner - TerraCorp - NMMC, 217.69435569755058, 0.027561578162072255
    Pirates - Boron - Duke's - Terran - Goner - TerraCorp - NMMC, 905.9120959070002, 0.008830878885649927
    Yaki - Pirates - Boron - Duke's - Strong Arms - Goner - NMMC, 460.141471122694, 0.017385957367591517
    Yaki - Boron - Duke's - Terran - TerraCorp - NMMC, 84.74537388465743, 0.10620048726493835
    Paranid - Pirates - Boron - Split - Terran - NMMC, 88.19547163960348, 0.10204605557048374
    Paranid - Yaki - Pirates - Boron - Strong Arms - NMMC, 109.0142772150666, 0.08255799359422007
    Paranid - Yaki - Boron - Terran - NMMC, 43.70617384742133, 0.2288006274562055
    Yaki - Pirates - Boron - Terran - NMMC, 41.862072010277856, 0.23887971903408958
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Goner - TerraCorp - NMMC, 192.9112474437624, 0.031102385576295254
    Paranid - Yaki - OTAS - Boron - Split - Goner - NMMC, 189.84510850486544, 0.04213961614815571
    Paranid - OTAS - Boron - Split - Terran - Goner - NMMC, 187.90203953955665, 0.042575376082151895
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Goner - NMMC, 181.8949554613649, 0.03848375004268232
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Goner - NMMC, 103.46768488350148, 0.067653973391611
    Yaki - OTAS - Boron - Terran - NMMC, 74.77164921905037, 0.1337405300597836
    Paranid - OTAS - Pirates - Boron - Split - Goner - NMMC, 274.4050155576691, 0.029153986065967936
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - NMMC, 64.1440098707215, 0.12471936219958078
    Paranid - Yaki - OTAS - Boron - Terran - NMMC, 21.183097830639554, 0.4248670365380772
    OTAS - Pirates - Boron - Split - Terran - Goner - TerraCorp - NMMC, 389.9698807357987, 0.017950104215208457
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - NMMC, 62.849290015952626, 0.1272886296403573
    Paranid - Yaki - Pirates - Boron - Duke's - NMMC, 101.04009353895368, 0.08907355174340033
    Paranid - Yaki - Boron - Duke's - Terran - NMMC, 41.83734951952695, 0.21511878986978814
    Yaki - Pirates - Boron - Duke's - Terran - NMMC, 25.715211055661648, 0.34998740552893476
    Paranid - Yaki - Pirates - Boron - Terran - NMMC, 17.578319036083656, 0.5119943483518175
    Paranid - OTAS - Boron - Duke's - Arteus - Goner - TerraCorp - NMMC, 133.77309845670763, 0.05232741171996833
    Paranid - Yaki - Boron - Strong Arms - Arteus - NMMC, 105.2692704552338, 0.08549503536102958
    Paranid - OTAS - Boron - Arteus - Terran - Goner - NMMC, 1313.469532088786, 0.006090738920512111
    OTAS - Pirates - Boron - Duke's - Arteus - Goner - NMMC, 414.6740394397924, 0.019292261485208167
    Yaki - Pirates - Boron - Duke's - Arteus - NMMC, 64.29314380811672, 0.13998382202090714
    Yaki - Boron - Arteus - Terran - Goner - NMMC, 229.81805510493754, 0.039161413997218356
    Paranid - Pirates - Boron - Arteus - Terran - NMMC, 77.87544707174649, 0.11556915996524961
    Paranid - Yaki - Pirates - Boron - Arteus - NMMC, 46.78105951214407, 0.19238555291086679
    Paranid - Yaki - Boron - Arteus - Terran - NMMC, 17.332007336234522, 0.5192704933365959
    Yaki - Pirates - Boron - Arteus - Terran - NMMC, 23.28128681930538, 0.3865765698370673
    Paranid - Pirates - Boron - Duke's - Arteus - NMMC, 65.21508205382642, 0.13800488654712864
    Paranid - Yaki - Boron - Duke's - Arteus - NMMC, 98.68624697796983, 0.09119811803167578
    Paranid - Boron - Duke's - Strong Arms - Arteus - Terran - Goner - NMMC, 4528.572278658551, 0.0015457410347601943
    Pirates - Boron - Duke's - Terran - Arteus - Goner - NMMC, 490.7147407364359, 0.016302750530774904
    Yaki - Boron - Arteus - Terran - TerraCorp - NMMC, 29.205420836941954, 0.308161969322349
    Paranid - Yaki - Pirates - Boron - Arteus - Terran - NMMC, 11.359079130132336, 0.7042824430000073
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - NMMC, 99.00214929023392, 0.0808063265025415
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - NMMC, 70.27126358760057, 0.1138445445772745
    Paranid - OTAS - Boron - Duke's - Terran - TerraCorp - NMMC, 130.7402805800013, 0.061190017066734985
    OTAS - Pirates - Boron - Duke's - Terran - NMMC, 137.5341529764757, 0.0654382915459507
    Yaki - OTAS - Pirates - Boron - Duke's - NMMC, 81.47064996293648, 0.11046923038044226
    Yaki - OTAS - Boron - Duke's - Terran - NMMC, 39.191645455729756, 0.2296407791851009
    Paranid - OTAS - Pirates - Boron - Terran - Goner - NMMC, 834.5634733900176, 0.009585849674805202
    Yaki - OTAS - Pirates - Boron - Terran - NMMC, 23.9229892355935, 0.3762071667285403
    Paranid - Pirates - Boron - Duke's - Terran - NMMC, 133.23071649404247, 0.06755198978759859
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - Goner - NMMC, 1348.0439702846365, 0.005192708957796062
    Paranid - Yaki - Strong Arms - Split - Arteus - Goner - NMMC, 133.08601171852757, 0.06011150155224225
    Paranid - OTAS - Split - Terran - Arteus - Goner - NMMC, 3320.6119187184368, 0.0024091945086698163
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Goner - NMMC, 109.1056577319972, 0.06415799277059052
    Yaki - Pirates - Duke's - Split - Arteus - Goner - NMMC, 235.2639416323718, 0.03400436099341123
    Yaki - Split - Terran - Arteus - TerraCorp - NMMC, 63.92289601610766, 0.14079462228576328
    Paranid - OTAS - Pirates - Strong Arms - Split - Arteus - Goner - NMMC, 105.2860742006528, 0.06648552577484743
    Paranid - Yaki - Pirates - Split - Arteus - NMMC, 64.756524815071, 0.13898213385758157
    Paranid - Yaki - Split - Terran - Arteus - NMMC, 22.49329144701676, 0.40011929873400776
    Yaki - Pirates - Split - Arteus - Terran - NMMC, 29.722064886903638, 0.3028053412253214
    Paranid - Pirates - Duke's - Split - Arteus - NMMC, 90.53985416803549, 0.09940373863753574
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - NMMC, 47.28149497342237, 0.16919938772022583
    Paranid - Duke's - Split - Terran - Arteus - TerraCorp - NMMC, 61.2807592803875, 0.13054668535349476
    Pirates - Duke's - Strong Arms - Split - Arteus - Terran - Goner - NMMC, 456.0010936700333, 0.015350840375539245
    Yaki - Duke's - Split - Terran - Arteus - Goner - NMMC, 1455.4346403060572, 0.005496639820471576
    Paranid - Pirates - Split - Arteus - Terran - NMMC, 60.66456847992669, 0.1483567793444045
    Paranid - OTAS - Pirates - Duke's - Split - NMMC, 73.2638003997846, 0.12284375026805817
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - NMMC, 31.101275115898307, 0.25722418036521505
    Paranid - OTAS - Duke's - Strong Arms - Split - Terran - NMMC, 92.1317152832526, 0.08683220512507069
    OTAS - Pirates - Duke's - Split - Terran - NMMC, 75.61061861531587, 0.1190309002203685
    Yaki - OTAS - Pirates - Duke's - Split - NMMC, 76.52411847953418, 0.11760997942638156
    Yaki - OTAS - Duke's - Split - Terran - NMMC, 51.24911488735735, 0.17561278901658087
    Paranid - OTAS - Pirates - Split - Terran - NMMC, 49.57354938382429, 0.18154842878643412
    Paranid - Yaki - OTAS - Pirates - Split - Goner - NMMC, 79.0102530996122, 0.10125268159708332
    Yaki - OTAS - Pirates - Split - Terran - NMMC, 23.034199769201223, 0.3907233630939418
    Paranid - Pirates - Duke's - Split - Terran - NMMC, 65.61332136327106, 0.13716726745428878
    Paranid - OTAS - Pirates - Duke's - Arteus - Goner - NMMC, 356.9731878501707, 0.022410646716015465
    Paranid - Yaki - OTAS - Duke's - Arteus - Goner - NMMC, 1011.5667125429497, 0.007908524371950734
    Paranid - OTAS - Duke's - Arteus - Terran - Goner - TerraCorp - NMMC, 78.76085587170488, 0.0888766370365812
    OTAS - Pirates - Duke's - Arteus - Terran - Goner - NMMC, 96.38311088917368, 0.08300209368837261
    Yaki - OTAS - Duke's - Arteus - Terran - NMMC, 33.902776787020386, 0.2654649811293815
    Paranid - Yaki - OTAS - Pirates - Arteus - Terran - NMMC, 17.28412539834786, 0.4628524623389215
    Paranid - Pirates - Duke's - Arteus - Terran - NMMC, 43.35934768575765, 0.2075676983248586
    Paranid - OTAS - Pirates - Duke's - Terran - NMMC, 66.54036788253715, 0.13525624048077978
    Paranid - Yaki - OTAS - Pirates - Duke's - NMMC, 77.16257616948857, 0.11663685230300484
    Paranid - Yaki - OTAS - Duke's - Terran - NMMC, 24.759786003691033, 0.3634926407949704
    Yaki - OTAS - Pirates - Duke's - Terran - NMMC, 16.14676398161307, 0.5573872269544932
    Paranid - OTAS - Boron - Split - Arteus - Argon - NMMC, 29.396737627909125, 0.2721390414562478
    Yaki - OTAS - Boron - Split - Arteus - Argon - NMMC, 45.311010149585464, 0.17655752925369705
    OTAS - Boron - Split - Arteus - Terran - Argon - NMMC, 464.5566997701332, 0.017220718168435567
    OTAS - Pirates - Boron - Split - Arteus - Argon - NMMC, 80.1996655173985, 0.09975103946368058
    Yaki - Pirates - Boron - Split - Arteus - Argon - NMMC, 103.9364327737121, 0.07697012285785686
    Yaki - Arteus - Terran - Goner - Argon - NMMC, 1037.896810255828, 0.00867138227140482
    Paranid - Pirates - Boron - Split - Strong Arms - Argon - NMMC, 164.4292905785416, 0.04865313212659459
    Paranid - Yaki - Boron - Strong Arms - Split - Argon - NMMC, 411.61990280325654, 0.01943540617331079
    Paranid - Boron - Arteus - Terran - Argon - NMMC, 809.5165238948218, 0.011117747117376129
    OTAS - Pirates - Boron - Split - Terran - Argon - NMMC, 54.856388084153565, 0.145835339864656
    Paranid - Pirates - Duke's - Strong Arms - Split - Argon - NMMC, 72.92912509871366, 0.10969554329866911
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Argon - NMMC, 303.547619047619, 0.02306063220644757
    Paranid - Boron - Duke's - Arteus - Terran - Argon - NMMC, 178.2136094227822, 0.04488994990849059
    Pirates - Duke's - Strong Arms - Terran - Arteus - Goner - Argon - NMMC, 749.6686807944686, 0.009337458238993901
    Yaki - Pirates - Duke's - Strong Arms - Goner - Argon - NMMC, 450.57759468340237, 0.01775498847345303
    Yaki - Split - Terran - Arteus - Goner - Argon - NMMC, 823.3254737098592, 0.009716691946809857
    Paranid - Pirates - Boron - Terran - Strong Arms - Argon - NMMC, 294.6800382743719, 0.027148089320360842
    Paranid - Yaki - Pirates - Boron - Argon - NMMC, 314.8599985074364, 0.028584132765875743
    Paranid - Yaki - Terran - Argon - NMMC, 63.887735517347174, 0.1565245648327094
    Yaki - Pirates - Terran - Argon - NMMC, 48.394855626894085, 0.20663353305764962
    Paranid - OTAS - Boron - Duke's - Split - Argon - NMMC, 364.8164374691128, 0.021928836473212147
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Argon - NMMC, 63.97516688100919, 0.10941745588596388
    Paranid - OTAS - Split - Terran - Goner - Argon - NMMC, 518.9901986774441, 0.01541454929281247
    OTAS - Pirates - Duke's - Strong Arms - Split - Argon - NMMC, 70.70564320857906, 0.1131451414196218
    Yaki - OTAS - Pirates - Boron - Split - Argon - NMMC, 36.59775525360611, 0.21859264166787198
    Yaki - OTAS - Terran - Argon - NMMC, 77.42913025497164, 0.129150359394072
    Paranid - OTAS - Pirates - Strong Arms - Split - Argon - NMMC, 43.09616133363512, 0.18563138229567247
    Paranid - Yaki - OTAS - Strong Arms - Split - Argon - NMMC, 28.412126716178065, 0.28156991132398207
    Paranid - Yaki - OTAS - Terran - Argon - NMMC, 27.572893246827324, 0.3264075307380224
    Yaki - OTAS - Pirates - Terran - Argon - NMMC, 26.25526017236808, 0.3427884523297127
    Paranid - Pirates - Duke's - Terran - Goner - Argon - NMMC, 775.5170422770946, 0.010315698513226968
    Paranid - Yaki - Pirates - Duke's - Goner - Argon - NMMC, 659.648378053663, 0.012127673266785767
    Paranid - Yaki - Duke's - Terran - Argon - NMMC, 57.13074142120199, 0.15753340103967176
    Yaki - Pirates - Duke's - Terran - Argon - NMMC, 27.76272855952716, 0.3241756292326507
    Paranid - Yaki - Pirates - Terran - Argon - NMMC, 21.824405246675855, 0.4123823718573416
    Paranid - OTAS - Boron - Duke's - Arteus - Argon - NMMC, 40.260939664894956, 0.19870375770130136
    Yaki - OTAS - Boron - Duke's - Arteus - Argon - NMMC, 31.427427971506464, 0.2545547159396297
    OTAS - Boron - Duke's - Arteus - Terran - Argon - NMMC, 120.25891646018077, 0.06652313388046283
    OTAS - Pirates - Boron - Duke's - Arteus - Argon - NMMC, 30.467095221632498, 0.2625783633721594
    Yaki - OTAS - Pirates - Boron - Arteus - Argon - NMMC, 27.328549976651626, 0.2927341555565468
    Yaki - OTAS - Arteus - Terran - Argon - NMMC, 38.90213510750837, 0.23134976975243038
    Paranid - OTAS - Pirates - Boron - Arteus - Argon - NMMC, 44.389963348902654, 0.18022091924520062
    Paranid - Yaki - Boron - Arteus - Argon - NMMC, 57.108792137870395, 0.15759394767573545
    Paranid - OTAS - Boron - Arteus - Terran - Argon - NMMC, 33.33690576965602, 0.23997428121483833
    OTAS - Pirates - Boron - Arteus - Terran - Argon - NMMC, 60.55081490073136, 0.13212043492916514
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Argon - NMMC, 80.87215673089756, 0.09892156118229954
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Argon - NMMC, 72.46160946163393, 0.11040328885098448
    Paranid - Yaki - Arteus - Terran - Argon - NMMC, 24.885371872486054, 0.36165824831215987
    Yaki - Pirates - Duke's - Arteus - Argon - NMMC, 125.63742602187406, 0.07163470539768188
    Paranid - Pirates - Boron - Arteus - Terran - Argon - NMMC, 34.644881584009525, 0.23091434100015598
    Paranid - Yaki - Pirates - Boron - Arteus - Argon - NMMC, 21.87819636241261, 0.3656608555604811
    Yaki - Pirates - Arteus - Terran - Argon - NMMC, 27.911317670072908, 0.3224498429771371
    Paranid - OTAS - Pirates - Boron - Duke's - Argon - NMMC, 66.07208536596579, 0.12107987746548193
    Paranid - Yaki - OTAS - Boron - Duke's - Argon - NMMC, 61.634475747020616, 0.1297974859530904
    Paranid - OTAS - Boron - Duke's - Terran - Argon - NMMC, 131.73904236181542, 0.06072611320513744
    OTAS - Pirates - Duke's - Terran - Goner - Argon - NMMC, 189.26286839124444, 0.042269252643167124
    Yaki - OTAS - Pirates - Duke's - Argon - NMMC, 113.89735815620045, 0.07901851408754602
    Yaki - OTAS - Duke's - Terran - Argon - NMMC, 40.210977323619296, 0.22381947913296654
    Paranid - OTAS - Pirates - Boron - Terran - Argon - NMMC, 49.94208493848533, 0.16018554311166144
    Paranid - Yaki - OTAS - Pirates - Boron - Argon - NMMC, 36.516960362383394, 0.21907628457052264
    Paranid - Yaki - Pirates - Duke's - Terran - Argon - NMMC, 15.900417795986314, 0.5031314335664445
    Paranid - OTAS - Duke's - Split - Arteus - Goner - Argon - NMMC, 363.8164374691126, 0.019240472059743833
    Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - Argon - NMMC, 63.17785245244622, 0.11079832137803164
    Paranid - OTAS - Split - Terran - Arteus - Argon - NMMC, 60.97746476040824, 0.13119600874574702
    OTAS - Pirates - Duke's - Split - Arteus - Argon - NMMC, 67.56824333427058, 0.11839881585233406
    Yaki - OTAS - Pirates - Split - Arteus - Argon - NMMC, 99.60899147777214, 0.08031403472030142
    Yaki - OTAS - Split - Terran - Argon - NMMC, 41.34595809613683, 0.21767544917143705
    Paranid - Pirates - Strong Arms - Split - Arteus - Argon - NMMC, 86.04532073753877, 0.09297425974391028
    Paranid - Yaki - Strong Arms - Split - Arteus - Argon - NMMC, 51.447083537019935, 0.15549958228911878
    Paranid - Yaki - Split - Terran - Argon - NMMC, 45.25063488192406, 0.19889223705886974
    OTAS - Pirates - Split - Arteus - Terran - Goner - Argon - NMMC, 211.32120992913445, 0.033124928644632574
    Paranid - Pirates - Duke's - Split - Arteus - Argon - NMMC, 61.98426676879573, 0.12906500983290456
    Paranid - Yaki - Duke's - Split - Arteus - Goner - Argon - NMMC, 1687.1752235721192, 0.004148946654858686
    Paranid - Duke's - Strong Arms - Split - Arteus - Terran - Goner - Argon - NMMC, 1695.9223300970793, 0.00353789787039159
    Pirates - Duke's - Split - Terran - Arteus - Goner - Argon - NMMC, 1067.8904165216322, 0.006554979698011178
    Yaki - Pirates - Duke's - Strong Arms - Split - Argon - NMMC, 86.24794823549337, 0.09275582971732403
    Paranid - Pirates - Split - Terran - Argon - NMMC, 164.20441025173704, 0.05480973371057671
    Paranid - Yaki - Pirates - Split - Goner - Argon - NMMC, 272.3059532409793, 0.029378718697788943
    Yaki - Pirates - Split - Terran - Argon - NMMC, 37.349782546844104, 0.24096525833081353
    Paranid - OTAS - Pirates - Duke's - Split - Argon - NMMC, 39.81353395024938, 0.20093669680256782
    Paranid - Yaki - OTAS - Duke's - Split - Argon - NMMC, 108.26049840758685, 0.07389583567111459
    Paranid - OTAS - Duke's - Split - Terran - Argon - NMMC, 111.17913836287323, 0.07195594531313163
    OTAS - Pirates - Duke's - Split - Terran - Argon - NMMC, 39.93539490862691, 0.20032354802811345
    Yaki - OTAS - Pirates - Duke's - Split - Argon - NMMC, 35.05938816249976, 0.22818424448595953
    Yaki - OTAS - Duke's - Split - Terran - Argon - NMMC, 30.27576905092694, 0.2642377138807996
    Paranid - OTAS - Pirates - Split - Terran - Argon - NMMC, 29.759541437876308, 0.268821346481436
    Paranid - Yaki - OTAS - Pirates - Split - Argon - NMMC, 32.775411264493336, 0.24408541926266106
    Paranid - Yaki - OTAS - Split - Terran - Argon - NMMC, 15.62431554079419, 0.5120224293417821
    Yaki - OTAS - Pirates - Split - Terran - Argon - NMMC, 16.135017166475443, 0.4958160203648257
    Paranid - Pirates - Duke's - Split - Terran - Argon - NMMC, 61.70933478528149, 0.12964002979186398
    Paranid - Yaki - Pirates - Duke's - Split - Argon - NMMC, 64.91859520916339, 0.12323125560903672
    Paranid - Yaki - Duke's - Split - Terran - Argon - NMMC, 44.57160379298841, 0.17948647388045044
    Yaki - Pirates - Duke's - Split - Terran - Argon - NMMC, 25.746555458017085, 0.3107211763936726
    Paranid - Yaki - Pirates - Split - Terran - Argon - NMMC, 15.02483515193438, 0.5324517653007352
    Paranid - OTAS - Pirates - Duke's - Arteus - Argon - NMMC, 65.19731408078641, 0.12270444132233957
    Paranid - Yaki - OTAS - Duke's - Arteus - Argon - NMMC, 60.76181387753217, 0.131661638938632
    Paranid - OTAS - Duke's - Arteus - Terran - Goner - Argon - NMMC, 130.7390423618155, 0.053541772018092015
    OTAS - Pirates - Duke's - Arteus - Terran - Argon - NMMC, 43.156056832104724, 0.1853737479103658
    Yaki - OTAS - Pirates - Duke's - Arteus - Argon - NMMC, 29.05701649663753, 0.27532076463960975
    Yaki - Strong Arms - Terran - Arteus - Argon - NMMC, 146.67270688553185, 0.061361109310022435
    Paranid - OTAS - Pirates - Arteus - Terran - Goner - Argon - NMMC, 318.4303474850646, 0.021982829385720916
    Paranid - Yaki - OTAS - Pirates - Arteus - Goner - Argon - NMMC, 155.15412481082944, 0.04511642863852121
    Paranid - Yaki - OTAS - Arteus - Terran - Argon - NMMC, 18.32107761613101, 0.43665553782471317
    Yaki - OTAS - Pirates - Arteus - Terran - Argon - NMMC, 20.144905382733203, 0.39712273887655175
    Paranid - Pirates - Duke's - Arteus - Terran - Argon - NMMC, 36.89270324576436, 0.2168450478325542
    Paranid - Yaki - Pirates - Duke's - Arteus - Argon - NMMC, 27.89026857007019, 0.28683839956224083
    Paranid - Yaki - Duke's - Arteus - Terran - Argon - NMMC, 20.43926589898794, 0.39140348971124855
    Yaki - Pirates - Duke's - Arteus - Terran - Argon - NMMC, 15.827006184696078, 0.5054651465123959
    Paranid - Yaki - Pirates - Arteus - Terran - Argon - NMMC, 15.097053128421749, 0.5299047391533107
    Paranid - OTAS - Pirates - Duke's - Terran - Argon - NMMC, 46.04523557851215, 0.17374218851284032
    Paranid - Yaki - OTAS - Pirates - Duke's - Argon - NMMC, 44.04728661163273, 0.1816229923658278
    Paranid - Yaki - OTAS - Duke's - Terran - Argon - NMMC, 20.478567913992205, 0.3906523167830458
    Yaki - OTAS - Pirates - Duke's - Terran - Argon - NMMC, 13.88170734978342, 0.5762979868700959
    Paranid - Yaki - OTAS - Pirates - Terran - Argon - NMMC, 17.383754387171244, 0.46019978318974586
    Paranid - OTAS - Boron - Duke's - Split - Arteus - NMMC, 76.12490097828051, 0.10509044868619942
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Goner - NMMC, 121.2551020408163, 0.04948245392577633
    Paranid - OTAS - Boron - Split - Arteus - Terran - NMMC, 39.266835965433735, 0.20373426590933716
    OTAS - Pirates - Boron - Duke's - Split - Arteus - NMMC, 66.14102633983673, 0.12095367191454666
    Yaki - OTAS - Pirates - Boron - Split - Arteus - Goner - NMMC, 119.58127295094862, 0.05853759394977632
    Yaki - Boron - Split - Arteus - Terran - Goner - NMMC, 229.81029992932963, 0.03481132047806443
    Paranid - Pirates - Boron - Split - Arteus - Goner - NMMC, 172.5380157290669, 0.046366593276244955
    Paranid - Yaki - Boron - Split - Arteus - NMMC, 126.87538808980968, 0.07093574361033114
    Paranid - Yaki - Boron - Split - Terran - NMMC, 36.25575271842884, 0.2482364680136758
    OTAS - Pirates - Boron - Split - Arteus - Terran - Goner - NMMC, 721.0125856946343, 0.009708568392403437
    Paranid - Pirates - Boron - Duke's - Split - Arteus - NMMC, 34.41853855922229, 0.23243287875906737
    Paranid - Yaki - Boron - Duke's - Split - Arteus - NMMC, 69.50898976926985, 0.11509302647837973
    Paranid - Boron - Duke's - Split - Arteus - Terran - Goner - NMMC, 357.3778426872521, 0.019587112472794873
    Pirates - Boron - Duke's - Split - Arteus - Terran - Goner - NMMC, 243.12293904855395, 0.028792017846584333
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - NMMC, 104.07129473417129, 0.07687038025648046
    Yaki - Boron - Duke's - Split - Arteus - Terran - NMMC, 107.32113473855347, 0.07454263337309015
    Paranid - Pirates - Boron - Split - Arteus - Terran - NMMC, 28.408054358601174, 0.2816102749950498
    Paranid - Yaki - Pirates - Boron - Split - NMMC, 93.25490025204525, 0.09650967376164894
    Yaki - Pirates - Boron - Split - Terran - NMMC, 35.330637458428804, 0.25473641709945644
    Paranid - OTAS - Pirates - Boron - Duke's - Split - NMMC, 33.05783452329638, 0.24200012237227075
    Paranid - Yaki - OTAS - Boron - Duke's - Split - NMMC, 70.27126358760057, 0.1138445445772745
    Paranid - OTAS - Boron - Duke's - Split - Terran - NMMC, 79.17819959614684, 0.10103791246586157
    OTAS - Pirates - Boron - Duke's - Split - Terran - NMMC, 44.25618367290512, 0.1807656995263653
    Yaki - OTAS - Pirates - Boron - Duke's - Split - NMMC, 37.20244117351633, 0.21503965190582816
    Yaki - OTAS - Boron - Split - Terran - NMMC, 48.625557699635124, 0.1850878514462269
    Paranid - OTAS - Pirates - Boron - Split - Terran - NMMC, 25.898572598347037, 0.30889733284028925
    Paranid - Yaki - OTAS - Pirates - Boron - Split - NMMC, 27.008824709480287, 0.29619948613283953
    Paranid - Yaki - OTAS - Boron - Split - Terran - NMMC, 14.069864541748933, 0.568591117296256
    Yaki - OTAS - Pirates - Boron - Split - Terran - NMMC, 16.77457950748794, 0.47691210360467823
    Paranid - Pirates - Boron - Duke's - Split - Terran - NMMC, 48.279367276199814, 0.16570225442750872
    Paranid - Yaki - Pirates - Boron - Duke's - Split - NMMC, 45.78793327094657, 0.1747185214204934
    Paranid - Yaki - Boron - Duke's - Split - Terran - NMMC, 36.08903772286153, 0.22167396264301592
    Yaki - Pirates - Boron - Duke's - Split - Terran - NMMC, 24.515143263439022, 0.3263289108300217
    Paranid - Yaki - Pirates - Boron - Split - Terran - NMMC, 13.413678270745349, 0.5964061339869507
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - NMMC, 29.55020371138942, 0.2707257140469929
    Paranid - Yaki - OTAS - Boron - Arteus - NMMC, 104.43835706296457, 0.08617523535509097
    Paranid - OTAS - Boron - Duke's - Arteus - Terran - NMMC, 45.55247755785652, 0.1756216221135095
    OTAS - Pirates - Boron - Duke's - Arteus - Terran - NMMC, 34.170962453210585, 0.23411690586573888
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - NMMC, 22.55386837710806, 0.35470633534954543
    Yaki - OTAS - Boron - Arteus - Terran - NMMC, 33.935488517931546, 0.2652090891588135
    Paranid - OTAS - Pirates - Boron - Arteus - Terran - NMMC, 54.03836769038989, 0.14804296173110923
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - NMMC, 37.568552974089286, 0.21294405471292793
    Paranid - Yaki - OTAS - Boron - Arteus - Terran - NMMC, 13.296797018449313, 0.6016486518445002
    Yaki - OTAS - Pirates - Boron - Arteus - Terran - NMMC, 17.45368982987981, 0.45835580200952214
    Paranid - Pirates - Boron - Duke's - Arteus - Terran - NMMC, 23.761349965988952, 0.33668120756820974
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - NMMC, 17.730379896557153, 0.4512029661334793
    Paranid - Yaki - Boron - Duke's - Arteus - Terran - NMMC, 15.2670952311997, 0.5240027574892747
    Yaki - Pirates - Boron - Duke's - Arteus - Terran - NMMC, 14.035099955227667, 0.5699995030687496
    Paranid - OTAS - Pirates - Boron - Duke's - Terran - NMMC, 32.510271285436566, 0.24607607638093482
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - NMMC, 29.364867835054834, 0.27243439490130644
    Paranid - Yaki - OTAS - Boron - Duke's - Terran - NMMC, 16.923336014513225, 0.47272003540787155
    Yaki - OTAS - Pirates - Boron - Duke's - Terran - NMMC, 12.980508070888618, 0.6163086958007136
    Paranid - Yaki - OTAS - Pirates - Boron - Terran - NMMC, 14.007092868818372, 0.5711392131774218
    Paranid - Yaki - Pirates - Boron - Duke's - Terran - NMMC, 13.955364931666612, 0.5732562379538293
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - NMMC, 28.53053082093662, 0.28040137248793645
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - NMMC, 40.85192581451617, 0.19582920120640457
    Paranid - OTAS - Duke's - Split - Arteus - Terran - NMMC, 61.280759280387514, 0.1305466853534947
    OTAS - Pirates - Duke's - Split - Arteus - Terran - NMMC, 38.40675138857626, 0.20829671114489332
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - NMMC, 31.512924591746255, 0.2538640923887886
    Yaki - OTAS - Split - Terran - Arteus - NMMC, 63.922896016107664, 0.14079462228576325
    Paranid - OTAS - Pirates - Split - Arteus - Terran - NMMC, 34.82989097255682, 0.2296877703781319
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - NMMC, 40.09370365388577, 0.19953257671232033
    Paranid - Yaki - OTAS - Split - Arteus - Terran - NMMC, 15.207384027183707, 0.5260602340086719
    Yaki - OTAS - Pirates - Split - Arteus - Terran - NMMC, 19.99680050904885, 0.4000640000574032
    Paranid - Pirates - Duke's - Split - Arteus - Terran - NMMC, 24.682233020685867, 0.3241197825697254
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - NMMC, 21.93192971944889, 0.3647649843098725
    Paranid - Yaki - Duke's - Split - Arteus - Terran - NMMC, 19.6762416034818, 0.406581712159113
    Yaki - Pirates - Duke's - Split - Arteus - Terran - NMMC, 16.34155010607208, 0.489549641745884
    Paranid - Yaki - Pirates - Split - Arteus - Terran - NMMC, 11.95218761573993, 0.6693335360185224
    Paranid - OTAS - Pirates - Duke's - Split - Terran - NMMC, 20.33230227031866, 0.39346257465778955
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - NMMC, 22.15780064569386, 0.3610466637876678
    Paranid - Yaki - OTAS - Duke's - Split - Terran - NMMC, 16.499455644000264, 0.4848644811448103
    Yaki - OTAS - Pirates - Duke's - Split - Terran - NMMC, 12.590226112326768, 0.6354135286075129
    Paranid - Yaki - OTAS - Pirates - Split - Terran - NMMC, 11.532427868741598, 0.6936960795292577
    Paranid - Yaki - Pirates - Duke's - Split - Terran - NMMC, 13.12028158104536, 0.6097430112748082
    Paranid - OTAS - Pirates - Duke's - Arteus - Terran - NMMC, 28.915302283409186, 0.27667011472296393
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - NMMC, 25.408274079964343, 0.31485806453529985
    Paranid - Yaki - OTAS - Duke's - Arteus - Terran - NMMC, 15.56110594668168, 0.5141022770110987
    Yaki - OTAS - Pirates - Duke's - Arteus - Terran - NMMC, 12.158701860676521, 0.6579649778134187
    Paranid - Yaki - Pirates - Duke's - Arteus - Terran - NMMC, 10.624619997649297, 0.7529681063200382
    Paranid - Yaki - OTAS - Pirates - Duke's - Terran - NMMC, 12.06089016199467, 0.663300958100835
    OTAS - Boron - Duke's - Split - Arteus - TerraCorp - Argon - NMMC, 27.92389360543429, 0.25068137341125396
    Yaki - OTAS - Boron - Split - TerraCorp - Argon - NMMC, 216.2417735405379, 0.03699562701977319
    Boron - Split - Arteus - Terran - TerraCorp - Argon - NMMC, 464.55669977013304, 0.017220718168435574
    OTAS - Pirates - Boron - Split - Arteus - TerraCorp - Argon - NMMC, 27.92389360543429, 0.25068137341125396
    Yaki - Pirates - Boron - Arteus - TerraCorp - Argon - NMMC, 36.35759997701205, 0.2200365262024498
    Yaki - Terran - TerraCorp - Argon - NMMC, 136.09628621020838, 0.07347739073904219
    Paranid - Boron - Split - Arteus - TerraCorp - Argon - NMMC, 58.823305735821684, 0.13600051714074668
    Paranid - Yaki - Boron - Arteus - Goner - TerraCorp - NMMC, 174.7801736940584, 0.04577178195281744
    Paranid - Boron - Arteus - Terran - TerraCorp - Argon - NMMC, 22.886615942076908, 0.3495492745737061
    Pirates - Boron - Split - Arteus - Terran - TerraCorp - Argon - NMMC, 27.071957880083218, 0.25857014224855474
    Paranid - Boron - Duke's - Split - Arteus - TerraCorp - Argon - NMMC, 36.277487951952885, 0.19295713113518315
    Yaki - Boron - Duke's - Split - Arteus - TerraCorp - Argon - NMMC, 88.09929078014181, 0.07945580421832237
    Boron - Duke's - Split - Terran - Arteus - TerraCorp - Argon - NMMC, 69.09843400447427, 0.10130475604623304
    Pirates - Boron - Duke's - Arteus - TerraCorp - Argon - NMMC, 38.81622864403928, 0.20609936306185947
    Yaki - Pirates - Boron - Duke's - TerraCorp - Argon - NMMC, 424.3028549412612, 0.018854457156804866
    Yaki - Duke's - Terran - TerraCorp - Argon - NMMC, 75.86989471781857, 0.11862412665094009
    Paranid - Pirates - Boron - Arteus - TerraCorp - Argon - NMMC, 43.33974503700938, 0.18458807252254275
    Paranid - Yaki - Pirates - Boron - TerraCorp - Argon - NMMC, 102.99626691553885, 0.07767271804676501
    Paranid - Yaki - Terran - TerraCorp - NMMC, 40.179936581441595, 0.24888043264405807
    Yaki - Pirates - Terran - TerraCorp - NMMC, 41.37338916903827, 0.2417012529271711
    Paranid - OTAS - Boron - Split - TerraCorp - Argon - NMMC, 96.38820795140512, 0.08299770449133428
    Yaki - OTAS - Boron - Duke's - TerraCorp - Argon - NMMC, 194.03744783076368, 0.04122915493599705
    OTAS - Boron - Duke's - Split - Terran - TerraCorp - Argon - NMMC, 43.33600815182777, 0.16152849093703991
    OTAS - Pirates - Boron - Duke's - TerraCorp - Argon - NMMC, 97.26561169461898, 0.08224900723512936
    Yaki - OTAS - Pirates - Boron - TerraCorp - Argon - NMMC, 79.70165606213853, 0.10037432589559855
    Yaki - OTAS - Terran - Goner - TerraCorp - NMMC, 147.70148843086415, 0.06093371228423811
    Paranid - OTAS - Pirates - Split - Goner - TerraCorp - Argon - NMMC, 370.7943409679595, 0.01887838951836882
    Paranid - Yaki - OTAS - Boron - TerraCorp - Argon - NMMC, 72.5561815080633, 0.11025938567496066
    Paranid - OTAS - Boron - Terran - TerraCorp - Argon - NMMC, 53.61277070866516, 0.1492181786961255
    OTAS - Pirates - Split - Terran - TerraCorp - Argon - NMMC, 83.68916934696463, 0.09559181985464593
    Paranid - Pirates - Boron - Duke's - Split - Goner - TerraCorp - NMMC, 746.1139185143068, 0.009381945338774397
    Paranid - Yaki - Pirates - Duke's - Goner - TerraCorp - NMMC, 574.9406754292859, 0.013914479079127096
    Paranid - Boron - Duke's - Split - Terran - TerraCorp - Argon - NMMC, 230.40250541090037, 0.030381614069326997
    Pirates - Boron - Duke's - Terran - TerraCorp - Argon - NMMC, 82.01866001915316, 0.09753877956713539
    Paranid - Pirates - Boron - Terran - TerraCorp - Argon - NMMC, 56.39133288704047, 0.14186577245877643
    Paranid - OTAS - Boron - Arteus - TerraCorp - Argon - NMMC, 39.26340690303668, 0.2037520590038576
    Yaki - OTAS - Boron - Arteus - TerraCorp - Argon - NMMC, 28.954678471734127, 0.2762938641439133
    OTAS - Boron - Duke's - Arteus - Terran - TerraCorp - Argon - NMMC, 15.098971722990512, 0.4636077296138929
    OTAS - Pirates - Duke's - Arteus - Goner - TerraCorp - Argon - NMMC, 96.26561169461897, 0.07271547831852902
    Yaki - OTAS - Pirates - Boron - Arteus - TerraCorp - Argon - NMMC, 18.559646874555032, 0.37716234836325924
    Yaki - Arteus - Terran - TerraCorp - Argon - NMMC, 30.527454561139766, 0.2948165881952255
    Paranid - OTAS - Pirates - Boron - Arteus - TerraCorp - Argon - NMMC, 25.776156822503328, 0.2715688008962142
    Paranid - Yaki - OTAS - Boron - Arteus - TerraCorp - NMMC, 79.79540161060166, 0.10025640373413593
    Paranid - OTAS - Boron - Arteus - Terran - TerraCorp - NMMC, 74.09020011709885, 0.10797649334670546
    OTAS - Pirates - Boron - Arteus - Terran - TerraCorp - Argon - NMMC, 20.404996958546484, 0.3430532243754195
    Paranid - Pirates - Duke's - Arteus - Goner - TerraCorp - NMMC, 514.1239597337822, 0.0155604496708196
    Paranid - Yaki - Duke's - Arteus - Goner - TerraCorp - Argon - NMMC, 106.9999515839568, 0.06542059034958998
    Paranid - Duke's - Arteus - Terran - TerraCorp - Argon - NMMC, 55.92841009886501, 0.1430400039239154
    Pirates - Duke's - Arteus - Terran - TerraCorp - Argon - NMMC, 30.04892193839422, 0.2662325129800484
    Yaki - Pirates - Duke's - Arteus - Goner - TerraCorp - NMMC, 99.37387982238407, 0.08050405211408473
    Yaki - Duke's - Arteus - Terran - TerraCorp - NMMC, 29.60819105643141, 0.30396993800960515
    Paranid - Pirates - Arteus - Terran - TerraCorp - Argon - NMMC, 88.68367796574029, 0.09020825684620916
    Paranid - Yaki - Pirates - Arteus - Goner - TerraCorp - Argon - NMMC, 198.0873089657641, 0.03533795292867463
    Paranid - Yaki - Arteus - Terran - TerraCorp - NMMC, 22.136421014996206, 0.4065697880385902
    Yaki - Pirates - Arteus - Terran - TerraCorp - NMMC, 28.051763681252524, 0.32083544201589204
    Paranid - OTAS - Pirates - Boron - Duke's - Goner - TerraCorp - NMMC, 335.6094611645723, 0.02085757646911933
    Paranid - Yaki - OTAS - Boron - Duke's - TerraCorp - Argon - NMMC, 36.810924369747895, 0.19016094053190277
    Paranid - OTAS - Boron - Duke's - Terran - TerraCorp - Argon - NMMC, 29.64663213723313, 0.2361145093175261
    OTAS - Pirates - Duke's - Terran - Goner - TerraCorp - NMMC, 120.7121608177998, 0.06627335593863669
    Yaki - OTAS - Pirates - Duke's - TerraCorp - Argon - NMMC, 71.26726449219964, 0.1122535017585194
    Yaki - OTAS - Duke's - Terran - TerraCorp - NMMC, 34.74106816752381, 0.25905939208896467
    Paranid - OTAS - Pirates - Boron - Terran - Goner - TerraCorp - NMMC, 140.25851679784085, 0.049907842745045755
    Paranid - Yaki - OTAS - Pirates - Boron - TerraCorp - Argon - NMMC, 31.17140837008854, 0.22456476514924043
    Paranid - Yaki - OTAS - Terran - TerraCorp - NMMC, 31.74316105894022, 0.28352563827178195
    Yaki - OTAS - Pirates - Terran - TerraCorp - NMMC, 34.75300344721485, 0.258970422906607
    Paranid - Pirates - Duke's - Terran - TerraCorp - NMMC, 70.88715196510515, 0.1269623584881832
    Paranid - Yaki - Duke's - Terran - TerraCorp - NMMC, 28.51708849570552, 0.31560024093467115
    Yaki - Pirates - Duke's - Terran - TerraCorp - NMMC, 17.697031025127874, 0.5085598814411848
    Paranid - Yaki - Pirates - Terran - TerraCorp - NMMC, 21.057758165477054, 0.4273959235962243
    Paranid - OTAS - Duke's - Split - Arteus - TerraCorp - Argon - NMMC, 51.573106631054415, 0.13572965557566383
    Yaki - OTAS - Duke's - Arteus - Goner - TerraCorp - Argon - NMMC, 193.03744783076354, 0.036262394051836615
    OTAS - Duke's - Split - Terran - Arteus - TerraCorp - Argon - NMMC, 42.65519800053066, 0.1641066113422546
    OTAS - Pirates - Duke's - Split - Goner - TerraCorp - Argon - NMMC, 161.00078402504033, 0.04347804914360725
    Yaki - OTAS - Pirates - Split - Arteus - TerraCorp - Argon - NMMC, 63.07219705319562, 0.1109839252007686
    Yaki - Split - Terran - TerraCorp - Argon - NMMC, 103.97931798546014, 0.08655567447805829
    Paranid - Pirates - Split - Arteus - Goner - TerraCorp - Argon - NMMC, 299.38522914929405, 0.02338124703042487
    Paranid - Yaki - Split - Arteus - Goner - TerraCorp - Argon - NMMC, 173.5385811535953, 0.04033685162957769
    Paranid - Split - Terran - Arteus - TerraCorp - Argon - NMMC, 60.977464760408225, 0.13119600874574705
    OTAS - Pirates - Split - Arteus - Terran - TerraCorp - Argon - NMMC, 42.65519800053066, 0.1641066113422546
    Paranid - Pirates - Duke's - Split - Arteus - TerraCorp - NMMC, 42.776575634751296, 0.1870182426080145
    Paranid - Yaki - Duke's - Split - Arteus - Goner - TerraCorp - NMMC, 199.91671301508867, 0.035014581294519766
    Paranid - Duke's - Split - Terran - Arteus - TerraCorp - Argon - NMMC, 33.039357127017354, 0.21186852919350155
    Pirates - Duke's - Split - Terran - TerraCorp - Argon - NMMC, 116.99975075206834, 0.068376214039572
    Yaki - Pirates - Duke's - Split - Arteus - TerraCorp - NMMC, 61.16096402785867, 0.1308023855928108
    Yaki - Duke's - Split - Terran - TerraCorp - Argon - NMMC, 71.6975699596816, 0.11157979279491227
    Paranid - Pirates - Split - Terran - TerraCorp - NMMC, 74.63817412216758, 0.12058172786044875
    Paranid - Yaki - Pirates - Split - TerraCorp - Argon - NMMC, 127.15438793491946, 0.06291564239288844
    Paranid - Yaki - Split - Terran - TerraCorp - NMMC, 25.743950754570427, 0.34959669111401614
    Yaki - Pirates - Split - Terran - TerraCorp - NMMC, 27.570228668046397, 0.3264390770335142
    Paranid - OTAS - Pirates - Duke's - Split - TerraCorp - NMMC, 58.54370068046903, 0.13665005640254832
    Paranid - Yaki - OTAS - Split - Goner - TerraCorp - Argon - NMMC, 238.84989663100413, 0.02930710918755055
    Paranid - OTAS - Split - Terran - TerraCorp - Argon - NMMC, 58.24610808978795, 0.13734823256633358
    OTAS - Pirates - Duke's - Split - Terran - TerraCorp - NMMC, 34.913213473251744, 0.229139606588465
    Yaki - OTAS - Pirates - Duke's - Split - TerraCorp - NMMC, 61.16096402785867, 0.1308023855928108
    Yaki - OTAS - Split - Terran - TerraCorp - NMMC, 54.24669817128624, 0.16590871524718648
    Paranid - OTAS - Pirates - Split - Terran - TerraCorp - NMMC, 38.553920678374396, 0.2075015941112144
    Paranid - Yaki - OTAS - Pirates - Split - Goner - TerraCorp - NMMC, 78.70165606213858, 0.08894349052163754
    Paranid - Yaki - OTAS - Split - Terran - TerraCorp - NMMC, 16.514021479879, 0.4844368169041898
    Yaki - OTAS - Pirates - Split - Terran - TerraCorp - NMMC, 19.370109420068516, 0.41300747592636483
    Paranid - Pirates - Duke's - Split - Terran - TerraCorp - NMMC, 28.72206310073385, 0.27853152372594014
    Paranid - Yaki - Pirates - Duke's - Split - TerraCorp - NMMC, 53.892200282079855, 0.14844448655142675
    Paranid - Yaki - Duke's - Split - Terran - TerraCorp - NMMC, 22.79560928412055, 0.35094477626324333
    Yaki - Pirates - Duke's - Split - Terran - TerraCorp - NMMC, 15.829745789875973, 0.5053776672216971
    Paranid - Yaki - Pirates - Split - Terran - TerraCorp - NMMC, 12.963647968896893, 0.6171102469917453
    Paranid - OTAS - Pirates - Duke's - Arteus - Goner - TerraCorp - NMMC, 127.52913829379585, 0.05488941659649356
    Paranid - Yaki - OTAS - Duke's - Arteus - Goner - TerraCorp - NMMC, 190.23717819882697, 0.03679617236901994
    Paranid - OTAS - Duke's - Arteus - Terran - TerraCorp - Argon - NMMC, 29.09299032767477, 0.24060778631412238
    OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp - NMMC, 35.33633183165039, 0.22639588166971203
    Yaki - OTAS - Pirates - Duke's - Arteus - TerraCorp - NMMC, 45.771034458291396, 0.17478302805871596
    Yaki - OTAS - Arteus - Terran - TerraCorp - NMMC, 58.768551882727344, 0.15314313032520355
    Paranid - OTAS - Pirates - Arteus - Terran - TerraCorp - Argon - NMMC, 73.32727383753974, 0.09546243346655506
    Paranid - Yaki - OTAS - Pirates - Arteus - Goner - TerraCorp - Argon - NMMC, 121.2551020408163, 0.04948245392577633
    Paranid - Yaki - OTAS - Arteus - Terran - TerraCorp - NMMC, 21.16888581587046, 0.37791313485201683
    Yaki - OTAS - Pirates - Arteus - Terran - TerraCorp - NMMC, 26.58135096710979, 0.30096288220635337
    Paranid - Pirates - Duke's - Arteus - Terran - TerraCorp - NMMC, 22.541508292026403, 0.35490082989831856
    Paranid - Yaki - Pirates - Duke's - Arteus - TerraCorp - NMMC, 27.9878123003684, 0.28583870415247487
    Paranid - Yaki - Duke's - Arteus - Terran - TerraCorp - NMMC, 13.67399839499781, 0.585051992029379
    Yaki - Pirates - Duke's - Arteus - Terran - TerraCorp - NMMC, 11.01435555476985, 0.7263248367296024
    Paranid - Yaki - Pirates - Arteus - Terran - TerraCorp - NMMC, 15.777532302809947, 0.5070501423454679
    Paranid - OTAS - Pirates - Duke's - Terran - TerraCorp - NMMC, 40.089078907354484, 0.1995555951407098
    Paranid - Yaki - OTAS - Pirates - Duke's - TerraCorp - NMMC, 71.11437254815469, 0.11249484054131034
    Paranid - Yaki - OTAS - Duke's - Terran - TerraCorp - NMMC, 18.81810711681665, 0.42512246052903296
    Yaki - OTAS - Pirates - Duke's - Terran - TerraCorp - NMMC, 13.026769427229876, 0.6141200275854724
    Paranid - Yaki - OTAS - Pirates - Terran - TerraCorp - NMMC, 19.958784114315698, 0.40082601997092077
    Paranid - Yaki - Pirates - Duke's - Terran - TerraCorp - NMMC, 12.514324257658943, 0.639267437481004
    Paranid - OTAS - Boron - Split - Arteus - Goner - TerraCorp - NMMC, 428.1765028392399, 0.016348398274036467
    Yaki - OTAS - Boron - Duke's - Arteus - Goner - TerraCorp - NMMC, 147.54206457480666, 0.04744409684229995
    OTAS - Boron - Duke's - Split - Arteus - Terran - TerraCorp - NMMC, 68.16505367854035, 0.10269191649156924
    Pirates - Boron - Duke's - Split - Arteus - Goner - TerraCorp - NMMC, 700.0160459258726, 0.009999770777741938
    Yaki - OTAS - Pirates - Boron - Split - Arteus - TerraCorp - NMMC, 87.09974927995695, 0.08036762514092348
    Yaki - Boron - Split - Terran - TerraCorp - NMMC, 144.4552309790335, 0.06230303976535316
    Paranid - Pirates - Boron - Split - Arteus - TerraCorp - NMMC, 70.36942730372769, 0.11368573408265062
    Paranid - Yaki - Boron - Split - Arteus - TerraCorp - NMMC, 52.564113823166906, 0.15219508935151324
    Paranid - Boron - Split - Arteus - Terran - TerraCorp - NMMC, 39.26683596543375, 0.20373426590933708
    OTAS - Pirates - Boron - Split - Arteus - Terran - TerraCorp - NMMC, 68.16505367854035, 0.10269191649156924
    Paranid - Pirates - Boron - Duke's - Arteus - TerraCorp - NMMC, 31.030192871106564, 0.2578134152510897
    Paranid - Yaki - Boron - Duke's - Arteus - TerraCorp - NMMC, 37.09437271925415, 0.21566613514527855
    Paranid - Boron - Duke's - Arteus - Terran - TerraCorp - NMMC, 31.835478697579795, 0.25129196504301904
    Pirates - Boron - Duke's - Split - Terran - TerraCorp - NMMC, 149.5837291641917, 0.05348175262577349
    Yaki - Pirates - Boron - Duke's - Arteus - TerraCorp - NMMC, 29.792461311620105, 0.26852430607603806
    Yaki - Boron - Duke's - Split - Terran - TerraCorp - NMMC, 83.48173505368142, 0.09582934512388543
    Paranid - Pirates - Boron - Split - Terran - TerraCorp - NMMC, 37.344553612895574, 0.2142213315206824
    Paranid - Yaki - Pirates - Boron - Split - TerraCorp - NMMC, 69.45613398478183, 0.11518061171894246
    Paranid - Yaki - Boron - Terran - TerraCorp - NMMC, 23.76013516867898, 0.3787857239071584
    Yaki - Pirates - Boron - Terran - TerraCorp - NMMC, 25.46142478921802, 0.3534758983248718
    OTAS - Pirates - Boron - Duke's - Split - Goner - TerraCorp - NMMC, 14308.868794325463, 0.0004892070855227929
    Paranid - Yaki - OTAS - Boron - Split - Goner - TerraCorp - NMMC, 136.20365904391912, 0.0513936266406972
    Paranid - OTAS - Boron - Split - Terran - TerraCorp - NMMC, 57.63465227932353, 0.13880538328275827
    OTAS - Pirates - Boron - Duke's - Terran - TerraCorp - NMMC, 43.184044359476616, 0.1852536074066074
    Yaki - OTAS - Pirates - Boron - Duke's - TerraCorp - NMMC, 61.382754824655834, 0.13032976481509448
    Yaki - OTAS - Boron - Terran - TerraCorp - NMMC, 38.655536547516014, 0.23282563906303702
    Paranid - OTAS - Pirates - Boron - Split - Goner - TerraCorp - NMMC, 186.98940200045973, 0.03743527667938523
    Paranid - Yaki - OTAS - Pirates - Boron - Split - TerraCorp - NMMC, 26.312577628059465, 0.26603246929845714
    Paranid - Yaki - OTAS - Boron - Terran - TerraCorp - NMMC, 17.2172965603796, 0.4646490215199975
    Yaki - OTAS - Pirates - Boron - Terran - TerraCorp - NMMC, 19.541055329174238, 0.4093944705256644
    Paranid - Pirates - Boron - Duke's - Terran - TerraCorp - NMMC, 37.80835571024317, 0.21159343879725012
    Paranid - Yaki - Pirates - Boron - Duke's - TerraCorp - NMMC, 63.60249259482626, 0.12578123393627438
    Paranid - Yaki - Boron - Duke's - Terran - TerraCorp - NMMC, 20.638558840463062, 0.3876239645335869
    Yaki - Pirates - Boron - Duke's - Terran - TerraCorp - NMMC, 15.02424811129144, 0.5324725697246452
    Paranid - Yaki - Pirates - Boron - Terran - TerraCorp - NMMC, 14.262900123838103, 0.5608957456435743
    OTAS - Pirates - Boron - Duke's - Arteus - TerraCorp - NMMC, 65.96744268069078, 0.12127194377874022
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - NMMC, 27.972793928146857, 0.2859921686961065
    Paranid - OTAS - Boron - Duke's - Arteus - Terran - TerraCorp - NMMC, 20.548003143563385, 0.340665706107444
    Pirates - Boron - Duke's - Terran - Arteus - TerraCorp - NMMC, 26.72053977387582, 0.29939514948801493
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - TerraCorp - NMMC, 17.774169255161787, 0.39382993936367144
    Yaki - OTAS - Boron - Arteus - Terran - TerraCorp - NMMC, 20.861487163393996, 0.3834817689334122
    Paranid - Pirates - Boron - Arteus - Terran - TerraCorp - NMMC, 38.102369505473455, 0.20996069545886875
    Paranid - Yaki - Pirates - Boron - Arteus - TerraCorp - NMMC, 40.55863206096457, 0.19724531113315225
    Paranid - Yaki - Boron - Arteus - Terran - TerraCorp - NMMC, 11.802362674489867, 0.6778303819871205
    Yaki - Pirates - Boron - Arteus - Terran - TerraCorp - NMMC, 15.567147592210102, 0.5139027527434281
    Paranid - Pirates - Boron - Duke's - Arteus - Terran - TerraCorp - NMMC, 13.076867990989827, 0.5352963725582542
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - TerraCorp - NMMC, 13.722366469373172, 0.510116095181049
    Paranid - Yaki - Boron - Duke's - Arteus - Terran - TerraCorp, 9.783002372076396, 0.8177448696970967
    Yaki - Boron - Duke's - Arteus - Terran - TerraCorp - NMMC, 18.408113974949643, 0.4345909641197713
    Paranid - Yaki - Pirates - Boron - Arteus - Terran - TerraCorp - NMMC, 9.265083257838242, 0.7555247810728537
    Paranid - OTAS - Pirates - Boron - Duke's - Terran - TerraCorp - NMMC, 22.26574580812928, 0.31438425913603496
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - TerraCorp - NMMC, 27.02131290201701, 0.2590547700395966
    Yaki - OTAS - Boron - Duke's - Terran - TerraCorp - NMMC, 21.786910010576037, 0.3671929610998785
    Yaki - OTAS - Pirates - Boron - Duke's - Terran - TerraCorp - NMMC, 10.261632833083398, 0.6821526470360616
    Paranid - Yaki - OTAS - Pirates - Boron - Terran - TerraCorp - NMMC, 12.554695313329312, 0.5575603250656433
    Paranid - Yaki - Pirates - Boron - Duke's - Terran - TerraCorp - NMMC, 10.392867540942765, 0.673538845022652
    OTAS - Pirates - Duke's - Split - Arteus - Goner - TerraCorp - NMMC, 202.34023851168104, 0.034595194962152284
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - NMMC, 51.94104000905209, 0.1540207896993551
    Paranid - OTAS - Split - Terran - Arteus - Goner - TerraCorp - NMMC, 98.05676030823105, 0.07138722488889333
    Pirates - Duke's - Split - Terran - Arteus - TerraCorp - NMMC, 38.40675138857626, 0.20829671114489332
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - TerraCorp - NMMC, 25.761662713204558, 0.2717215918059527
    Yaki - OTAS - Split - Terran - Arteus - TerraCorp - NMMC, 34.663614324316384, 0.2307895514054353
    Paranid - Pirates - Split - Arteus - Terran - TerraCorp - NMMC, 34.82989097255681, 0.22968777037813196
    Paranid - Yaki - Pirates - Split - Arteus - TerraCorp - NMMC, 57.746124309508275, 0.1385374359865524
    Paranid - Yaki - Split - Terran - Arteus - TerraCorp - NMMC, 15.207384027183704, 0.526060234008672
    Yaki - Pirates - Split - Arteus - Terran - TerraCorp - NMMC, 19.99680050904885, 0.4000640000574032
    Paranid - Pirates - Duke's - Split - Arteus - Terran - TerraCorp - NMMC, 14.408376318428104, 0.48582851011790285
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - TerraCorp - NMMC, 17.679736684420185, 0.39593349861192056
    Yaki - Duke's - Split - Terran - Arteus - TerraCorp - NMMC, 28.92617775434061, 0.27656609414285765
    Yaki - Pirates - Duke's - Split - Arteus - Terran - TerraCorp - NMMC, 10.161331258595006, 0.6888861136260094
    Paranid - Yaki - Pirates - Split - Arteus - Terran - TerraCorp - NMMC, 10.005446763427946, 0.699618934117615
    Paranid - OTAS - Duke's - Split - Terran - Goner - TerraCorp - NMMC, 80.2375859093694, 0.08724090986369774
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - TerraCorp - NMMC, 21.082053724911578, 0.33203596249868483
    Yaki - OTAS - Duke's - Split - Terran - TerraCorp - NMMC, 26.809011089428616, 0.2984071278613696
    Yaki - OTAS - Pirates - Duke's - Split - Terran - TerraCorp - NMMC, 10.161331258595006, 0.6888861136260094
    Paranid - Yaki - OTAS - Pirates - Split - Terran - TerraCorp - NMMC, 10.616931220969951, 0.6593242297900549
    Paranid - Yaki - Pirates - Duke's - Split - Terran - TerraCorp - NMMC, 9.961707209310557, 0.7026907991691984
    Paranid - OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp - NMMC, 19.657113157013715, 0.35610518920487466
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - TerraCorp - NMMC, 23.064469208479835, 0.3034971209060556
    Yaki - OTAS - Duke's - Arteus - Terran - TerraCorp - NMMC, 19.02396199704861, 0.4205222866425577
    Yaki - OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp - NMMC, 9.461620695950952, 0.7398309681760559
    Paranid - Yaki - OTAS - Pirates - Arteus - Terran - TerraCorp - NMMC, 15.671495214738133, 0.44667084436314064
    Paranid - Yaki - Pirates - Duke's - Arteus - Terran - TerraCorp - NMMC, 8.164326124937542, 0.8573885820923831
    Paranid - Yaki - OTAS - Pirates - Duke's - Terran - TerraCorp - NMMC, 10.467330243012563, 0.6687474109907663
    Paranid - OTAS - Boron - Duke's - Split - Arteus - Argon - NMMC, 21.21533855823751, 0.3299499548774363
    Yaki - OTAS - Boron - Duke's - Split - Arteus - Argon - NMMC, 26.634215710757786, 0.26281982829975503
    OTAS - Boron - Duke's - Split - Arteus - Terran - Argon - NMMC, 69.09843400447426, 0.10130475604623307
    OTAS - Pirates - Boron - Duke's - Split - Argon - NMMC, 68.38851934314161, 0.11697869871783217
    Yaki - OTAS - Pirates - Boron - Split - Arteus - Argon - NMMC, 17.600692804282787, 0.3977116172550143
    Yaki - Boron - Split - Arteus - Terran - Argon - NMMC, 66.26045941677624, 0.1207356554786354
    Paranid - Pirates - Boron - Split - Arteus - Argon - NMMC, 44.9846357931537, 0.17783849660993667
    Paranid - Yaki - Boron - Split - Arteus - Argon - NMMC, 42.98570222357557, 0.18610839386526035
    Paranid - Boron - Split - Arteus - Terran - Argon - NMMC, 127.90261297710913, 0.06254758846429329
    OTAS - Pirates - Boron - Split - Arteus - Terran - Argon - NMMC, 27.071957880083218, 0.25857014224855474
    Paranid - Pirates - Boron - Duke's - Arteus - Argon - NMMC, 37.362058335450094, 0.21412096539685
    Paranid - Yaki - Boron - Duke's - Arteus - Argon - NMMC, 43.50807706127392, 0.18387390434960674
    Paranid - Boron - Duke's - Split - Arteus - Terran - Argon - NMMC, 101.1078546307151, 0.06923299901443564
    Pirates - Boron - Duke's - Terran - Arteus - Argon - NMMC, 103.0875997428236, 0.07760390211779004
    Yaki - Pirates - Boron - Duke's - Arteus - Argon - NMMC, 35.49709518017914, 0.22537055382681112
    Yaki - Duke's - Split - Terran - Arteus - Argon - NMMC, 182.83317695427024, 0.04375573478111655
    Paranid - Pirates - Boron - Split - Terran - Argon - NMMC, 63.96195910506331, 0.12507434281147137
    Paranid - Yaki - Pirates - Boron - Split - Argon - NMMC, 54.93318357361174, 0.14563146498290627
    Paranid - Yaki - Boron - Terran - Argon - NMMC, 38.42446440486668, 0.23422577619221407
    Yaki - Pirates - Boron - Terran - Argon - NMMC, 32.257066674263655, 0.2790086306012649
    Paranid - OTAS - Pirates - Boron - Split - Argon - NMMC, 32.945681232806244, 0.24282393626858317
    Paranid - Yaki - OTAS - Boron - Split - Argon - NMMC, 30.86273825851592, 0.2592122556653757
    Paranid - OTAS - Boron - Split - Terran - Argon - NMMC, 39.264584533356846, 0.2037459480362941
    OTAS - Pirates - Boron - Duke's - Terran - Argon - NMMC, 43.74394239249595, 0.18288246469006778
    Yaki - OTAS - Pirates - Boron - Duke's - Argon - NMMC, 29.552730620545706, 0.2707025656180219
    Yaki - OTAS - Boron - Terran - Argon - NMMC, 27.067117699622255, 0.3325067744514815
    Paranid - OTAS - Pirates - Boron - Split - Terran - Argon - NMMC, 16.16438710598396, 0.43305075250323855
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Argon - NMMC, 14.677425761382967, 0.47692286875109574
    Paranid - Yaki - OTAS - Boron - Terran - Argon - NMMC, 14.747030861369726, 0.5424820816613486
    Yaki - OTAS - Pirates - Boron - Terran - Argon - NMMC, 14.841309028399149, 0.5390360098756677
    Paranid - Pirates - Boron - Duke's - Terran - Argon - NMMC, 100.2366754656185, 0.07981110669162232
    Paranid - Yaki - Pirates - Boron - Duke's - Argon - NMMC, 68.58582033554742, 0.11664218581714143
    Paranid - Yaki - Boron - Duke's - Terran - Argon - NMMC, 38.0597020850507, 0.2101960751590403
    Yaki - Pirates - Boron - Duke's - Terran - Argon - NMMC, 23.99530411253237, 0.3333985667563065
    Paranid - Yaki - Pirates - Boron - Terran - Argon - NMMC, 15.763516185351872, 0.5075009855627223
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - Argon - NMMC, 15.686381933578785, 0.4462469439823832
    Paranid - Yaki - OTAS - Boron - Arteus - Argon - NMMC, 19.68872367376393, 0.40632395134176946
    Paranid - OTAS - Boron - Duke's - Arteus - Terran - Argon - NMMC, 20.929399629598244, 0.3344577543495628
    OTAS - Pirates - Boron - Duke's - Arteus - Terran - Argon - NMMC, 17.872744632901124, 0.3916578087908232
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - Argon - NMMC, 12.148271795052642, 0.5762136473478257
    Yaki - OTAS - Boron - Arteus - Terran - Argon - NMMC, 14.96305867430701, 0.5346500454306684
    Paranid - OTAS - Pirates - Boron - Arteus - Terran - Argon - NMMC, 20.31733262975576, 0.34453341526476494
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - Argon - NMMC, 14.296626833407846, 0.4896259853158264
    Paranid - Yaki - OTAS - Boron - Arteus - Terran - Argon, 10.611482853519721, 0.7539002899435946
    Yaki - Pirates - Boron - Arteus - Terran - Argon - NMMC, 16.849688817192828, 0.47478621633873036
    Paranid - Pirates - Boron - Duke's - Arteus - Terran - Argon - NMMC, 19.743659222830523, 0.35454420687658394
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Argon - NMMC, 14.171581886587983, 0.49394626909116024
    Paranid - Yaki - Boron - Arteus - Terran - Argon - NMMC, 14.138209824744395, 0.5658425005122338
    Yaki - Pirates - Boron - Duke's - Arteus - Terran - Argon - NMMC, 12.47081103697342, 0.5613107262427779
    Paranid - Yaki - Pirates - Boron - Arteus - Terran - Argon - NMMC, 9.38548657428802, 0.7458324024645486
    Paranid - OTAS - Pirates - Boron - Duke's - Terran - Argon - NMMC, 22.565316368354846, 0.31021058538388857
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Argon - NMMC, 18.692954784437436, 0.37447263317770146
    Yaki - OTAS - Boron - Duke's - Terran - Argon - NMMC, 22.134214972623443, 0.3614313861998154
    Yaki - OTAS - Pirates - Boron - Duke's - Terran - Argon - NMMC, 10.432741965695325, 0.6709645482479315
    Paranid - Yaki - OTAS - Pirates - Boron - Terran - Argon - NMMC, 10.645973351888262, 0.6575255985173417
    Paranid - Yaki - Pirates - Boron - Duke's - Terran - Argon - NMMC, 13.49352485136336, 0.5187673404175585
    Paranid - OTAS - Pirates - Split - Arteus - Argon - NMMC, 74.40875184830507, 0.10751423456624247
    Paranid - Yaki - OTAS - Split - Arteus - Argon - NMMC, 48.50121455196945, 0.1649443230216005
    Paranid - OTAS - Duke's - Split - Arteus - Terran - Argon - NMMC, 33.039357127017354, 0.21186852919350155
    OTAS - Pirates - Duke's - Split - Arteus - Terran - Argon - NMMC, 23.725074652053003, 0.2950464899546383
    Yaki - Pirates - Duke's - Split - Arteus - Argon - NMMC, 88.37647630104364, 0.09052182588440141
    Yaki - OTAS - Split - Terran - Arteus - Argon - NMMC, 26.948912820085077, 0.29685798656922385
    Paranid - Pirates - Split - Arteus - Terran - Argon - NMMC, 42.26861131201896, 0.18926574002977056
    Paranid - Yaki - Pirates - Split - Arteus - Argon - NMMC, 36.76450038366187, 0.2176012162960114
    Paranid - Yaki - Split - Terran - Arteus - Argon - NMMC, 19.906123382146973, 0.40188638673740407
    Yaki - Pirates - Split - Arteus - Terran - Argon - NMMC, 23.24830042406836, 0.344111176046134
    Paranid - Pirates - Duke's - Split - Arteus - Terran - Argon - NMMC, 22.789954891982276, 0.30715286770763495
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Argon - NMMC, 19.31773199752411, 0.36236137870103835
    Paranid - Yaki - Duke's - Split - Arteus - Terran - Argon - NMMC, 18.291149821124073, 0.3826987405633649
    Yaki - Pirates - Duke's - Split - Arteus - Terran - Argon - NMMC, 15.181040610513389, 0.4611014606701112
    Paranid - Yaki - Pirates - Split - Arteus - Terran - Argon - NMMC, 10.911073237924029, 0.641550088369844
    Paranid - OTAS - Pirates - Duke's - Split - Terran - Argon - NMMC, 17.031416092340553, 0.41100516610289806
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Argon - NMMC, 17.165017111474263, 0.40780617662890206
    Paranid - Yaki - OTAS - Duke's - Split - Terran - Argon - NMMC, 13.975309558291288, 0.5008833593848396
    Yaki - OTAS - Pirates - Duke's - Split - Terran - Argon - NMMC, 10.774635067375602, 0.6496739756128931
    Paranid - Yaki - OTAS - Pirates - Split - Terran - Argon - NMMC, 9.809364970236757, 0.7136037879352194
    Paranid - Yaki - Pirates - Duke's - Split - Terran - Argon - NMMC, 12.974017503341738, 0.5395398918027511
    Paranid - OTAS - Pirates - Duke's - Arteus - Terran - Argon - NMMC, 22.186653661873304, 0.3155049926266782
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - Argon - NMMC, 18.32423498083148, 0.38200776225160415
    Yaki - OTAS - Duke's - Arteus - Terran - Argon - NMMC, 21.780935218695394, 0.3672936868722377
    Yaki - OTAS - Pirates - Duke's - Arteus - Terran - Argon - NMMC, 10.24104395798073, 0.6835240653903236
    Paranid - Yaki - OTAS - Pirates - Arteus - Terran - Argon - NMMC, 13.510853402262912, 0.5181019874605094
    Paranid - Yaki - Pirates - Duke's - Arteus - Terran - Argon - NMMC, 10.149057821586982, 0.6897191959150182
    Paranid - Yaki - OTAS - Pirates - Duke's - Terran - Argon - NMMC, 11.036342775050727, 0.6342680852414739
    Paranid - OTAS - Pirates - Boron - Split - Arteus - NMMC, 42.28493249120352, 0.1891926870561808
    Paranid - Yaki - OTAS - Boron - Split - Arteus - NMMC, 29.904807846519486, 0.2675155125910997
    Paranid - OTAS - Boron - Duke's - Split - Arteus - Terran - NMMC, 24.412011851603463, 0.28674408494276626
    OTAS - Pirates - Boron - Duke's - Split - Arteus - Terran - NMMC, 23.39776583253336, 0.29917386344070807
    Yaki - Pirates - Boron - Duke's - Split - Arteus - NMMC, 58.277815734437205, 0.13727350449191053
    Yaki - OTAS - Boron - Split - Arteus - Terran - NMMC, 27.821916411049088, 0.28754309666543715
    Paranid - OTAS - Pirates - Boron - Split - Arteus - Terran - NMMC, 17.459785232154324, 0.4009213118560385
    Paranid - Yaki - Pirates - Boron - Split - Arteus - NMMC, 23.21914942005757, 0.34454319817113116
    Paranid - Yaki - Boron - Split - Arteus - Terran - NMMC, 15.371921363324262, 0.5204294122325615
    Yaki - Pirates - Boron - Split - Arteus - Terran - NMMC, 21.04343765224906, 0.38016602288100887
    Paranid - Pirates - Boron - Duke's - Split - Arteus - Terran - NMMC, 17.788491370301077, 0.3935128535794164
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Arteus - NMMC, 14.440469963459684, 0.4847487663291342
    Paranid - Yaki - Boron - Duke's - Split - Arteus - Terran - NMMC, 14.412632839395298, 0.48568502909935324
    Yaki - Pirates - Boron - Duke's - Split - Arteus - Terran - NMMC, 13.800045843857582, 0.5072446917352603
    Paranid - Yaki - Pirates - Boron - Split - Arteus - Terran - NMMC, 9.12375208461837, 0.767228212152018
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Terran - NMMC, 15.498530069044646, 0.4516557356610975
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Split - NMMC, 15.181782664245528, 0.4610789229966803
    Yaki - OTAS - Boron - Duke's - Split - Terran - NMMC, 32.816470166877465, 0.243780027508096
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Terran - NMMC, 10.774635067375602, 0.6496739756128931
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Terran - NMMC, 8.975001496964802, 0.7799441596045733
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Terran - NMMC, 11.932074293445863, 0.5866540743754011
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - Terran - NMMC, 15.704041019083236, 0.4457451423804701
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Arteus - NMMC, 12.602510315774936, 0.5554448934858551
    Yaki - OTAS - Boron - Duke's - Arteus - Terran - NMMC, 19.661740691950044, 0.4068815739837002
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - Terran - NMMC, 9.136989917466162, 0.7661166383273427
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - Terran - NMMC, 10.215579098054755, 0.6852279183402276
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Terran - NMMC, 8.313970525814062, 0.8419563165716895
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Terran - NMMC, 9.585227997276245, 0.7302904012287587
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - Terran - NMMC, 14.408376318428104, 0.48582851011790285
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Arteus - NMMC, 13.815843234388954, 0.5066646951071601
    Yaki - OTAS - Duke's - Split - Arteus - Terran - NMMC, 28.926177754340607, 0.2765660941428577
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - Terran - NMMC, 10.161331258595006, 0.6888861136260094
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - Terran - NMMC, 10.005446763427948, 0.6996189341176149
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Terran - NMMC, 9.002967546770492, 0.7775214076508598
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Terran - NMMC, 8.37860433862869, 0.8354613390355745
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - Terran - NMMC, 9.034428288017613, 0.7748138318042901
    OTAS - Boron - Duke's - Strong Arms - Split - Arteus - TerraCorp - Argon, 23.80756434950096, 0.29402419740374364
    Yaki - OTAS - Boron - Strong Arms - Arteus - TerraCorp - Argon, 30.53234019019233, 0.26201725613452254
    Boron - Strong Arms - Split - Arteus - Terran - TerraCorp - Argon, 527.050803572924, 0.015178802395836024
    OTAS - Pirates - Boron - Split - Strong Arms - Arteus - TerraCorp - Argon, 29.448318512222656, 0.23770457376351112
    Yaki - Pirates - Boron - Strong Arms - Arteus - TerraCorp - Argon, 33.843242308921546, 0.23638397074889866
    Yaki - Boron - Strong Arms - Terran - TerraCorp - Argon, 34.05112074182326, 0.26430848101119203
    Paranid - Boron - Strong Arms - Split - Arteus - TerraCorp - Argon, 38.98457308347821, 0.20520937815246787
    Paranid - Yaki - Boron - Strong Arms - Arteus - TerraCorp - Argon, 19.962209475532184, 0.4007572413166816
    Paranid - Boron - Strong Arms - Arteus - Terran - TerraCorp - Argon, 24.56458906331451, 0.3256720468386519
    Pirates - Boron - Split - Arteus - Strong Arms - Terran - TerraCorp - Argon, 29.448318512222656, 0.23770457376351112
    Paranid - Boron - Duke's - Strong Arms - Split - Arteus - TerraCorp - Argon, 23.807564349500964, 0.2940241974037436
    Yaki - Boron - Duke's - Strong Arms - Split - Arteus - TerraCorp - Argon, 42.7391304347826, 0.16378433367243136
    Boron - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp - Argon, 63.157562448531415, 0.11083391645623539
    Pirates - Boron - Duke's - Split - Strong Arms - Arteus - TerraCorp - Argon, 23.80756434950096, 0.29402419740374364
    Yaki - Pirates - Boron - Duke's - Strong Arms - TerraCorp - Argon, 36.951380273960396, 0.21650070824654938
    Yaki - Duke's - Strong Arms - Terran - TerraCorp - Argon, 37.308234544342305, 0.24123360726981455
    Paranid - Pirates - Boron - Split - Strong Arms - TerraCorp - Argon, 53.7061769955951, 0.14895865703969485
    Paranid - Yaki - Pirates - Boron - Strong Arms - TerraCorp - Argon, 37.93918579326518, 0.21086377666597497
    Paranid - Yaki - Strong Arms - Terran - TerraCorp, 29.781961132334494, 0.3357737240863875
    Yaki - Pirates - Strong Arms - Terran - TerraCorp, 38.48945866849781, 0.259811396313158
    Paranid - OTAS - Boron - Strong Arms - Split - TerraCorp - Argon, 38.98457308347821, 0.20520937815246787
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - TerraCorp - Argon, 26.143385753931533, 0.26775414882700554
    OTAS - Boron - Duke's - Strong Arms - Split - Terran - TerraCorp - Argon, 34.75635289860011, 0.20140202916060101
    OTAS - Pirates - Duke's - Strong Arms - Split - TerraCorp - Argon, 32.97685749368089, 0.24259437096251457
    Yaki - OTAS - Pirates - Boron - Strong Arms - TerraCorp - Argon, 54.1807798117815, 0.1476538364303944
    Yaki - OTAS - Strong Arms - Terran - TerraCorp - Argon, 32.01204410273811, 0.28114418345532005
    Paranid - OTAS - Pirates - Strong Arms - Split - TerraCorp - Argon, 43.38768877781612, 0.18438410123588686
    Paranid - Yaki - OTAS - Boron - Strong Arms - TerraCorp - Argon, 39.41601752512497, 0.2029631734078806
    Paranid - OTAS - Boron - Strong Arms - Terran - TerraCorp - Argon, 52.908886455858365, 0.15120333342631134
    OTAS - Pirates - Strong Arms - Split - Terran - TerraCorp - Argon, 66.0675862710756, 0.12108812280769521
    Paranid - Pirates - Duke's - Strong Arms - Split - TerraCorp - Argon, 32.881450785048315, 0.2432982672296722
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - TerraCorp - Argon, 42.7391304347826, 0.16378433367243136
    Paranid - Boron - Duke's - Strong Arms - Split - Terran - TerraCorp - Argon, 63.15756244853142, 0.11083391645623537
    Pirates - Boron - Duke's - Terran - Strong Arms - TerraCorp - Argon, 52.54818089447975, 0.15224123583011434
    Paranid - Pirates - Boron - Terran - Strong Arms - TerraCorp - Argon, 50.20020898189435, 0.15936188637950394
    Paranid - OTAS - Boron - Strong Arms - Arteus - TerraCorp - Argon, 43.042560108094776, 0.18586255045957373
    Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 12.33870331251886, 0.5673205540891638
    OTAS - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp - Argon, 15.199153432246368, 0.46055196634497236
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - TerraCorp, 48.23651533061799, 0.16584945958818095
    Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - TerraCorp - Argon, 20.692168543995905, 0.338292237718658
    Yaki - Strong Arms - Terran - Arteus - TerraCorp - Argon, 29.31066208572107, 0.30705549992964587
    Paranid - Pirates - Boron - Arteus - Strong Arms - TerraCorp - Argon, 44.00671313693511, 0.18179044581463072
    Paranid - Yaki - OTAS - Boron - Strong Arms - Arteus - TerraCorp, 63.33092095355858, 0.12632060105152282
    Paranid - OTAS - Boron - Strong Arms - Arteus - Terran - TerraCorp, 92.6878676009398, 0.0863111883687233
    OTAS - Pirates - Boron - Arteus - Strong Arms - Terran - TerraCorp - Argon, 25.066135946111448, 0.27926123176898837
    Paranid - Pirates - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 32.661967933675975, 0.244933190071246
    Paranid - Yaki - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 30.557021077025507, 0.26180562496044
    Paranid - Duke's - Strong Arms - Terran - Arteus - TerraCorp - Argon, 41.94474601443832, 0.1907271055413286
    Pirates - Duke's - Strong Arms - Terran - Arteus - TerraCorp - Argon, 25.087913341333195, 0.31887865248720093
    Yaki - Pirates - Duke's - Strong Arms - Arteus - TerraCorp, 31.747248554311206, 0.2834891340143497
    Yaki - Duke's - Strong Arms - Terran - Arteus - TerraCorp - Argon, 15.594841969117512, 0.5129901294185867
    Paranid - Pirates - Strong Arms - Arteus - Terran - TerraCorp - Argon, 100.46460205588414, 0.07963003721002093
    Paranid - Yaki - Pirates - Strong Arms - Arteus - TerraCorp - Argon, 68.66113303811174, 0.11651424388175242
    Paranid - Yaki - Strong Arms - Terran - Arteus - TerraCorp, 21.615252836875303, 0.4163726451835036
    Yaki - Pirates - Strong Arms - Arteus - Terran - TerraCorp, 30.919958373563787, 0.2910741305426497
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - TerraCorp, 64.47476349713094, 0.12407955556682254
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - TerraCorp - Argon, 19.79795396419437, 0.35357188993670075
    Paranid - OTAS - Boron - Duke's - Strong Arms - Terran - TerraCorp - Argon, 25.370211162440157, 0.27591414021666844
    OTAS - Pirates - Duke's - Strong Arms - Terran - TerraCorp, 71.43717144142754, 0.12598483140362357
    Yaki - OTAS - Pirates - Duke's - Strong Arms - TerraCorp - Argon, 24.075199908489385, 0.3322921525224405
    Yaki - OTAS - Duke's - Strong Arms - Terran - TerraCorp, 24.718385472235113, 0.3641014503196107
    Paranid - OTAS - Pirates - Boron - Strong Arms - Terran - Goner - TerraCorp, 164.16186454967647, 0.04264084121608983
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - TerraCorp - Argon, 23.80756434950096, 0.29402419740374364
    Paranid - Yaki - OTAS - Strong Arms - Terran - TerraCorp, 27.326128495913974, 0.3293551079270433
    Yaki - OTAS - Pirates - Strong Arms - Terran - TerraCorp, 35.621670674956945, 0.2526551907720392
    Paranid - Pirates - Duke's - Strong Arms - Terran - TerraCorp, 39.851387801146686, 0.22583906098600243
    Paranid - Yaki - Pirates - Duke's - Strong Arms - TerraCorp - Argon, 23.617523368691323, 0.33873153738910816
    Paranid - Yaki - Duke's - Strong Arms - Terran - TerraCorp, 17.929071143485583, 0.5019780404669817
    Yaki - Pirates - Duke's - Strong Arms - Terran - TerraCorp, 12.721920660115144, 0.7074403496491026
    Paranid - Yaki - Pirates - Strong Arms - Terran - TerraCorp, 19.417591167129558, 0.46349724445920765
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - TerraCorp - Argon, 23.347814979526795, 0.2998139228933479
    Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - TerraCorp - Argon, 25.66922896610812, 0.2727000491227188
    OTAS - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp - Argon, 34.19042993434687, 0.20473565303043972
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - TerraCorp - Argon, 17.654948107020942, 0.3964894123487268
    Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - TerraCorp - Argon, 34.19042993434687, 0.20473565303043972
    Yaki - Strong Arms - Split - Terran - Arteus - TerraCorp - Argon, 23.725567765544568, 0.3371889802198113
    Paranid - Pirates - Strong Arms - Split - Arteus - TerraCorp - Argon, 52.309401346493004, 0.15293617961728684
    Paranid - Yaki - Strong Arms - Split - Arteus - TerraCorp - Argon, 32.67771249520372, 0.24481517796492647
    Paranid - Strong Arms - Split - Terran - Arteus - TerraCorp - Argon, 42.79862699713878, 0.1869218842121927
    OTAS - Pirates - Strong Arms - Split - Arteus - Terran - TerraCorp - Argon, 43.47382556394369, 0.16101642561232657
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus - TerraCorp, 18.38026392124875, 0.435249462917205
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - TerraCorp - Argon, 18.15834440858173, 0.3854976997072356
    Paranid - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp - Argon, 23.131910971075527, 0.3026122661786525
    Pirates - Duke's - Strong Arms - Split - Terran - TerraCorp - Argon, 47.442450070995676, 0.16862535531002992
    Yaki - Pirates - Duke's - Strong Arms - Split - TerraCorp - Argon, 33.92670836883024, 0.235802421886289
    Yaki - Duke's - Strong Arms - Split - Terran - TerraCorp - Argon, 33.92670836883024, 0.235802421886289
    Paranid - Pirates - Strong Arms - Split - Terran - TerraCorp, 40.791232793715, 0.22063564603486796
    Paranid - Yaki - Pirates - Strong Arms - Split - TerraCorp - Argon, 22.089097171152446, 0.3621696232314876
    Paranid - Yaki - Strong Arms - Split - Terran - TerraCorp, 16.364272907375796, 0.5499786058898755
    Yaki - Pirates - Strong Arms - Split - Terran - TerraCorp, 22.36438762008208, 0.40242550580363123
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - TerraCorp, 18.38026392124875, 0.435249462917205
    Paranid - Yaki - OTAS - Strong Arms - Split - TerraCorp - Argon, 28.060185678558952, 0.2851014633917007
    Paranid - OTAS - Strong Arms - Split - Terran - TerraCorp - Argon, 35.94275764528254, 0.22257613283186672
    OTAS - Pirates - Duke's - Strong Arms - Split - Terran - TerraCorp, 23.5344717821445, 0.3399268984685505
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - TerraCorp, 18.418867119202798, 0.4343372449687478
    Yaki - OTAS - Strong Arms - Split - Terran - TerraCorp, 41.03748102761642, 0.2193117066309064
    Paranid - OTAS - Pirates - Strong Arms - Split - Terran - TerraCorp, 28.784373988493474, 0.27792857344050603
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - TerraCorp, 23.347867838098907, 0.34264370757425866
    Paranid - Yaki - OTAS - Strong Arms - Split - Terran - TerraCorp, 12.640476351465452, 0.6328875413838763
    Yaki - OTAS - Pirates - Strong Arms - Split - Terran - TerraCorp, 17.85351178241406, 0.44809111493012277
    Paranid - Pirates - Duke's - Strong Arms - Split - Terran - TerraCorp, 16.406456253624725, 0.48761291752035346
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - TerraCorp, 13.225967291583567, 0.6048706929050742
    Paranid - Yaki - Duke's - Strong Arms - Split - Terran - TerraCorp, 13.225967291583565, 0.6048706929050743
    Yaki - Pirates - Duke's - Strong Arms - Split - Terran - TerraCorp, 10.700837644093165, 0.7476050255202199
    Paranid - Yaki - Pirates - Strong Arms - Split - Terran - TerraCorp, 9.973973894733032, 0.802087521426597
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - TerraCorp, 48.045503985419494, 0.16650881635933681
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus - TerraCorp, 40.237360016448775, 0.19882020084641863
    Paranid - OTAS - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 59.14137881930872, 0.1352690816431917
    OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 30.226815837520384, 0.26466565459632846
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - TerraCorp, 23.00640299343975, 0.34772928224725924
    Yaki - OTAS - Strong Arms - Terran - Arteus - TerraCorp, 62.96833314867137, 0.14292898588804237
    Paranid - OTAS - Pirates - Strong Arms - Arteus - Terran - TerraCorp - Argon, 88.09959075373267, 0.0794555336762835
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Arteus - TerraCorp - Argon, 62.25443207421285, 0.11244179356829365
    Paranid - Yaki - OTAS - Strong Arms - Arteus - Terran - TerraCorp, 21.3615983759357, 0.37450381096070845
    Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran - TerraCorp, 30.226815837520377, 0.2646656545963285
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 18.536928136695686, 0.43157096693724606
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - TerraCorp, 14.795908728742177, 0.5406900073977472
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 10.983564460059739, 0.7283610005741695
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 9.207418218733293, 0.8688646274069862
    Paranid - Yaki - Pirates - Strong Arms - Arteus - Terran - Argon, 14.641963077953626, 0.5463748240183438
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Terran - TerraCorp, 28.430800085997184, 0.2813849760049553
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - TerraCorp, 21.821184159694187, 0.3666162175917458
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Terran - TerraCorp, 13.76330508579846, 0.5812557340064144
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran - TerraCorp, 10.252697945936177, 0.7802824234347926
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Terran - TerraCorp, 19.24642937539234, 0.41566151538884705
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Terran - TerraCorp, 9.011207104826973, 0.8877833909415637
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Arteus - TerraCorp, 23.347814979526795, 0.2998139228933479
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Arteus - TerraCorp, 41.991068419278726, 0.166702116986054
    OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp, 62.25443207421285, 0.11244179356829365
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - TerraCorp, 23.347814979526795, 0.2998139228933479
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Arteus - TerraCorp, 62.254432074212865, 0.11244179356829362
    Yaki - Boron - Strong Arms - Split - Terran - TerraCorp, 72.60600361664095, 0.12395669161905563
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus - TerraCorp, 43.38768877781613, 0.18438410123588683
    Paranid - Yaki - Boron - Strong Arms - Split - Arteus - TerraCorp, 28.06018567855895, 0.2851014633917008
    Paranid - Boron - Strong Arms - Split - Arteus - Terran - TerraCorp, 35.94275764528253, 0.22257613283186678
    OTAS - Pirates - Boron - Split - Strong Arms - Arteus - Terran - TerraCorp, 88.09959075373268, 0.07945553367628348
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus - TerraCorp, 22.61771220983577, 0.3537050929722697
    Paranid - Yaki - Boron - Duke's - Strong Arms - Arteus - TerraCorp, 22.060838226061037, 0.3626335462878919
    Paranid - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 28.73483111750453, 0.27840776120401844
    Pirates - Boron - Duke's - Split - Strong Arms - Terran - TerraCorp, 63.576141745453704, 0.12583336736649445
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - TerraCorp, 42.81634020849132, 0.186844554229636
    Yaki - Boron - Duke's - Strong Arms - Split - Terran - TerraCorp, 42.81634020849132, 0.186844554229636
    Paranid - Pirates - Boron - Split - Strong Arms - Terran - TerraCorp, 27.38029197863633, 0.29218096016806755
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - TerraCorp, 22.08909717115245, 0.36216962323148755
    Paranid - Yaki - Boron - Strong Arms - Terran - TerraCorp, 19.74112551408254, 0.45590105759571586
    Yaki - Pirates - Boron - Strong Arms - Terran - TerraCorp, 25.075941014578596, 0.3589097611438629
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - TerraCorp, 52.30940134649299, 0.15293617961728687
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - TerraCorp, 32.677712495203735, 0.24481517796492636
    Paranid - OTAS - Boron - Strong Arms - Split - Terran - TerraCorp, 42.7986269971388, 0.18692188421219263
    OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - TerraCorp, 35.8653877322666, 0.22305628088338586
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - TerraCorp, 26.771057512564347, 0.29883018241791137
    Yaki - OTAS - Boron - Strong Arms - Terran - TerraCorp, 38.89943916277046, 0.23136580356185807
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Terran - TerraCorp, 18.592652899924772, 0.3764928027042511
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Split - TerraCorp, 15.478181938727655, 0.4522494972413677
    Paranid - Yaki - OTAS - Boron - Strong Arms - Terran - TerraCorp, 16.735592842259265, 0.47802310174510787
    Yaki - OTAS - Pirates - Boron - Strong Arms - Terran - TerraCorp, 21.43101345289239, 0.37329079269092136
    Paranid - Pirates - Boron - Duke's - Strong Arms - Terran - TerraCorp, 27.184578416267126, 0.29428449753750224
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - TerraCorp, 21.022876956957038, 0.38053783106753064
    Paranid - Yaki - Boron - Duke's - Strong Arms - Terran - TerraCorp, 14.749933048893647, 0.5423753432291043
    Yaki - Pirates - Boron - Duke's - Strong Arms - Terran - TerraCorp, 11.544000124850266, 0.6930006855057762
    Paranid - Yaki - Pirates - Boron - Strong Arms - Terran - TerraCorp, 13.781806109062984, 0.5804754425284767
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - TerraCorp, 17.654948107020946, 0.3964894123487267
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - TerraCorp, 15.590707861503331, 0.4489853868203407
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 19.59190544667287, 0.3572904135870435
    Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 24.518267623449738, 0.3262873267746147
    Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - TerraCorp, 19.143401249324224, 0.41789856963283395
    Yaki - OTAS - Boron - Strong Arms - Arteus - Terran - TerraCorp, 24.236388419729316, 0.3300821830981923
    Paranid - Pirates - Boron - Arteus - Strong Arms - Terran - TerraCorp, 46.08135152149722, 0.17360601926503727
    Paranid - Yaki - Pirates - Boron - Strong Arms - Arteus - TerraCorp, 35.900453286918705, 0.22283841198503795
    Paranid - Yaki - Boron - Strong Arms - Arteus - Terran - TerraCorp, 12.646242156352132, 0.632598988781948
    Yaki - Pirates - Boron - Strong Arms - Arteus - Terran - TerraCorp, 18.083156836572638, 0.44240063127806545
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 12.055133725439056, 0.5806654790753932
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - TerraCorp, 9.877802037656755, 0.7086596768505965
    Yaki - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 16.360776090334983, 0.48897435890745705
    Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 7.664983862866034, 0.9132439317859975
    Paranid - Yaki - Pirates - Boron - Strong Arms - Arteus - Terran, 12.038202665072138, 0.6645510316262865
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - TerraCorp, 18.630827475871765, 0.37572136874035755
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Strong Arms - TerraCorp, 14.89488743972727, 0.4699599126428962
    Yaki - OTAS - Boron - Duke's - Strong Arms - Terran - TerraCorp, 18.04246271100112, 0.4433984499866595
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - TerraCorp, 8.757782034841714, 0.7992891319002228
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Terran - TerraCorp, 13.089477632793734, 0.5347806991520077
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Terran - TerraCorp, 8.00876571291282, 0.8740422995160976
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - TerraCorp, 12.735355168169878, 0.5496509447569594
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - TerraCorp, 15.952040967058938, 0.4388153224063957
    Paranid - OTAS - Strong Arms - Split - Arteus - Terran - Goner - TerraCorp, 66.85486398883711, 0.10470442361783586
    Pirates - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp, 28.430800085997184, 0.2813849760049553
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - TerraCorp, 21.821184159694187, 0.3666162175917458
    Yaki - OTAS - Strong Arms - Split - Arteus - Terran - TerraCorp, 32.44991681434243, 0.24653375987898085
    Paranid - Pirates - Strong Arms - Split - Arteus - Terran - TerraCorp, 28.784373988493474, 0.27792857344050603
    Paranid - Yaki - Pirates - Strong Arms - Split - Arteus - TerraCorp, 23.347867838098907, 0.34264370757425866
    Paranid - Yaki - Strong Arms - Split - Arteus - Terran - TerraCorp, 12.640476351465452, 0.6328875413838763
    Yaki - Pirates - Strong Arms - Split - Arteus - Terran - TerraCorp, 19.24642937539234, 0.41566151538884705
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp, 10.669847137670452, 0.6560543848173921
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - TerraCorp, 8.7733513517238, 0.797870701784288
    Yaki - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp, 21.821184159694187, 0.3666162175917458
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp, 8.055536154676947, 0.8689676100498767
    Paranid - Yaki - Pirates - Strong Arms - Split - Arteus - Terran - TerraCorp, 8.95554048972484, 0.7816390320641693
    Paranid - OTAS - Duke's - Strong Arms - Split - Terran - TerraCorp, 37.101888452045756, 0.2156224476374029
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - TerraCorp, 8.7733513517238, 0.797870701784288
    Yaki - OTAS - Duke's - Strong Arms - Split - Terran - TerraCorp, 18.418867119202794, 0.4343372449687479
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Terran - TerraCorp, 7.49121323952464, 0.9344280794287187
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Terran - TerraCorp, 8.95554048972484, 0.7816390320641693
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Terran - TerraCorp, 6.407548031630935, 1.0924615727333482
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 16.748014846659075, 0.41795998296457043
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - TerraCorp, 13.456431668931284, 0.5201973429673681
    Yaki - OTAS - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 16.122086580243035, 0.49621368550418754
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 8.191901356927549, 0.8545024768981615
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran - TerraCorp, 16.74801484665907, 0.41795998296457054
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 6.7464014067667515, 1.0375902022341696
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran - TerraCorp, 8.055536154676947, 0.8689676100498767
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Argon, 16.38514724093087, 0.4272161792061087
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Argon, 19.797953964194374, 0.3535718899367007
    OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Terran - Argon, 63.15756244853142, 0.11083391645623537
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - Argon, 16.38514724093087, 0.4272161792061087
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Arteus - Argon, 16.38514724093087, 0.4272161792061087
    Yaki - Boron - Strong Arms - Split - Arteus - Terran - Argon, 52.64521118838208, 0.15196064028261447
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Argon, 21.192662645072502, 0.377489140179376
    Paranid - Yaki - Boron - Strong Arms - Split - Arteus - Argon, 23.383518758024234, 0.3421213070105088
    Paranid - Boron - Strong Arms - Split - Arteus - Terran - Argon, 79.56783299087787, 0.10054314286675581
    OTAS - Pirates - Boron - Split - Strong Arms - Arteus - Terran - Argon, 29.448318512222656, 0.23770457376351112
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus - Argon, 26.405340975925967, 0.30296900946265704
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Arteus - Argon, 19.797953964194374, 0.3535718899367007
    Paranid - Boron - Duke's - Strong Arms - Split - Arteus - Terran - Argon, 63.15756244853142, 0.11083391645623537
    Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Argon, 78.34616187251343, 0.10211093701077244
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Argon, 64.7142973157918, 0.12362028688902743
    Yaki - Duke's - Strong Arms - Split - Arteus - Terran - Argon, 74.45240422597443, 0.1074511976230986
    Paranid - Pirates - Boron - Split - Strong Arms - Terran - Argon, 35.18648428293457, 0.2273600265281404
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Argon, 18.76160947608114, 0.4264026500604367
    Paranid - Yaki - Boron - Strong Arms - Split - Terran - Argon, 18.888521415215983, 0.42353765147310357
    Yaki - Pirates - Boron - Strong Arms - Terran - Argon, 26.360387519001247, 0.341421384397804
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Argon, 11.699454401811282, 0.598318499272605
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Argon, 16.412969057151365, 0.48741942863252313
    Paranid - OTAS - Boron - Strong Arms - Split - Terran - Argon, 29.29196971447588, 0.27311239489799344
    OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - Argon, 36.35945943995901, 0.22002527329127472
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Argon, 17.831667238622657, 0.4486400454284123
    Yaki - OTAS - Boron - Strong Arms - Terran - Argon, 25.405715102067976, 0.3542510007627149
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Terran - Argon, 14.087634311521786, 0.49688967254601035
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Argon, 9.969749318501616, 0.7021239728675597
    Paranid - Yaki - OTAS - Boron - Strong Arms - Terran - Argon, 13.697602140296773, 0.5840438288439491
    Yaki - OTAS - Pirates - Boron - Strong Arms - Terran - Argon, 15.367832548537168, 0.5205678793501367
    Paranid - Pirates - Boron - Duke's - Strong Arms - Terran - Argon, 51.39496404539767, 0.15565727398765222
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Argon, 21.701936229812464, 0.3686307025918826
    Paranid - Yaki - Boron - Duke's - Strong Arms - Terran - Argon, 22.63622748513672, 0.3534157803129041
    Yaki - Pirates - Boron - Duke's - Strong Arms - Terran - Argon, 16.574002300486505, 0.48268365449455575
    Paranid - Yaki - Pirates - Boron - Strong Arms - Terran - Argon, 13.48656767193981, 0.5931828019255649
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Argon, 13.708803392941876, 0.5106207886535177
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - Argon, 11.253981919931123, 0.6220020655624833
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - Terran - Argon, 19.955962259804036, 0.35077236110531407
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Argon, 17.212044630861794, 0.406691950324644
    Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - Argon, 21.730999004314633, 0.36813770036120386
    Yaki - OTAS - Boron - Strong Arms - Arteus - Terran - Argon, 16.239318939241016, 0.492631497043182
    Paranid - OTAS - Pirates - Boron - Strong Arms - Arteus - Terran - Argon, 23.09509700713285, 0.30309463510103773
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - Argon, 14.580806584409826, 0.48008318054808985
    Paranid - Yaki - Boron - Strong Arms - Arteus - Terran - Argon, 13.100448047495963, 0.610666136837139
    Yaki - Pirates - Boron - Strong Arms - Arteus - Terran - Argon, 17.153030401979514, 0.46638989219518756
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Argon, 17.212044630861794, 0.406691950324644
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - Argon, 10.136127101563819, 0.6905990749583268
    Paranid - Yaki - Boron - Duke's - Strong Arms - Arteus - Terran - Argon, 11.274987008487788, 0.6208432874228959
    Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Argon, 10.656868223985695, 0.6568533881506496
    Paranid - Yaki - Pirates - Boron - Strong Arms - Arteus - Terran - Argon, 9.66392812296539, 0.7243431357239897
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - Argon, 18.891878547837614, 0.37052958932986724
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Strong Arms - Argon, 11.841694537346712, 0.5911316136320843
    Yaki - OTAS - Boron - Duke's - Strong Arms - Terran - Argon, 18.34410361152612, 0.43610743645022665
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - Argon, 8.90828466363833, 0.7857853968870651
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Terran - Argon, 10.690536562493794, 0.6547847209613866
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Terran - Argon, 9.785774869610227, 0.7153240385427765
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Argon, 11.49226299275534, 0.6091054481099817
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - Argon, 12.94828293488652, 0.5406122213424857
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - Terran - Argon, 23.131910971075524, 0.30261226617865256
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - Argon, 18.63082747587176, 0.3757213687403576
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Argon, 11.046806055737811, 0.6336673210954162
    Yaki - OTAS - Strong Arms - Split - Arteus - Terran - Argon, 23.72556776554457, 0.33718898021981125
    Paranid - Pirates - Strong Arms - Split - Arteus - Terran - Argon, 30.342756013615663, 0.2636543627220339
    Paranid - Yaki - Pirates - Strong Arms - Split - Arteus - Argon, 17.732384304775543, 0.4511519636897055
    Paranid - Yaki - Strong Arms - Split - Arteus - Terran - Argon, 14.611757228960336, 0.5475043059259218
    Yaki - Pirates - Strong Arms - Split - Arteus - Terran - Argon, 19.99799537075347, 0.40004009660387185
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - Argon, 15.530585952280633, 0.4507234963000263
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Argon, 9.585686286294797, 0.7302554862460187
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - Terran - Argon, 12.571752581144887, 0.5568038310345528
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - Argon, 11.424503745760024, 0.6127180799951955
    Paranid - Yaki - Pirates - Strong Arms - Split - Arteus - Terran - Argon, 9.027651507027452, 0.7753954607741499
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Terran - Argon, 11.284667025798818, 0.6203107264039529
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Argon, 7.85455942536155, 0.8912021185297463
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Terran - Argon, 9.274596986986055, 0.7547497761705735
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Terran - Argon, 7.862002563833977, 0.8903583970069817
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Terran - Argon, 7.977528314277163, 0.8774647640513281
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Terran - Argon, 7.946801107889849, 0.8808575809265148
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - Argon, 18.57929423848177, 0.3767635040464279
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Argon, 11.607742531717937, 0.6030457671569327
    Yaki - OTAS - Duke's - Strong Arms - Arteus - Terran - Argon, 18.06129610368381, 0.44293609683794
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - Argon, 8.757782034841712, 0.7992891319002229
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran - Argon, 13.914177158084579, 0.5030840070864541
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran - Argon, 8.025127487929064, 0.8722602862732085
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran - Argon, 8.418766049593184, 0.8314757719557081
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Arteus, 10.842993248535583, 0.645578194097409
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Arteus, 12.110787417516361, 0.5779970995011929
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - Terran, 35.94275764528253, 0.22257613283186678
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - Terran, 20.382032903778022, 0.34343973601879907
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Arteus, 12.110787417516361, 0.5779970995011929
    Yaki - OTAS - Boron - Strong Arms - Split - Arteus - Terran, 28.060185678558952, 0.2851014633917007
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Arteus - Terran, 17.33378318400505, 0.4038356731298757
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Arteus, 12.583339875179341, 0.5562911015228565
    Paranid - Yaki - Boron - Strong Arms - Split - Arteus - Terran, 12.956769557492365, 0.6174378547447369
    Yaki - Pirates - Boron - Strong Arms - Split - Arteus - Terran, 20.35666343048832, 0.39299171140287864
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - Terran, 13.801296555142315, 0.5071987238323507
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Arteus, 8.78040793854306, 0.7972294737323463
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Arteus - Terran, 11.249029294261842, 0.6222759152712597
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - Terran, 11.249029294261842, 0.6222759152712597
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Arteus - Terran, 8.402250438134661, 0.8331101353786871
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Terran, 11.284667025798816, 0.620310726403953
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Strong Arms - Split, 7.999929086268081, 0.8750077562581817
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Terran, 23.963420109049686, 0.3338421629130824
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Terran, 8.418766049593184, 0.8314757719557081
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Terran, 7.977528314277163, 0.8774647640513281
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Terran, 7.7701005742368725, 0.9008892398651472
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran, 14.545618985601616, 0.4812445594050789
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Strong Arms - Arteus, 9.654804307146094, 0.725027641919048
    Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - Terran, 17.901502191631398, 0.44688987071374625
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran, 8.425422647620662, 0.8308188553575765
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - Terran, 11.49818865113967, 0.6087915420752972
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran, 7.135552231765484, 0.981003259823109
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Strong Arms - Terran, 7.862002563833977, 0.8903583970069817
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Terran, 10.669847137670452, 0.6560543848173921
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus, 7.541460021155782, 0.9282022287943126
    Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - Terran, 21.82118415969418, 0.3666162175917459
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Terran, 8.055536154676945, 0.8689676100498769
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - Terran, 8.95554048972484, 0.7816390320641693
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Terran, 6.445220947109114, 1.0860760333033614
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Terran, 5.6862158294911485, 1.2310471867239026
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran, 7.49121323952464, 0.9344280794287187
    Paranid - OTAS - Boron - Duke's - Split - Arteus - TerraCorp - Argon, 11.59273088976216, 0.6038266622907533
    Yaki - OTAS - Boron - Duke's - Split - Arteus - TerraCorp - Argon, 13.196857952283954, 0.5304292904651993
    OTAS - Boron - Duke's - Split - Arteus - Terran - TerraCorp - Argon, 13.229591824021405, 0.5291168535744141
    OTAS - Pirates - Boron - Duke's - Split - Arteus - TerraCorp - Argon, 11.23577134995711, 0.6230101861254698
    Yaki - OTAS - Pirates - Boron - Split - Arteus - TerraCorp - Argon, 15.756790877310634, 0.4442528973383671
    Yaki - Boron - Split - Terran - TerraCorp - Argon, 47.65126442635986, 0.1888722179431057
    Paranid - OTAS - Pirates - Boron - Split - Arteus - TerraCorp - Argon, 13.405949859160023, 0.5221562122445981
    Paranid - Yaki - Boron - Split - Arteus - TerraCorp - Argon, 20.57336199283355, 0.38885234230490334
    Paranid - OTAS - Boron - Split - Terran - TerraCorp - Argon, 20.536933004207338, 0.38954209951218444
    OTAS - Pirates - Boron - Split - Arteus - Terran - TerraCorp - Argon, 15.484529718250734, 0.4520641005809494
    Paranid - Pirates - Boron - Duke's - Arteus - TerraCorp - Argon, 16.58500490462717, 0.4823634389018494
    Paranid - Yaki - Boron - Duke's - Split - Arteus - TerraCorp - Argon, 15.907507018970898, 0.4400438102370141
    Paranid - Boron - Duke's - Split - Arteus - Terran - TerraCorp - Argon, 14.580806584409828, 0.4800831805480898
    Pirates - Boron - Duke's - Split - Terran - TerraCorp - Argon, 56.82431357253719, 0.14078480666181503
    Yaki - Pirates - Boron - Duke's - Arteus - TerraCorp - Argon, 15.799238888903663, 0.5063535057767036
    Yaki - Boron - Duke's - Split - Terran - TerraCorp - Argon, 41.59187385804858, 0.19234526502228977
    Paranid - Pirates - Boron - Split - Terran - TerraCorp - Argon, 26.696988875815073, 0.2996592625937391
    Paranid - Yaki - Pirates - Boron - Split - Arteus - TerraCorp - Argon, 13.380535591052162, 0.5231479676105822
    Paranid - Yaki - Boron - Terran - TerraCorp - Argon, 19.329113375529413, 0.46561887372412886
    Yaki - Pirates - Boron - Terran - TerraCorp - Argon, 19.609297250015764, 0.4589659631985417
    Paranid - OTAS - Pirates - Boron - Duke's - Split - TerraCorp - Argon, 15.378590584308014, 0.45517825327521566
    Paranid - Yaki - OTAS - Boron - Duke's - Split - TerraCorp - Argon, 19.79795396419437, 0.35357188993670075
    Paranid - OTAS - Boron - Duke's - Split - Terran - TerraCorp - Argon, 16.385147240930873, 0.4272161792061086
    OTAS - Pirates - Boron - Duke's - Terran - TerraCorp - Argon, 19.712624808013445, 0.4058312922766071
    Yaki - OTAS - Pirates - Boron - Duke's - Split - TerraCorp - Argon, 15.121759542763828, 0.46290909336339037
    Yaki - OTAS - Boron - Terran - TerraCorp - Argon, 17.59255550114467, 0.5115800259612318
    Paranid - OTAS - Pirates - Boron - Split - Terran - TerraCorp - Argon, 13.405949859160023, 0.5221562122445981
    Paranid - Yaki - OTAS - Pirates - Boron - Split - TerraCorp - Argon, 15.378590584308014, 0.45517825327521566
    Paranid - Yaki - OTAS - Boron - Terran - TerraCorp - Argon, 12.545759995065097, 0.6376656338991673
    Yaki - OTAS - Pirates - Boron - Terran - TerraCorp - Argon, 13.372877768758622, 0.5982257624973883
    Paranid - Pirates - Boron - Duke's - Terran - TerraCorp - Argon, 27.881812139392903, 0.2869253963840168
    Paranid - Yaki - Pirates - Boron - Duke's - TerraCorp - Argon, 39.86846797421478, 0.2006598298478401
    Paranid - Yaki - Boron - Duke's - Terran - TerraCorp - Argon, 17.56104653978346, 0.45555371554175295
    Yaki - Pirates - Boron - Duke's - Terran - TerraCorp - Argon, 13.376142120023632, 0.5980797698033031
    Paranid - Yaki - Pirates - Boron - Terran - TerraCorp - Argon, 13.286498569178109, 0.6021149935287181
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - TerraCorp - Argon, 10.643597803545108, 0.6576723518872989
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - TerraCorp - Argon, 9.882811911989766, 0.7083004373995668
    Paranid - OTAS - Boron - Duke's - Arteus - Terran - TerraCorp - Argon, 10.05042105634051, 0.6964882327575629
    Pirates - Boron - Duke's - Terran - Arteus - TerraCorp - Argon, 15.153099697195305, 0.5279447875262593
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - TerraCorp - Argon, 9.017014437332003, 0.7763101688091777
    Yaki - OTAS - Boron - Arteus - Terran - TerraCorp - Argon, 10.528282478544156, 0.7598580315738483
    Paranid - OTAS - Pirates - Boron - Arteus - Terran - TerraCorp - Argon, 15.061952074810055, 0.46474719646113843
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - TerraCorp - Argon, 14.741735296937698, 0.4748423342979243
    Paranid - Yaki - Boron - Arteus - Terran - TerraCorp - Argon, 9.362979959611877, 0.8544288286965023
    Yaki - Pirates - Boron - Arteus - Terran - TerraCorp - Argon, 11.342982721555819, 0.7052818642487282
    Paranid - Pirates - Boron - Duke's - Arteus - Terran - TerraCorp - Argon, 9.763154890511565, 0.7169813526980946
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - TerraCorp - Argon, 10.050333754284683, 0.6964942827909315
    Yaki - Boron - Duke's - Arteus - Terran - TerraCorp - Argon, 11.842181568405378, 0.6755512026047451
    Yaki - Pirates - Boron - Duke's - Arteus - Terran - TerraCorp - Argon, 7.08447382304565, 0.9880762036594929
    Paranid - Yaki - Pirates - Boron - Arteus - Terran - TerraCorp - Argon, 8.177401231516022, 0.8560176762541293
    Paranid - OTAS - Pirates - Boron - Duke's - Terran - TerraCorp - Argon, 14.741735296937698, 0.4748423342979243
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - TerraCorp - Argon, 16.446995603321934, 0.4256096474292334
    Yaki - OTAS - Boron - Duke's - Terran - TerraCorp - Argon, 12.855833372208979, 0.6222856012815126
    Yaki - OTAS - Pirates - Boron - Duke's - Terran - TerraCorp - Argon, 8.264873840905747, 0.8469578767620815
    Paranid - Yaki - OTAS - Pirates - Boron - Terran - TerraCorp - Argon, 10.64359780354511, 0.6576723518872988
    Paranid - Yaki - Pirates - Boron - Duke's - Terran - TerraCorp - Argon, 10.050333754284683, 0.6964942827909315
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - TerraCorp - Argon, 15.059207729104791, 0.4648318906227161
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - TerraCorp - Argon, 19.385453880628724, 0.36109549165598237
    Paranid - OTAS - Duke's - Split - Arteus - Terran - TerraCorp - Argon, 16.052222549410235, 0.43607668523491677
    OTAS - Pirates - Duke's - Split - Arteus - Terran - TerraCorp - Argon, 13.043860479257892, 0.5366509409642392
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - TerraCorp - Argon, 14.817823282555649, 0.4724040681630198
    Yaki - OTAS - Split - Terran - Arteus - TerraCorp - Argon, 18.36644677451648, 0.4355769027191494
    Paranid - OTAS - Pirates - Split - Arteus - Terran - TerraCorp - Argon, 18.69962375173272, 0.3743390825899037
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - TerraCorp - Argon, 23.347814979526795, 0.2998139228933479
    Paranid - Yaki - Split - Terran - Arteus - TerraCorp - Argon, 13.655293749309733, 0.5858533801518839
    Yaki - Pirates - Split - Arteus - Terran - TerraCorp - Argon, 16.694468402272694, 0.4792006434245563
    Paranid - Pirates - Duke's - Split - Arteus - Terran - TerraCorp - Argon, 12.500043625312422, 0.5599980455928244
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - TerraCorp - Argon, 14.849386630153377, 0.4713999422565845
    Paranid - Yaki - Duke's - Split - Arteus - Terran - TerraCorp - Argon, 10.632281858705204, 0.6583723130203452
    Yaki - Pirates - Duke's - Split - Arteus - Terran - TerraCorp - Argon, 9.248440824908926, 0.7568843367788898
    Paranid - Yaki - Pirates - Split - Arteus - Terran - TerraCorp - Argon, 10.255040414692346, 0.6825911665809854
    Paranid - OTAS - Pirates - Duke's - Split - Terran - TerraCorp - Argon, 12.91918691338992, 0.5418297642822199
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - TerraCorp - Argon, 16.17871128104869, 0.43266734157000575
    Yaki - OTAS - Duke's - Split - Terran - TerraCorp - Argon, 16.955250281803234, 0.4718302512222886
    Yaki - OTAS - Pirates - Duke's - Split - Terran - TerraCorp - Argon, 8.871700684994048, 0.7890257176777934
    Paranid - Yaki - OTAS - Pirates - Split - Terran - TerraCorp - Argon, 10.45420632998864, 0.669586937453109
    Paranid - Yaki - Pirates - Duke's - Split - Terran - TerraCorp - Argon, 10.15001212800168, 0.6896543483616654
    Paranid - OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp - Argon, 14.438755080216094, 0.484806339681692
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - TerraCorp - Argon, 16.09511706846746, 0.43491451290615085
    Yaki - OTAS - Duke's - Arteus - Terran - TerraCorp - Argon, 12.590563791141134, 0.635396486822051
    Yaki - OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp - Argon, 8.084133352769458, 0.8658936826669175
    Paranid - Yaki - OTAS - Pirates - Arteus - Terran - TerraCorp - Argon, 14.43875508021609, 0.4848063396816921
    Paranid - Yaki - Pirates - Duke's - Arteus - Terran - TerraCorp - Argon, 7.935819454365503, 0.8820765190353836
    Paranid - Yaki - OTAS - Pirates - Duke's - Terran - TerraCorp - Argon, 9.840760936192442, 0.7113271062459545
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Arteus - TerraCorp, 12.766857477124502, 0.5482946772565225
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Arteus - TerraCorp, 15.590707861503331, 0.4489853868203407
    Paranid - OTAS - Boron - Duke's - Split - Arteus - Terran - TerraCorp, 14.295034347487201, 0.4896805303045997
    OTAS - Pirates - Boron - Duke's - Split - Arteus - Terran - TerraCorp, 13.896922970845004, 0.5037086277793741
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Arteus - TerraCorp, 14.81782328255565, 0.4724040681630197
    Yaki - OTAS - Boron - Split - Arteus - Terran - TerraCorp, 20.908012596653084, 0.38262842836055233
    Paranid - OTAS - Pirates - Boron - Split - Arteus - Terran - TerraCorp, 16.683295077786273, 0.41958138169722037
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Arteus - TerraCorp, 18.66559242747169, 0.37502158194012225
    Paranid - Yaki - Boron - Split - Arteus - Terran - TerraCorp, 11.654501870459724, 0.6864300241160313
    Yaki - Pirates - Boron - Split - Arteus - Terran - TerraCorp, 16.78037657029056, 0.47674734631187576
    Paranid - Pirates - Boron - Duke's - Split - Arteus - Terran - TerraCorp, 10.740629410708651, 0.6517308932585311
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Arteus - TerraCorp, 11.813569427862387, 0.5925389479229242
    Paranid - Yaki - Boron - Duke's - Split - Arteus - Terran - TerraCorp, 9.136866494410334, 0.7661269872206619
    Yaki - Pirates - Boron - Duke's - Split - Arteus - Terran - TerraCorp, 8.871700684994048, 0.7890257176777934
    Paranid - Yaki - Pirates - Boron - Split - Arteus - Terran - TerraCorp, 9.01668120021014, 0.776338859561416
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Terran - TerraCorp, 12.528210941583009, 0.5587389957464678
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Split - TerraCorp, 14.89488743972727, 0.4699599126428962
    Yaki - OTAS - Boron - Duke's - Split - Terran - TerraCorp, 19.520440890959655, 0.40982680896848883
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Terran - TerraCorp, 9.248440824908926, 0.7568843367788898
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Terran - TerraCorp, 9.948792415830136, 0.7036029808865918
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Terran - TerraCorp, 9.525755071321644, 0.7348498830370189
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - Terran - TerraCorp, 11.473915872660552, 0.6100794251663667
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Arteus - TerraCorp, 11.768375933589915, 0.5948144450433669
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - Terran - TerraCorp, 8.107011270932315, 0.8634501379193213
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - Terran - TerraCorp, 7.537449388104937, 0.9286961198103564
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - Terran - TerraCorp, 11.473915872660552, 0.6100794251663667
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Terran - TerraCorp, 6.71938466294939, 1.041762058748909
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Terran - TerraCorp, 8.886756148145375, 0.7876889928459292
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - Terran - TerraCorp, 11.528321609731586, 0.6072002705138776
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Arteus - TerraCorp, 13.456431668931284, 0.5201973429673681
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - Terran - TerraCorp, 9.818770641119608, 0.7129202072085278
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - Terran - TerraCorp, 8.63585461582787, 0.8105740903940576
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - Terran - TerraCorp, 11.528321609731584, 0.6072002705138777
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Terran - TerraCorp, 7.491213239524639, 0.9344280794287189
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Terran - TerraCorp, 8.055536154676947, 0.8689676100498767
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp, 8.300290688757755, 0.8433439577581396
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Arteus - Argon, 10.383132254285266, 0.6741703590562472
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Arteus - Argon, 11.253981919931123, 0.6220020655624833
    Paranid - OTAS - Boron - Duke's - Split - Arteus - Terran - Argon, 14.580806584409826, 0.48008318054808985
    OTAS - Pirates - Boron - Duke's - Split - Arteus - Terran - Argon, 14.176604584863664, 0.49377126646206154
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Arteus - Argon, 10.832534549837604, 0.6462014930850085
    Yaki - OTAS - Boron - Split - Arteus - Terran - Argon, 15.137069635407975, 0.5285038777443917
    Paranid - OTAS - Pirates - Boron - Split - Arteus - Terran - Argon, 12.417600221755839, 0.563716005910376
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Arteus - Argon, 10.71466888687561, 0.6533099691558639
    Paranid - Yaki - Boron - Split - Arteus - Terran - Argon, 14.389020855074879, 0.5559794568772531
    Yaki - Pirates - Boron - Split - Arteus - Terran - Argon, 18.52155258242867, 0.4319292329515384
    Paranid - Pirates - Boron - Duke's - Split - Arteus - Terran - Argon, 16.237010083567174, 0.4311138543348211
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Arteus - Argon, 12.965339784769075, 0.5399010065454044
    Paranid - Yaki - Boron - Duke's - Split - Arteus - Terran - Argon, 13.591762013729976, 0.5150178463196176
    Yaki - Pirates - Boron - Duke's - Split - Arteus - Terran - Argon, 13.086460657696035, 0.5349039884121273
    Paranid - Yaki - Pirates - Boron - Split - Arteus - Terran - Argon, 9.52830878400172, 0.7346529335566018
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Terran - Argon, 12.719091389570282, 0.5503537780804086
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Split - Argon, 11.841694537346712, 0.5911316136320843
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Terran - Argon, 10.832534549837604, 0.6462014930850085
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Terran - Argon, 9.405797101449275, 0.7442218798151001
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Terran - Argon, 8.68350790521657, 0.8061258279957099
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Terran - Argon, 12.422558995382207, 0.5634909846354591
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - Terran - Argon, 11.689122650699344, 0.5988473394606052
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Arteus - Argon, 9.285076380728555, 0.7538979447200567
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - Terran - Argon, 8.275825392346263, 0.8458370818787229
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - Terran - Argon, 7.696775124078267, 0.9094718095766491
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - Terran - Argon, 9.17186436293815, 0.7632036108477288
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Terran - Argon, 9.016483099569829, 0.7763559164585986
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - Terran - Argon, 12.500043625312424, 0.5599980455928243
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Arteus - Argon, 11.607742531717937, 0.6030457671569327
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - Terran - Argon, 10.632281858705205, 0.658372313020345
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - Terran - Argon, 9.248440824908927, 0.7568843367788896
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - Terran - Argon, 10.255040414692346, 0.6825911665809854
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - Terran - Argon, 8.842497923236742, 0.7916315119062751
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Arteus - Terran, 10.74062941070865, 0.6517308932585312
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Split - Arteus, 9.654804307146094, 0.725027641919048
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Arteus - Terran, 9.136866494410334, 0.7661269872206619
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Arteus - Terran, 8.871700684994048, 0.7890257176777934
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Arteus - Terran, 9.01668120021014, 0.776338859561416
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Split - Terran, 7.862002563833977, 0.8903583970069817
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Arteus - Terran, 7.3331679277541735, 0.9545669850961387
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Arteus - Terran, 7.49121323952464, 0.9344280794287187
    OTAS - Boron - Split - Arteus - Teladi - TerraCorp - Argon, 117.28573088415514, 0.06820949095590936
    Yaki - Boron - Strong Arms - Arteus - Teladi - TerraCorp - Argon - NMMC, 179.01801506714708, 0.03910220989420758
    Boron - Arteus - Terran - Teladi - TerraCorp - Argon - NMMC, 186.13672373754423, 0.042979159831351324
    Pirates - Boron - Split - Arteus - Strong Arms - Teladi - TerraCorp - Argon - NMMC, 170.99999999999983, 0.03508771929824565
    Yaki - Pirates - Boron - Strong Arms - Split - Teladi - TerraCorp - Argon, 100.13898929826284, 0.06990284252970219
    Yaki - Terran - Teladi - TerraCorp - Argon, 157.93451002081366, 0.06331738388704365
    Paranid - Boron - Arteus - Teladi - TerraCorp - Argon, 196.9008422297632, 0.04570828594779659
    Paranid - Yaki - Boron - Strong Arms - Teladi - TerraCorp - Argon - NMMC, 913.6515550869808, 0.007661564149949475
    Paranid - Boron - Strong Arms - Terran - Teladi - TerraCorp - Argon - NMMC, 913.6515550869829, 0.007661564149949457
    Pirates - Boron - Split - Terran - Teladi - TerraCorp - Argon, 232.42595084271818, 0.03441956447201359
    Paranid - Boron - Duke's - Arteus - Teladi - TerraCorp - Argon, 39.943395279423186, 0.20028342468225765
    Yaki - Boron - Duke's - Arteus - Teladi - TerraCorp - Argon, 88.12448492734765, 0.09078067243848777
    Boron - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 46.68206140116971, 0.17137203799229705
    Pirates - Boron - Duke's - Arteus - Teladi - TerraCorp - Argon, 31.67725638471453, 0.25254712412089775
    Yaki - Pirates - Duke's - Strong Arms - Teladi - TerraCorp - Argon, 67.23342253881044, 0.11898843905175295
    Yaki - Duke's - Strong Arms - Terran - Teladi - TerraCorp, 61.492535240948754, 0.14635922823371855
    Paranid - Pirates - Strong Arms - Split - Teladi - TerraCorp - Argon - NMMC, 137.95508077053952, 0.050741154011160264
    Paranid - Yaki - Pirates - Boron - Strong Arms - Teladi - NMMC, 108.0142772150666, 0.07406428303983599
    Terran - Paranid - Teladi - Yaki, 82.2155413275132, 0.13379465515139632
    Terran - Pirates - Teladi - Yaki, 85.76569881120207, 0.12825640264664015
    Paranid - OTAS - Boron - Strong Arms - Split - Teladi - Argon, 65.38323825026279, 0.12235551823510127
    Yaki - OTAS - Boron - Strong Arms - Split - Teladi - Argon - NMMC, 201.67081130984815, 0.03471003044285453
    OTAS - Boron - Split - Terran - Teladi - TerraCorp - Argon, 68.24620636477412, 0.11722263296570973
    OTAS - Pirates - Boron - Split - Teladi - TerraCorp - Argon, 393.30751743459035, 0.020340318059978227
    Yaki - OTAS - Pirates - Boron - Teladi - Argon - NMMC, 157.78235070303876, 0.050702755817453586
    Yaki - OTAS - Terran - Teladi - Argon, 91.92748250509956, 0.1087813973307195
    Paranid - OTAS - Pirates - Boron - Strong Arms - Teladi - TerraCorp - Argon - NMMC, 170.99999999999977, 0.03508771929824566
    Paranid - Yaki - OTAS - Boron - Teladi - Argon, 173.77452948601146, 0.051791249423146814
    Paranid - OTAS - Boron - Terran - Teladi - Argon - NMMC, 248.70223029804737, 0.03216698133511998
    OTAS - Pirates - Boron - Terran - Strong Arms - Teladi - Argon - NMMC, 386.981554677205, 0.0180887174476286
    Paranid - Pirates - Boron - Duke's - Strong Arms - Teladi - TerraCorp - Argon, 63.55080213903742, 0.11014809828340628
    Paranid - Yaki - Boron - Duke's - Strong Arms - Teladi - TerraCorp - Argon, 122.25510204081614, 0.05725732409648619
    Paranid - Boron - Duke's - Terran - Teladi - TerraCorp - Argon - NMMC, 1524.8243494423755, 0.004590692693594435
    Pirates - Duke's - Strong Arms - Terran - TerraCorp - Argon - NMMC, 121.91576285406197, 0.06561907839248252
    Paranid - Pirates - Boron - Terran - Strong Arms - Teladi - TerraCorp - NMMC, 95.74884563238994, 0.0731079310018547
    OTAS - Boron - Duke's - Arteus - Teladi - TerraCorp - Argon, 31.91750104377511, 0.2506461890305239
    Yaki - OTAS - Boron - Arteus - Teladi - Argon, 99.19660938483189, 0.09072890752832713
    OTAS - Boron - Arteus - Terran - Teladi - TerraCorp - Argon - NMMC, 23.35265858754951, 0.29975173806258
    OTAS - Pirates - Boron - Arteus - Teladi - TerraCorp - Argon, 123.83635011362202, 0.06460138717476621
    Yaki - Pirates - Boron - Arteus - Teladi - Argon - NMMC, 160.24827028957773, 0.04992253573497889
    Yaki - Strong Arms - Terran - Arteus - TerraCorp - NMMC, 61.39728631187525, 0.146586283215896
    Paranid - OTAS - Boron - Arteus - Teladi - Argon, 142.64343171136915, 0.06309438781738641
    Paranid - Yaki - Boron - Strong Arms - Arteus - Teladi - NMMC, 104.2692704552338, 0.07672442671817352
    Paranid - Boron - Arteus - Terran - Teladi - TerraCorp, 90.7491713574411, 0.09917445928570491
    Pirates - Boron - Arteus - Terran - Teladi - TerraCorp - Argon, 34.24003903320215, 0.2336445934609624
    Paranid - Pirates - Boron - Arteus - Teladi - Argon, 212.378833029271, 0.04237710449590605
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Teladi - TerraCorp, 64.76870699931831, 0.12351643827140474
    Paranid - Duke's - Strong Arms - Terran - Arteus - Teladi - TerraCorp - NMMC, 63.7687069993184, 0.10977170981489119
    Pirates - Duke's - Arteus - Terran - Teladi - TerraCorp, 39.6061130480204, 0.2272376486197461
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Teladi, 51.0928905488069, 0.17614975201692057
    Yaki - Duke's - Arteus - Terran - Teladi - TerraCorp, 29.608191056431405, 0.30396993800960515
    Paranid - Pirates - Arteus - Terran - Teladi - TerraCorp - Argon, 84.89878098583837, 0.09422985709694051
    Paranid - Yaki - Pirates - Strong Arms - Arteus - Teladi - Argon, 81.06280792154382, 0.09868890808399772
    Paranid - Yaki - Arteus - Terran - Teladi, 34.82648370989818, 0.2871378024637572
    Yaki - Pirates - Arteus - Terran - Teladi, 50.89395869731422, 0.19648697519235658
    Paranid - OTAS - Boron - Duke's - Strong Arms - Teladi - TerraCorp - Argon - NMMC, 170.99999999999977, 0.03508771929824566
    Yaki - OTAS - Boron - Duke's - Strong Arms - Teladi - Argon, 361.2808296872444, 0.02214343896111367
    OTAS - Boron - Duke's - Terran - Teladi - TerraCorp - Argon - NMMC, 57.870165621561405, 0.12096042796518149
    OTAS - Pirates - Boron - Duke's - Strong Arms - Teladi - Argon - NMMC, 126.14106779931939, 0.055493425908970856
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Teladi, 54.332477671704055, 0.1656467804465161
    Yaki - OTAS - Duke's - Terran - Teladi, 74.2118369962445, 0.13474939315282078
    Paranid - OTAS - Pirates - Boron - Strong Arms - Terran - Teladi - NMMC, 113.44821102410245, 0.06170216292359892
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Teladi - NMMC, 63.14400987072151, 0.11085770470281373
    Paranid - Yaki - OTAS - Terran - Teladi, 45.529520678065424, 0.2196377174868362
    Yaki - OTAS - Pirates - Terran - Teladi, 55.840492632707665, 0.1790815146595369
    Paranid - Pirates - Duke's - Strong Arms - Terran - Teladi - NMMC, 61.41905129365092, 0.1302527445718945
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Teladi, 33.189777843221606, 0.2711678289174835
    Paranid - Yaki - Duke's - Terran - Teladi, 61.77043282558763, 0.16188975117327695
    Yaki - Pirates - Duke's - Terran - Teladi, 29.231819968819387, 0.3420929661809175
    Paranid - Yaki - Pirates - Terran - Teladi, 28.63425158119279, 0.3492321065785453
    Paranid - OTAS - Strong Arms - Split - Arteus - Teladi - TerraCorp - Argon, 86.63882533147229, 0.08079518591368978
    Yaki - OTAS - Duke's - Strong Arms - Split - Teladi - TerraCorp - Argon, 95.83018385147368, 0.07304587885221253
    OTAS - Duke's - Strong Arms - Split - Terran - Teladi - TerraCorp - Argon - NMMC, 94.83018385147369, 0.0632709940686966
    Pirates - Duke's - Strong Arms - Split - Arteus - Teladi - TerraCorp - Argon, 47.16627111223759, 0.1484111386151916
    Yaki - Pirates - Strong Arms - Split - Arteus - TerraCorp - Argon - NMMC, 63.177852452446224, 0.11079832137803163
    Yaki - Split - Terran - Teladi - TerraCorp - Argon, 114.11822648055377, 0.07886557894880743
    Paranid - Pirates - Strong Arms - Split - Arteus - Teladi - Argon, 79.8892449387464, 0.10013863575921705
    Paranid - Yaki - Strong Arms - Split - Arteus - Teladi - Argon, 57.85799732853213, 0.1382695628846952
    Paranid - Split - Terran - Arteus - Teladi - TerraCorp - Argon, 49.66654807465014, 0.1610742101097058
    Pirates - Split - Arteus - Terran - Teladi - TerraCorp - Argon - NMMC, 98.6228782504009, 0.07097744584402803
    Paranid - Duke's - Strong Arms - Split - Arteus - Teladi - TerraCorp - Argon - NMMC, 105.61913933803015, 0.05680788574499951
    Paranid - Yaki - Duke's - Strong Arms - Split - Teladi - TerraCorp - Argon, 94.06906416019612, 0.07441341170439689
    Paranid - Duke's - Strong Arms - Split - Terran - Teladi - TerraCorp - Argon - NMMC, 93.06906416019615, 0.06446825327127427
    Pirates - Duke's - Strong Arms - Split - Terran - TerraCorp - NMMC, 88.55518975086505, 0.09033914356128238
    Yaki - Pirates - Duke's - Strong Arms - Split - Teladi, 147.44022770185865, 0.06104168543607414
    Yaki - Duke's - Strong Arms - Split - Terran - Teladi - TerraCorp, 53.89220028207983, 0.14844448655142684
    Paranid - Pirates - Strong Arms - Split - Terran - Teladi, 48.47276866184174, 0.18567125931646838
    Paranid - Yaki - Pirates - Strong Arms - Split - Teladi, 32.86241023687177, 0.27386913909016813
    Paranid - Yaki - Split - Terran - Teladi, 49.81070394878787, 0.20076006173856428
    Yaki - Pirates - Split - Terran - Teladi, 52.987073120395834, 0.18872527601738376
    Paranid - OTAS - Duke's - Strong Arms - Split - Teladi - TerraCorp - Argon, 62.74918432639611, 0.11155523494279711
    Paranid - Yaki - OTAS - Strong Arms - Split - Teladi - Argon, 32.31200294517334, 0.2475860135805977
    Paranid - OTAS - Strong Arms - Split - Terran - Teladi - Argon, 56.67868781286092, 0.14114652806384706
    OTAS - Pirates - Duke's - Strong Arms - Split - Teladi - Argon, 50.113064716891316, 0.15963900921237187
    Yaki - OTAS - Pirates - Strong Arms - Split - Teladi - Argon, 60.88803380353414, 0.13138870645443068
    Yaki - OTAS - Strong Arms - Split - Terran - Teladi, 70.74826729107554, 0.12721159605184135
    Paranid - OTAS - Pirates - Strong Arms - Split - Teladi - Argon, 42.93358036347606, 0.18633433159480134
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Teladi, 23.013824515469743, 0.3476171461471974
    Paranid - Yaki - OTAS - Split - Terran - Teladi, 21.60071275172332, 0.4166529180516033
    OTAS - Pirates - Strong Arms - Split - Terran - Teladi - Argon - NMMC, 113.44821102410228, 0.06170216292359901
    Paranid - Pirates - Duke's - Strong Arms - Split - Teladi, 61.47705283352004, 0.1463960874047104
    Paranid - Yaki - Pirates - Duke's - Split - Teladi, 76.07661840631599, 0.11830178823054532
    Paranid - Yaki - Duke's - Split - Terran - Teladi, 46.81699812772387, 0.1922378700028275
    Yaki - Pirates - Duke's - Split - Terran - Teladi, 26.90083188685102, 0.33456214431789194
    Paranid - Yaki - Pirates - Split - Terran - Teladi, 17.38931773963645, 0.5175591207633059
    OTAS - Pirates - Duke's - Arteus - Teladi - TerraCorp - Argon, 70.28061996207745, 0.1138293885898659
    Yaki - OTAS - Duke's - Strong Arms - Arteus - Teladi - TerraCorp - Argon, 48.550331500966784, 0.14418027196911332
    OTAS - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon - NMMC, 56.999407660615006, 0.1228082937577052
    OTAS - Pirates - Duke's - Terran - Teladi - TerraCorp - NMMC, 70.03733232122815, 0.11422479604602558
    Yaki - OTAS - Pirates - Duke's - Arteus - Teladi, 59.8098968271885, 0.15047676851883085
    Yaki - OTAS - Arteus - Terran - Teladi - TerraCorp - NMMC, 57.768551882727344, 0.13848365138597113
    Paranid - OTAS - Pirates - Strong Arms - Arteus - Terran - Teladi - Argon - NMMC, 86.10788851106679, 0.06968002704222466
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Arteus - Teladi - Argon, 68.17540626892475, 0.10267632249066175
    Paranid - Yaki - OTAS - Arteus - Terran - Teladi, 30.38554428872312, 0.2961934765585271
    Yaki - OTAS - Pirates - Arteus - Terran - Teladi, 43.033427231180426, 0.2091397450556514
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Teladi - TerraCorp, 47.62118369002942, 0.1679924642796097
    Paranid - Yaki - Pirates - Duke's - Arteus - Teladi, 34.72006188180883, 0.25921612785821224
    Paranid - Yaki - Duke's - Arteus - Terran - Teladi, 22.393122694714922, 0.40190910944832725
    Yaki - Pirates - Duke's - Arteus - Terran - Teladi, 17.163290845445452, 0.5243749628812175
    Paranid - Yaki - Pirates - Arteus - Terran - Teladi, 21.745032098769965, 0.4138876392143425
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Teladi - Argon - NMMC, 121.92017358628598, 0.05741461641740465
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Teladi - Argon, 108.26049840758684, 0.07389583567111459
    Paranid - OTAS - Duke's - Strong Arms - Terran - TerraCorp - Argon - NMMC, 110.2263447222948, 0.0635056892944773
    Yaki - OTAS - Pirates - Duke's - Terran - Teladi, 16.14676398161307, 0.5573872269544932
    Paranid - Yaki - OTAS - Pirates - Terran - Teladi, 26.27385485744829, 0.3425458520963329
    Paranid - Yaki - Pirates - Duke's - Terran - Teladi, 16.223570202673933, 0.5547484239021964
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - Teladi - TerraCorp, 86.63882533147228, 0.0807951859136898
    Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - Teladi - TerraCorp, 64.31135674247234, 0.1088454723172879
    OTAS - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp - NMMC, 66.20762095019293, 0.10572800985049745
    Pirates - Boron - Duke's - Split - Strong Arms - Arteus - Teladi - TerraCorp, 62.749184326396154, 0.11155523494279702
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - TerraCorp - NMMC, 87.10788851106685, 0.08036011570996428
    Yaki - Boron - Strong Arms - Terran - Teladi - TerraCorp, 93.42056627817593, 0.09633852971090906
    Paranid - Pirates - Boron - Split - Strong Arms - Teladi - TerraCorp - NMMC, 137.9550807705395, 0.05074115401116028
    Paranid - Yaki - Boron - Split - Arteus - Teladi, 146.77178849348002, 0.0613196861084772
    Paranid - Boron - Strong Arms - Split - Arteus - Terran - Teladi - NMMC, 117.54732270617387, 0.0595504843398049
    OTAS - Pirates - Boron - Split - Strong Arms - Terran - Teladi - TerraCorp - NMMC, 86.10788851106678, 0.06968002704222467
    Paranid - Boron - Duke's - Strong Arms - Split - Arteus - Teladi - TerraCorp, 62.74918432639614, 0.11155523494279705
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Teladi - TerraCorp, 94.06906416019612, 0.07441341170439689
    Paranid - Boron - Duke's - Strong Arms - Split - Terran - Teladi - TerraCorp - NMMC, 93.06906416019618, 0.06446825327127424
    Pirates - Boron - Duke's - Terran - Teladi - TerraCorp - NMMC, 174.0467562068749, 0.04596466015425801
    Yaki - Pirates - Boron - Duke's - Strong Arms - Teladi - TerraCorp, 79.64272237690523, 0.10044860046521761
    Yaki - Boron - Duke's - Terran - Teladi - TerraCorp, 84.74537388465743, 0.10620048726493835
    Paranid - Pirates - Boron - Split - Terran - Teladi, 66.41043668013279, 0.13552086765140067
    Paranid - Yaki - Pirates - Boron - Split - Teladi, 111.12440443411505, 0.08099031032680173
    Paranid - Yaki - Boron - Terran - Teladi, 45.1548163025851, 0.22146031849602504
    Yaki - Pirates - Boron - Terran - Teladi, 48.58560628309561, 0.2058222746410247
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Teladi - TerraCorp - NMMC, 105.61913933803017, 0.0568078857449995
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Teladi, 35.014028419563765, 0.22847985110819394
    Paranid - OTAS - Boron - Split - Terran - Teladi, 109.61015709713513, 0.08210917891509191
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Teladi - NMMC, 99.19062694242137, 0.07057118415093185
    Yaki - OTAS - Pirates - Boron - Duke's - Teladi, 81.47064996293648, 0.11046923038044226
    Yaki - OTAS - Boron - Terran - Teladi, 88.67536131671817, 0.11277089657727368
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Teladi, 46.693138599400555, 0.17133138272488505
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Teladi, 32.097052200230486, 0.2492440723245779
    Paranid - Yaki - OTAS - Boron - Terran - Teladi, 23.457599353356898, 0.38367097435791336
    Yaki - OTAS - Pirates - Boron - Terran - Teladi, 28.92385082802412, 0.31116188689785257
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Teladi, 45.55366263966823, 0.1756170533043721
    Paranid - Yaki - Pirates - Boron - Duke's - Teladi, 101.04009353895368, 0.08907355174340033
    Paranid - Yaki - Boron - Duke's - Terran - Teladi, 41.837349519526946, 0.21511878986978816
    Yaki - Pirates - Boron - Duke's - Terran - Teladi, 25.715211055661648, 0.34998740552893476
    Paranid - Yaki - Pirates - Boron - Terran - Teladi, 19.662033995337964, 0.45773494248529817
    Paranid - OTAS - Boron - Duke's - Arteus - Teladi - TerraCorp - NMMC, 88.02789410563415, 0.07952024833855444
    Paranid - Yaki - OTAS - Boron - Arteus - Teladi - NMMC, 103.43835706296457, 0.07734074889772537
    Paranid - OTAS - Boron - Arteus - Terran - Teladi - TerraCorp, 64.96151189598552, 0.12314984313803173
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Teladi - NMMC, 87.79750639908329, 0.07972891585532649
    Yaki - Pirates - Boron - Duke's - Arteus - Teladi, 64.29314380811672, 0.13998382202090714
    Yaki - Boron - Strong Arms - Arteus - Terran - Teladi, 142.27383480800103, 0.06325829350242458
    Paranid - Pirates - Boron - Arteus - Terran - Teladi, 67.33536897743068, 0.1336593255027176
    Paranid - Yaki - Pirates - Boron - Arteus - Teladi, 62.08155333367705, 0.14497059942470572
    Paranid - Yaki - Boron - Arteus - Terran - Teladi, 18.861137650881126, 0.47717164078803864
    Yaki - Pirates - Boron - Arteus - Terran - Teladi, 27.635657820117547, 0.3256662120576842
    Paranid - Pirates - Boron - Duke's - Arteus - Teladi, 49.791256532998105, 0.18075462695012406
    Paranid - Yaki - Boron - Duke's - Arteus - Teladi, 98.68624697796983, 0.09119811803167578
    Paranid - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi - NMMC, 181.7167379354338, 0.038521492733856945
    Pirates - Boron - Duke's - Terran - Arteus - Teladi - NMMC, 141.28901837683551, 0.0566215272206294
    Yaki - Boron - Arteus - Terran - Teladi - TerraCorp, 34.079089729357165, 0.26409156088013175
    Paranid - Yaki - Pirates - Boron - Arteus - Terran - Teladi, 13.237714343913561, 0.6043339350103322
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Teladi - NMMC, 64.8846609946018, 0.1078837415915971
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Teladi, 70.27126358760057, 0.1138445445772745
    Paranid - OTAS - Boron - Duke's - Terran - Teladi - TerraCorp - NMMC, 73.3681226261695, 0.0954092833432157
    OTAS - Pirates - Boron - Duke's - Terran - Teladi - NMMC, 75.74399286182677, 0.105618936865313
    Yaki - OTAS - Boron - Duke's - Terran - Teladi, 39.191645455729756, 0.2296407791851009
    Paranid - Yaki - OTAS - Pirates - Boron - Terran - Teladi, 16.33231780825712, 0.489826373324394
    Paranid - Pirates - Boron - Duke's - Terran - Teladi - NMMC, 76.57905776588971, 0.10446720335025336
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Teladi - NMMC, 69.23395430359594, 0.10110645954591138
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - Teladi, 51.324516549079924, 0.155870927539081
    Paranid - OTAS - Strong Arms - Split - Arteus - Terran - Teladi - TerraCorp, 48.03627555136282, 0.14572320438363806
    Pirates - Duke's - Split - Terran - Arteus - Teladi - TerraCorp, 28.92617775434061, 0.27656609414285765
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Teladi, 34.500569388668595, 0.2318802310151881
    Yaki - Split - Terran - Arteus - Teladi - TerraCorp - NMMC, 62.92289601610766, 0.1271397298362122
    Paranid - Pirates - Split - Arteus - Terran - Teladi, 53.29196760748904, 0.1688809853351191
    Paranid - Yaki - Pirates - Split - Arteus - Teladi - NMMC, 63.75652481507101, 0.12547735346624364
    Paranid - Yaki - Split - Terran - Arteus - Teladi, 24.20853725435229, 0.3717696738732924
    Yaki - Pirates - Split - Arteus - Terran - Teladi, 35.5870519336455, 0.2529009713077981
    Paranid - Pirates - Duke's - Split - Arteus - Teladi, 67.82453757636321, 0.13269533890838486
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - Teladi, 47.28149497342237, 0.16919938772022583
    Paranid - Duke's - Split - Terran - Arteus - Teladi - TerraCorp, 43.157316924339504, 0.18536833543255388
    Yaki - Duke's - Split - Terran - Arteus - Teladi - TerraCorp, 28.92617775434061, 0.27656609414285765
    Paranid - Yaki - Pirates - Split - Arteus - Terran - Teladi, 13.712379692669481, 0.5834144167023562
    Paranid - OTAS - Pirates - Duke's - Split - Teladi, 57.73532075279447, 0.15588377933389047
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Teladi, 31.10127511589831, 0.257224180365215
    Paranid - OTAS - Duke's - Strong Arms - Split - Terran - Teladi - NMMC, 54.33159073935773, 0.1288384879725086
    OTAS - Pirates - Duke's - Split - Terran - Teladi, 51.24911488735735, 0.17561278901658087
    Yaki - OTAS - Pirates - Duke's - Split - Teladi, 76.52411847953418, 0.11760997942638156
    Yaki - OTAS - Duke's - Split - Terran - Teladi, 51.24911488735735, 0.17561278901658087
    Paranid - OTAS - Pirates - Split - Terran - Teladi, 45.48547437663279, 0.1978653652257733
    Yaki - OTAS - Pirates - Split - Terran - Teladi, 27.859462673116916, 0.3230500209425999
    Paranid - Pirates - Duke's - Split - Terran - Teladi, 46.81699812772388, 0.19223787000282747
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - Teladi, 50.15339537522579, 0.15951063612239003
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus - Teladi, 51.9410400090521, 0.15402078969935504
    Paranid - OTAS - Duke's - Arteus - Terran - Teladi - TerraCorp, 51.53438684539652, 0.1552361537549685
    OTAS - Pirates - Duke's - Arteus - Terran - Teladi - NMMC, 58.83809919068022, 0.1359663230124738
    Yaki - OTAS - Duke's - Arteus - Terran - Teladi, 33.902776787020386, 0.2654649811293815
    Paranid - Yaki - OTAS - Pirates - Arteus - Terran - Teladi, 21.31524678743468, 0.3753181973345011
    Paranid - Pirates - Duke's - Arteus - Terran - Teladi, 32.166747356899975, 0.2797920442543421
    Paranid - OTAS - Pirates - Duke's - Terran - Teladi, 46.08682789914609, 0.19528356387849283
    Paranid - Yaki - OTAS - Pirates - Duke's - Teladi, 77.16257616948857, 0.11663685230300484
    Paranid - Yaki - OTAS - Duke's - Terran - Teladi, 24.759786003691033, 0.3634926407949704
    OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Teladi - Argon - NMMC, 1633.4999999999973, 0.0036730945821854973
    Yaki - OTAS - Boron - Split - Arteus - Teladi - Argon, 52.41631901168029, 0.1526242237311114
    OTAS - Boron - Split - Arteus - Terran - Teladi - Argon, 175.34920052890647, 0.04562324764452629
    OTAS - Pirates - Boron - Split - Arteus - Teladi - Argon, 80.87499341785883, 0.09891809151273993
    Yaki - Pirates - Boron - Split - Arteus - Teladi - Argon - NMMC, 102.9364327737121, 0.06800313369502795
    Yaki - Strong Arms - Terran - Arteus - Teladi - Argon - NMMC, 145.67270688553185, 0.05491763125048757
    Paranid - OTAS - Boron - Split - Arteus - Teladi - Argon, 27.09986399081354, 0.2952044335983341
    Paranid - Yaki - Boron - Strong Arms - Split - Teladi - Argon, 435.8858503010333, 0.018353428987141946
    Paranid - Boron - Arteus - Terran - Teladi - Argon - NMMC, 161.69010029801768, 0.04947736432381989
    OTAS - Pirates - Boron - Split - Terran - Teladi - Argon, 47.235065324486285, 0.16936570204874604
    Paranid - Boron - Duke's - Strong Arms - Split - Arteus - Teladi - Argon - NMMC, 1633.4999999999852, 0.0036730945821855246
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Teladi - Argon, 303.547619047619, 0.02306063220644757
    Paranid - Boron - Duke's - Arteus - Terran - Teladi - Argon - NMMC, 89.20366459272788, 0.07847211246263822
    Pirates - Boron - Duke's - Split - Strong Arms - Arteus - Teladi - Argon - NMMC, 1633.4999999999973, 0.0036730945821854973
    Yaki - Pirates - Boron - Duke's - Strong Arms - Teladi - Argon, 114.4303107831423, 0.06991154655833154
    Yaki - Strong Arms - Split - Terran - Arteus - Teladi - Argon, 142.75374006908618, 0.05604056325339267
    Paranid - Pirates - Boron - Split - Strong Arms - Teladi - Argon, 116.27350909274038, 0.06880329029735532
    Paranid - Yaki - Pirates - Boron - Teladi - Argon - NMMC, 313.8599985074364, 0.02548907168178188
    Paranid - Yaki - Terran - Teladi - Argon, 67.07759031817228, 0.14908108583755814
    Yaki - Pirates - Terran - Teladi - Argon, 56.7315135575892, 0.17626887373362277
    Paranid - OTAS - Boron - Duke's - Split - Teladi - Argon - NMMC, 176.42023543228885, 0.03967798808820115
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Teladi - Argon, 63.97516688100919, 0.10941745588596388
    Paranid - OTAS - Boron - Split - Terran - Teladi - Argon, 31.642627524433696, 0.25282350505888257
    OTAS - Pirates - Boron - Duke's - Split - Teladi - Argon, 52.66666666666664, 0.15189873417721525
    Yaki - OTAS - Pirates - Boron - Split - Teladi - Argon, 43.62431232883107, 0.1833839795501566
    Yaki - OTAS - Boron - Terran - Teladi - Argon, 29.47232711281187, 0.3053712034869355
    Paranid - OTAS - Pirates - Boron - Split - Teladi - Argon, 31.834618364968808, 0.2512987562245538
    Paranid - Yaki - OTAS - Boron - Split - Teladi - Argon, 32.928776974866224, 0.2429485919293697
    Paranid - Yaki - OTAS - Terran - Teladi - Argon, 30.8617936778041, 0.2916227129880927
    Yaki - OTAS - Pirates - Terran - Teladi - Argon, 31.778694426825723, 0.2832086138945571
    Paranid - Pirates - Duke's - Strong Arms - Split - Teladi - Argon, 51.43406531135165, 0.15553894003074994
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Teladi - Argon, 28.858170935104695, 0.27721784648064274
    Paranid - Yaki - Duke's - Terran - Teladi - Argon, 57.13074142120199, 0.15753340103967176
    Yaki - Pirates - Duke's - Terran - Teladi - Argon, 27.76272855952716, 0.3241756292326507
    Paranid - Pirates - Boron - Terran - Teladi - Argon - NMMC, 304.2776893497302, 0.026291773205905256
    Paranid - OTAS - Boron - Duke's - Arteus - Teladi - Argon, 31.947819698534737, 0.25040832443307276
    Yaki - OTAS - Boron - Duke's - Arteus - Teladi - Argon, 31.427427971506464, 0.2545547159396297
    OTAS - Boron - Duke's - Arteus - Terran - Teladi - Argon - NMMC, 67.14891985748432, 0.10424590618667696
    OTAS - Pirates - Boron - Duke's - Arteus - Teladi - Argon, 24.748635272965323, 0.32325014740263125
    Yaki - OTAS - Pirates - Boron - Arteus - Teladi - Argon, 34.326940961150385, 0.23305309986852668
    Yaki - OTAS - Arteus - Terran - Teladi - Argon, 46.054058507316505, 0.19542251631460864
    Paranid - OTAS - Pirates - Boron - Arteus - Teladi - Argon, 45.303359339018286, 0.17658734620833877
    Paranid - Yaki - Boron - Arteus - Teladi - Argon, 62.30754325288373, 0.14444478999071209
    Paranid - OTAS - Boron - Arteus - Terran - Teladi - Argon, 28.841855370238168, 0.2773746659951418
    OTAS - Pirates - Boron - Arteus - Terran - Teladi - Argon, 54.49245917850049, 0.14680930390376523
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Teladi - Argon, 55.72732437197748, 0.14355614754802054
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Teladi - Argon, 72.46160946163393, 0.11040328885098448
    Paranid - Yaki - Arteus - Terran - Teladi - Argon, 27.340517717330652, 0.32918176945475563
    Pirates - Duke's - Strong Arms - Terran - Arteus - Teladi - Argon - NMMC, 146.29465899753475, 0.04784863677161282
    Yaki - Pirates - Duke's - Arteus - Teladi - Argon, 125.63742602187409, 0.07163470539768187
    Paranid - Pirates - Boron - Arteus - Terran - Teladi - Argon, 30.59457019285051, 0.2614843074955006
    Paranid - Yaki - Pirates - Boron - Arteus - Teladi - Argon, 25.378392899062238, 0.3152287866224819
    Yaki - Pirates - Arteus - Terran - Teladi - Argon, 33.2880662394158, 0.2703671620715313
    Paranid - OTAS - Pirates - Boron - Duke's - Teladi - Argon, 50.978473230317256, 0.15692898380570455
    Paranid - Yaki - OTAS - Boron - Duke's - Teladi - Argon, 61.634475747020616, 0.1297974859530904
    Paranid - OTAS - Boron - Duke's - Terran - Teladi - Argon - NMMC, 74.20064701855316, 0.0943388000140985
    OTAS - Pirates - Duke's - Terran - Teladi - Argon - NMMC, 93.72771255287239, 0.08535362468690516
    Yaki - OTAS - Pirates - Duke's - Teladi - Argon, 113.89735815620045, 0.07901851408754602
    Yaki - OTAS - Duke's - Terran - Teladi - Argon, 40.21097732361929, 0.22381947913296657
    Paranid - OTAS - Pirates - Boron - Terran - Teladi - Argon, 43.323178520115164, 0.1846586578656864
    Paranid - Yaki - OTAS - Pirates - Boron - Teladi - Argon, 43.77721729832896, 0.18274345638468373
    Paranid - Pirates - Duke's - Terran - Teladi - Argon - NMMC, 175.48392294856654, 0.04558822179023636
    Paranid - Yaki - Pirates - Terran - Teladi - Argon, 24.76156072533664, 0.3634665883879839
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - Teladi - Argon, 37.14231989827692, 0.18846426446089437
    Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - Teladi - Argon, 63.17785245244622, 0.11079832137803164
    Paranid - OTAS - Split - Terran - Arteus - Teladi - Argon, 49.66654807465016, 0.1610742101097057
    OTAS - Pirates - Duke's - Split - Arteus - Teladi - Argon, 51.94579599690188, 0.15400668805762704
    Yaki - OTAS - Pirates - Split - Arteus - Teladi - Argon - NMMC, 98.60899147777214, 0.07098744135901541
    Yaki - OTAS - Split - Terran - Teladi - Argon, 45.696337412770035, 0.19695232724461
    Paranid - OTAS - Pirates - Split - Arteus - Teladi - Argon, 79.90718806204502, 0.10011614967339723
    Paranid - Yaki - OTAS - Split - Arteus - Teladi - Argon, 57.25796584999258, 0.13971855061981803
    Paranid - Yaki - Split - Terran - Teladi - Argon, 46.02285157147351, 0.1955550273981393
    OTAS - Pirates - Split - Arteus - Terran - Teladi - Argon - NMMC, 98.62287825040092, 0.07097744584402801
    Paranid - Pirates - Duke's - Split - Arteus - Teladi - Argon, 48.9251448787161, 0.16351510087158147
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - Teladi - Argon, 34.319094427385195, 0.20396808589489746
    Paranid - Yaki - Duke's - Split - Terran - Teladi - Argon, 44.57160379298841, 0.17948647388045044
    Pirates - Duke's - Split - Terran - Arteus - Teladi - Argon - NMMC, 181.83317695427033, 0.038496825041782375
    Yaki - Pirates - Duke's - Strong Arms - Split - Teladi - Argon, 86.24794823549337, 0.09275582971732403
    Paranid - Pirates - Split - Terran - Teladi - Argon, 107.88819092835506, 0.08341969517290913
    Paranid - Yaki - Pirates - Strong Arms - Split - Teladi - Argon, 24.7890608801376, 0.3227229961910357
    Yaki - Pirates - Split - Terran - Teladi - Argon, 41.91523274047646, 0.21471907494167225
    Paranid - OTAS - Pirates - Duke's - Split - Teladi - Argon, 33.28463096960433, 0.24035117010327184
    Paranid - Yaki - OTAS - Duke's - Split - Teladi - Argon, 108.26049840758685, 0.07389583567111459
    Paranid - OTAS - Duke's - Split - Terran - Teladi - Argon - NMMC, 68.26928391517565, 0.10253513144648589
    OTAS - Pirates - Duke's - Split - Terran - Teladi - Argon, 30.27576905092694, 0.2642377138807996
    Yaki - OTAS - Pirates - Duke's - Split - Teladi - Argon, 35.05938816249976, 0.22818424448595953
    Yaki - OTAS - Duke's - Split - Terran - Teladi - Argon, 30.27576905092694, 0.2642377138807996
    Paranid - OTAS - Pirates - Split - Terran - Teladi - Argon, 27.49621061020729, 0.29094918254045515
    Paranid - Yaki - OTAS - Pirates - Split - Teladi - Argon, 39.284713267060035, 0.20364155251981808
    Paranid - Yaki - OTAS - Split - Terran - Teladi - Argon, 16.825133458475417, 0.47547914075951153
    Yaki - OTAS - Pirates - Split - Terran - Teladi - Argon, 18.777871975513882, 0.4260333657845736
    Paranid - Pirates - Duke's - Split - Terran - Teladi - Argon, 44.57160379298841, 0.17948647388045044
    Paranid - Yaki - Pirates - Duke's - Split - Teladi - Argon, 64.91859520916339, 0.12323125560903672
    Yaki - Pirates - Duke's - Split - Terran - Teladi - Argon, 25.74655545801708, 0.31072117639367264
    Paranid - Yaki - Pirates - Split - Terran - Teladi - Argon, 16.369880664161187, 0.4887024019371451
    Paranid - OTAS - Pirates - Duke's - Arteus - Teladi - Argon, 50.19987482518708, 0.15936294717583863
    Paranid - Yaki - OTAS - Duke's - Arteus - Teladi - Argon, 60.76181387753217, 0.131661638938632
    Paranid - OTAS - Duke's - Arteus - Terran - Teladi - Argon - NMMC, 73.2776963807951, 0.0955270204404868
    OTAS - Pirates - Duke's - Arteus - Terran - Teladi - Argon, 31.737605639204723, 0.2520669041938623
    Yaki - OTAS - Pirates - Duke's - Arteus - Teladi - Argon, 29.05701649663753, 0.27532076463960975
    Yaki - Duke's - Strong Arms - Terran - Arteus - Teladi - Argon, 74.20964658221386, 0.10780269639388626
    Paranid - Yaki - OTAS - Arteus - Terran - Teladi - Argon, 21.07669338058156, 0.37956618030846256
    Yaki - OTAS - Pirates - Arteus - Terran - Teladi - Argon, 24.78396297655585, 0.3227893782591397
    Paranid - Pirates - Duke's - Arteus - Terran - Teladi - Argon, 28.00037782897694, 0.28571043036858546
    Paranid - Yaki - Pirates - Duke's - Arteus - Teladi - Argon, 27.89026857007019, 0.28683839956224083
    Paranid - Yaki - Duke's - Arteus - Terran - Teladi - Argon, 20.43926589898794, 0.39140348971124855
    Yaki - Pirates - Duke's - Arteus - Terran - Teladi - Argon, 15.827006184696078, 0.5054651465123959
    Paranid - Yaki - Pirates - Arteus - Terran - Teladi - Argon, 17.712780058927372, 0.4516512920831951
    Paranid - OTAS - Pirates - Duke's - Terran - Teladi - Argon, 34.04642612949202, 0.23497326766612264
    Paranid - Yaki - OTAS - Pirates - Duke's - Teladi - Argon, 44.04728661163273, 0.1816229923658278
    Paranid - Yaki - OTAS - Duke's - Terran - Teladi - Argon, 20.478567913992205, 0.3906523167830458
    Yaki - OTAS - Pirates - Duke's - Terran - Teladi - Argon, 13.881707349783419, 0.576297986870096
    Paranid - Yaki - OTAS - Pirates - Terran - Teladi - Argon, 20.445678958355234, 0.3912807207965455
    Paranid - Yaki - Pirates - Duke's - Terran - Teladi - Argon, 15.900417795986314, 0.5031314335664445
    Paranid - OTAS - Boron - Duke's - Split - Arteus - Teladi, 56.93773524548503, 0.14050435911277967
    Paranid - Yaki - OTAS - Boron - Split - Arteus - Teladi, 34.65394416736295, 0.23085395305549064
    Paranid - OTAS - Boron - Split - Arteus - Terran - Teladi, 33.508559096649876, 0.23874497190181554
    OTAS - Pirates - Boron - Duke's - Split - Arteus - Teladi, 50.26726823767024, 0.1591492890000497
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Arteus - Teladi, 73.35479826418606, 0.09542661374092556
    Yaki - Boron - Strong Arms - Split - Arteus - Terran - Teladi, 135.70049832526612, 0.05895335756855122
    Paranid - Pirates - Boron - Split - Arteus - Teladi - NMMC, 107.8207367866773, 0.07419722994314121
    Paranid - Yaki - Pirates - Boron - Split - Arteus - Teladi, 27.182967052237057, 0.29430194226504164
    Paranid - Yaki - Boron - Split - Terran - Teladi, 36.68059117326715, 0.24536136720062482
    Yaki - Pirates - Boron - Split - Terran - Teladi, 39.78119574994216, 0.2262375434004667
    Paranid - Pirates - Boron - Duke's - Split - Arteus - Teladi, 28.447890679602665, 0.28121592880473406
    Paranid - Yaki - Boron - Duke's - Split - Arteus - Teladi, 69.50898976926985, 0.11509302647837973
    Paranid - Boron - Duke's - Split - Arteus - Terran - Teladi - NMMC, 128.89648411625996, 0.054307144589655784
    Pirates - Boron - Duke's - Split - Arteus - Terran - Teladi - NMMC, 106.32113473855348, 0.0658382739914617
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Teladi, 104.07129473417129, 0.07687038025648046
    Yaki - Boron - Duke's - Split - Arteus - Terran - Teladi, 107.32113473855347, 0.07454263337309015
    Paranid - Pirates - Boron - Split - Arteus - Terran - Teladi, 25.644753032335657, 0.311954651694744
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Teladi, 27.81471288246081, 0.28761756534415206
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Teladi, 70.27126358760057, 0.1138445445772745
    Paranid - OTAS - Boron - Duke's - Split - Terran - Teladi, 53.14574865729452, 0.15052944406874885
    OTAS - Pirates - Boron - Duke's - Split - Terran - Teladi, 32.816470166877465, 0.243780027508096
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Teladi, 37.202441173516334, 0.2150396519058281
    Yaki - OTAS - Boron - Split - Terran - Teladi, 54.59958846803888, 0.16483640724267282
    Paranid - OTAS - Pirates - Boron - Split - Terran - Teladi, 23.982462471010553, 0.3335770882439706
    Paranid - Yaki - OTAS - Boron - Split - Terran - Teladi, 15.152155977411853, 0.5279776694436117
    Yaki - OTAS - Pirates - Boron - Split - Terran - Teladi, 19.7170283997877, 0.40574065410820925
    Paranid - Pirates - Boron - Duke's - Split - Terran - Teladi, 36.089037722861526, 0.22167396264301598
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Teladi, 45.78793327094657, 0.1747185214204934
    Paranid - Yaki - Boron - Duke's - Split - Terran - Teladi, 36.08903772286153, 0.22167396264301592
    Yaki - Pirates - Boron - Duke's - Split - Terran - Teladi, 24.515143263439022, 0.3263289108300217
    Paranid - Yaki - Pirates - Boron - Split - Terran - Teladi, 14.542898294288541, 0.5500966752371399
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - Teladi, 24.34205273646713, 0.32864935782573096
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - Teladi, 27.972793928146857, 0.2859921686961065
    Paranid - OTAS - Boron - Duke's - Arteus - Terran - Teladi, 32.91188651100823, 0.24307327376460763
    OTAS - Pirates - Boron - Duke's - Arteus - Terran - Teladi, 25.65997582669786, 0.3117695844310352
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - Teladi, 22.55386837710806, 0.35470633534954543
    Yaki - OTAS - Boron - Arteus - Terran - Teladi, 40.05868808740642, 0.2246703631522422
    Paranid - OTAS - Pirates - Boron - Arteus - Terran - Teladi, 50.93402646106705, 0.15706592539105543
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - Teladi, 50.88932358976021, 0.15720389731432263
    Paranid - Yaki - OTAS - Boron - Arteus - Terran - Teladi, 15.227820792390384, 0.5253542256025067
    Yaki - OTAS - Pirates - Boron - Arteus - Terran - Teladi, 21.50140202348525, 0.3720687605050997
    Paranid - Pirates - Boron - Duke's - Arteus - Terran - Teladi, 18.714302216250783, 0.4274805390848667
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Teladi, 17.73037989655715, 0.45120296613347943
    Paranid - Yaki - Boron - Duke's - Arteus - Terran - Teladi, 15.2670952311997, 0.5240027574892747
    Yaki - Pirates - Boron - Duke's - Arteus - Terran - Teladi, 14.035099955227667, 0.5699995030687496
    Paranid - OTAS - Pirates - Boron - Duke's - Terran - Teladi, 24.95556889208041, 0.3205697307320764
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Teladi, 29.364867835054834, 0.27243439490130644
    Paranid - Yaki - OTAS - Boron - Duke's - Terran - Teladi, 16.923336014513225, 0.47272003540787155
    Yaki - OTAS - Pirates - Boron - Duke's - Terran - Teladi, 12.980508070888618, 0.6163086958007136
    Paranid - Yaki - Pirates - Boron - Duke's - Terran - Teladi, 13.955364931666612, 0.5732562379538293
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - Teladi, 24.13786378558978, 0.33142949479961736
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - Teladi, 51.94104000905209, 0.1540207896993551
    Paranid - OTAS - Duke's - Split - Arteus - Terran - Teladi, 43.15731692433951, 0.18536833543255385
    OTAS - Pirates - Duke's - Split - Arteus - Terran - Teladi, 28.926177754340607, 0.2765660941428577
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - Teladi, 31.512924591746255, 0.2538640923887886
    Yaki - OTAS - Split - Terran - Arteus - Teladi - NMMC, 62.922896016107664, 0.1271397298362122
    Paranid - OTAS - Pirates - Split - Arteus - Terran - Teladi, 33.581256250674315, 0.23822813358387565
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - Teladi, 53.51590264581354, 0.149488275530859
    Paranid - Yaki - OTAS - Split - Arteus - Terran - Teladi, 17.10735473419233, 0.4676351267803236
    Yaki - OTAS - Pirates - Split - Arteus - Terran - Teladi, 24.62003336631456, 0.32493863354977015
    Paranid - Pirates - Duke's - Split - Arteus - Terran - Teladi, 19.676241603481802, 0.4065817121591129
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Teladi, 21.93192971944889, 0.3647649843098725
    Paranid - Yaki - Duke's - Split - Arteus - Terran - Teladi, 19.676241603481802, 0.4065817121591129
    Yaki - Pirates - Duke's - Split - Arteus - Terran - Teladi, 16.341550106072084, 0.4895496417458839
    Paranid - OTAS - Pirates - Duke's - Split - Terran - Teladi, 16.499455644000264, 0.4848644811448103
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Teladi, 22.157800645693865, 0.36104666378766775
    Paranid - Yaki - OTAS - Duke's - Split - Terran - Teladi, 16.499455644000264, 0.4848644811448103
    Yaki - OTAS - Pirates - Duke's - Split - Terran - Teladi, 12.590226112326768, 0.6354135286075129
    Paranid - Yaki - OTAS - Pirates - Split - Terran - Teladi, 13.356965612597897, 0.5989384289837982
    Paranid - Yaki - Pirates - Duke's - Split - Terran - Teladi, 13.12028158104536, 0.6097430112748082
    Paranid - OTAS - Pirates - Duke's - Arteus - Terran - Teladi, 22.388291537690225, 0.35732963305985926
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - Teladi, 25.408274079964347, 0.3148580645352998
    Paranid - Yaki - OTAS - Duke's - Arteus - Terran - Teladi, 15.56110594668168, 0.5141022770110987
    Yaki - OTAS - Pirates - Duke's - Arteus - Terran - Teladi, 12.15870186067652, 0.6579649778134188
    Paranid - Yaki - Pirates - Duke's - Arteus - Terran - Teladi, 10.624619997649297, 0.7529681063200382
    Paranid - Yaki - OTAS - Pirates - Duke's - Terran - Teladi, 12.060890161994669, 0.6633009581008351
    OTAS - Boron - Duke's - Split - Arteus - Teladi - TerraCorp - Argon, 23.192395281594635, 0.30182307239111106
    Yaki - OTAS - Boron - Split - Teladi - TerraCorp - Argon - NMMC, 215.2417735405379, 0.032521568117824695
    Boron - Split - Arteus - Terran - Teladi - TerraCorp - Argon, 175.3492005289065, 0.045623247644526285
    OTAS - Pirates - Boron - Split - Arteus - Teladi - TerraCorp - Argon, 30.029883012761122, 0.23310114118744213
    Yaki - Pirates - Boron - Arteus - Teladi - TerraCorp - Argon, 46.091764794947096, 0.17356679735719333
    Yaki - Boron - Terran - Teladi - TerraCorp - Argon, 48.80092930939322, 0.1844227175048422
    Paranid - Boron - Split - Arteus - Teladi - TerraCorp - Argon, 52.28650904033376, 0.15300313879874458
    Paranid - Yaki - Boron - Arteus - Teladi - TerraCorp - Argon, 26.375586287806424, 0.3033107932731885
    Paranid - Boron - Split - Terran - Teladi - TerraCorp - Argon - NMMC, 133.00862644415912, 0.052628165459168944
    Pirates - Boron - Split - Arteus - Terran - Teladi - TerraCorp - Argon, 25.31622723024421, 0.27650249527059867
    Paranid - Boron - Duke's - Split - Arteus - Teladi - TerraCorp - Argon, 30.04004761759408, 0.23302226711185994
    Yaki - Boron - Duke's - Split - Arteus - Teladi - TerraCorp - Argon, 88.09929078014181, 0.07945580421832237
    Boron - Duke's - Split - Terran - Arteus - Teladi - TerraCorp - Argon, 46.17670682730923, 0.1515915811445469
    Pirates - Boron - Duke's - Split - Arteus - Teladi - TerraCorp - Argon, 27.851187365731867, 0.2513357835728328
    Yaki - Pirates - Boron - Duke's - Teladi - TerraCorp - Argon, 424.3028549412612, 0.018854457156804866
    Yaki - Duke's - Terran - Teladi - TerraCorp - Argon, 75.86989471781857, 0.11862412665094009
    Paranid - Pirates - Boron - Arteus - Teladi - TerraCorp - Argon, 44.78451512354454, 0.17863317215628766
    Paranid - Yaki - Pirates - Boron - Teladi - TerraCorp - Argon, 130.38995615961161, 0.06135441897232577
    Paranid - Yaki - Terran - Teladi - TerraCorp, 45.44943968980486, 0.2200247146774657
    Yaki - Pirates - Terran - Teladi - TerraCorp, 53.111760556052644, 0.1882822165054439
    Paranid - OTAS - Boron - Split - Teladi - TerraCorp - Argon, 81.94122384744654, 0.09763095575548078
    Yaki - OTAS - Boron - Duke's - Teladi - TerraCorp - Argon, 194.03744783076368, 0.04122915493599705
    OTAS - Boron - Duke's - Split - Terran - Teladi - TerraCorp - Argon, 32.05635023840483, 0.21836547042756324
    OTAS - Pirates - Boron - Duke's - Teladi - TerraCorp - Argon, 71.23394835726808, 0.1123060027485301
    Yaki - OTAS - Pirates - Boron - Teladi - TerraCorp - Argon - NMMC, 78.70165606213853, 0.0889434905216376
    Yaki - OTAS - Terran - Teladi - TerraCorp - Argon, 41.629331932769105, 0.21619371683732272
    Paranid - OTAS - Pirates - Boron - Split - Teladi - TerraCorp - Argon, 24.66309806173054, 0.28382484562480104
    Paranid - Yaki - OTAS - Boron - Teladi - TerraCorp - Argon, 86.10184685122935, 0.09291322187110296
    Paranid - OTAS - Boron - Terran - Teladi - TerraCorp - Argon, 44.05353649242922, 0.1815972254889192
    OTAS - Pirates - Boron - Terran - Teladi - TerraCorp - Argon, 57.600379630324106, 0.13888797350544452
    Paranid - Pirates - Boron - Duke's - Split - Teladi - TerraCorp - Argon, 76.31237091375255, 0.09172824689081313
    Paranid - Yaki - Pirates - Duke's - Teladi - TerraCorp - Argon, 142.17088246672324, 0.05627031260689047
    Paranid - Boron - Duke's - Split - Terran - Teladi - TerraCorp - Argon - NMMC, 108.80172413793102, 0.05514618492987878
    Pirates - Boron - Duke's - Terran - Teladi - TerraCorp - Argon, 54.31619113136939, 0.14728573254798302
    Paranid - Pirates - Boron - Terran - Teladi - TerraCorp - Argon, 47.40530004732637, 0.1687575016298456
    Paranid - OTAS - Boron - Arteus - Teladi - TerraCorp - Argon, 39.689171626532456, 0.20156631323219532
    Yaki - OTAS - Boron - Arteus - Teladi - TerraCorp - Argon, 35.60467065360683, 0.22468962226419534
    OTAS - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 12.031727523521036, 0.5817950902158959
    OTAS - Pirates - Boron - Duke's - Arteus - Teladi - TerraCorp, 50.30208731874605, 0.15903912593739714
    Yaki - OTAS - Pirates - Boron - Arteus - Teladi - TerraCorp - Argon, 23.553711013001433, 0.29719308333774086
    Yaki - Arteus - Terran - Teladi - TerraCorp - Argon, 35.580649262738305, 0.2529464803618751
    Paranid - OTAS - Pirates - Boron - Arteus - Teladi - TerraCorp - Argon, 27.644107125592182, 0.2532185238683142
    Paranid - Yaki - OTAS - Boron - Arteus - Teladi - TerraCorp - NMMC, 78.79540161060167, 0.08883767144932189
    Paranid - Boron - Arteus - Terran - Teladi - TerraCorp - Argon, 20.443035831032063, 0.3913313103847415
    OTAS - Pirates - Boron - Arteus - Terran - Teladi - TerraCorp - Argon, 20.40499695854648, 0.3430532243754196
    Paranid - Pirates - Duke's - Arteus - Teladi - TerraCorp - Argon, 53.66903463777616, 0.14906174582780776
    Paranid - Yaki - Boron - Duke's - Arteus - Teladi - TerraCorp, 37.09437271925415, 0.21566613514527855
    Paranid - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 39.641171482081795, 0.201810383015953
    Pirates - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 23.163043204741296, 0.34537776100000805
    Yaki - Pirates - Duke's - Arteus - Teladi - TerraCorp - Argon, 38.816902202756765, 0.20609578678413557
    Yaki - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 19.15951436819854, 0.41754711764921393
    Paranid - Pirates - Boron - Arteus - Terran - Teladi - TerraCorp, 37.223059128291325, 0.2149205408515071
    Paranid - Yaki - Pirates - Boron - Arteus - Teladi - TerraCorp, 54.828200220851734, 0.14591031563639612
    Paranid - Yaki - Arteus - Terran - Teladi - TerraCorp, 26.33887288321686, 0.341700270922937
    Yaki - Pirates - Arteus - Terran - Teladi - TerraCorp, 36.77708458024094, 0.24471760344036053
    Paranid - OTAS - Pirates - Boron - Duke's - Teladi - TerraCorp - Argon, 31.171408370088542, 0.2245647651492404
    Paranid - Yaki - OTAS - Boron - Duke's - Teladi - TerraCorp - Argon, 36.810924369747895, 0.19016094053190277
    Paranid - OTAS - Boron - Duke's - Terran - Teladi - TerraCorp - Argon, 22.90732819706769, 0.3055790679637642
    OTAS - Pirates - Duke's - Terran - Teladi - TerraCorp - Argon, 31.530875899999273, 0.25371956127613265
    Yaki - OTAS - Pirates - Duke's - Teladi - TerraCorp - Argon, 71.26726449219964, 0.1122535017585194
    Yaki - OTAS - Duke's - Terran - Teladi - TerraCorp, 34.74106816752381, 0.25905939208896467
    Paranid - OTAS - Pirates - Boron - Terran - Teladi - TerraCorp, 118.23965195509528, 0.06765919780479578
    Paranid - Yaki - OTAS - Pirates - Boron - Teladi - TerraCorp - Argon, 37.62144826160536, 0.1860640757720075
    Paranid - Yaki - OTAS - Terran - Teladi - TerraCorp, 37.375512242901095, 0.24079937531048587
    Yaki - OTAS - Pirates - Terran - Teladi - TerraCorp, 45.68327761890936, 0.19700863136568583
    Paranid - Pirates - Duke's - Terran - Teladi - TerraCorp, 48.801289486781094, 0.18442135637497548
    Paranid - Yaki - Duke's - Terran - Teladi - TerraCorp, 28.51708849570552, 0.31560024093467115
    Yaki - Pirates - Duke's - Terran - Teladi - TerraCorp, 17.697031025127874, 0.5085598814411848
    Paranid - Yaki - Pirates - Terran - Teladi - TerraCorp, 25.292902205475222, 0.35583105200366233
    Paranid - OTAS - Duke's - Split - Arteus - Teladi - TerraCorp - Argon, 41.90757166730941, 0.16703425470630281
    Yaki - OTAS - Duke's - Split - Arteus - Teladi - TerraCorp - Argon, 63.07219705319561, 0.11098392520076861
    OTAS - Duke's - Split - Terran - Arteus - Teladi - TerraCorp - Argon, 31.481491471119483, 0.22235287061992173
    OTAS - Pirates - Duke's - Split - Teladi - TerraCorp - Argon - NMMC, 108.74863585071493, 0.0643686235256254
    Yaki - OTAS - Pirates - Split - Arteus - Teladi - TerraCorp - Argon - NMMC, 62.07219705319562, 0.09666163411064738
    Yaki - Split - Terran - Arteus - Teladi - TerraCorp - Argon, 30.462535282623232, 0.26261766874549825
    Paranid - OTAS - Pirates - Split - Arteus - Teladi - TerraCorp - Argon, 57.39913375684217, 0.12195305994780063
    Paranid - Yaki - OTAS - Split - Arteus - Teladi - TerraCorp - Argon, 43.26724000529217, 0.16178522131626155
    Paranid - OTAS - Split - Terran - Teladi - TerraCorp - Argon, 47.9458132412131, 0.16685502777379915
    OTAS - Pirates - Split - Terran - Teladi - TerraCorp - Argon, 76.91148676395538, 0.10401567225650363
    Paranid - Pirates - Duke's - Split - Arteus - Teladi - TerraCorp, 35.563680727705076, 0.22494859464216768
    Paranid - Yaki - Duke's - Split - Arteus - Teladi - TerraCorp - Argon, 52.60066621664771, 0.1330781623785699
    Paranid - Duke's - Split - Terran - Arteus - Teladi - TerraCorp - Argon, 25.494082729331442, 0.27457351865993446
    Pirates - Duke's - Split - Terran - Teladi - TerraCorp - Argon - NMMC, 70.6975699596816, 0.09901330419124812
    Yaki - Pirates - Duke's - Split - Arteus - Teladi - TerraCorp, 61.16096402785867, 0.1308023855928108
    Yaki - Duke's - Split - Terran - Teladi - TerraCorp - Argon, 71.6975699596816, 0.11157979279491227
    Paranid - Pirates - Split - Terran - Teladi - TerraCorp, 63.81288531448262, 0.1410373462294677
    Paranid - Yaki - Pirates - Split - Teladi - TerraCorp - Argon - NMMC, 126.15438793491946, 0.0554875665808086
    Paranid - Yaki - Split - Terran - Teladi - TerraCorp, 27.5013029408491, 0.3272572219344501
    Yaki - Pirates - Split - Terran - Teladi - TerraCorp, 32.83280715911498, 0.2741160680042991
    Paranid - OTAS - Pirates - Duke's - Split - Teladi - TerraCorp, 47.75165016462443, 0.16753347732318982
    Paranid - Yaki - OTAS - Duke's - Split - Teladi - TerraCorp - Argon, 62.74918432639613, 0.11155523494279707
    Paranid - OTAS - Duke's - Split - Terran - Teladi - TerraCorp, 54.07232801854139, 0.14794998279446747
    OTAS - Pirates - Duke's - Split - Terran - Teladi - TerraCorp, 26.809011089428616, 0.2984071278613696
    Yaki - OTAS - Pirates - Duke's - Split - Teladi - TerraCorp, 61.16096402785867, 0.1308023855928108
    Yaki - OTAS - Split - Terran - Teladi - TerraCorp, 65.53999131734568, 0.13732073836296158
    Paranid - OTAS - Pirates - Split - Terran - Teladi - TerraCorp, 36.84934229459172, 0.217100211342826
    Paranid - Yaki - OTAS - Pirates - Split - Teladi - TerraCorp - Argon, 37.05046324579907, 0.1889315108845147
    Paranid - Yaki - OTAS - Split - Terran - Teladi - TerraCorp, 18.44619965216068, 0.43369366866106357
    Yaki - OTAS - Pirates - Split - Terran - Teladi - TerraCorp, 23.760673761820307, 0.3366907891667092
    Paranid - Pirates - Duke's - Split - Terran - Teladi - TerraCorp, 22.795609284120555, 0.3509447762632433
    Paranid - Yaki - Pirates - Duke's - Split - Teladi - TerraCorp, 53.892200282079855, 0.14844448655142675
    Paranid - Yaki - Duke's - Split - Terran - Teladi - TerraCorp, 22.79560928412055, 0.35094477626324333
    Yaki - Pirates - Duke's - Split - Terran - Teladi - TerraCorp, 15.829745789875973, 0.5053776672216971
    Paranid - Yaki - Pirates - Split - Terran - Teladi - TerraCorp, 14.739066319315956, 0.5427752224383289
    Paranid - OTAS - Pirates - Duke's - Arteus - Teladi - TerraCorp - Argon, 30.564421563694808, 0.2290244552939545
    Paranid - Yaki - OTAS - Duke's - Arteus - Teladi - TerraCorp - Argon, 36.12659335115363, 0.19376308006568432
    Paranid - OTAS - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 22.428846391372247, 0.31209808466532213
    OTAS - Pirates - Duke's - Arteus - Terran - Teladi - TerraCorp, 26.581350967109795, 0.30096288220635325
    Yaki - OTAS - Pirates - Duke's - Arteus - Teladi - TerraCorp, 45.771034458291396, 0.17478302805871596
    Yaki - OTAS - Arteus - Terran - Teladi - TerraCorp - Argon, 25.724948753839254, 0.310982154971487
    Paranid - OTAS - Pirates - Arteus - Terran - Teladi - TerraCorp - Argon, 73.32727383753974, 0.09546243346655506
    Paranid - Yaki - OTAS - Arteus - Terran - Teladi - TerraCorp, 25.611270204237726, 0.31236248480468937
    Yaki - OTAS - Pirates - Arteus - Terran - Teladi - TerraCorp, 35.3363318316504, 0.22639588166971197
    Paranid - Pirates - Duke's - Arteus - Terran - Teladi - TerraCorp, 17.848188731157745, 0.44822475381125526
    Paranid - Yaki - Pirates - Duke's - Arteus - Teladi - TerraCorp, 27.9878123003684, 0.28583870415247487
    Paranid - Yaki - Duke's - Arteus - Terran - Teladi - TerraCorp, 13.67399839499781, 0.585051992029379
    Yaki - Pirates - Duke's - Arteus - Terran - Teladi - TerraCorp, 11.01435555476985, 0.7263248367296024
    Paranid - Yaki - Pirates - Arteus - Terran - Teladi - TerraCorp, 19.689345694665754, 0.4063111148567707
    Paranid - OTAS - Pirates - Duke's - Terran - Teladi - TerraCorp, 30.132592654168047, 0.2654932515039794
    Paranid - Yaki - OTAS - Pirates - Duke's - Teladi - TerraCorp, 71.11437254815469, 0.11249484054131034
    Paranid - Yaki - OTAS - Duke's - Terran - Teladi - TerraCorp, 18.81810711681665, 0.42512246052903296
    Yaki - OTAS - Pirates - Duke's - Terran - Teladi - TerraCorp, 13.026769427229876, 0.6141200275854724
    Paranid - Yaki - OTAS - Pirates - Terran - Teladi - TerraCorp, 24.433113536291156, 0.32742450069318374
    Paranid - Yaki - Pirates - Duke's - Terran - Teladi - TerraCorp, 12.514324257658943, 0.639267437481004
    Paranid - OTAS - Boron - Duke's - Split - Arteus - Teladi - TerraCorp, 29.47838816200954, 0.23746210143949778
    Yaki - OTAS - Boron - Duke's - Split - Arteus - Teladi - TerraCorp, 87.09974927995695, 0.08036762514092348
    OTAS - Boron - Duke's - Split - Arteus - Terran - Teladi - TerraCorp, 45.39360497027876, 0.15420674353982716
    OTAS - Pirates - Boron - Duke's - Split - Arteus - Teladi - TerraCorp, 27.319708054763815, 0.2562252856424427
    Yaki - OTAS - Pirates - Boron - Split - Arteus - Teladi - TerraCorp - NMMC, 86.09974927995695, 0.06968661407469083
    Yaki - Boron - Split - Terran - Teladi - TerraCorp - NMMC, 143.4552309790335, 0.055766526918556415
    Paranid - Pirates - Boron - Split - Arteus - Teladi - TerraCorp, 74.1575144984709, 0.10787848074607405
    Paranid - Yaki - Boron - Split - Arteus - Teladi - TerraCorp, 61.2570487938146, 0.1305972154637622
    Paranid - Boron - Split - Arteus - Terran - Teladi - TerraCorp, 33.50855909664987, 0.2387449719018156
    OTAS - Pirates - Boron - Split - Arteus - Terran - Teladi - TerraCorp, 68.16505367854036, 0.10269191649156922
    Paranid - Pirates - Boron - Duke's - Arteus - Teladi - TerraCorp, 25.83283934964679, 0.3096833411039419
    Paranid - Yaki - Boron - Duke's - Split - Arteus - Teladi - TerraCorp, 29.493153186653778, 0.23734322185556053
    Paranid - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp, 24.191416375171798, 0.3306958086261779
    Pirates - Boron - Duke's - Split - Terran - Teladi - TerraCorp - NMMC, 82.4817350536814, 0.08486727389335597
    Yaki - Pirates - Boron - Duke's - Arteus - Teladi - TerraCorp, 29.7924613116201, 0.2685243060760381
    Yaki - Boron - Duke's - Split - Terran - Teladi - TerraCorp, 83.48173505368142, 0.09582934512388543
    Paranid - Pirates - Boron - Split - Terran - Teladi - TerraCorp, 32.98358690853304, 0.24254487609806788
    Paranid - Yaki - Pirates - Boron - Split - Teladi - TerraCorp, 83.34955816410086, 0.09598131263334815
    Paranid - Yaki - Boron - Terran - Teladi - TerraCorp, 25.676166413528357, 0.3505196163262926
    Yaki - Pirates - Boron - Terran - Teladi - TerraCorp, 30.25148301390696, 0.2975060758463509
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Teladi - TerraCorp, 23.54506968692453, 0.297302156803017
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Teladi - TerraCorp, 52.6767222550556, 0.1328860206241891
    Paranid - OTAS - Boron - Split - Terran - Teladi - TerraCorp, 46.897842478445114, 0.17058354024872058
    OTAS - Pirates - Boron - Duke's - Terran - Teladi - TerraCorp, 31.764528275640284, 0.2518532600446352
    Yaki - OTAS - Pirates - Boron - Duke's - Teladi - TerraCorp, 61.382754824655834, 0.13032976481509448
    Yaki - OTAS - Boron - Terran - Teladi - TerraCorp, 45.728317689053675, 0.19681458787088502
    Paranid - OTAS - Pirates - Boron - Split - Terran - Teladi - TerraCorp, 19.785247688857766, 0.3537989571867787
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Teladi - TerraCorp, 31.484110752418797, 0.222334372250365
    Paranid - Yaki - OTAS - Boron - Terran - Teladi - TerraCorp, 19.49647591719987, 0.410330566096941
    Yaki - OTAS - Pirates - Boron - Terran - Teladi - TerraCorp, 23.948325883105156, 0.33405257799852167
    Paranid - Pirates - Boron - Duke's - Terran - Teladi - TerraCorp, 28.71426699495808, 0.278607146802832
    Paranid - Yaki - Pirates - Boron - Duke's - Teladi - TerraCorp, 63.60249259482626, 0.12578123393627438
    Paranid - Yaki - Boron - Duke's - Terran - Teladi - TerraCorp, 20.638558840463062, 0.3876239645335869
    Yaki - Pirates - Boron - Duke's - Terran - Teladi - TerraCorp, 15.024248111291437, 0.5324725697246453
    Paranid - Yaki - Pirates - Boron - Terran - Teladi - TerraCorp, 16.426658694834288, 0.48701322335964586
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - Teladi - TerraCorp, 18.34717388784865, 0.38153014969984594
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - Teladi - TerraCorp, 21.242762232433094, 0.3295240008529831
    Paranid - OTAS - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp, 16.156372840871814, 0.4332655645511999
    Pirates - Boron - Duke's - Terran - Arteus - Teladi - TerraCorp, 20.653464811796333, 0.38734420945345494
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - Teladi - TerraCorp, 17.774169255161784, 0.3938299393636715
    Yaki - OTAS - Boron - Arteus - Terran - Teladi - TerraCorp, 25.240648419566075, 0.3169490683051768
    Paranid - OTAS - Pirates - Boron - Arteus - Terran - Teladi - TerraCorp, 34.99545790807747, 0.20002595817968413
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - Teladi - TerraCorp, 48.52401223061789, 0.1442584748913881
    Paranid - Yaki - Boron - Arteus - Terran - Teladi - TerraCorp, 13.586825490521658, 0.5888056783816721
    Yaki - Pirates - Boron - Arteus - Terran - Teladi - TerraCorp, 19.18827078616409, 0.41692136249028167
    Paranid - Pirates - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp, 10.608337959388553, 0.6598583139788533
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Teladi - TerraCorp, 13.722366469373174, 0.510116095181049
    Yaki - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp, 18.408113974949643, 0.4345909641197713
    Yaki - Pirates - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp, 8.425978656846597, 0.83076403170237
    Paranid - Yaki - Pirates - Boron - Arteus - Terran - Teladi - TerraCorp, 11.224131171747445, 0.6236562895504896
    Paranid - OTAS - Pirates - Boron - Duke's - Terran - Teladi - TerraCorp, 17.660340337362918, 0.39636835226728456
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Teladi - TerraCorp, 27.02131290201701, 0.2590547700395966
    Yaki - OTAS - Boron - Duke's - Terran - Teladi - TerraCorp, 21.786910010576037, 0.3671929610998785
    Yaki - OTAS - Pirates - Boron - Duke's - Terran - Teladi - TerraCorp, 10.261632833083398, 0.6821526470360616
    Paranid - Yaki - OTAS - Pirates - Boron - Terran - Teladi - TerraCorp, 14.875264237751802, 0.47057987596850626
    Paranid - Yaki - Pirates - Boron - Duke's - Terran - Teladi - TerraCorp, 10.392867540942765, 0.673538845022652
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - Teladi - TerraCorp, 20.170797126956742, 0.3470363593437282
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - Teladi - TerraCorp, 39.49822958166616, 0.17722313314136948
    Paranid - OTAS - Duke's - Split - Arteus - Terran - Teladi - TerraCorp, 21.55633608343428, 0.3247305095312275
    OTAS - Pirates - Duke's - Split - Arteus - Terran - Teladi - TerraCorp, 16.59707836141662, 0.42176097790036127
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - Teladi - TerraCorp, 25.761662713204558, 0.2717215918059527
    Yaki - OTAS - Split - Terran - Arteus - Teladi - TerraCorp, 42.471597789619146, 0.18836117349828901
    Paranid - Pirates - Split - Arteus - Terran - Teladi - TerraCorp, 33.581256250674315, 0.23822813358387565
    Paranid - Yaki - Pirates - Split - Arteus - Teladi - TerraCorp - NMMC, 56.74612430950827, 0.12335644213902894
    Paranid - Yaki - Split - Terran - Arteus - Teladi - TerraCorp, 17.10735473419233, 0.4676351267803236
    Yaki - Pirates - Split - Arteus - Terran - Teladi - TerraCorp, 24.62003336631456, 0.32493863354977015
    Paranid - Pirates - Duke's - Split - Arteus - Terran - Teladi - TerraCorp, 11.822079962133458, 0.5921123882109789
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Teladi - TerraCorp, 17.679736684420185, 0.39593349861192056
    Paranid - Yaki - Duke's - Split - Arteus - Terran - Teladi - TerraCorp, 11.822079962133456, 0.5921123882109789
    Yaki - Pirates - Duke's - Split - Arteus - Terran - Teladi - TerraCorp, 10.161331258595006, 0.6888861136260094
    Paranid - Yaki - Pirates - Split - Arteus - Terran - Teladi - TerraCorp, 11.862080563448048, 0.5901157020944438
    Paranid - OTAS - Pirates - Duke's - Split - Terran - Teladi - TerraCorp, 13.024174651015851, 0.537462080136803
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Teladi - TerraCorp, 21.082053724911578, 0.33203596249868483
    Yaki - OTAS - Duke's - Split - Terran - Teladi - TerraCorp, 26.809011089428616, 0.2984071278613696
    Yaki - OTAS - Pirates - Duke's - Split - Terran - Teladi - TerraCorp, 10.161331258595006, 0.6888861136260094
    Paranid - Yaki - OTAS - Pirates - Split - Terran - Teladi - TerraCorp, 12.487275032785401, 0.5605706594610487
    Paranid - Yaki - Pirates - Duke's - Split - Terran - Teladi - TerraCorp, 9.961707209310557, 0.7026907991691984
    Paranid - OTAS - Pirates - Duke's - Arteus - Terran - Teladi - TerraCorp, 15.671495214738133, 0.44667084436314064
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - Teladi - TerraCorp, 23.064469208479835, 0.3034971209060556
    Yaki - OTAS - Duke's - Arteus - Terran - Teladi - TerraCorp, 19.02396199704861, 0.4205222866425577
    Yaki - OTAS - Pirates - Duke's - Arteus - Terran - Teladi - TerraCorp, 9.461620695950952, 0.7398309681760559
    Paranid - Yaki - OTAS - Pirates - Arteus - Terran - Teladi - TerraCorp, 19.65711315701371, 0.3561051892048747
    Paranid - Yaki - Pirates - Duke's - Arteus - Terran - Teladi - TerraCorp, 8.164326124937544, 0.8573885820923829
    Paranid - Yaki - OTAS - Pirates - Duke's - Terran - Teladi - TerraCorp, 10.467330243012563, 0.6687474109907663
    Paranid - OTAS - Boron - Duke's - Split - Arteus - Teladi - Argon, 17.811255651622112, 0.3930099110874586
    Yaki - OTAS - Boron - Duke's - Split - Arteus - Teladi - Argon, 26.634215710757786, 0.26281982829975503
    OTAS - Boron - Duke's - Split - Arteus - Terran - Teladi - Argon, 46.17670682730923, 0.1515915811445469
    OTAS - Pirates - Boron - Duke's - Split - Arteus - Teladi - Argon, 16.962697051613713, 0.4126702244755393
    Yaki - OTAS - Pirates - Boron - Split - Arteus - Teladi - Argon, 21.08950150908298, 0.331918703577948
    Yaki - Boron - Split - Arteus - Terran - Teladi - Argon, 69.68665955881744, 0.11479959077745407
    Paranid - Pirates - Boron - Split - Arteus - Teladi - Argon, 41.69832369031234, 0.19185423518256725
    Paranid - Yaki - Boron - Split - Arteus - Teladi - Argon, 45.25922058360872, 0.1767595618493111
    Paranid - Boron - Split - Arteus - Terran - Teladi - Argon - NMMC, 73.08288209405744, 0.09578166322164228
    OTAS - Pirates - Boron - Split - Arteus - Terran - Teladi - Argon, 25.316227230244216, 0.27650249527059856
    Paranid - Pirates - Boron - Duke's - Arteus - Teladi - Argon, 30.272079823071927, 0.26426991626464935
    Paranid - Yaki - Boron - Duke's - Arteus - Teladi - Argon, 43.50807706127392, 0.18387390434960674
    Paranid - Boron - Duke's - Split - Arteus - Terran - Teladi - Argon - NMMC, 62.11675126903552, 0.09659230203481248
    Pirates - Boron - Duke's - Terran - Arteus - Teladi - Argon - NMMC, 62.12464340574939, 0.1126767030964105
    Yaki - Pirates - Boron - Duke's - Arteus - Teladi - Argon, 35.49709518017914, 0.22537055382681112
    Yaki - Duke's - Split - Terran - Arteus - Teladi - Argon, 182.83317695427024, 0.04375573478111655
    Paranid - Pirates - Boron - Split - Terran - Teladi - Argon, 49.68270386532091, 0.16102183209847584
    Paranid - Yaki - Pirates - Boron - Split - Teladi - Argon, 60.23906847569194, 0.13280417845817474
    Paranid - Yaki - Boron - Terran - Teladi - Argon, 39.01620005821439, 0.2306734122382879
    Yaki - Pirates - Boron - Terran - Teladi - Argon, 35.66915868426556, 0.2523188191699653
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Teladi - Argon, 16.962697051613713, 0.4126702244755393
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Teladi - Argon, 26.634215710757786, 0.26281982829975503
    Paranid - OTAS - Boron - Duke's - Split - Terran - Teladi - Argon, 25.93396557780119, 0.26991629872416506
    OTAS - Pirates - Boron - Duke's - Terran - Teladi - Argon, 32.22722545105498, 0.2482373176105396
    Yaki - OTAS - Pirates - Boron - Duke's - Teladi - Argon, 29.552730620545706, 0.2707025656180219
    Yaki - OTAS - Boron - Split - Terran - Teladi - Argon, 23.03507432462016, 0.3472964700378459
    Paranid - OTAS - Pirates - Boron - Split - Terran - Teladi - Argon, 14.893570050870988, 0.4700014822564745
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Teladi - Argon, 16.548038774277217, 0.42301085315808035
    Paranid - Yaki - OTAS - Boron - Terran - Teladi - Argon, 15.941145339306411, 0.5018459984976258
    Yaki - OTAS - Pirates - Boron - Terran - Teladi - Argon, 17.087966679787776, 0.46816570689259773
    Paranid - Pirates - Boron - Duke's - Terran - Teladi - Argon - NMMC, 62.76668147742279, 0.11152413725294531
    Paranid - Yaki - Pirates - Boron - Duke's - Teladi - Argon, 68.58582033554742, 0.11664218581714143
    Paranid - Yaki - Boron - Duke's - Terran - Teladi - Argon, 38.0597020850507, 0.2101960751590403
    Yaki - Pirates - Boron - Duke's - Terran - Teladi - Argon, 23.99530411253237, 0.3333985667563065
    Paranid - Yaki - Pirates - Boron - Terran - Teladi - Argon, 17.187170231847045, 0.4654634760745177
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - Teladi - Argon, 13.260792488756113, 0.5278719206212851
    Paranid - Yaki - OTAS - Boron - Arteus - Teladi - Argon, 22.596583281189403, 0.3540358248169149
    Paranid - OTAS - Boron - Duke's - Arteus - Terran - Teladi - Argon, 16.488375809286758, 0.4245415122123421
    OTAS - Pirates - Boron - Duke's - Arteus - Terran - Teladi - Argon, 14.216355711185278, 0.49239060573677645
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - Teladi - Argon, 12.148271795052644, 0.5762136473478255
    Yaki - OTAS - Boron - Arteus - Terran - Teladi - Argon, 16.776059802212217, 0.4768700215854655
    Paranid - OTAS - Pirates - Boron - Arteus - Terran - Teladi - Argon, 19.29926541396358, 0.3627081057155313
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - Teladi - Argon, 17.15883447484065, 0.407953116528039
    Paranid - Yaki - Boron - Arteus - Terran - Teladi - Argon, 14.95885047583956, 0.5348004522754616
    Yaki - Pirates - Boron - Arteus - Terran - Teladi - Argon, 19.075722004912105, 0.41938124270944793
    Paranid - Pirates - Boron - Duke's - Arteus - Terran - Teladi - Argon, 15.779549736796099, 0.44361215096504325
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Teladi - Argon, 14.171581886587983, 0.49394626909116024
    Paranid - Yaki - Boron - Duke's - Arteus - Terran - Teladi - Argon, 13.392458449170705, 0.5226822264610765
    Yaki - Pirates - Boron - Duke's - Arteus - Terran - Teladi - Argon, 12.470811036973421, 0.5613107262427778
    Paranid - Yaki - Pirates - Boron - Arteus - Terran - Teladi - Argon, 10.603393509713523, 0.6601660113422615
    Paranid - OTAS - Pirates - Boron - Duke's - Terran - Teladi - Argon, 17.92051618989858, 0.39061374827728196
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Teladi - Argon, 18.692954784437436, 0.37447263317770146
    Yaki - OTAS - Boron - Duke's - Terran - Teladi - Argon, 22.134214972623443, 0.3614313861998154
    Yaki - OTAS - Pirates - Boron - Duke's - Terran - Teladi - Argon, 10.432741965695325, 0.6709645482479315
    Paranid - Yaki - OTAS - Pirates - Boron - Terran - Teladi - Argon, 12.103162703902077, 0.5783612243552828
    Paranid - Yaki - Pirates - Boron - Duke's - Terran - Teladi - Argon, 13.49352485136336, 0.5187673404175585
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - Teladi - Argon, 16.633950092504147, 0.4208260792578938
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - Teladi - Argon, 26.152765169029067, 0.26765812160809754
    Paranid - OTAS - Duke's - Split - Arteus - Terran - Teladi - Argon, 25.494082729331446, 0.27457351865993446
    OTAS - Pirates - Duke's - Split - Arteus - Terran - Teladi - Argon, 18.798921508428485, 0.3723617866515137
    Yaki - Pirates - Duke's - Split - Arteus - Teladi - Argon, 88.37647630104364, 0.09052182588440141
    Yaki - OTAS - Split - Terran - Arteus - Teladi - Argon, 30.46253528262324, 0.26261766874549813
    Paranid - Pirates - Split - Arteus - Terran - Teladi - Argon, 37.28103479808599, 0.21458631830709593
    Paranid - Yaki - Pirates - Split - Arteus - Teladi - Argon, 43.9062343194224, 0.18220647076675198
    Paranid - Yaki - Split - Terran - Arteus - Teladi - Argon, 21.093140130065507, 0.37927022485367407
    Yaki - Pirates - Split - Arteus - Terran - Teladi - Argon, 26.772008164772895, 0.29881957120148156
    Paranid - Pirates - Duke's - Split - Arteus - Terran - Teladi - Argon, 18.291149821124076, 0.38269874056336484
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Teladi - Argon, 19.317731997524113, 0.3623613787010383
    Paranid - Yaki - Duke's - Split - Arteus - Terran - Teladi - Argon, 18.291149821124073, 0.3826987405633649
    Yaki - Pirates - Duke's - Split - Arteus - Terran - Teladi - Argon, 15.181040610513389, 0.4611014606701112
    Paranid - Yaki - Pirates - Split - Arteus - Terran - Teladi - Argon, 12.30766836499532, 0.5687511064166264
    Paranid - OTAS - Pirates - Duke's - Split - Terran - Teladi - Argon, 13.975309558291286, 0.5008833593848397
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Teladi - Argon, 17.165017111474263, 0.40780617662890206
    Paranid - Yaki - OTAS - Duke's - Split - Terran - Teladi - Argon, 13.975309558291288, 0.5008833593848396
    Yaki - OTAS - Pirates - Duke's - Split - Terran - Teladi - Argon, 10.774635067375602, 0.6496739756128931
    Paranid - Yaki - OTAS - Pirates - Split - Terran - Teladi - Argon, 11.182207243456824, 0.6259944792291335
    Paranid - Yaki - Pirates - Duke's - Split - Terran - Teladi - Argon, 12.974017503341738, 0.5395398918027511
    Paranid - OTAS - Pirates - Duke's - Arteus - Terran - Teladi - Argon, 17.58871309545584, 0.3979824994591842
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - Teladi - Argon, 18.324234980831477, 0.3820077622516042
    Yaki - OTAS - Duke's - Arteus - Terran - Teladi - Argon, 21.780935218695394, 0.3672936868722377
    Yaki - OTAS - Pirates - Duke's - Arteus - Terran - Teladi - Argon, 10.241043957980729, 0.6835240653903237
    Paranid - Yaki - OTAS - Pirates - Arteus - Terran - Teladi - Argon, 16.25947147276464, 0.4305182989327372
    Paranid - Yaki - Pirates - Duke's - Arteus - Terran - Teladi - Argon, 10.149057821586982, 0.6897191959150182
    Paranid - Yaki - OTAS - Pirates - Duke's - Terran - Teladi - Argon, 11.036342775050727, 0.6342680852414739
    Paranid - OTAS - Pirates - Boron - Split - Arteus - Teladi, 44.62802391212937, 0.1792595615649855
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Arteus - Teladi, 18.732764572210172, 0.37367682559702986
    Paranid - OTAS - Boron - Duke's - Split - Arteus - Terran - Teladi, 19.188538091847313, 0.3648011102510258
    OTAS - Pirates - Boron - Duke's - Split - Arteus - Terran - Teladi, 18.3942737127108, 0.3805532150564262
    Yaki - Pirates - Boron - Duke's - Split - Arteus - Teladi, 58.277815734437205, 0.13727350449191053
    Yaki - OTAS - Boron - Split - Arteus - Terran - Teladi, 31.875838811078825, 0.25097378762059447
    Paranid - OTAS - Pirates - Boron - Split - Arteus - Terran - Teladi, 16.870026101011483, 0.41493711735160255
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Arteus - Teladi, 18.955546530792816, 0.36928505272209766
    Paranid - Yaki - Boron - Split - Arteus - Terran - Teladi, 16.284717641100947, 0.4912581339334264
    Yaki - Pirates - Boron - Split - Arteus - Terran - Teladi, 24.395226377205784, 0.3279330093642818
    Paranid - Pirates - Boron - Duke's - Split - Arteus - Terran - Teladi, 14.412632839395298, 0.48568502909935324
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Arteus - Teladi, 14.440469963459684, 0.4847487663291342
    Paranid - Yaki - Boron - Duke's - Split - Arteus - Terran - Teladi, 14.412632839395298, 0.48568502909935324
    Yaki - Pirates - Boron - Duke's - Split - Arteus - Terran - Teladi, 13.800045843857582, 0.5072446917352603
    Paranid - Yaki - Pirates - Boron - Split - Arteus - Terran - Teladi, 10.308881298404248, 0.6790261520504225
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Terran - Teladi, 12.709176147014658, 0.5507831443224017
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Split - Teladi, 15.181782664245532, 0.4610789229966802
    Yaki - OTAS - Boron - Duke's - Split - Terran - Teladi, 32.816470166877465, 0.243780027508096
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Terran - Teladi, 10.774635067375602, 0.6496739756128931
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Terran - Teladi, 10.24197465877192, 0.6834619527206823
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Terran - Teladi, 11.932074293445865, 0.586654074375401
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - Terran - Teladi, 12.621694922000575, 0.5546006335328599
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Arteus - Teladi, 12.602510315774934, 0.5554448934858552
    Yaki - OTAS - Boron - Duke's - Arteus - Terran - Teladi, 19.661740691950044, 0.4068815739837002
    Yaki - OTAS - Pirates - Boron - Duke's - Arteus - Terran - Teladi, 9.136989917466162, 0.7661166383273427
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - Terran - Teladi, 12.263765365357926, 0.5707871759984297
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Terran - Teladi, 8.313970525814062, 0.8419563165716895
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Terran - Teladi, 9.585227997276245, 0.7302904012287587
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - Terran - Teladi, 11.822079962133456, 0.5921123882109789
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Arteus - Teladi, 13.815843234388954, 0.5066646951071601
    Yaki - OTAS - Duke's - Split - Arteus - Terran - Teladi, 28.926177754340607, 0.2765660941428577
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - Terran - Teladi, 10.161331258595006, 0.6888861136260094
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - Terran - Teladi, 11.862080563448048, 0.5901157020944438
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Terran - Teladi, 9.002967546770494, 0.7775214076508595
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Terran - Teladi, 8.37860433862869, 0.8354613390355745
    Paranid - Yaki - OTAS - Pirates - Duke's - Arteus - Terran - Teladi, 9.034428288017613, 0.7748138318042901
    OTAS - Boron - Strong Arms - Split - Arteus - Teladi - TerraCorp - Argon, 87.63799613996812, 0.07987403076652029
    Yaki - OTAS - Boron - Strong Arms - Split - Teladi - TerraCorp - Argon, 55.391010054172625, 0.12637429779947995
    Boron - Strong Arms - Split - Arteus - Terran - Teladi - TerraCorp - Argon, 159.2439678284182, 0.043957709013771516
    OTAS - Pirates - Boron - Split - Strong Arms - Teladi - TerraCorp - Argon, 81.19087405913487, 0.08621658629886893
    Yaki - Pirates - Boron - Strong Arms - Arteus - Teladi - Argon, 87.16055132988751, 0.09178464199614104
    Yaki - Strong Arms - Terran - Teladi - TerraCorp - Argon, 66.6220339904801, 0.13509044171911724
    Paranid - Boron - Strong Arms - Arteus - Teladi - TerraCorp - Argon, 111.08981551031344, 0.07201380219465113
    Paranid - Yaki - Boron - Strong Arms - Split - Teladi - TerraCorp - Argon, 52.161515453639076, 0.1341985549906342
    Paranid - Boron - Strong Arms - Split - Terran - Teladi - TerraCorp - Argon, 52.161515453639076, 0.1341985549906342
    Pirates - Boron - Split - Terran - Strong Arms - Teladi - TerraCorp - Argon, 100.13898929826281, 0.0699028425297022
    Paranid - Boron - Duke's - Strong Arms - Arteus - Teladi - TerraCorp - Argon, 28.032732232156377, 0.24970808917335188
    Yaki - Boron - Duke's - Strong Arms - Arteus - Teladi - TerraCorp - Argon, 43.11587982832618, 0.16235317539319133
    Boron - Duke's - Strong Arms - Terran - Arteus - Teladi - TerraCorp - Argon, 43.11587982832618, 0.16235317539319133
    Pirates - Boron - Duke's - Strong Arms - Arteus - Teladi - TerraCorp - Argon, 23.407942238267143, 0.29904380012338067
    Yaki - Pirates - Boron - Duke's - Strong Arms - Teladi - TerraCorp - Argon, 36.21224983917779, 0.1933047527035105
    Yaki - Duke's - Strong Arms - Terran - Teladi - TerraCorp - Argon, 36.569104109559696, 0.2187639045253144
    Paranid - Pirates - Boron - Split - Strong Arms - Teladi - TerraCorp - Argon, 43.00654307524535, 0.16276593047138482
    Paranid - Yaki - Pirates - Boron - Strong Arms - Teladi - Argon, 49.29289869617381, 0.16229518270592133
    Paranid - Yaki - Strong Arms - Terran - Teladi, 40.104089587424006, 0.24935112859751435
    Yaki - Pirates - Strong Arms - Terran - Teladi, 51.97218591121031, 0.19241061011141763
    Paranid - OTAS - Boron - Strong Arms - Split - Teladi - TerraCorp - Argon, 31.765585691146565, 0.2203642667904902
    Yaki - OTAS - Boron - Duke's - Strong Arms - Teladi - TerraCorp - Argon, 49.33459856216374, 0.14188825295050683
    OTAS - Boron - Strong Arms - Split - Terran - Teladi - TerraCorp - Argon, 55.39101005417262, 0.12637429779947998
    OTAS - Pirates - Boron - Duke's - Strong Arms - Teladi - TerraCorp - Argon, 37.30239634842144, 0.1876555043439247
    Yaki - OTAS - Pirates - Boron - Strong Arms - Teladi - Argon, 79.64681040718095, 0.10044344474187156
    Yaki - OTAS - Strong Arms - Terran - Teladi - Argon, 58.015836899897714, 0.1551300555317141
    Paranid - OTAS - Pirates - Strong Arms - Split - Teladi - TerraCorp - Argon, 36.01957482203435, 0.19433877369695857
    Paranid - Yaki - OTAS - Boron - Strong Arms - Teladi - Argon, 52.89147225140204, 0.15125311622967608
    Paranid - OTAS - Boron - Strong Arms - Terran - Teladi - TerraCorp - Argon, 39.07550455251123, 0.17914036121000357
    OTAS - Pirates - Boron - Terran - Strong Arms - Teladi - TerraCorp - Argon, 54.05217722218454, 0.12950449657607876
    Paranid - Pirates - Duke's - Strong Arms - Split - Teladi - TerraCorp, 34.00455864069623, 0.23526257418985289
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Teladi - TerraCorp - Argon, 41.99999999999999, 0.14285714285714288
    Paranid - Boron - Duke's - Strong Arms - Split - Terran - Teladi - TerraCorp - Argon, 41.99999999999999, 0.14285714285714288
    Pirates - Boron - Duke's - Terran - Strong Arms - Teladi - TerraCorp - Argon, 36.21224983917777, 0.19330475270351058
    Paranid - Pirates - Boron - Terran - Strong Arms - Teladi - Argon, 144.40198741441492, 0.05540089955300297
    OTAS - Boron - Duke's - Strong Arms - Arteus - Teladi - TerraCorp - Argon, 28.032732232156384, 0.24970808917335183
    Yaki - OTAS - Boron - Strong Arms - Arteus - Teladi - Argon, 69.71982203843058, 0.11474498594661191
    OTAS - Boron - Strong Arms - Arteus - Terran - Teladi - TerraCorp - Argon, 30.19782681980856, 0.23180476005009346
    OTAS - Pirates - Boron - Arteus - Strong Arms - Teladi - TerraCorp - Argon, 111.2157031924072, 0.06294075206169174
    Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - Teladi - Argon, 28.244625614432543, 0.24783475963027507
    Yaki - Strong Arms - Terran - Arteus - Teladi - TerraCorp - Argon, 28.91365181970761, 0.27668590774642937
    Paranid - OTAS - Boron - Strong Arms - Arteus - Teladi - Argon, 108.486621755538, 0.07374181139151952
    Paranid - Yaki - Boron - Strong Arms - Arteus - Teladi - TerraCorp, 85.06443983435936, 0.09404634904524026
    Paranid - Boron - Strong Arms - Arteus - Terran - Teladi - TerraCorp, 85.06443983435949, 0.09404634904524012
    Pirates - Boron - Arteus - Terran - Strong Arms - Teladi - TerraCorp - Argon, 33.5603261523649, 0.20857961773731837
    Paranid - Pirates - Boron - Arteus - Strong Arms - Teladi - Argon, 108.0952558732293, 0.07400879840075633
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Teladi - TerraCorp - Argon, 29.817890642242897, 0.2347583899876246
    Paranid - Duke's - Strong Arms - Terran - Arteus - Teladi - TerraCorp - Argon, 29.81789064224291, 0.2347583899876245
    Pirates - Duke's - Strong Arms - Terran - Arteus - Teladi - TerraCorp, 31.008118119528596, 0.2579969532224428
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Teladi - TerraCorp, 31.008118119528596, 0.2579969532224428
    Yaki - Duke's - Strong Arms - Terran - Arteus - Teladi - TerraCorp, 22.25849250064308, 0.3594133789504778
    Paranid - Pirates - Strong Arms - Arteus - Terran - Teladi - TerraCorp - Argon, 68.64274816092343, 0.10197726908586859
    Paranid - Yaki - Pirates - Strong Arms - Arteus - Teladi - TerraCorp - Argon, 68.64274816092333, 0.10197726908586874
    Paranid - Yaki - Strong Arms - Terran - Arteus - Teladi, 25.96061676240937, 0.3466789746317538
    Yaki - Pirates - Strong Arms - Arteus - Terran - Teladi, 39.41904710596573, 0.22831602133370515
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Teladi - TerraCorp - Argon, 62.74918432639613, 0.11155523494279707
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Teladi - TerraCorp - Argon, 62.749184326396126, 0.11155523494279708
    OTAS - Boron - Duke's - Strong Arms - Terran - Teladi - TerraCorp - Argon, 49.33459856216374, 0.14188825295050683
    OTAS - Pirates - Duke's - Strong Arms - Terran - Teladi - TerraCorp, 45.85796527390771, 0.17445169998747947
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Teladi - TerraCorp, 45.85796527390771, 0.17445169998747947
    Yaki - OTAS - Duke's - Strong Arms - Terran - Teladi, 42.7833307332637, 0.21036230339594786
    Paranid - OTAS - Pirates - Boron - Strong Arms - Terran - Teladi - TerraCorp, 96.44756749405083, 0.07257829494177528
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Teladi - TerraCorp, 96.44756749405079, 0.07257829494177533
    Paranid - Yaki - OTAS - Strong Arms - Terran - Teladi, 31.086706781334904, 0.2895128153427878
    Yaki - OTAS - Pirates - Strong Arms - Terran - Teladi, 41.48959998993613, 0.21692183106569052
    Paranid - Pirates - Duke's - Strong Arms - Terran - Teladi - TerraCorp, 28.526147746307924, 0.2804444564736373
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Teladi - TerraCorp, 28.52614774630792, 0.28044445647363736
    Paranid - Yaki - Duke's - Strong Arms - Terran - Teladi, 28.476896792984594, 0.31604567258245597
    Yaki - Pirates - Duke's - Strong Arms - Terran - Teladi, 18.047883506588843, 0.49867343152532645
    Paranid - Yaki - Pirates - Strong Arms - Terran - Teladi, 20.544509567582793, 0.43807324630426375
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - Teladi - TerraCorp - Argon, 18.646323445846114, 0.32177925141251557
    Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - Teladi - TerraCorp - Argon, 24.93009853132551, 0.2406729356669328
    OTAS - Duke's - Strong Arms - Terran - Arteus - Teladi - TerraCorp - Argon, 48.5503315009668, 0.14418027196911326
    OTAS - Pirates - Duke's - Strong Arms - Split - Teladi - TerraCorp - Argon, 25.94584118679039, 0.2697927559798623
    Yaki - OTAS - Pirates - Strong Arms - Split - Teladi - TerraCorp - Argon, 48.58876324840718, 0.14406623120273537
    Yaki - Strong Arms - Split - Terran - Teladi - TerraCorp - Argon, 48.09862794578277, 0.1663249107441833
    Paranid - Pirates - Strong Arms - Split - Arteus - Teladi - TerraCorp - Argon, 42.83345076827542, 0.16342367645953354
    Paranid - Yaki - Strong Arms - Split - Arteus - Teladi - TerraCorp - Argon, 32.276173230026494, 0.2168782510278482
    Paranid - Strong Arms - Split - Terran - Arteus - Teladi - TerraCorp - Argon, 32.27617323002651, 0.2168782510278481
    Pirates - Strong Arms - Split - Arteus - Terran - Teladi - TerraCorp - Argon, 96.44756749405076, 0.07257829494177534
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Teladi - TerraCorp - Argon, 25.696079755564238, 0.272415094698802
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - Teladi - TerraCorp, 26.758295995873485, 0.26160111245796447
    Paranid - Duke's - Strong Arms - Split - Arteus - Terran - Teladi - TerraCorp, 26.758295995873496, 0.26160111245796436
    Pirates - Duke's - Strong Arms - Split - Terran - Teladi - TerraCorp - Argon, 33.18757793404763, 0.21092229188616368
    Yaki - Pirates - Duke's - Strong Arms - Split - Teladi - TerraCorp, 53.89220028207984, 0.14844448655142678
    Yaki - Duke's - Strong Arms - Split - Terran - Teladi - TerraCorp - Argon, 33.18757793404763, 0.21092229188616368
    Paranid - Pirates - Strong Arms - Split - Terran - Teladi - TerraCorp, 31.430421547520396, 0.25453047099303494
    Paranid - Yaki - Pirates - Strong Arms - Split - Teladi - TerraCorp, 31.430421547520382, 0.25453047099303505
    Paranid - Yaki - Strong Arms - Split - Terran - Teladi, 22.655808195999384, 0.39724912579323657
    Yaki - Pirates - Strong Arms - Split - Terran - Teladi, 30.715475802308617, 0.29301190246655884
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Teladi, 16.704205228276894, 0.47892131895372025
    Paranid - Yaki - OTAS - Strong Arms - Split - Teladi - TerraCorp - Argon, 27.626284940917806, 0.25338187943005575
    Paranid - OTAS - Strong Arms - Split - Terran - Teladi - TerraCorp - Argon, 27.626284940917802, 0.25338187943005575
    OTAS - Pirates - Strong Arms - Split - Terran - Teladi - TerraCorp - Argon, 48.588763248407176, 0.14406623120273537
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Teladi, 20.16666401423425, 0.39669426705147437
    Yaki - OTAS - Strong Arms - Split - Terran - Teladi - TerraCorp, 40.73852422774626, 0.19637432017115994
    Paranid - OTAS - Pirates - Strong Arms - Split - Terran - Teladi, 26.57574812967581, 0.30102633276640667
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Teladi - TerraCorp, 22.97388116342583, 0.3046938368926503
    Paranid - Yaki - OTAS - Strong Arms - Split - Terran - Teladi, 13.675718812565973, 0.5849783919693623
    Yaki - OTAS - Pirates - Strong Arms - Split - Terran - Teladi, 19.909056594606064, 0.4018271765909506
    Paranid - Pirates - Duke's - Strong Arms - Split - Terran - Teladi, 20.528281038111462, 0.3897062781412493
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Teladi, 14.649507857456097, 0.5460934304307209
    Paranid - Yaki - Duke's - Strong Arms - Split - Terran - Teladi, 20.528281038111466, 0.38970627814124925
    Yaki - Pirates - Duke's - Strong Arms - Split - Terran - Teladi, 15.648916050880985, 0.5112175165352507
    Paranid - Yaki - Pirates - Strong Arms - Split - Terran - Teladi, 10.620834049967561, 0.753236512534007
    OTAS - Pirates - Duke's - Strong Arms - Arteus - Teladi - TerraCorp - Argon, 36.648181378812, 0.19100538516890833
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus - Teladi - TerraCorp, 39.49822958166616, 0.17722313314136948
    Paranid - OTAS - Duke's - Strong Arms - Arteus - Terran - Teladi - TerraCorp, 39.498229581666166, 0.17722313314136945
    OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - Teladi, 45.85796527390772, 0.17445169998747942
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Teladi, 26.63411131939479, 0.30036669532782384
    Yaki - OTAS - Strong Arms - Terran - Arteus - Teladi - TerraCorp, 62.88211754844742, 0.12722217876706227
    Paranid - OTAS - Pirates - Strong Arms - Arteus - Terran - Teladi - TerraCorp - Argon, 62.223736654069334, 0.09642622450266508
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Arteus - Teladi - TerraCorp - Argon, 62.223736654069334, 0.09642622450266508
    Paranid - Yaki - OTAS - Strong Arms - Arteus - Terran - Teladi, 24.07298960773352, 0.33232266246773007
    Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran - Teladi, 35.38546174200333, 0.22608154892334845
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Terran - Teladi, 23.310109492107514, 0.3431987311217346
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - Teladi, 16.31391172561736, 0.49037901727994426
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Terran - Teladi, 15.667747193947049, 0.5106030816664349
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran - Teladi, 12.694742361817491, 0.6301821472219818
    Paranid - Yaki - Strong Arms - Terran - Teladi - Argon, 33.5451739980532, 0.26829492673140753
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Terran - Teladi, 29.673169072169458, 0.2696038289858032
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Teladi, 22.157800645693865, 0.36104666378766775
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Terran - Teladi, 16.499455644000264, 0.4848644811448103
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran - Teladi, 11.677345596547118, 0.6850872001566456
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Terran - Teladi, 19.909056594606056, 0.40182717659095074
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Terran - Teladi, 10.312684268473225, 0.7757437144135885
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - Teladi - TerraCorp, 55.520085129023656, 0.12608049832295165
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Teladi - TerraCorp, 41.251937984496124, 0.14544771211124682
    OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Terran - Teladi - TerraCorp, 41.251937984496124, 0.14544771211124682
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Teladi - TerraCorp, 47.07090733935955, 0.14871181363752403
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Arteus - Teladi - TerraCorp, 62.223736654069334, 0.09642622450266508
    Yaki - Boron - Strong Arms - Split - Terran - Teladi - TerraCorp, 72.33207922950454, 0.11060099592349017
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus - Teladi, 50.990228503666415, 0.1568928054406496
    Paranid - Yaki - Boron - Strong Arms - Split - Arteus - Teladi, 39.57173787395803, 0.2021644848017848
    Paranid - Boron - Strong Arms - Split - Arteus - Terran - Teladi - TerraCorp, 27.626284940917806, 0.25338187943005575
    OTAS - Pirates - Boron - Split - Strong Arms - Arteus - Terran - Teladi - TerraCorp, 62.22373665406934, 0.09642622450266507
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Teladi - TerraCorp, 25.893220017784515, 0.2703410388971366
    Paranid - Yaki - Boron - Duke's - Strong Arms - Arteus - Teladi, 37.20847958649222, 0.21500475399441576
    Paranid - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi - TerraCorp, 21.321707791278435, 0.3283039083231093
    Pirates - Boron - Duke's - Split - Strong Arms - Terran - Teladi - TerraCorp, 42.0772097737087, 0.16636084088384212
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Teladi - TerraCorp, 42.07720977370871, 0.1663608408838421
    Yaki - Boron - Duke's - Strong Arms - Terran - Teladi - TerraCorp, 44.440939154343, 0.1800141975446574
    Paranid - Pirates - Boron - Split - Strong Arms - Terran - Teladi, 33.670352339569405, 0.23759775125959695
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Teladi, 23.54987189247173, 0.33970460801348934
    Paranid - Yaki - Boron - Strong Arms - Terran - Teladi, 27.811186584892685, 0.32361078778597996
    Yaki - Pirates - Boron - Strong Arms - Terran - Teladi, 35.260517872474516, 0.2552429896960103
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Teladi - TerraCorp, 42.83345076827541, 0.16342367645953357
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Teladi - TerraCorp, 32.2761732300265, 0.21687825102784816
    Paranid - OTAS - Boron - Strong Arms - Split - Terran - Teladi, 56.678687812860915, 0.14114652806384706
    OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - Teladi - TerraCorp, 26.031927077781738, 0.26890056887008196
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Teladi, 30.767989726439268, 0.26001048723457915
    Yaki - OTAS - Boron - Strong Arms - Terran - Teladi, 66.58485862613976, 0.13516586481820353
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Terran - Teladi, 17.565371376556925, 0.39851135794044934
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Teladi, 15.205141001955226, 0.4603706074872881
    Paranid - Yaki - OTAS - Boron - Strong Arms - Terran - Teladi, 18.94452620482156, 0.4222855675305263
    Yaki - OTAS - Pirates - Boron - Strong Arms - Terran - Teladi, 24.868154266968517, 0.3216965728182777
    Paranid - Pirates - Boron - Duke's - Strong Arms - Terran - Teladi, 40.94945139246964, 0.19536281263761088
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Teladi, 24.397008936980807, 0.3279090490422233
    Paranid - Yaki - Boron - Duke's - Strong Arms - Terran - Teladi, 23.65945369132236, 0.3381312224860958
    Yaki - Pirates - Boron - Duke's - Strong Arms - Terran - Teladi, 16.917848843915063, 0.4728733584162152
    Paranid - Yaki - Pirates - Boron - Strong Arms - Terran - Teladi, 15.118737189535807, 0.529144722850072
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Teladi - TerraCorp, 36.648181378812026, 0.1910053851689082
    Paranid - Yaki - OTAS - Boron - Strong Arms - Arteus - Teladi, 73.11552226252194, 0.10941589080463555
    Paranid - OTAS - Boron - Strong Arms - Arteus - Terran - Teladi - TerraCorp, 63.25340012850074, 0.1106659876904536
    Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi - TerraCorp, 18.404270814541615, 0.3803465005779608
    Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - Teladi, 30.524990227475765, 0.2620803459848168
    Yaki - Boron - Strong Arms - Arteus - Terran - Teladi - TerraCorp, 30.834949387742896, 0.2594458612336836
    Paranid - Pirates - Boron - Arteus - Strong Arms - Terran - Teladi, 61.01172555501266, 0.13112233635789586
    Paranid - Yaki - Pirates - Boron - Strong Arms - Arteus - Teladi, 38.01553507064628, 0.21044028408736526
    Paranid - Yaki - Boron - Strong Arms - Arteus - Terran - Teladi, 15.887689203079386, 0.5035345227202344
    Yaki - Pirates - Boron - Strong Arms - Arteus - Terran - Teladi, 24.213286243861884, 0.3303971183187914
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus - Teladi, 30.035572077651754, 0.26635084490208444
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - Teladi, 11.298065533486398, 0.6195750926787124
    Yaki - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi - TerraCorp, 15.621645655552376, 0.4480961964152606
    Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi, 11.117371406663619, 0.6296452411227608
    Paranid - Yaki - Pirates - Strong Arms - Arteus - Terran - Teladi, 17.51383257700093, 0.4567818017459843
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Teladi - TerraCorp, 47.16627111223758, 0.14841113861519162
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Teladi - TerraCorp, 52.6767222550556, 0.1328860206241891
    Yaki - OTAS - Boron - Duke's - Strong Arms - Terran - Teladi, 29.128069913203504, 0.27464916226301933
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - Teladi, 10.071148978467658, 0.6950547564102325
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Terran - Teladi, 13.606675147301106, 0.5144533785234415
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Terran - Teladi, 9.385936106350373, 0.745796681405482
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Teladi - TerraCorp, 36.443473987965895, 0.1920782854650874
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - Teladi - TerraCorp, 48.036275551362806, 0.1457232043836381
    Paranid - OTAS - Duke's - Strong Arms - Split - Terran - Teladi - TerraCorp, 26.758295995873496, 0.26160111245796436
    Pirates - Duke's - Strong Arms - Split - Arteus - Terran - Teladi - TerraCorp, 21.082053724911574, 0.3320359624986849
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Teladi - TerraCorp, 21.082053724911574, 0.3320359624986849
    Yaki - Strong Arms - Split - Terran - Arteus - Teladi - TerraCorp, 51.75347928917348, 0.15457897922765462
    Paranid - Pirates - Strong Arms - Split - Arteus - Terran - Teladi, 31.716275490013285, 0.25223642676830116
    Paranid - Yaki - Pirates - Strong Arms - Split - Arteus - Teladi, 23.881524756458877, 0.3349869860313823
    Paranid - Yaki - Strong Arms - Split - Arteus - Terran - Teladi, 15.900812702130652, 0.503118937997932
    Yaki - Pirates - Strong Arms - Split - Arteus - Terran - Teladi, 25.384394369672563, 0.31515425908911265
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus - Teladi, 21.583569097932067, 0.370652321851926
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Teladi, 9.623949347371411, 0.7273521240956977
    Yaki - Duke's - Strong Arms - Split - Arteus - Terran - Teladi - TerraCorp, 21.082053724911574, 0.3320359624986849
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - Teladi, 11.481031389821519, 0.6097013205804692
    Paranid - Yaki - Pirates - Strong Arms - Split - Arteus - Terran - Teladi, 9.425851321807539, 0.7426384907859603
    OTAS - Pirates - Duke's - Strong Arms - Split - Terran - Teladi, 29.673169072169454, 0.26960382898580326
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Teladi - TerraCorp, 26.758295995873496, 0.26160111245796436
    Yaki - OTAS - Duke's - Strong Arms - Split - Terran - Teladi, 29.673169072169454, 0.26960382898580326
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Terran - Teladi, 8.37860433862869, 0.8354613390355745
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Terran - Teladi, 8.867319597420126, 0.789415552591179
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Terran - Teladi, 7.3097243590126935, 0.9576284489262838
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - Teladi - TerraCorp, 36.4434739879659, 0.19207828546508735
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Teladi, 13.815843234388954, 0.5066646951071601
    Yaki - OTAS - Duke's - Strong Arms - Arteus - Terran - Teladi, 25.94572230331382, 0.3083359910538405
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - Teladi, 9.513567511153566, 0.7357912782763463
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran - Teladi, 17.415191991344997, 0.4019479086695605
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran - Teladi, 7.655760152723986, 0.9143442140764217
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran - Teladi, 8.37860433862869, 0.8354613390355745
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - Teladi - Argon, 20.108496060133074, 0.34811156334451776
    Yaki - OTAS - Boron - Strong Arms - Split - Arteus - Teladi - Argon, 36.14057458305796, 0.1936881214744569
    OTAS - Boron - Strong Arms - Split - Arteus - Terran - Teladi - Argon, 159.24396782841816, 0.04395770901377152
    OTAS - Pirates - Boron - Split - Strong Arms - Arteus - Teladi - Argon, 58.27259364911725, 0.12012508044776278
    Yaki - Pirates - Boron - Strong Arms - Split - Arteus - Teladi - Argon, 52.40368831695206, 0.13357838398057129
    Yaki - Boron - Strong Arms - Arteus - Terran - Teladi - Argon, 52.25164482913818, 0.1531052280968348
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus - Teladi - Argon, 24.66309806173054, 0.28382484562480104
    Paranid - Yaki - Boron - Strong Arms - Arteus - Teladi - Argon, 34.833024451020485, 0.229667108328448
    Paranid - Boron - Strong Arms - Split - Arteus - Terran - Teladi - Argon, 52.161515453639076, 0.1341985549906342
    OTAS - Pirates - Boron - Split - Strong Arms - Terran - Teladi - Argon, 37.7534706935517, 0.18541341687018995
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Teladi - Argon, 37.74977987060218, 0.18543154487243202
    Paranid - Yaki - Boron - Duke's - Strong Arms - Arteus - Teladi - Argon, 23.79146113060223, 0.29422320729163265
    Paranid - Boron - Duke's - Strong Arms - Split - Arteus - Terran - Teladi - Argon, 41.99999999999999, 0.14285714285714288
    Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi - Argon, 49.55813953488372, 0.14124824026278743
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Teladi - Argon, 63.97516688100919, 0.10941745588596388
    Yaki - Duke's - Strong Arms - Split - Arteus - Terran - Teladi - Argon, 73.71327379119182, 0.0949625439215867
    Paranid - Pirates - Strong Arms - Split - Terran - Teladi - Argon, 37.82862839086764, 0.21148004409092747
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Teladi - Argon, 18.217635422902546, 0.3842430610506046
    Paranid - Yaki - Boron - Strong Arms - Terran - Teladi - Argon, 23.81811638120054, 0.33587878537340343
    Yaki - Pirates - Strong Arms - Terran - Teladi - Argon, 36.1477449096663, 0.2489781872283076
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Teladi - Argon, 37.74977987060218, 0.18543154487243202
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Teladi - Argon, 15.823222021485323, 0.44238777604808655
    Paranid - OTAS - Boron - Strong Arms - Split - Terran - Teladi - Argon, 22.531642326415575, 0.3106742020218101
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Teladi - Argon, 25.394097568102417, 0.2756546075806496
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Teladi - Argon, 23.38416403789352, 0.2993478829799798
    Yaki - OTAS - Boron - Strong Arms - Terran - Teladi - Argon, 24.8929964543114, 0.32137553286054565
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Teladi - Argon, 17.6950384876792, 0.3955911146999765
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Teladi - Argon, 26.032723383578855, 0.26889234356538816
    Paranid - Yaki - OTAS - Strong Arms - Terran - Teladi - Argon, 22.219544550262707, 0.3600433835132509
    Yaki - OTAS - Pirates - Strong Arms - Terran - Teladi - Argon, 24.868154266968517, 0.3216965728182777
    Paranid - Pirates - Boron - Duke's - Strong Arms - Terran - Teladi - Argon, 35.55539627088292, 0.1968758819806053
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Teladi - Argon, 20.962805795029855, 0.3339247650550507
    Paranid - Yaki - Duke's - Strong Arms - Terran - Teladi - Argon, 26.834780795974723, 0.2981205645324302
    Yaki - Pirates - Duke's - Strong Arms - Terran - Teladi - Argon, 17.128023730788147, 0.46707081480858503
    Paranid - Yaki - Pirates - Strong Arms - Terran - Teladi - Argon, 17.44916088248607, 0.45847476872252896
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - Teladi - Argon, 26.04114134041141, 0.26880542248496586
    Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - Teladi - Argon, 23.79146113060223, 0.29422320729163265
    Paranid - OTAS - Boron - Strong Arms - Arteus - Terran - Teladi - Argon, 27.870806172202855, 0.25115886339095206
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Teladi - Argon, 20.7596742753665, 0.33719218842976856
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Teladi - Argon, 34.31959303593173, 0.23310299721865016
    Yaki - OTAS - Strong Arms - Terran - Arteus - Teladi - Argon, 37.401853357450086, 0.21389314383819105
    Paranid - OTAS - Pirates - Boron - Strong Arms - Arteus - Teladi - Argon, 39.45171588188347, 0.1774320797847592
    Paranid - Yaki - OTAS - Boron - Strong Arms - Arteus - Teladi - Argon, 18.220609437182684, 0.3841803439195148
    Paranid - Yaki - Boron - Strong Arms - Arteus - Terran - Teladi - Argon, 12.477529165300805, 0.5610085063528879
    OTAS - Pirates - Boron - Arteus - Strong Arms - Terran - Teladi - Argon, 54.052177222184554, 0.12950449657607874
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus - Teladi - Argon, 20.759674275366496, 0.3371921884297686
    Paranid - Yaki - Pirates - Boron - Strong Arms - Arteus - Teladi - Argon, 18.376301164183285, 0.38092540699341043
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Terran - Teladi - Argon, 14.37225304027373, 0.48704959343428594
    Yaki - Pirates - Strong Arms - Arteus - Terran - Teladi - Argon, 26.316111478704137, 0.3039962802435255
    Paranid - Pirates - Boron - Arteus - Strong Arms - Terran - Teladi - Argon, 27.89038789919223, 0.25098252578275315
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Teladi - Argon, 27.85118736573186, 0.25133578357283287
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Teladi - Argon, 26.634215710757786, 0.26281982829975503
    Yaki - OTAS - Duke's - Strong Arms - Terran - Teladi - Argon, 26.820968708312527, 0.29827408871777955
    OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - Teladi - Argon, 26.440715883668897, 0.2647432100854557
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Teladi - Argon, 29.31033536834965, 0.27294126455607487
    Paranid - OTAS - Pirates - Boron - Strong Arms - Terran - Teladi - Argon, 37.7534706935517, 0.18541341687018995
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Terran - Teladi - Argon, 10.060376923018305, 0.6957989798557037
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Teladi - Argon, 25.00292290244745, 0.27996726731956584
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - Teladi - Argon, 21.546937597232866, 0.3248721526394064
    Paranid - OTAS - Strong Arms - Split - Arteus - Terran - Teladi - Argon, 32.27617323002651, 0.2168782510278481
    OTAS - Pirates - Strong Arms - Split - Arteus - Terran - Teladi - Argon, 96.44756749405073, 0.07257829494177537
    Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - Teladi - Argon, 42.71311475409833, 0.16388409134523138
    Yaki - OTAS - Strong Arms - Split - Terran - Teladi - Argon, 29.44115281486045, 0.27172849005973676
    Paranid - OTAS - Pirates - Strong Arms - Split - Arteus - Teladi - Argon, 29.514150775013924, 0.23717436606463557
    Paranid - Yaki - Pirates - Strong Arms - Split - Arteus - Teladi - Argon, 17.24812632591174, 0.4058411834266281
    Paranid - Yaki - Strong Arms - Split - Terran - Teladi - Argon, 21.07541351762194, 0.3795892305178687
    Yaki - Pirates - Strong Arms - Split - Terran - Teladi - Argon, 24.871866046015683, 0.3216485640924216
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus - Teladi - Argon, 18.584140399705543, 0.3766652559356962
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Teladi - Argon, 26.138661599330653, 0.2678025412050651
    Paranid - Yaki - Duke's - Strong Arms - Split - Terran - Teladi - Argon, 19.777728227655416, 0.3539334709945009
    Yaki - Pirates - Duke's - Strong Arms - Split - Terran - Teladi - Argon, 14.981310392373874, 0.4672488465069984
    Paranid - Pirates - Strong Arms - Split - Arteus - Terran - Teladi - Argon, 23.821714173403834, 0.29384955041628663
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Teladi - Argon, 12.643288729206976, 0.5536534164429432
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Teladi - Argon, 19.45848826314036, 0.35974017638666683
    Paranid - OTAS - Duke's - Strong Arms - Split - Terran - Teladi - Argon, 30.784557449072878, 0.22738673478025961
    OTAS - Pirates - Duke's - Strong Arms - Split - Terran - Teladi - Argon, 19.411105674442698, 0.36061830363514175
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Teladi - Argon, 13.713796680730736, 0.5104348681088224
    Yaki - OTAS - Duke's - Strong Arms - Split - Terran - Teladi - Argon, 19.411105674442698, 0.36061830363514175
    Paranid - OTAS - Pirates - Strong Arms - Split - Terran - Teladi - Argon, 17.56537137655693, 0.39851135794044923
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Teladi - Argon, 14.6058900792117, 0.4792587074144131
    Paranid - Yaki - OTAS - Strong Arms - Split - Terran - Teladi - Argon, 10.824649491562347, 0.6466722091515661
    Yaki - OTAS - Pirates - Strong Arms - Split - Terran - Teladi - Argon, 13.606675147301107, 0.5144533785234414
    Paranid - Pirates - Duke's - Strong Arms - Split - Terran - Teladi - Argon, 19.777728227655416, 0.3539334709945009
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Teladi - Argon, 13.8612259486877, 0.5050058361297197
    Paranid - Yaki - Pirates - Strong Arms - Split - Terran - Teladi - Argon, 9.869556261665664, 0.7092517449025235
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - Teladi - Argon, 27.355639941237992, 0.255888731356186
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus - Teladi - Argon, 26.152765169029074, 0.2676581216080975
    Yaki - OTAS - Duke's - Strong Arms - Arteus - Terran - Teladi - Argon, 17.3221656689012, 0.40410651495887884
    OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - Teladi - Argon, 26.031927077781738, 0.26890056887008196
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Teladi - Argon, 16.78786107745564, 0.41696794890686073
    Paranid - Yaki - OTAS - Strong Arms - Arteus - Terran - Teladi - Argon, 17.132083724517486, 0.40859011154506547
    Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran - Teladi - Argon, 21.02435325226153, 0.3329472215392419
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Terran - Teladi - Argon, 20.514234566152396, 0.34122647751867374
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - Teladi - Argon, 14.076626756425899, 0.49727822731426335
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran - Teladi - Argon, 11.700460814169688, 0.5982670350489737
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Terran - Teladi - Argon, 23.224289674267077, 0.3014085725840788
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Teladi - Argon, 17.165017111474263, 0.40780617662890206
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Terran - Teladi - Argon, 13.975309558291286, 0.5008833593848397
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran - Teladi - Argon, 10.071148978467658, 0.6950547564102325
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Terran - Teladi - Argon, 15.676874783265129, 0.44651756786833646
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Teladi, 30.661661163743467, 0.2282981330534465
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Arteus - Teladi, 20.110611169228815, 0.34807495113379144
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - Terran - Teladi, 27.626284940917806, 0.25338187943005575
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - Teladi, 30.66166116374347, 0.22829813305344648
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - Teladi, 25.93896118131567, 0.2698643153466853
    Yaki - OTAS - Boron - Strong Arms - Split - Terran - Teladi, 39.44191193825986, 0.20282992397840016
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Arteus - Teladi, 27.16174235695817, 0.2577154259106935
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Arteus - Teladi, 15.29509180653241, 0.4576631568180818
    Paranid - Yaki - Boron - Strong Arms - Split - Terran - Teladi, 19.729472781494145, 0.40548473284617326
    Yaki - Pirates - Boron - Strong Arms - Split - Terran - Teladi, 26.34752435683717, 0.3036338401912893
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - Teladi, 15.671543456344507, 0.4466694693792973
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Arteus - Teladi, 25.938961181315666, 0.2698643153466853
    Yaki - Boron - Duke's - Strong Arms - Split - Arteus - Terran - Teladi, 67.29872154661678, 0.10401386295505197
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Terran - Teladi, 15.178122017978737, 0.46119012561029515
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus - Terran - Teladi, 19.885891888144286, 0.352008350411143
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Teladi, 12.950187266234463, 0.5405327240519044
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Teladi, 20.3829067762192, 0.34342501179306384
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Terran - Teladi, 30.784557449072878, 0.22738673478025961
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Terran - Teladi, 23.224289674267077, 0.3014085725840788
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Teladi, 16.405435649084097, 0.4266878460122334
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Terran - Teladi, 23.224289674267077, 0.3014085725840788
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Terran - Teladi, 10.824649491562347, 0.6466722091515661
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Terran - Teladi, 15.676874783265127, 0.4465175678683365
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Terran - Teladi, 18.673747446561872, 0.3748578061276506
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Teladi, 13.374189928587885, 0.5233961860401884
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Terran - Teladi, 18.673747446561872, 0.3748578061276506
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Terran - Teladi, 9.511077866671494, 0.7359838809152476
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Teladi, 18.39513078158566, 0.3805354842601777
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - Teladi, 18.732764572210172, 0.37367682559702986
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi, 29.493153186653785, 0.23734322185556048
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi, 23.336069473706782, 0.2999648251770522
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Teladi, 15.861543456245384, 0.4413189686936673
    Yaki - OTAS - Boron - Strong Arms - Arteus - Terran - Teladi, 36.735970548096375, 0.21777020943345005
    Paranid - OTAS - Pirates - Boron - Strong Arms - Arteus - Terran - Teladi, 48.5887632484072, 0.14406623120273532
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - Teladi, 35.013346134491, 0.19992376544395535
    Paranid - Yaki - OTAS - Boron - Strong Arms - Arteus - Terran - Teladi, 13.612608038027838, 0.5142291602347601
    Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - Terran - Teladi, 19.86317901866392, 0.3524108599848308
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi, 15.484920209855854, 0.4520527006361088
    Paranid - Yaki - Boron - Duke's - Strong Arms - Arteus - Terran - Teladi, 11.939735135482495, 0.5862776619891178
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - Teladi, 19.4111056744427, 0.3606183036351417
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Strong Arms - Teladi, 15.181782664245532, 0.4610789229966802
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Terran - Teladi, 12.709176147014658, 0.5507831443224017
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Teladi, 11.878901181805746, 0.589280093576459
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - Teladi, 18.053305555252564, 0.3877406261460726
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - Terran - Teladi, 26.758295995873493, 0.2616011124579644
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - Teladi, 21.08205372491157, 0.33203596249868494
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Teladi, 14.998693990247087, 0.466707301619178
    Yaki - OTAS - Strong Arms - Split - Arteus - Terran - Teladi, 51.753479289173484, 0.1545789792276546
    Paranid - OTAS - Pirates - Strong Arms - Split - Arteus - Terran - Teladi, 22.973881163425833, 0.3046938368926502
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - Teladi, 19.846210137064496, 0.3527121778745505
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - Terran - Teladi, 12.070175646446515, 0.5799418504784406
    Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - Terran - Teladi, 18.819357654121426, 0.371957434926957
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - Teladi, 12.631596005185576, 0.5541659183151781
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - Terran - Teladi, 12.631596005185575, 0.5541659183151781
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Terran - Teladi, 9.971876303402253, 0.7019742109728845
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Teladi, 8.490151854930206, 0.824484664068184
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Terran - Teladi, 9.971876303402253, 0.7019742109728845
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - Teladi, 17.67973668442019, 0.3959334986119204
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus - Terran - Teladi, 11.822079962133456, 0.5921123882109789
    Paranid - OTAS - Boron - Split - Arteus - Teladi - TerraCorp - Argon, 15.739708325641498, 0.44473505195749574
    Yaki - OTAS - Boron - Split - Arteus - Teladi - TerraCorp - Argon, 23.758090828747576, 0.294636469338265
    OTAS - Boron - Split - Arteus - Terran - Teladi - TerraCorp - Argon, 19.33962662154146, 0.3619511450238157
    OTAS - Pirates - Boron - Duke's - Split - Teladi - TerraCorp - Argon, 25.394097568102424, 0.2756546075806495
    Yaki - Pirates - Boron - Split - Arteus - Teladi - TerraCorp - Argon, 35.182457170006415, 0.19896279461593738
    Yaki - Boron - Split - Terran - Teladi - TerraCorp - Argon, 47.11349816652384, 0.16980271708383443
    Paranid - Pirates - Boron - Split - Arteus - Teladi - TerraCorp - Argon, 20.61820147522974, 0.33950584916000787
    Paranid - Yaki - Boron - Split - Arteus - Teladi - TerraCorp - Argon, 20.01326320603704, 0.3497680477158986
    Paranid - Boron - Split - Arteus - Terran - Teladi - TerraCorp - Argon, 14.988613012812126, 0.4670211976262557
    OTAS - Pirates - Boron - Split - Terran - Teladi - TerraCorp - Argon, 21.66800095764784, 0.3230570283655683
    Paranid - Pirates - Boron - Duke's - Arteus - Teladi - TerraCorp - Argon, 13.793117873768349, 0.5074994692325909
    Paranid - Yaki - Boron - Duke's - Arteus - Teladi - TerraCorp - Argon, 16.821916105000852, 0.41612382063414444
    Paranid - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 12.975770109937955, 0.5394670174249466
    Pirates - Boron - Duke's - Split - Terran - Teladi - TerraCorp - Argon, 40.85274342326597, 0.17134712172141278
    Yaki - Pirates - Boron - Duke's - Split - Teladi - TerraCorp - Argon, 164.3873873873871, 0.04258234230284438
    Yaki - Boron - Duke's - Terran - Teladi - TerraCorp - Argon, 41.09967290550508, 0.19464875105924365
    Paranid - Pirates - Split - Terran - Teladi - TerraCorp - Argon, 38.874789603624734, 0.20578889510579035
    Paranid - Yaki - Pirates - Boron - Split - Teladi - TerraCorp - Argon, 39.33765875841159, 0.1779465331932899
    Paranid - Yaki - Terran - Teladi - TerraCorp - Argon, 32.16517451667002, 0.2798057257651636
    Yaki - Pirates - Terran - Teladi - TerraCorp - Argon, 31.61791445881181, 0.2846487554302219
    Paranid - OTAS - Boron - Duke's - Split - Teladi - TerraCorp - Argon, 42.66326530612244, 0.1640755800047836
    Yaki - OTAS - Boron - Duke's - Split - Teladi - TerraCorp - Argon, 63.975166881009145, 0.10941745588596395
    Paranid - OTAS - Boron - Split - Terran - Teladi - TerraCorp - Argon, 16.666821189437293, 0.4199961060622823
    OTAS - Pirates - Boron - Duke's - Terran - Teladi - TerraCorp - Argon, 15.409702388343884, 0.45425925975669057
    Yaki - OTAS - Pirates - Boron - Split - Teladi - TerraCorp - Argon, 31.952906944539457, 0.21907239964582484
    Yaki - OTAS - Boron - Terran - Teladi - TerraCorp - Argon, 17.0403646025421, 0.46947352281456184
    Paranid - OTAS - Pirates - Boron - Terran - Teladi - TerraCorp - Argon, 25.776156822503328, 0.2715688008962142
    Paranid - Yaki - OTAS - Boron - Split - Teladi - TerraCorp - Argon, 24.860684447762043, 0.28156907806414555
    Paranid - Yaki - OTAS - Terran - Teladi - TerraCorp - Argon, 23.647567879363216, 0.3383011750219543
    Yaki - OTAS - Pirates - Terran - Teladi - TerraCorp - Argon, 24.598971402079314, 0.325216850299837
    Paranid - Pirates - Duke's - Terran - Teladi - TerraCorp - Argon, 37.220916688485474, 0.2149329117000187
    Paranid - Yaki - Pirates - Boron - Duke's - Teladi - TerraCorp - Argon, 39.12933753943217, 0.17889390519187362
    Paranid - Yaki - Duke's - Terran - Teladi - TerraCorp - Argon, 24.188779660510967, 0.3307318563515745
    Yaki - Pirates - Duke's - Terran - Teladi - TerraCorp - Argon, 15.546295145072655, 0.5145920571651807
    Paranid - Yaki - Pirates - Terran - Teladi - TerraCorp - Argon, 19.85948319220112, 0.40283022083583847
    Paranid - OTAS - Boron - Duke's - Arteus - Teladi - TerraCorp - Argon, 14.105263157894736, 0.49626865671641796
    Yaki - OTAS - Boron - Duke's - Arteus - Teladi - TerraCorp - Argon, 14.277589271287768, 0.4902788465891087
    Paranid - OTAS - Boron - Arteus - Terran - Teladi - TerraCorp - Argon, 14.349097336730884, 0.48783556454672367
    OTAS - Pirates - Boron - Duke's - Arteus - Teladi - TerraCorp - Argon, 12.236059280494938, 0.5720796082737559
    Yaki - Pirates - Boron - Duke's - Arteus - Teladi - TerraCorp - Argon, 15.060108454121053, 0.46480408964681247
    Yaki - Boron - Arteus - Terran - Teladi - TerraCorp - Argon, 14.877271820639018, 0.537732999467128
    Paranid - Pirates - Boron - Arteus - Terran - Teladi - TerraCorp - Argon, 14.954726132193976, 0.4680794511462608
    Paranid - Yaki - OTAS - Boron - Arteus - Teladi - TerraCorp - Argon, 16.725755255201772, 0.41851622800847654
    Paranid - Yaki - Arteus - Terran - Teladi - TerraCorp - Argon, 17.86450846290798, 0.4478152878715008
    Yaki - Pirates - Arteus - Terran - Teladi - TerraCorp - Argon, 21.028056191797926, 0.3804441041545452
    Pirates - Boron - Duke's - Terran - Arteus - Teladi - TerraCorp - Argon, 11.825702643037268, 0.591931000744506
    Paranid - Yaki - Pirates - Boron - Arteus - Teladi - TerraCorp - Argon, 18.253158815525172, 0.3834952662574858
    Yaki - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 11.103051133622769, 0.6304573324716374
    Yaki - Pirates - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 9.152483560024155, 0.764819729431071
    Paranid - Yaki - Pirates - Arteus - Terran - Teladi - TerraCorp - Argon, 14.399023794001643, 0.486144067830214
    Paranid - OTAS - Pirates - Duke's - Terran - Teladi - TerraCorp - Argon, 21.200842563869347, 0.3301755568870389
    Yaki - OTAS - Pirates - Boron - Duke's - Teladi - TerraCorp - Argon, 21.577323323679824, 0.32441465954759635
    Yaki - OTAS - Duke's - Terran - Teladi - TerraCorp - Argon, 20.54981359716279, 0.3892979350968186
    Yaki - OTAS - Pirates - Duke's - Terran - Teladi - TerraCorp - Argon, 10.552766237920538, 0.6633331812890964
    Paranid - Yaki - OTAS - Pirates - Terran - Teladi - TerraCorp - Argon, 17.88156233259571, 0.39146467572578547
    Paranid - Yaki - Pirates - Duke's - Terran - Teladi - TerraCorp - Argon, 11.63633551017026, 0.601563954037071
    OTAS - Pirates - Duke's - Split - Arteus - Teladi - TerraCorp - Argon, 24.910939458372862, 0.28100104420779753
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - Teladi - TerraCorp - Argon, 18.646323445846114, 0.32177925141251557
    Paranid - OTAS - Split - Terran - Arteus - Teladi - TerraCorp - Argon, 24.548161277987383, 0.2851537400594227
    OTAS - Pirates - Split - Arteus - Terran - Teladi - TerraCorp - Argon, 42.65519800053066, 0.1641066113422546
    Yaki - Pirates - Duke's - Split - Arteus - Teladi - TerraCorp - Argon, 30.700684493945264, 0.22800794560070894
    Yaki - OTAS - Split - Terran - Teladi - TerraCorp - Argon, 24.912995373316107, 0.32111754849714563
    Paranid - Pirates - Split - Arteus - Terran - Teladi - TerraCorp - Argon, 20.714738823985147, 0.3379236426526822
    Paranid - Yaki - Pirates - Split - Arteus - Teladi - TerraCorp - Argon, 34.612387894493104, 0.2022397305074035
    Paranid - Yaki - Split - Terran - Teladi - TerraCorp - Argon, 22.466068762800063, 0.35609256272048007
    Yaki - Pirates - Split - Terran - Teladi - TerraCorp - Argon, 23.123275197158044, 0.34597175061875474
    Paranid - Pirates - Duke's - Split - Arteus - Teladi - TerraCorp - Argon, 23.489457168059204, 0.29800603521474944
    Paranid - Yaki - Pirates - Duke's - Split - Teladi - TerraCorp - Argon, 42.07720977370872, 0.16636084088384206
    Yaki - Duke's - Split - Terran - Arteus - Teladi - TerraCorp - Argon, 18.79892150842849, 0.37236178665151365
    Pirates - Duke's - Split - Terran - Arteus - Teladi - TerraCorp - Argon, 18.79892150842849, 0.37236178665151365
    Paranid - Yaki - Pirates - Split - Terran - Teladi - TerraCorp - Argon, 12.848890712277244, 0.5447941115501457
    Paranid - OTAS - Pirates - Duke's - Split - Teladi - TerraCorp - Argon, 25.864124144699677, 0.270645159327172
    Yaki - OTAS - Pirates - Duke's - Split - Teladi - TerraCorp - Argon, 26.98309636754519, 0.25942167291147067
    Paranid - OTAS - Duke's - Split - Terran - Teladi - TerraCorp - Argon, 25.864124144699687, 0.27064515932717187
    OTAS - Pirates - Duke's - Split - Terran - Teladi - TerraCorp - Argon, 16.216119847020625, 0.4316692319763599
    Yaki - OTAS - Duke's - Split - Terran - Teladi - TerraCorp - Argon, 16.216119847020625, 0.4316692319763599
    Paranid - OTAS - Pirates - Split - Terran - Teladi - TerraCorp - Argon, 20.77214278966809, 0.3369897882409006
    Paranid - Yaki - OTAS - Split - Terran - Teladi - TerraCorp - Argon, 13.314346442196673, 0.5257486749642593
    Yaki - OTAS - Pirates - Split - Terran - Teladi - TerraCorp - Argon, 14.854415914550243, 0.47124033959109346
    Paranid - Pirates - Duke's - Split - Terran - Teladi - TerraCorp - Argon, 19.973663926951488, 0.3504614889687085
    Paranid - Yaki - Duke's - Split - Terran - Teladi - TerraCorp - Argon, 19.973663926951488, 0.3504614889687085
    Yaki - Pirates - Duke's - Split - Terran - Teladi - TerraCorp - Argon, 14.033775167384634, 0.4987966471251752
    OTAS - Pirates - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 15.083216551938568, 0.46409199098187887
    Yaki - OTAS - Pirates - Duke's - Arteus - Teladi - TerraCorp - Argon, 21.144175879224267, 0.3310604319593285
    Yaki - OTAS - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 11.851433356358525, 0.5906458560343136
    Yaki - OTAS - Pirates - Arteus - Terran - Teladi - TerraCorp - Argon, 18.9185019958407, 0.3700081540038939
    Paranid - Yaki - OTAS - Arteus - Terran - Teladi - TerraCorp - Argon, 16.37395322366237, 0.4275082446115787
    Paranid - Pirates - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 13.88769509163485, 0.5040433242386203
    Paranid - Yaki - Pirates - Duke's - Arteus - Teladi - TerraCorp - Argon, 20.12072902877454, 0.34789991903321893
    Paranid - Yaki - Duke's - Arteus - Terran - Teladi - TerraCorp - Argon, 11.193278041513977, 0.6253753345568815
    Paranid - Yaki - OTAS - Pirates - Duke's - Teladi - TerraCorp - Argon, 38.013999101994735, 0.18414268862422012
    Paranid - Yaki - OTAS - Duke's - Terran - Teladi - TerraCorp - Argon, 14.586923616278682, 0.47988185748694506
    Paranid - OTAS - Pirates - Boron - Split - Arteus - Teladi - TerraCorp, 38.7960628116767, 0.18043068014348007
    Paranid - Yaki - OTAS - Boron - Split - Arteus - Teladi - TerraCorp, 30.378994374270462, 0.23042237388636738
    Paranid - OTAS - Boron - Split - Arteus - Terran - Teladi - TerraCorp, 21.154287931703536, 0.33090218033334184
    Pirates - Boron - Duke's - Split - Arteus - Terran - Teladi - TerraCorp, 18.394273712710795, 0.3805532150564263
    Yaki - Pirates - Boron - Duke's - Split - Arteus - Teladi - TerraCorp, 26.983096367545205, 0.2594216729114705
    Yaki - Boron - Split - Arteus - Terran - Teladi - TerraCorp, 31.875838811078825, 0.25097378762059447
    Paranid - Pirates - Boron - Split - Arteus - Terran - Teladi - TerraCorp, 16.870026101011486, 0.4149371173516025
    Paranid - Yaki - Pirates - Boron - Split - Arteus - Teladi - TerraCorp, 23.68653976565495, 0.29552649180737967
    Paranid - Yaki - Boron - Split - Terran - Teladi - TerraCorp, 20.076915954271733, 0.39846757431376567
    Yaki - Pirates - Boron - Split - Terran - Teladi - TerraCorp, 24.183912847833287, 0.33079841340549426
    Paranid - Pirates - Boron - Duke's - Split - Arteus - Teladi - TerraCorp, 16.96790624599769, 0.4125435335695073
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Teladi - TerraCorp, 33.18757793404764, 0.21092229188616365
    Paranid - Boron - Duke's - Split - Arteus - Terran - Teladi - TerraCorp, 19.188538091847313, 0.3648011102510258
    Yaki - Boron - Duke's - Split - Arteus - Terran - Teladi - TerraCorp, 18.3942737127108, 0.3805532150564262
    Paranid - Yaki - Pirates - Boron - Split - Terran - Teladi - TerraCorp, 11.786570148275272, 0.5938962659993424
    Paranid - OTAS - Boron - Duke's - Split - Terran - Teladi - TerraCorp, 25.53241406064025, 0.2741613066189037
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Teladi - TerraCorp, 30.700684493945285, 0.22800794560070878
    Yaki - OTAS - Boron - Split - Terran - Teladi - TerraCorp, 31.701228451720404, 0.25235615118775767
    OTAS - Pirates - Boron - Duke's - Split - Terran - Teladi - TerraCorp, 18.78131045617704, 0.37271094667932236
    Paranid - Yaki - OTAS - Boron - Split - Terran - Teladi - TerraCorp, 12.721538470586534, 0.5502479135039129
    Yaki - OTAS - Pirates - Boron - Split - Terran - Teladi - TerraCorp, 16.542916697519093, 0.42314182728428873
    Paranid - Pirates - Boron - Duke's - Split - Terran - Teladi - TerraCorp, 18.06281455996081, 0.3875365036142622
    Paranid - Yaki - Boron - Duke's - Split - Terran - Teladi - TerraCorp, 18.06281455996081, 0.3875365036142622
    Yaki - Pirates - Boron - Duke's - Split - Terran - Teladi - TerraCorp, 14.033775167384634, 0.4987966471251752
    OTAS - Pirates - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp, 13.920983464544765, 0.5028380371134152
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Arteus - Teladi - TerraCorp, 11.029245498807306, 0.5440082008011188
    Yaki - OTAS - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp, 11.583221491249843, 0.6043223817560526
    Yaki - OTAS - Pirates - Boron - Arteus - Terran - Teladi - TerraCorp, 17.536109953233154, 0.39917632922399654
    Paranid - Yaki - OTAS - Boron - Arteus - Terran - Teladi - TerraCorp, 12.680437431419527, 0.5520314293460755
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Terran - Teladi - TerraCorp, 5.980254228166782, 1.0033018281631265
    Paranid - Yaki - OTAS - Boron - Duke's - Terran - Teladi - TerraCorp, 12.942752089249973, 0.5408432419727857
    Paranid - OTAS - Pirates - Split - Arteus - Terran - Teladi - TerraCorp, 27.537989793152114, 0.25419429858822495
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - Teladi - TerraCorp, 53.07325648179838, 0.13189316925372138
    Yaki - OTAS - Duke's - Split - Arteus - Terran - Teladi - TerraCorp, 16.59707836141662, 0.42176097790036127
    Yaki - OTAS - Pirates - Split - Arteus - Terran - Teladi - TerraCorp, 20.817044936313824, 0.3362629048174368
    Paranid - Yaki - OTAS - Split - Arteus - Terran - Teladi - TerraCorp, 14.64073589794738, 0.47811804330009083
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Terran - Teladi - TerraCorp, 6.75208280474203, 0.8886146946814933
    Paranid - Yaki - OTAS - Duke's - Split - Terran - Teladi - TerraCorp, 13.024174651015853, 0.537462080136803
    Paranid - Yaki - OTAS - Duke's - Arteus - Terran - Teladi - TerraCorp, 11.72289679098005, 0.5971220360300374
    Paranid - OTAS - Pirates - Boron - Split - Arteus - Teladi - Argon, 15.326030449313034, 0.4567392726479781
    Paranid - Yaki - OTAS - Boron - Split - Arteus - Teladi - Argon, 13.84921128330062, 0.5054439459986144
    Paranid - OTAS - Boron - Split - Arteus - Terran - Teladi - Argon, 14.988613012812126, 0.4670211976262557
    OTAS - Pirates - Boron - Duke's - Split - Terran - Teladi - Argon, 19.102109224298765, 0.3664516791211557
    Yaki - Pirates - Boron - Duke's - Split - Arteus - Teladi - Argon, 34.24029478228608, 0.20443749227361763
    Yaki - OTAS - Boron - Split - Arteus - Terran - Teladi - Argon, 14.549011128692502, 0.4811323558750401
    Paranid - Pirates - Boron - Split - Arteus - Terran - Teladi - Argon, 18.731583177069382, 0.3737003932785127
    Paranid - Yaki - Pirates - Boron - Split - Arteus - Teladi - Argon, 17.714576968757736, 0.39515479327254216
    Paranid - Yaki - Boron - Split - Terran - Teladi - Argon, 33.73859135834227, 0.23711719066842143
    Yaki - Pirates - Boron - Split - Terran - Teladi - Argon, 31.727652655813948, 0.2521459777306922
    Paranid - Pirates - Boron - Duke's - Split - Arteus - Teladi - Argon, 21.524378233356344, 0.3252126460569298
    Paranid - Yaki - Boron - Duke's - Split - Arteus - Teladi - Argon, 38.01272873370101, 0.1841488425900348
    Yaki - Boron - Duke's - Split - Arteus - Terran - Teladi - Argon, 56.95305164319248, 0.12290825158684364
    Yaki - Pirates - Boron - Duke's - Split - Terran - Teladi - Argon, 23.07883742544417, 0.30330817237278057
    Paranid - Yaki - Pirates - Boron - Split - Terran - Teladi - Argon, 13.540571417742457, 0.5169648890022301
    Paranid - Pirates - Boron - Duke's - Split - Terran - Teladi - Argon, 33.66011600475959, 0.20796125595675874
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Teladi - Argon, 19.10210922429877, 0.36645167912115567
    Yaki - OTAS - Boron - Duke's - Split - Terran - Teladi - Argon, 19.102109224298765, 0.3664516791211557
    Yaki - OTAS - Pirates - Boron - Split - Terran - Teladi - Argon, 12.672004869939826, 0.5523987776082065
    Paranid - Yaki - OTAS - Boron - Split - Terran - Teladi - Argon, 11.161817013390722, 0.6271380360027555
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Teladi - Argon, 39.06616414203285, 0.17918319225174248
    Paranid - Yaki - Boron - Duke's - Split - Terran - Teladi - Argon, 33.66011600475959, 0.20796125595675874
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - Terran - Teladi - Argon, 9.085500101303436, 0.6603929264322191
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - Teladi - Argon, 13.790042240842048, 0.5076126583041246
    Yaki - OTAS - Boron - Duke's - Arteus - Terran - Teladi - Argon, 11.841380247683464, 0.5911473032351456
    Yaki - OTAS - Pirates - Boron - Arteus - Terran - Teladi - Argon, 12.198541306857836, 0.5738391028823017
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - Terran - Teladi - Argon, 8.577706987678392, 0.6994876379688433
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Terran - Teladi - Argon, 7.669640072359803, 0.7823052898692172
    Paranid - Yaki - OTAS - Boron - Duke's - Terran - Teladi - Argon, 13.145357300023697, 0.5325073971163478
    Paranid - OTAS - Pirates - Split - Arteus - Terran - Teladi - Argon, 20.714738823985147, 0.3379236426526822
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - Teladi - Argon, 18.768931153058727, 0.3729567732395474
    Yaki - OTAS - Duke's - Split - Arteus - Terran - Teladi - Argon, 18.798921508428485, 0.3723617866515137
    Yaki - OTAS - Pirates - Split - Arteus - Terran - Teladi - Argon, 16.193833034141072, 0.4322633180941206
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - Teladi - Argon, 24.849892836904022, 0.28169135561037334
    Paranid - Yaki - OTAS - Split - Arteus - Terran - Teladi - Argon, 13.06152724794631, 0.5359250772991055
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Terran - Teladi - Argon, 8.712044417337903, 0.6887017228768205
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Terran - Teladi - Argon, 7.679635614810575, 0.7812870689370586
    Paranid - Yaki - OTAS - Duke's - Arteus - Terran - Teladi - Argon, 12.89111387748655, 0.5430097093646051
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Arteus - Teladi, 13.026948020935233, 0.5373476572371749
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Arteus - Teladi, 17.61036778269341, 0.3974931180528354
    Yaki - OTAS - Boron - Duke's - Split - Arteus - Terran - Teladi, 18.3942737127108, 0.3805532150564262
    Yaki - OTAS - Pirates - Boron - Split - Arteus - Terran - Teladi, 16.291814368332613, 0.4296636238138291
    Paranid - Yaki - OTAS - Boron - Split - Arteus - Terran - Teladi, 11.048580298407815, 0.6335655632614403
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Arteus - Terran - Teladi, 7.497968611437646, 0.800216740151113
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Terran - Teladi, 12.709176147014658, 0.5507831443224017
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - Terran - Teladi, 10.038336806469381, 0.6973266722320701
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - Terran - Teladi, 11.822079962133456, 0.5921123882109789
    OTAS - Boron - Strong Arms - Split - Arteus - TerraCorp - Argon - NMMC, 92.51295067995704, 0.07566508200798909
    Yaki - Boron - Strong Arms - Split - Arteus - TerraCorp - Argon - NMMC, 122.2551020408163, 0.057257324096486116
    Boron - Strong Arms - Arteus - Terran - TerraCorp - Argon - NMMC, 3163.250303846225, 0.002529044252449048
    OTAS - Pirates - Boron - Split - Strong Arms - TerraCorp - Argon - NMMC, 79.58696403351927, 0.087954102597152
    Yaki - Pirates - Boron - Strong Arms - Arteus - Argon - NMMC, 64.95161290322578, 0.12316861186987837
    Yaki - Strong Arms - Terran - TerraCorp - Argon - NMMC, 58.17635742235053, 0.15470201983705376
    Paranid - Boron - Strong Arms - Arteus - TerraCorp - Argon - NMMC, 131.4714784633294, 0.06084969982467639
    Paranid - Yaki - Boron - Strong Arms - Split - TerraCorp - Argon - NMMC, 49.25446428571427, 0.1421190972536935
    Paranid - Boron - Strong Arms - Split - Terran - TerraCorp - Argon - NMMC, 77.7036695187966, 0.09008583562847945
    Pirates - Boron - Split - Terran - Strong Arms - TerraCorp - Argon - NMMC, 148.07481258605713, 0.04727340104470358
    Paranid - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon - NMMC, 35.46511589874792, 0.19737705129696564
    Yaki - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon - NMMC, 43.11587982832618, 0.16235317539319133
    Boron - Duke's - Strong Arms - Terran - Arteus - TerraCorp - Argon - NMMC, 65.27782888684452, 0.10723395859464184
    Pirates - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon - NMMC, 29.14877052667404, 0.2401473500775719
    Yaki - Pirates - Duke's - Strong Arms - TerraCorp - Argon - NMMC, 67.23342253881044, 0.11898843905175295
    Yaki - Duke's - Strong Arms - Terran - TerraCorp - NMMC, 61.492535240948754, 0.14635922823371855
    Paranid - Pirates - Boron - Split - Strong Arms - TerraCorp - Argon - NMMC, 47.32498409209231, 0.14791341474892652
    Paranid - Yaki - Pirates - Boron - Strong Arms - TerraCorp - NMMC, 96.74884563238979, 0.08268832509275689
    Paranid - Yaki - Strong Arms - Terran - NMMC, 36.178724108262564, 0.27640554625629216
    Yaki - Pirates - Strong Arms - Terran - NMMC, 40.76041403938248, 0.24533607510311492
    Paranid - OTAS - Boron - Strong Arms - Split - TerraCorp - Argon - NMMC, 35.465115898747925, 0.19737705129696562
    Yaki - OTAS - Boron - Strong Arms - Split - TerraCorp - Argon - NMMC, 47.06571964813601, 0.1487282049936153
    OTAS - Boron - Strong Arms - Split - Terran - TerraCorp - Argon - NMMC, 73.153143509292, 0.09568966778728863
    OTAS - Pirates - Boron - Duke's - Strong Arms - TerraCorp - Argon - NMMC, 48.816954008045855, 0.14339280568071253
    Yaki - OTAS - Pirates - Boron - Strong Arms - Argon - NMMC, 57.86948134865649, 0.13824212371631578
    Yaki - OTAS - Strong Arms - Terran - Argon - NMMC, 49.03417148554053, 0.1835454689522789
    Paranid - OTAS - Pirates - Strong Arms - Split - TerraCorp - Argon - NMMC, 34.91808562032589, 0.2004691802440992
    Paranid - Yaki - OTAS - Boron - Strong Arms - Argon - NMMC, 45.51203009149101, 0.175777700619329
    Paranid - OTAS - Boron - Strong Arms - Terran - TerraCorp - Argon - NMMC, 47.26281898402099, 0.14810796627189374
    OTAS - Pirates - Boron - Terran - Strong Arms - TerraCorp - Argon - NMMC, 60.09516902979665, 0.11648190882913116
    Paranid - Pirates - Duke's - Strong Arms - Split - TerraCorp - NMMC, 44.11922578935027, 0.18132684463223475
    Paranid - Yaki - Duke's - Strong Arms - Split - TerraCorp - Argon - NMMC, 94.06906416019612, 0.07441341170439689
    Paranid - Boron - Duke's - Strong Arms - Split - Terran - TerraCorp - Argon - NMMC, 63.127659574468076, 0.09504550050556118
    Pirates - Boron - Duke's - Terran - Strong Arms - TerraCorp - NMMC, 160.55752288574385, 0.04982637908342028
    Paranid - Pirates - Boron - Terran - Strong Arms - TerraCorp - Argon - NMMC, 43.80359377172252, 0.1598042397269893
    OTAS - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon - NMMC, 35.465115898747925, 0.19737705129696562
    Yaki - OTAS - Boron - Strong Arms - Arteus - Argon - NMMC, 55.647382581475576, 0.14376237711247025
    OTAS - Boron - Strong Arms - Arteus - Terran - TerraCorp - Argon - NMMC, 32.815612513400254, 0.21331309897511588
    OTAS - Pirates - Boron - Arteus - Strong Arms - TerraCorp - Argon - NMMC, 92.51295067995697, 0.07566508200798915
    Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - Argon - NMMC, 22.18210862619808, 0.3155696384848049
    Yaki - Strong Arms - Terran - Arteus - TerraCorp - Argon - NMMC, 24.454684105628147, 0.32713569169183554
    Paranid - OTAS - Boron - Strong Arms - Arteus - Argon - NMMC, 130.24278120462222, 0.061423749754171295
    Paranid - Yaki - Boron - Strong Arms - Arteus - TerraCorp - NMMC, 62.59932721748612, 0.12779690063131108
    Paranid - Boron - Strong Arms - Arteus - Terran - TerraCorp - NMMC, 109.93604542293971, 0.07276958134361532
    Pirates - Boron - Arteus - Terran - Strong Arms - TerraCorp - Argon - NMMC, 35.814066561875066, 0.19545392835818506
    Paranid - Pirates - Boron - Arteus - Strong Arms - Argon - NMMC, 121.00616929859778, 0.06611233168004024
    Paranid - Yaki - Duke's - Strong Arms - Arteus - TerraCorp - NMMC, 64.76870699931831, 0.12351643827140474
    Paranid - Duke's - Strong Arms - Terran - Arteus - TerraCorp - Argon - NMMC, 41.78996383870723, 0.1675043325478155
    Pirates - Duke's - Strong Arms - Terran - Arteus - TerraCorp - NMMC, 43.862589090823356, 0.18238777431571424
    Yaki - Pirates - Duke's - Strong Arms - Arteus - NMMC, 51.09289054880689, 0.1761497520169206
    Yaki - Duke's - Strong Arms - Terran - Arteus - TerraCorp - NMMC, 22.25849250064308, 0.3594133789504778
    Paranid - Pirates - Strong Arms - Arteus - Terran - TerraCorp - Argon - NMMC, 71.06988675905997, 0.09849459903786384
    Paranid - Yaki - Pirates - Strong Arms - Arteus - TerraCorp - Argon - NMMC, 45.73278599806177, 0.15306305634423129
    Paranid - Yaki - Strong Arms - Terran - Arteus - NMMC, 22.37491053465406, 0.40223624519351175
    Yaki - Pirates - Strong Arms - Arteus - Terran - NMMC, 30.42942811439952, 0.29576632088399674
    Paranid - OTAS - Pirates - Duke's - Strong Arms - TerraCorp - Argon - NMMC, 91.57213461887599, 0.07644246832438777
    Yaki - OTAS - Boron - Duke's - Strong Arms - TerraCorp - Argon - NMMC, 49.33459856216374, 0.14188825295050683
    OTAS - Boron - Duke's - Strong Arms - Terran - TerraCorp - Argon - NMMC, 77.87290691874676, 0.08989005646474528
    OTAS - Pirates - Duke's - Strong Arms - Terran - TerraCorp - NMMC, 71.43136557048803, 0.11199561895685237
    Yaki - OTAS - Pirates - Duke's - Strong Arms - TerraCorp - NMMC, 45.85796527390771, 0.17445169998747947
    Yaki - OTAS - Duke's - Strong Arms - Terran - NMMC, 42.7833307332637, 0.21036230339594786
    Paranid - OTAS - Pirates - Boron - Strong Arms - Terran - TerraCorp - NMMC, 111.33574031600082, 0.06287289220992391
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - TerraCorp - NMMC, 63.17785245244626, 0.11079832137803156
    Paranid - Yaki - OTAS - Strong Arms - Terran - NMMC, 26.489485365513726, 0.3397574500151282
    Yaki - OTAS - Pirates - Strong Arms - Terran - NMMC, 31.482320708743632, 0.28587473214769765
    Paranid - Pirates - Duke's - Strong Arms - Terran - TerraCorp - NMMC, 39.678567907855296, 0.2016201799061456
    Paranid - Yaki - Pirates - Duke's - Strong Arms - TerraCorp - NMMC, 28.52614774630792, 0.28044445647363736
    Paranid - Yaki - Duke's - Strong Arms - Terran - NMMC, 28.476896792984594, 0.31604567258245597
    Yaki - Pirates - Duke's - Strong Arms - Terran - NMMC, 18.047883506588843, 0.49867343152532645
    Paranid - Yaki - Pirates - Strong Arms - Terran - NMMC, 16.97299181278975, 0.5302541884936386
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - Argon - NMMC, 49.730261877894065, 0.14075936332665115
    Yaki - OTAS - Duke's - Strong Arms - Arteus - TerraCorp - Argon - NMMC, 48.550331500966784, 0.14418027196911332
    OTAS - Duke's - Strong Arms - Terran - Arteus - TerraCorp - Argon - NMMC, 76.92130899242773, 0.09100209151002737
    Pirates - Duke's - Strong Arms - Split - Arteus - TerraCorp - Argon - NMMC, 64.39936230276301, 0.10869672850315895
    Yaki - OTAS - Pirates - Strong Arms - Split - TerraCorp - Argon - NMMC, 35.510492417296774, 0.19712483616786952
    Yaki - Strong Arms - Split - Terran - TerraCorp - Argon - NMMC, 43.8886806666083, 0.1822793458014931
    Paranid - Pirates - Strong Arms - Split - Arteus - TerraCorp - Argon - NMMC, 41.66652585081654, 0.16800056777142652
    Paranid - Yaki - Strong Arms - Split - Arteus - TerraCorp - Argon - NMMC, 27.85754232658023, 0.25127844796706855
    Paranid - Strong Arms - Split - Terran - Arteus - TerraCorp - Argon - NMMC, 38.585075998152455, 0.18141729202075893
    Pirates - Strong Arms - Split - Arteus - Terran - TerraCorp - Argon - NMMC, 111.33574031600074, 0.06287289220992397
    Paranid - Pirates - Duke's - Strong Arms - Arteus - TerraCorp - NMMC, 65.3829696619256, 0.1223560208623964
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - TerraCorp - NMMC, 26.758295995873485, 0.26160111245796447
    Paranid - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp - NMMC, 36.90498827954663, 0.18967625587567302
    Pirates - Duke's - Strong Arms - Split - Terran - TerraCorp - Argon - NMMC, 47.32878003386944, 0.14790155155046586
    Yaki - Pirates - Duke's - Strong Arms - Split - TerraCorp - NMMC, 53.89220028207984, 0.14844448655142678
    Yaki - Duke's - Strong Arms - Split - Terran - TerraCorp - NMMC, 53.89220028207984, 0.14844448655142678
    Paranid - Pirates - Strong Arms - Split - Terran - NMMC, 59.69888313121839, 0.15075658920147575
    Paranid - Yaki - Pirates - Strong Arms - Split - TerraCorp - NMMC, 25.415368166441723, 0.3147701795074975
    Paranid - Yaki - Strong Arms - Split - Terran - NMMC, 21.62048057139835, 0.4162719681590272
    Yaki - Pirates - Strong Arms - Split - Terran - NMMC, 25.98610308778363, 0.3463389631603134
    OTAS - Pirates - Duke's - Strong Arms - Split - TerraCorp - Argon - NMMC, 32.67178942262025, 0.2142521154704053
    Paranid - Yaki - OTAS - Strong Arms - Split - TerraCorp - Argon - NMMC, 23.87846532963451, 0.2931511679401192
    Paranid - OTAS - Strong Arms - Split - Terran - Argon - NMMC, 79.03798666574907, 0.10121715313716083
    OTAS - Pirates - Strong Arms - Split - Terran - TerraCorp - Argon - NMMC, 51.506744365145394, 0.13590453223708115
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - NMMC, 20.16666401423425, 0.39669426705147437
    Yaki - OTAS - Strong Arms - Split - Terran - NMMC, 58.88395763909993, 0.15284298747650496
    Paranid - OTAS - Pirates - Strong Arms - Split - Terran - NMMC, 28.325099421660752, 0.2824350192353516
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - NMMC, 18.154370037403293, 0.4406652493872092
    Paranid - Yaki - OTAS - Strong Arms - Split - Terran - NMMC, 12.192529183156399, 0.6561394998382905
    Yaki - OTAS - Pirates - Strong Arms - Split - Terran - NMMC, 16.08170582711626, 0.49745966541128706
    Paranid - Pirates - Duke's - Strong Arms - Split - Terran - NMMC, 27.237431972006444, 0.2937134458278623
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - NMMC, 14.649507857456097, 0.5460934304307209
    Paranid - Yaki - Duke's - Strong Arms - Split - Terran - NMMC, 20.528281038111466, 0.38970627814124925
    Yaki - Pirates - Duke's - Strong Arms - Split - Terran - NMMC, 15.648916050880983, 0.5112175165352507
    Paranid - Yaki - Pirates - Strong Arms - Split - Terran - NMMC, 9.23692458026619, 0.8660891328582716
    OTAS - Pirates - Duke's - Strong Arms - Arteus - TerraCorp - Argon - NMMC, 48.06307179676422, 0.14564196041400887
    Paranid - Yaki - OTAS - Duke's - Strong Arms - TerraCorp - Argon - NMMC, 62.749184326396126, 0.11155523494279708
    Paranid - OTAS - Duke's - Strong Arms - Arteus - Terran - TerraCorp - NMMC, 59.09913966781916, 0.1184450406443338
    OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - NMMC, 71.43136557048808, 0.11199561895685227
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - NMMC, 26.634111319394794, 0.30036669532782384
    Yaki - OTAS - Strong Arms - Terran - Arteus - TerraCorp - NMMC, 46.536727916291774, 0.17190723022877863
    Paranid - OTAS - Pirates - Strong Arms - Arteus - Terran - TerraCorp - Argon - NMMC, 62.223736654069334, 0.09642622450266508
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Arteus - Argon - NMMC, 45.408837757790636, 0.1541550135534802
    Paranid - Yaki - OTAS - Strong Arms - Arteus - Terran - NMMC, 20.06997089232358, 0.39860546101040256
    Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran - NMMC, 26.634111319394794, 0.30036669532782384
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Terran - NMMC, 31.468720795130242, 0.25422069273429104
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - NMMC, 16.313911725617356, 0.4903790172799444
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Terran - NMMC, 15.667747193947049, 0.5106030816664349
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran - NMMC, 12.694742361817491, 0.6301821472219818
    Paranid - Yaki - Pirates - Strong Arms - Arteus - Terran - NMMC, 14.039710554781397, 0.5698123169124382
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Terran - NMMC, 41.572465280326895, 0.19243506359450363
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - NMMC, 22.15780064569386, 0.3610466637876678
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Terran - NMMC, 16.499455644000268, 0.4848644811448102
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran - NMMC, 11.677345596547116, 0.6850872001566457
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Terran - NMMC, 16.08170582711626, 0.49745966541128706
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Terran - NMMC, 10.312684268473225, 0.7757437144135885
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - TerraCorp - NMMC, 78.62407078252056, 0.08903125887951628
    Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - TerraCorp - NMMC, 64.31135674247234, 0.1088454723172879
    OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp - NMMC, 62.22373665406935, 0.09642622450266507
    Pirates - Boron - Duke's - Split - Strong Arms - Arteus - TerraCorp - NMMC, 91.572134618876, 0.07644246832438775
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Arteus - NMMC, 48.4738244812488, 0.14440783401994248
    Yaki - Boron - Strong Arms - Terran - TerraCorp - NMMC, 79.89272059089784, 0.11265106424508678
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus - NMMC, 53.14566535131872, 0.15052968002406417
    Paranid - Yaki - Boron - Strong Arms - Split - Arteus - NMMC, 35.4975807820009, 0.22536747078990835
    Paranid - Boron - Strong Arms - Split - Arteus - Terran - TerraCorp - NMMC, 32.320103269264, 0.21658346638566928
    OTAS - Pirates - Boron - Split - Strong Arms - Arteus - Terran - TerraCorp - NMMC, 62.22373665406935, 0.09642622450266507
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - TerraCorp - NMMC, 32.57474827289672, 0.21489037893269722
    Paranid - Yaki - Boron - Duke's - Strong Arms - Arteus - NMMC, 37.20847958649222, 0.21500475399441576
    Paranid - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp - NMMC, 28.44832365614465, 0.2460601926710731
    Pirates - Boron - Duke's - Split - Strong Arms - Terran - TerraCorp - NMMC, 63.54900550204902, 0.11015121235491715
    Yaki - Pirates - Boron - Duke's - Strong Arms - TerraCorp - NMMC, 79.64272237690523, 0.10044860046521761
    Yaki - Boron - Duke's - Strong Arms - Terran - TerraCorp - NMMC, 44.440939154343, 0.1800141975446574
    Paranid - Pirates - Boron - Split - Strong Arms - Terran - NMMC, 40.70363164027299, 0.19654265915881175
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - NMMC, 20.27134186336003, 0.394645803614008
    Paranid - Yaki - Boron - Strong Arms - Terran - NMMC, 26.126798262228984, 0.3444738964824147
    Yaki - Pirates - Boron - Strong Arms - Terran - NMMC, 29.652370937119144, 0.3035170448624635
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - TerraCorp - NMMC, 64.30206531166547, 0.1088612001196497
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - NMMC, 30.644097051147654, 0.2610616976785874
    Paranid - OTAS - Boron - Strong Arms - Split - Terran - NMMC, 79.03798666574906, 0.10121715313716086
    OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - NMMC, 92.39209235192112, 0.0865874967906131
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - NMMC, 30.767989726439268, 0.26001048723457915
    Yaki - OTAS - Boron - Strong Arms - Terran - NMMC, 55.85940208832593, 0.16111880298627315
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - NMMC, 46.65599776041416, 0.1714677722911693
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Split - NMMC, 12.483239807972412, 0.5607518647145956
    Paranid - Yaki - OTAS - Boron - Strong Arms - Terran - NMMC, 16.74333025365274, 0.47780219817707487
    Yaki - OTAS - Pirates - Boron - Strong Arms - Terran - NMMC, 20.15443257867196, 0.39693501510262547
    Paranid - Pirates - Boron - Duke's - Strong Arms - Terran - NMMC, 61.26491953268261, 0.13058043756561682
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - NMMC, 24.397008936980807, 0.3279090490422233
    Paranid - Yaki - Boron - Duke's - Strong Arms - Terran - NMMC, 23.65945369132236, 0.3381312224860958
    Yaki - Pirates - Boron - Duke's - Strong Arms - Terran - NMMC, 16.91784884391506, 0.4728733584162153
    Paranid - Yaki - Pirates - Boron - Strong Arms - Terran - NMMC, 13.028469684567778, 0.6140398829400509
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - TerraCorp - NMMC, 48.06307179676426, 0.14564196041400873
    Paranid - Yaki - OTAS - Boron - Strong Arms - Arteus - NMMC, 54.12173412355574, 0.1478149237002757
    Paranid - OTAS - Boron - Strong Arms - Arteus - Terran - TerraCorp - NMMC, 72.22772028588489, 0.09691569901823381
    Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp - NMMC, 24.181379730086668, 0.2894789328869661
    Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - NMMC, 30.524990227475765, 0.2620803459848168
    Yaki - Boron - Strong Arms - Arteus - Terran - NMMC, 122.18954134735296, 0.07365605845442492
    Paranid - Pirates - Boron - Arteus - Strong Arms - Terran - NMMC, 69.78360245193498, 0.11464011198777219
    Paranid - Yaki - Pirates - Boron - Strong Arms - Arteus - NMMC, 28.805125378706208, 0.2777283519798143
    Paranid - Yaki - Boron - Strong Arms - Arteus - Terran - NMMC, 14.260100309915321, 0.5610058713568408
    Yaki - Pirates - Boron - Strong Arms - Arteus - Terran - NMMC, 19.982063872831528, 0.400359044536793
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus - NMMC, 38.95229089327923, 0.20537944794872917
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - NMMC, 11.298065533486398, 0.6195750926787124
    Yaki - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp - NMMC, 15.621645655552376, 0.4480961964152606
    Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - NMMC, 11.117371406663619, 0.6296452411227608
    Paranid - Yaki - Pirates - Boron - Strong Arms - Arteus - Terran - NMMC, 9.572246618498486, 0.7312807827655018
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - TerraCorp - NMMC, 64.399362302763, 0.10869672850315898
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - TerraCorp - NMMC, 52.6767222550556, 0.1328860206241891
    Paranid - OTAS - Boron - Duke's - Strong Arms - Terran - TerraCorp - NMMC, 85.74534192565167, 0.08163708771573365
    Yaki - OTAS - Boron - Duke's - Strong Arms - Terran - NMMC, 29.128069913203504, 0.27464916226301933
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Terran - NMMC, 11.345809974458065, 0.6169678511942781
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Terran - NMMC, 9.385936106350373, 0.745796681405482
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - TerraCorp - NMMC, 47.87256175769142, 0.1462215461840278
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - TerraCorp - NMMC, 37.68014649778728, 0.1857742246413789
    Paranid - OTAS - Strong Arms - Split - Arteus - Terran - TerraCorp - NMMC, 55.73522257987726, 0.12559382874927805
    Pirates - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp - NMMC, 28.142110433406504, 0.24873756417679846
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - NMMC, 34.500569388668595, 0.2318802310151881
    Yaki - Strong Arms - Split - Terran - Arteus - TerraCorp - NMMC, 42.6850611233797, 0.18741919981972793
    Paranid - Pirates - Strong Arms - Split - Arteus - Terran - NMMC, 35.13111644359313, 0.2277183536949325
    Paranid - Yaki - Pirates - Strong Arms - Split - Arteus - NMMC, 19.112424608217964, 0.41857588265175727
    Paranid - Yaki - Strong Arms - Split - Arteus - Terran - NMMC, 14.532845910456718, 0.5504771776492735
    Yaki - Pirates - Strong Arms - Split - Arteus - Terran - NMMC, 20.940781361756983, 0.38202967987670067
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus - NMMC, 27.133206464991584, 0.29484167344253764
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - NMMC, 9.623949347371411, 0.7273521240956977
    Yaki - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp - NMMC, 21.082053724911578, 0.33203596249868483
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - NMMC, 11.481031389821519, 0.6097013205804692
    Paranid - Yaki - Pirates - Strong Arms - Split - Arteus - Terran - NMMC, 7.9359125394656225, 0.8820661726283788
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - NMMC, 20.57075674102546, 0.3889015898012704
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - TerraCorp - NMMC, 26.758295995873496, 0.26160111245796436
    Paranid - OTAS - Duke's - Strong Arms - Split - Terran - TerraCorp - NMMC, 36.90498827954663, 0.18967625587567302
    OTAS - Pirates - Duke's - Strong Arms - Split - Terran - NMMC, 41.57246528032688, 0.19243506359450369
    Yaki - OTAS - Duke's - Strong Arms - Split - Terran - NMMC, 29.673169072169454, 0.26960382898580326
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Terran - NMMC, 7.3269971744156175, 0.9553709157200954
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Terran - NMMC, 7.3097243590126935, 0.9576284489262838
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - NMMC, 70.5769971259678, 0.11335137970975695
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus - NMMC, 51.941040009052095, 0.15402078969935507
    Yaki - OTAS - Duke's - Strong Arms - Arteus - Terran - NMMC, 25.94572230331382, 0.3083359910538405
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - NMMC, 9.513567511153568, 0.735791278276346
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran - NMMC, 13.815843234388954, 0.5066646951071601
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran - NMMC, 7.655760152723986, 0.9143442140764217
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran - NMMC, 8.37860433862869, 0.8354613390355745
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - Argon - NMMC, 21.998853347810524, 0.31819840285887846
    Yaki - OTAS - Boron - Strong Arms - Split - Arteus - Argon - NMMC, 31.17140837008855, 0.22456476514924034
    OTAS - Boron - Strong Arms - Split - Arteus - Terran - Argon - NMMC, 391.09393482546653, 0.017898513315282912
    OTAS - Pirates - Boron - Split - Strong Arms - Arteus - Argon - NMMC, 58.272593649117255, 0.12012508044776277
    Yaki - Pirates - Boron - Strong Arms - Split - Arteus - Argon - NMMC, 42.66326530612244, 0.1640755800047836
    Yaki - Boron - Strong Arms - Arteus - Terran - Argon - NMMC, 49.27137599454306, 0.16236607641901502
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus - Argon - NMMC, 26.494084216242662, 0.2642099248596986
    Paranid - Yaki - Boron - Strong Arms - Arteus - Argon - NMMC, 31.39729908095146, 0.2547989869884556
    Paranid - Boron - Strong Arms - Arteus - Terran - Argon - NMMC, 345.3116391670684, 0.023167478568915097
    OTAS - Pirates - Boron - Split - Strong Arms - Terran - Argon - NMMC, 43.186178236047496, 0.16208889709432778
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Argon - NMMC, 50.443274353499554, 0.13876973867606135
    Paranid - Yaki - Boron - Duke's - Strong Arms - Arteus - Argon - NMMC, 23.79146113060223, 0.29422320729163265
    Paranid - Boron - Duke's - Strong Arms - Arteus - Terran - Argon - NMMC, 115.67191232260777, 0.06051598749813241
    Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Argon - NMMC, 78.34600859486912, 0.08934724468475896
    Yaki - Pirates - Boron - Duke's - Strong Arms - Argon - NMMC, 114.4303107831423, 0.06991154655833154
    Yaki - Strong Arms - Split - Terran - Arteus - Argon - NMMC, 126.12213782734344, 0.06343057719931536
    Paranid - Pirates - Strong Arms - Split - Terran - Argon - NMMC, 46.354634140105325, 0.17258252919913614
    Paranid - Yaki - Pirates - Boron - Strong Arms - Argon - NMMC, 41.184708623269216, 0.19424685198525427
    Paranid - Yaki - Strong Arms - Terran - Argon - NMMC, 31.140998192776145, 0.2890080768858512
    Yaki - Pirates - Strong Arms - Terran - Argon - NMMC, 30.360348649520684, 0.2964392834843841
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Argon - NMMC, 50.443274353499554, 0.13876973867606135
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Argon - NMMC, 14.486190959305603, 0.48321881298295033
    Paranid - OTAS - Boron - Strong Arms - Split - Terran - Argon - NMMC, 27.61603835182139, 0.253475893639115
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Argon - NMMC, 32.3223808284195, 0.2165682050823818
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Argon - NMMC, 19.372089070202275, 0.36134461155081343
    Yaki - OTAS - Boron - Strong Arms - Terran - Argon - NMMC, 22.49918817628363, 0.3555683848376712
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Argon - NMMC, 18.29557170660473, 0.38260624550327604
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Argon - NMMC, 21.42981225596783, 0.326647752037614
    Paranid - Yaki - OTAS - Strong Arms - Terran - Argon - NMMC, 19.45192586314442, 0.4112703316003073
    Yaki - OTAS - Pirates - Strong Arms - Terran - Argon - NMMC, 20.154432578671955, 0.3969350151026255
    Paranid - Pirates - Duke's - Strong Arms - Terran - Argon - NMMC, 89.87741076064336, 0.08901012982344547
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Argon - NMMC, 28.858170935104695, 0.27721784648064274
    Paranid - Yaki - Duke's - Strong Arms - Terran - Argon - NMMC, 26.834780795974723, 0.2981205645324302
    Yaki - Pirates - Duke's - Strong Arms - Terran - Argon - NMMC, 17.128023730788147, 0.46707081480858503
    Paranid - Yaki - Pirates - Strong Arms - Terran - Argon - NMMC, 14.878938333039414, 0.5376727707941101
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - Argon - NMMC, 33.32054753585693, 0.21008058143303782
    Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - Argon - NMMC, 23.79146113060223, 0.29422320729163265
    OTAS - Boron - Duke's - Strong Arms - Arteus - Terran - Argon - NMMC, 115.67191232260778, 0.060515987498132404
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Argon - NMMC, 26.045531091910647, 0.2687601176300872
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Argon - NMMC, 34.31959303593173, 0.23310299721865016
    Yaki - OTAS - Strong Arms - Terran - Arteus - Argon - NMMC, 31.330763248108518, 0.25534009295107013
    Paranid - OTAS - Pirates - Boron - Strong Arms - Arteus - Argon - NMMC, 38.80596788499428, 0.180384625909738
    Paranid - Yaki - OTAS - Boron - Strong Arms - Arteus - Argon - NMMC, 15.587446780598917, 0.4490793199507584
    Paranid - OTAS - Boron - Strong Arms - Arteus - Terran - Argon - NMMC, 32.291866028708135, 0.216772855237813
    OTAS - Pirates - Boron - Arteus - Strong Arms - Terran - Argon - NMMC, 60.09516902979666, 0.11648190882913115
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus - Argon - NMMC, 26.045531091910647, 0.2687601176300872
    Paranid - Yaki - Pirates - Boron - Strong Arms - Arteus - Argon - NMMC, 15.422551252847377, 0.45388080643970174
    Paranid - Yaki - Strong Arms - Terran - Arteus - Argon - NMMC, 18.22347243589357, 0.4389942711600303
    Yaki - Pirates - Strong Arms - Arteus - Terran - Argon - NMMC, 21.67050687876642, 0.3691653381600733
    Paranid - Pirates - Boron - Arteus - Strong Arms - Terran - Argon - NMMC, 31.481125044763694, 0.22235545870887868
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Argon - NMMC, 35.64673617613741, 0.19637141435366334
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Argon - NMMC, 26.634215710757786, 0.26281982829975503
    Paranid - OTAS - Boron - Duke's - Strong Arms - Terran - Argon - NMMC, 86.62770959797156, 0.08080555324025224
    OTAS - Pirates - Duke's - Strong Arms - Terran - Argon - NMMC, 92.39209235192104, 0.08658749679061319
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Argon - NMMC, 29.31033536834965, 0.27294126455607487
    Yaki - OTAS - Duke's - Strong Arms - Terran - Argon - NMMC, 26.820968708312527, 0.29827408871777955
    Paranid - OTAS - Pirates - Boron - Strong Arms - Terran - Argon - NMMC, 43.1861782360475, 0.16208889709432775
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Terran - Argon - NMMC, 10.060376923018307, 0.6957989798557036
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Argon - NMMC, 31.871137729146202, 0.2196344560865328
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - Argon - NMMC, 18.500350470832526, 0.37837121037442684
    Paranid - OTAS - Strong Arms - Split - Arteus - Terran - Argon - NMMC, 38.585075998152455, 0.18141729202075893
    OTAS - Pirates - Strong Arms - Split - Arteus - Terran - Argon - NMMC, 111.33574031600071, 0.06287289220992398
    Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - Argon - NMMC, 31.538536096620653, 0.221950694812054
    Yaki - OTAS - Strong Arms - Split - Terran - Argon - NMMC, 26.326939154975882, 0.30387125343008103
    Paranid - OTAS - Pirates - Strong Arms - Split - Arteus - Argon - NMMC, 28.600974632020854, 0.24474690425979384
    Paranid - Yaki - Pirates - Strong Arms - Split - Argon - NMMC, 21.339274525974517, 0.37489559404947287
    Paranid - Yaki - Strong Arms - Split - Terran - Argon - NMMC, 20.358300094522907, 0.39296011763537564
    Yaki - Pirates - Strong Arms - Split - Terran - Argon - NMMC, 21.77090575329333, 0.3674628924793275
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus - Argon - NMMC, 23.14433308136424, 0.30244984702697625
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - Argon - NMMC, 34.319094427385195, 0.20396808589489746
    Paranid - Yaki - Duke's - Strong Arms - Split - Terran - Argon - NMMC, 19.777728227655416, 0.3539334709945009
    Pirates - Duke's - Strong Arms - Split - Arteus - Terran - Argon - NMMC, 140.8738856799438, 0.04968983403995499
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Argon - NMMC, 26.138661599330653, 0.2678025412050651
    Paranid - Pirates - Strong Arms - Split - Arteus - Terran - Argon - NMMC, 26.60620966399763, 0.26309647591299323
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Argon - NMMC, 15.409783056056744, 0.4542568817832047
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Argon - NMMC, 19.45848826314036, 0.35974017638666683
    Paranid - OTAS - Duke's - Strong Arms - Split - Terran - Argon - NMMC, 43.32873904883136, 0.16155558997715166
    OTAS - Pirates - Duke's - Strong Arms - Split - Terran - Argon - NMMC, 25.61086394330419, 0.27332150978960273
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Argon - NMMC, 13.713796680730736, 0.5104348681088224
    Yaki - OTAS - Duke's - Strong Arms - Split - Terran - Argon - NMMC, 19.411105674442698, 0.36061830363514175
    Paranid - OTAS - Pirates - Strong Arms - Split - Terran - Argon - NMMC, 18.80900670183805, 0.37216213014140437
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Argon - NMMC, 12.021563621955533, 0.5822869819709292
    Paranid - Yaki - OTAS - Strong Arms - Split - Terran - Argon - NMMC, 9.788028682409024, 0.7151593264719739
    Yaki - OTAS - Pirates - Strong Arms - Split - Terran - Argon - NMMC, 11.345809974458065, 0.6169678511942781
    Paranid - Pirates - Duke's - Strong Arms - Split - Terran - Argon - NMMC, 26.119054828165517, 0.2680035723364515
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Argon - NMMC, 13.8612259486877, 0.5050058361297197
    Yaki - Pirates - Duke's - Strong Arms - Split - Terran - Argon - NMMC, 14.981310392373874, 0.4672488465069984
    Paranid - Yaki - Pirates - Strong Arms - Split - Terran - Argon - NMMC, 8.728561387881783, 0.8019649159732536
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - Argon - NMMC, 35.07653175792275, 0.19956362984544238
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus - Argon - NMMC, 26.152765169029074, 0.2676581216080975
    Paranid - OTAS - Duke's - Strong Arms - Arteus - Terran - Argon - NMMC, 85.68264086533037, 0.08169682831090701
    OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - Argon - NMMC, 35.654674404038595, 0.19632769382987583
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Argon - NMMC, 16.78786107745564, 0.41696794890686073
    Yaki - OTAS - Duke's - Strong Arms - Arteus - Terran - Argon - NMMC, 17.3221656689012, 0.40410651495887884
    Paranid - Yaki - OTAS - Strong Arms - Arteus - Terran - Argon - NMMC, 14.615406366341134, 0.4789466556414608
    Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran - Argon - NMMC, 16.78786107745564, 0.41696794890686073
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Terran - Argon - NMMC, 27.239095523922067, 0.25698356958484253
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - Argon - NMMC, 14.076626756425899, 0.49727822731426335
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Terran - Argon - NMMC, 14.37225304027373, 0.48704959343428594
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran - Argon - NMMC, 11.700460814169688, 0.5982670350489737
    Paranid - Yaki - Pirates - Strong Arms - Arteus - Terran - Argon - NMMC, 11.701355013316032, 0.5982213164231036
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Terran - Argon - NMMC, 31.292941071326517, 0.22369262077491484
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Argon - NMMC, 17.165017111474263, 0.40780617662890206
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Terran - Argon - NMMC, 13.975309558291286, 0.5008833593848397
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran - Argon - NMMC, 10.071148978467658, 0.6950547564102325
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Terran - Argon - NMMC, 12.968291580688348, 0.5397781162187938
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Arteus - NMMC, 39.891397287111275, 0.17547643040976324
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Arteus - NMMC, 17.202314380306248, 0.40692198998605794
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - Terran - NMMC, 32.32010326926401, 0.21658346638566922
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - NMMC, 39.89139728711129, 0.17547643040976318
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - NMMC, 25.93896118131567, 0.2698643153466853
    Yaki - Boron - Strong Arms - Split - Arteus - Terran - NMMC, 118.54732270617387, 0.06748359910099737
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Arteus - NMMC, 26.1344691029585, 0.2678455021383074
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Arteus - NMMC, 12.765169570858525, 0.5483671768826501
    Paranid - Yaki - Boron - Strong Arms - Split - Terran - NMMC, 19.10121196002409, 0.41882159188342466
    Yaki - Pirates - Boron - Strong Arms - Split - Terran - NMMC, 22.85752457059707, 0.34999415511034176
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - NMMC, 19.32121129671662, 0.36229612587434185
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Arteus - NMMC, 25.938961181315666, 0.2698643153466853
    Paranid - Boron - Duke's - Strong Arms - Split - Arteus - Terran - NMMC, 121.9740563581152, 0.05738925316583746
    Pirates - Boron - Duke's - Split - Strong Arms - Arteus - Terran - NMMC, 121.97405635811516, 0.057389253165837484
    Yaki - Boron - Duke's - Strong Arms - Split - Arteus - Terran - NMMC, 67.29872154661678, 0.10401386295505197
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus - Terran - NMMC, 21.92070608506074, 0.3193327793747755
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Split - NMMC, 15.776754359710782, 0.4436907516210022
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Split - NMMC, 20.3829067762192, 0.34342501179306384
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Terran - NMMC, 43.32873904883135, 0.1615555899771517
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Terran - NMMC, 31.292941071326517, 0.22369262077491484
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Split - NMMC, 16.405435649084097, 0.4266878460122334
    Yaki - OTAS - Boron - Strong Arms - Split - Terran - NMMC, 34.74415005158013, 0.2302545892797331
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Terran - NMMC, 18.809006701838047, 0.3721621301414045
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Terran - NMMC, 9.788028682409022, 0.715159326471974
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Terran - NMMC, 12.968291580688348, 0.5397781162187938
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Terran - NMMC, 24.51204026010337, 0.285573943487415
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Split - NMMC, 13.374189928587885, 0.5233961860401884
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Terran - NMMC, 18.67374744656187, 0.37485780612765063
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Terran - NMMC, 15.178122017978737, 0.46119012561029515
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Terran - NMMC, 8.419628759159142, 0.8313905755506352
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - NMMC, 22.813203218763622, 0.3068398564144895
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - NMMC, 18.732764572210172, 0.37367682559702986
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - Terran - NMMC, 41.21246827507494, 0.16985151079227057
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - NMMC, 31.47340222465379, 0.22241001942004066
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - NMMC, 15.861543456245384, 0.4413189686936673
    Yaki - OTAS - Boron - Strong Arms - Arteus - Terran - NMMC, 30.81177655462883, 0.25964098453771783
    Paranid - OTAS - Pirates - Boron - Strong Arms - Arteus - Terran - NMMC, 51.506744365145416, 0.1359045322370811
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - NMMC, 25.980760068010913, 0.26943014683465033
    Paranid - Yaki - OTAS - Boron - Strong Arms - Arteus - Terran - NMMC, 11.675149460407816, 0.5995640590073857
    Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - Terran - NMMC, 15.861543456245384, 0.4413189686936673
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - NMMC, 20.029863669648194, 0.3494781649765941
    Paranid - Yaki - Boron - Duke's - Strong Arms - Arteus - Terran - NMMC, 11.939735135482497, 0.5862776619891177
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - NMMC, 25.610863943304192, 0.27332150978960273
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Strong Arms - NMMC, 15.181782664245528, 0.4610789229966803
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Terran - NMMC, 12.709176147014658, 0.5507831443224017
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Terran - NMMC, 10.07114897846766, 0.6950547564102324
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - NMMC, 14.466697286605923, 0.48386994358975016
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - NMMC, 18.053305555252564, 0.3877406261460726
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - Terran - NMMC, 36.90498827954663, 0.18967625587567302
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - NMMC, 28.142110433406504, 0.24873756417679846
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - NMMC, 14.998693990247087, 0.466707301619178
    Yaki - OTAS - Strong Arms - Split - Arteus - Terran - NMMC, 42.685061123379704, 0.1874191998197279
    Paranid - OTAS - Pirates - Strong Arms - Split - Arteus - Terran - NMMC, 23.737982547570656, 0.29488605385786587
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - NMMC, 15.402320253068174, 0.45447698041505047
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - Terran - NMMC, 10.502101094821395, 0.6665332905100021
    Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - Terran - NMMC, 14.998693990247087, 0.466707301619178
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - NMMC, 16.155310475535792, 0.4332940558833701
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - Terran - NMMC, 12.631596005185576, 0.5541659183151781
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Terran - NMMC, 12.63808671324863, 0.5538813080513074
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - NMMC, 8.490151854930206, 0.824484664068184
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Terran - NMMC, 9.971876303402253, 0.7019742109728845
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Terran - NMMC, 8.37860433862869, 0.8354613390355745
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - NMMC, 23.18661870335385, 0.30189826682178017
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - NMMC, 13.815843234388954, 0.5066646951071601
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus - Terran - NMMC, 11.822079962133456, 0.5921123882109789
    Paranid - OTAS - Boron - Split - Arteus - TerraCorp - Argon - NMMC, 15.857975236707937, 0.4414182703348184
    Yaki - OTAS - Boron - Split - Arteus - TerraCorp - Argon - NMMC, 20.217382686685497, 0.346236706723169
    OTAS - Boron - Split - Arteus - Terran - TerraCorp - Argon - NMMC, 20.896837385967736, 0.3349789190923461
    Pirates - Boron - Duke's - Split - Arteus - TerraCorp - Argon - NMMC, 33.56326836785261, 0.20856133327899326
    Yaki - Pirates - Boron - Split - Arteus - TerraCorp - Argon - NMMC, 29.004448213276206, 0.24134229165566026
    Yaki - Boron - Terran - TerraCorp - Argon - NMMC, 46.32885880826814, 0.19426336481212447
    Paranid - Pirates - Boron - Split - Arteus - TerraCorp - Argon - NMMC, 20.519314033541775, 0.3411420083808597
    Paranid - Yaki - Boron - Arteus - TerraCorp - Argon - NMMC, 23.287447808604945, 0.343532707652228
    Paranid - Boron - Split - Arteus - Terran - TerraCorp - Argon - NMMC, 16.91838467648986, 0.41375108403388805
    OTAS - Pirates - Boron - Split - Terran - TerraCorp - Argon - NMMC, 22.917131889437734, 0.30544834466071324
    Paranid - Pirates - Boron - Duke's - Split - TerraCorp - Argon - NMMC, 100.13898929826289, 0.06990284252970216
    Paranid - Yaki - Boron - Duke's - Arteus - TerraCorp - Argon - NMMC, 16.821916105000852, 0.41612382063414444
    Paranid - Boron - Duke's - Arteus - Terran - TerraCorp - Argon - NMMC, 16.162190731428346, 0.4331096023008862
    Pirates - Boron - Duke's - Split - Terran - TerraCorp - Argon - NMMC, 56.7339936166066, 0.12338281784469746
    Yaki - Pirates - Boron - Duke's - Split - TerraCorp - Argon - NMMC, 164.3873873873871, 0.04258234230284438
    Yaki - Boron - Duke's - Terran - TerraCorp - Argon - NMMC, 41.09967290550508, 0.19464875105924365
    Paranid - Pirates - Split - Terran - TerraCorp - Argon - NMMC, 44.344313824736346, 0.18040644470492187
    Paranid - Yaki - Pirates - Boron - Split - TerraCorp - Argon - NMMC, 35.53181076672102, 0.19700656535512615
    Paranid - Yaki - Terran - TerraCorp - Argon - NMMC, 29.441850370946536, 0.30568730859665244
    Yaki - Pirates - Terran - TerraCorp - Argon - NMMC, 26.623219756078417, 0.3380507723129614
    Paranid - OTAS - Boron - Duke's - Split - TerraCorp - Argon - NMMC, 52.40368831695206, 0.13357838398057129
    Yaki - OTAS - Boron - Duke's - Split - TerraCorp - Argon - NMMC, 63.975166881009145, 0.10941745588596395
    Paranid - OTAS - Boron - Split - Terran - TerraCorp - Argon - NMMC, 18.900630779283453, 0.37035800983280087
    OTAS - Pirates - Boron - Duke's - Split - TerraCorp - Argon - NMMC, 30.010464984553575, 0.23325196739213835
    Yaki - OTAS - Pirates - Boron - Split - TerraCorp - Argon - NMMC, 26.731390769317002, 0.26186441477765476
    Yaki - OTAS - Terran - TerraCorp - Argon - NMMC, 35.34766266764871, 0.2546137232501396
    Paranid - OTAS - Pirates - Boron - Split - TerraCorp - Argon - NMMC, 24.66309806173054, 0.28382484562480104
    Paranid - Yaki - OTAS - Boron - Split - TerraCorp - Argon - NMMC, 22.907328197067685, 0.3055790679637643
    Paranid - Yaki - OTAS - Terran - TerraCorp - Argon - NMMC, 20.673855054030906, 0.38696217899816376
    Yaki - OTAS - Pirates - Terran - TerraCorp - Argon - NMMC, 20.1093863861002, 0.3978241725729471
    Paranid - Pirates - Duke's - Terran - TerraCorp - Argon - NMMC, 50.74245988645758, 0.15765889193982657
    Paranid - Yaki - Pirates - Duke's - TerraCorp - Argon - NMMC, 142.17088246672324, 0.05627031260689047
    Paranid - Yaki - Duke's - Terran - TerraCorp - Argon - NMMC, 24.188779660510967, 0.3307318563515745
    Yaki - Pirates - Duke's - Terran - TerraCorp - Argon - NMMC, 15.546295145072655, 0.5145920571651807
    Paranid - Yaki - Pirates - Terran - TerraCorp - Argon - NMMC, 17.0772989132305, 0.46845815843874844
    Paranid - OTAS - Boron - Duke's - Arteus - TerraCorp - Argon - NMMC, 16.592617158287403, 0.4218743754057965
    Yaki - OTAS - Boron - Duke's - Arteus - TerraCorp - Argon - NMMC, 14.277589271287768, 0.4902788465891087
    Paranid - OTAS - Boron - Arteus - Terran - TerraCorp - Argon - NMMC, 15.04176758941156, 0.4653708387920813
    OTAS - Pirates - Boron - Duke's - Arteus - TerraCorp - Argon - NMMC, 14.339181960850777, 0.48817289710888595
    Yaki - Pirates - Duke's - Arteus - TerraCorp - Argon - NMMC, 38.816902202756765, 0.20609578678413557
    Yaki - Boron - Arteus - Terran - TerraCorp - Argon - NMMC, 13.37343036336491, 0.598201043609211
    Paranid - Pirates - Boron - Arteus - Terran - TerraCorp - Argon - NMMC, 15.481941467086951, 0.45213967607882355
    Paranid - Yaki - OTAS - Boron - Arteus - TerraCorp - Argon - NMMC, 14.121034077555816, 0.4957144045934926
    Paranid - Yaki - Arteus - Terran - TerraCorp - Argon - NMMC, 15.4670195834401, 0.5172295772202468
    Yaki - Pirates - Arteus - Terran - TerraCorp - Argon - NMMC, 17.117843067727076, 0.46734860042517307
    Paranid - Pirates - Duke's - Arteus - TerraCorp - Argon - NMMC, 68.80417545351864, 0.11627201325019121
    Paranid - Yaki - Pirates - Boron - Arteus - TerraCorp - Argon - NMMC, 15.308714918759229, 0.45725588575839454
    Yaki - Duke's - Arteus - Terran - TerraCorp - Argon - NMMC, 19.15951436819854, 0.41754711764921393
    Pirates - Boron - Duke's - Terran - Arteus - TerraCorp - Argon - NMMC, 14.671086629574742, 0.4771289391672622
    Paranid - Yaki - Pirates - Arteus - Terran - TerraCorp - Argon - NMMC, 11.873391558556825, 0.589553537881541
    Paranid - OTAS - Pirates - Boron - Duke's - TerraCorp - Argon - NMMC, 37.62144826160536, 0.1860640757720075
    Yaki - OTAS - Pirates - Boron - Duke's - TerraCorp - Argon - NMMC, 21.577323323679824, 0.32441465954759635
    Yaki - OTAS - Duke's - Terran - TerraCorp - Argon - NMMC, 20.54981359716279, 0.3892979350968186
    OTAS - Pirates - Duke's - Terran - TerraCorp - Argon - NMMC, 42.369395549627264, 0.18881553291525252
    Paranid - OTAS - Pirates - Boron - Terran - TerraCorp - Argon - NMMC, 27.644107125592182, 0.2532185238683142
    Paranid - Yaki - Pirates - Duke's - Terran - TerraCorp - Argon - NMMC, 11.63633551017026, 0.601563954037071
    OTAS - Pirates - Duke's - Split - Arteus - TerraCorp - Argon - NMMC, 29.481949738251537, 0.23743341475539548
    Yaki - OTAS - Duke's - Split - Arteus - TerraCorp - Argon - NMMC, 63.07219705319561, 0.11098392520076861
    Paranid - OTAS - Split - Terran - Arteus - TerraCorp - Argon - NMMC, 26.573925233929067, 0.26341610952764094
    Pirates - Duke's - Split - Terran - Arteus - TerraCorp - Argon - NMMC, 23.725074652053003, 0.2950464899546383
    Yaki - Pirates - Duke's - Split - Arteus - TerraCorp - Argon - NMMC, 30.700684493945264, 0.22800794560070894
    Yaki - Split - Terran - Arteus - TerraCorp - Argon - NMMC, 26.948912820085077, 0.29685798656922385
    Paranid - OTAS - Pirates - Split - Arteus - TerraCorp - Argon - NMMC, 51.5731066310544, 0.13572965557566385
    Paranid - Yaki - OTAS - Split - Arteus - TerraCorp - Argon - NMMC, 36.12659335115363, 0.19376308006568432
    Paranid - Yaki - Split - Terran - TerraCorp - Argon - NMMC, 21.365906274075865, 0.3744283016773658
    Yaki - Pirates - Split - Terran - TerraCorp - Argon - NMMC, 20.220372899546298, 0.39564057694403365
    Paranid - Pirates - Duke's - Split - Arteus - TerraCorp - Argon - NMMC, 27.437678521266527, 0.2551236247838682
    Paranid - Yaki - Duke's - Split - Arteus - TerraCorp - Argon - NMMC, 52.60066621664771, 0.1330781623785699
    Yaki - Duke's - Split - Terran - Arteus - TerraCorp - Argon - NMMC, 18.79892150842849, 0.37236178665151365
    Yaki - Pirates - Duke's - Split - Terran - TerraCorp - Argon - NMMC, 14.033775167384634, 0.4987966471251752
    Paranid - Pirates - Split - Arteus - Terran - TerraCorp - Argon - NMMC, 21.555124778633413, 0.324748757981618
    Paranid - Yaki - Pirates - Split - Arteus - TerraCorp - Argon - NMMC, 28.495027699280328, 0.24565689403336824
    Paranid - OTAS - Pirates - Duke's - Split - TerraCorp - Argon - NMMC, 30.12371760659431, 0.23237503721876768
    Paranid - Yaki - OTAS - Duke's - Split - TerraCorp - Argon - NMMC, 62.74918432639613, 0.11155523494279707
    Paranid - OTAS - Duke's - Split - Terran - TerraCorp - Argon - NMMC, 33.245820210363036, 0.21055278395020718
    OTAS - Pirates - Duke's - Split - Terran - TerraCorp - Argon - NMMC, 20.077372217695892, 0.348651204156603
    Yaki - OTAS - Pirates - Duke's - Split - TerraCorp - Argon - NMMC, 26.98309636754519, 0.25942167291147067
    Yaki - OTAS - Split - Terran - TerraCorp - Argon - NMMC, 22.116242202045168, 0.3617251035196301
    Paranid - OTAS - Pirates - Split - Terran - TerraCorp - Argon - NMMC, 21.634777528869854, 0.32355313063233804
    Paranid - Yaki - OTAS - Pirates - Split - TerraCorp - Argon - NMMC, 30.66166116374347, 0.22829813305344648
    Paranid - Yaki - OTAS - Split - Terran - TerraCorp - Argon - NMMC, 12.066135963395261, 0.5801360121612857
    Yaki - OTAS - Pirates - Split - Terran - TerraCorp - Argon - NMMC, 12.53514986642062, 0.5584297016465454
    Paranid - Pirates - Duke's - Split - Terran - TerraCorp - Argon - NMMC, 24.83320461288958, 0.28188065572361437
    Paranid - Yaki - Pirates - Duke's - Split - TerraCorp - Argon - NMMC, 42.07720977370872, 0.16636084088384206
    Paranid - Yaki - Duke's - Split - Terran - TerraCorp - Argon - NMMC, 19.973663926951488, 0.3504614889687085
    Paranid - Yaki - Pirates - Split - Terran - TerraCorp - Argon - NMMC, 11.492817044247644, 0.6090760840488296
    Paranid - OTAS - Pirates - Duke's - Arteus - TerraCorp - Argon - NMMC, 36.9521045292604, 0.18943440675908116
    Paranid - Yaki - OTAS - Duke's - Arteus - TerraCorp - Argon - NMMC, 36.12659335115363, 0.19376308006568432
    Yaki - OTAS - Arteus - Terran - TerraCorp - Argon - NMMC, 21.298389275282208, 0.37561525881604485
    OTAS - Pirates - Duke's - Arteus - Terran - TerraCorp - Argon - NMMC, 18.9185019958407, 0.3700081540038939
    Yaki - OTAS - Pirates - Duke's - Arteus - TerraCorp - Argon - NMMC, 21.144175879224267, 0.3310604319593285
    Paranid - Yaki - OTAS - Arteus - Terran - TerraCorp - Argon - NMMC, 13.798891002669261, 0.5072871434846408
    Yaki - OTAS - Pirates - Arteus - Terran - TerraCorp - Argon - NMMC, 15.083216551938568, 0.46409199098187887
    Paranid - Pirates - Duke's - Arteus - Terran - TerraCorp - Argon - NMMC, 17.21241825730562, 0.4066831223456313
    Paranid - Yaki - Pirates - Duke's - Arteus - TerraCorp - Argon - NMMC, 20.12072902877454, 0.34789991903321893
    Paranid - Yaki - Duke's - Arteus - Terran - TerraCorp - Argon - NMMC, 11.193278041513977, 0.6253753345568815
    Yaki - Pirates - Duke's - Arteus - Terran - TerraCorp - Argon - NMMC, 9.152483560024155, 0.764819729431071
    Paranid - OTAS - Pirates - Duke's - Terran - TerraCorp - Argon - NMMC, 26.980737941991183, 0.2594443493372961
    Paranid - Yaki - OTAS - Pirates - Duke's - TerraCorp - Argon - NMMC, 38.013999101994735, 0.18414268862422012
    Paranid - Yaki - OTAS - Duke's - Terran - TerraCorp - Argon - NMMC, 14.586923616278682, 0.47988185748694506
    Yaki - OTAS - Pirates - Duke's - Terran - TerraCorp - Argon - NMMC, 10.552766237920538, 0.6633331812890964
    Paranid - Yaki - OTAS - Pirates - Terran - TerraCorp - Argon - NMMC, 14.97399554161301, 0.46747709925162395
    Paranid - OTAS - Boron - Duke's - Split - Arteus - TerraCorp - NMMC, 35.65465147288832, 0.19632782009726774
    Yaki - OTAS - Boron - Duke's - Split - Arteus - TerraCorp - NMMC, 87.09974927995695, 0.08036762514092348
    Paranid - OTAS - Boron - Split - Arteus - Terran - TerraCorp - NMMC, 22.852253547373742, 0.30631552312723503
    OTAS - Pirates - Boron - Duke's - Split - Arteus - TerraCorp - NMMC, 32.973985249748495, 0.21228856466639537
    Yaki - Pirates - Boron - Duke's - Split - Arteus - TerraCorp - NMMC, 26.983096367545205, 0.2594216729114705
    Yaki - Boron - Split - Arteus - Terran - TerraCorp - NMMC, 27.821916411049088, 0.28754309666543715
    Paranid - OTAS - Pirates - Boron - Split - Arteus - TerraCorp - NMMC, 35.65465147288832, 0.19632782009726774
    Paranid - Yaki - OTAS - Boron - Split - Arteus - TerraCorp - NMMC, 25.718737256932975, 0.2721751044800233
    Paranid - Yaki - Boron - Split - Terran - TerraCorp - NMMC, 19.12224444646599, 0.4183609315525977
    Yaki - Pirates - Boron - Split - Terran - TerraCorp - NMMC, 20.946723099215102, 0.38192131352038394
    Paranid - Pirates - Boron - Duke's - Split - Arteus - TerraCorp - NMMC, 19.713981800326014, 0.3550779376231462
    Paranid - Yaki - Boron - Duke's - Split - Arteus - TerraCorp - NMMC, 29.493153186653778, 0.23734322185556053
    Paranid - Boron - Duke's - Split - Arteus - Terran - TerraCorp - NMMC, 24.412011851603474, 0.28674408494276615
    Pirates - Boron - Duke's - Split - Arteus - Terran - TerraCorp - NMMC, 23.39776583253336, 0.29917386344070807
    Yaki - Boron - Duke's - Split - Arteus - Terran - TerraCorp - NMMC, 18.3942737127108, 0.3805532150564262
    Paranid - Pirates - Boron - Split - Arteus - Terran - TerraCorp - NMMC, 17.459785232154328, 0.40092131185603846
    Paranid - Yaki - Pirates - Boron - Split - Arteus - TerraCorp - NMMC, 19.752523015233876, 0.3543851078974236
    Paranid - OTAS - Pirates - Boron - Duke's - Split - TerraCorp - NMMC, 27.49552235940967, 0.25458690722434746
    Paranid - Yaki - OTAS - Boron - Duke's - Split - TerraCorp - NMMC, 52.6767222550556, 0.1328860206241891
    Paranid - OTAS - Boron - Duke's - Split - Terran - TerraCorp - NMMC, 33.08020081457549, 0.21160693791543506
    OTAS - Pirates - Boron - Duke's - Split - Terran - TerraCorp - NMMC, 23.702628151116222, 0.29532590037575013
    Yaki - OTAS - Pirates - Boron - Duke's - Split - TerraCorp - NMMC, 30.700684493945285, 0.22800794560070878
    Yaki - OTAS - Boron - Split - Terran - TerraCorp - NMMC, 27.791390908794853, 0.28785892819305864
    Paranid - OTAS - Pirates - Boron - Split - Terran - TerraCorp - NMMC, 20.70379536186328, 0.33810225988294457
    Paranid - Yaki - OTAS - Boron - Split - Terran - TerraCorp - NMMC, 11.539639540670604, 0.6066047362509911
    Yaki - OTAS - Pirates - Boron - Split - Terran - TerraCorp - NMMC, 13.827984850905628, 0.5062198198417576
    Paranid - Pirates - Boron - Duke's - Split - Terran - TerraCorp - NMMC, 22.39631135499219, 0.31255146836667297
    Paranid - Yaki - Pirates - Boron - Duke's - Split - TerraCorp - NMMC, 33.18757793404764, 0.21092229188616365
    Paranid - Yaki - Boron - Duke's - Split - Terran - TerraCorp - NMMC, 18.062814559960806, 0.3875365036142623
    Yaki - Pirates - Boron - Duke's - Split - Terran - TerraCorp - NMMC, 14.033775167384634, 0.4987966471251752
    Paranid - Yaki - Pirates - Boron - Split - Terran - TerraCorp - NMMC, 10.551583700225759, 0.6634075224035071
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - TerraCorp - NMMC, 21.70967098686331, 0.32243694546249707
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - TerraCorp - NMMC, 21.242762232433094, 0.3295240008529831
    Yaki - OTAS - Boron - Duke's - Arteus - Terran - TerraCorp - NMMC, 11.583221491249843, 0.6043223817560526
    OTAS - Pirates - Boron - Duke's - Arteus - Terran - TerraCorp - NMMC, 17.53610995323315, 0.3991763292239966
    Paranid - OTAS - Pirates - Boron - Arteus - Terran - TerraCorp - NMMC, 34.99545790807747, 0.20002595817968413
    Paranid - Yaki - OTAS - Pirates - Boron - Arteus - TerraCorp - NMMC, 35.446927628275105, 0.197478327978312
    Paranid - Yaki - OTAS - Boron - Arteus - Terran - TerraCorp - NMMC, 10.718485902134745, 0.6530773155755
    Yaki - OTAS - Pirates - Boron - Arteus - Terran - TerraCorp - NMMC, 13.920983464544769, 0.5028380371134151
    Paranid - Yaki - Boron - Duke's - Arteus - Terran - TerraCorp - NMMC, 9.043871937293787, 0.7740047679284833
    Paranid - Yaki - OTAS - Boron - Duke's - Terran - TerraCorp - NMMC, 12.942752089249973, 0.5408432419727857
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - TerraCorp - NMMC, 23.444809925533868, 0.2985735445172564
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - TerraCorp - NMMC, 39.49822958166616, 0.17722313314136948
    Paranid - OTAS - Duke's - Split - Arteus - Terran - TerraCorp - NMMC, 27.537989793152114, 0.25419429858822495
    OTAS - Pirates - Duke's - Split - Arteus - Terran - TerraCorp - NMMC, 20.81704493631382, 0.33626290481743687
    Yaki - OTAS - Duke's - Split - Arteus - Terran - TerraCorp - NMMC, 16.59707836141662, 0.42176097790036127
    Paranid - OTAS - Pirates - Split - Arteus - Terran - TerraCorp - NMMC, 27.537989793152114, 0.25419429858822495
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - TerraCorp - NMMC, 39.498229581666166, 0.17722313314136945
    Paranid - Yaki - OTAS - Split - Arteus - Terran - TerraCorp - NMMC, 12.675159147959294, 0.552261310354198
    Yaki - OTAS - Pirates - Split - Arteus - Terran - TerraCorp - NMMC, 16.597078361416624, 0.4217609779003612
    Paranid - Yaki - Duke's - Split - Arteus - Terran - TerraCorp - NMMC, 11.822079962133456, 0.5921123882109789
    Paranid - OTAS - Pirates - Duke's - Split - Terran - TerraCorp - NMMC, 15.848855223051725, 0.4416722786273353
    Paranid - Yaki - OTAS - Duke's - Split - Terran - TerraCorp - NMMC, 13.024174651015853, 0.537462080136803
    Paranid - Yaki - OTAS - Duke's - Arteus - Terran - TerraCorp - NMMC, 11.722896790980052, 0.5971220360300373
    OTAS - Pirates - Boron - Duke's - Split - Arteus - Argon - NMMC, 20.21893449158379, 0.34621013302722636
    Paranid - Yaki - OTAS - Boron - Split - Arteus - Argon - NMMC, 12.51871110230645, 0.5591629955187893
    Paranid - OTAS - Boron - Split - Arteus - Terran - Argon - NMMC, 16.918384676489858, 0.4137510840338881
    Pirates - Boron - Duke's - Split - Arteus - Terran - Argon - NMMC, 88.67247954969882, 0.07894219306314386
    Yaki - Pirates - Boron - Duke's - Split - Arteus - Argon - NMMC, 34.24029478228608, 0.20443749227361763
    Yaki - OTAS - Boron - Split - Terran - Argon - NMMC, 21.55086497277996, 0.3712147985755784
    Paranid - OTAS - Pirates - Boron - Split - Arteus - Argon - NMMC, 15.237437173289072, 0.4593948391971625
    Paranid - Yaki - Pirates - Boron - Split - Arteus - Argon - NMMC, 15.837626559511483, 0.4419854183135833
    Paranid - Yaki - Boron - Split - Arteus - Terran - Argon - NMMC, 13.194155509084489, 0.5305379336464796
    Yaki - Pirates - Boron - Split - Terran - Argon - NMMC, 29.121471232713755, 0.2747113954535772
    Paranid - Pirates - Boron - Duke's - Split - Arteus - Argon - NMMC, 25.636285349783662, 0.273050479213014
    Paranid - Yaki - Boron - Duke's - Split - Arteus - Argon - NMMC, 38.012728733701, 0.18414884259003483
    Yaki - Boron - Duke's - Split - Arteus - Terran - Argon - NMMC, 56.95305164319249, 0.12290825158684363
    Yaki - Pirates - Boron - Duke's - Split - Terran - Argon - NMMC, 23.07883742544417, 0.30330817237278057
    Paranid - Pirates - Boron - Split - Arteus - Terran - Argon - NMMC, 20.952394287314476, 0.3340906964622232
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Argon - NMMC, 19.70836124941431, 0.3551792009195095
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Argon - NMMC, 26.634215710757786, 0.26281982829975503
    Paranid - OTAS - Boron - Duke's - Split - Terran - Argon - NMMC, 33.55115470197394, 0.20863663448185774
    OTAS - Pirates - Boron - Duke's - Split - Terran - Argon - NMMC, 24.07182464366789, 0.2907964021680988
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Argon - NMMC, 19.10210922429877, 0.36645167912115567
    Yaki - OTAS - Boron - Duke's - Split - Terran - Argon - NMMC, 19.102109224298765, 0.3664516791211557
    Paranid - Yaki - OTAS - Boron - Split - Terran - Argon - NMMC, 10.55632225749408, 0.6631097298143398
    Yaki - OTAS - Pirates - Boron - Split - Terran - Argon - NMMC, 11.169669005330466, 0.6266971739860342
    Paranid - Pirates - Boron - Duke's - Split - Terran - Argon - NMMC, 44.47382764595814, 0.15739594207462312
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Argon - NMMC, 39.06616414203285, 0.17918319225174248
    Paranid - Yaki - Boron - Duke's - Split - Terran - Argon - NMMC, 33.66011600475959, 0.20796125595675874
    Paranid - Yaki - Pirates - Boron - Split - Terran - Argon - NMMC, 12.683428560599598, 0.5519012439384987
    Paranid - OTAS - Pirates - Boron - Duke's - Arteus - Terran - Argon - NMMC, 11.156140999592111, 0.5378203807409184
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - Argon - NMMC, 13.790042240842048, 0.5076126583041246
    Yaki - OTAS - Boron - Duke's - Arteus - Terran - Argon - NMMC, 11.841380247683464, 0.5911473032351456
    Yaki - OTAS - Pirates - Boron - Arteus - Terran - Argon - NMMC, 10.310816862454278, 0.6788986841081177
    Paranid - Yaki - OTAS - Boron - Arteus - Terran - Argon - NMMC, 8.90419467052536, 0.7861463342857249
    Paranid - Yaki - Pirates - Boron - Duke's - Arteus - Terran - Argon - NMMC, 7.669640072359803, 0.7823052898692172
    Paranid - Yaki - OTAS - Boron - Duke's - Terran - Argon - NMMC, 13.145357300023695, 0.5325073971163479
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - Argon - NMMC, 19.353399086938165, 0.36169356961818566
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - Argon - NMMC, 26.152765169029067, 0.26765812160809754
    Yaki - OTAS - Duke's - Split - Arteus - Terran - Argon - NMMC, 18.798921508428485, 0.3723617866515137
    Yaki - OTAS - Pirates - Duke's - Split - Arteus - Argon - NMMC, 18.768931153058727, 0.3729567732395474
    Paranid - OTAS - Pirates - Split - Arteus - Terran - Argon - NMMC, 21.55512477863341, 0.32474875798161806
    Paranid - Yaki - OTAS - Pirates - Split - Arteus - Argon - NMMC, 20.480483951854467, 0.34178879837290976
    Paranid - Yaki - OTAS - Split - Arteus - Terran - Argon - NMMC, 11.774822667405896, 0.5944887832049335
    Yaki - OTAS - Pirates - Split - Arteus - Terran - Argon - NMMC, 13.626845959515531, 0.5136918712368616
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Terran - Argon - NMMC, 8.712044417337903, 0.6887017228768205
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Terran - Argon - NMMC, 7.679635614810575, 0.7812870689370586
    Paranid - Yaki - OTAS - Duke's - Arteus - Terran - Argon - NMMC, 12.891113877486552, 0.5430097093646051
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Arteus - NMMC, 15.160962055904339, 0.46171212448051047
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Arteus - NMMC, 18.732764572210172, 0.37367682559702986
    Yaki - OTAS - Boron - Duke's - Split - Arteus - Terran - NMMC, 18.3942737127108, 0.3805532150564262
    Yaki - OTAS - Pirates - Boron - Duke's - Split - Arteus - NMMC, 17.61036778269341, 0.3974931180528354
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Arteus - NMMC, 15.662365454969926, 0.44693121355936594
    Paranid - Yaki - OTAS - Boron - Split - Arteus - Terran - NMMC, 9.906950610743875, 0.7065746338140265
    Yaki - OTAS - Pirates - Boron - Split - Arteus - Terran - NMMC, 13.542546978231265, 0.5168894751668228
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Arteus - Terran - NMMC, 7.497968611437646, 0.800216740151113
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Terran - NMMC, 12.709176147014658, 0.5507831443224017
    Paranid - Yaki - OTAS - Boron - Duke's - Arteus - Terran - NMMC, 10.038336806469381, 0.6973266722320701
    Paranid - Yaki - OTAS - Duke's - Split - Arteus - Terran - NMMC, 11.822079962133456, 0.5921123882109789
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - TerraCorp - Argon, 14.806762656482517, 0.47275695318418204
    Yaki - OTAS - Boron - Strong Arms - Split - Arteus - TerraCorp - Argon, 19.19881053525913, 0.36460592113997436
    OTAS - Boron - Strong Arms - Split - Arteus - Terran - TerraCorp - Argon, 23.43326415130505, 0.29872065431439926
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - TerraCorp - Argon, 17.98322087538066, 0.38925173907990646
    Yaki - Pirates - Boron - Strong Arms - Split - Arteus - TerraCorp - Argon, 23.80756434950096, 0.29402419740374364
    Yaki - Boron - Strong Arms - Split - Terran - TerraCorp - Argon, 31.116091051056536, 0.25710170300225943
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus - TerraCorp - Argon, 17.171284634760703, 0.4076573272700602
    Paranid - Yaki - Boron - Strong Arms - Split - Arteus - TerraCorp - Argon, 13.549421032058076, 0.516627240635443
    Paranid - Boron - Strong Arms - Split - Arteus - Terran - TerraCorp - Argon, 16.363662240015163, 0.42777710131919183
    OTAS - Pirates - Boron - Split - Strong Arms - Terran - TerraCorp - Argon, 23.095097007132846, 0.3030946351010378
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - TerraCorp - Argon, 23.807564349500964, 0.2940241974037436
    Paranid - Yaki - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 12.33870331251886, 0.5673205540891638
    Paranid - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp - Argon, 15.199153432246371, 0.46055196634497225
    Pirates - Boron - Duke's - Split - Strong Arms - Terran - TerraCorp - Argon, 34.75635289860011, 0.20140202916060101
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - TerraCorp - Argon, 26.143385753931533, 0.26775414882700554
    Yaki - Boron - Duke's - Strong Arms - Terran - TerraCorp - Argon, 27.065702735954876, 0.29557702890797527
    Paranid - Pirates - Strong Arms - Split - Terran - TerraCorp - Argon, 27.38029197863633, 0.29218096016806755
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - TerraCorp - Argon, 15.37859058430801, 0.45517825327521577
    Paranid - Yaki - Strong Arms - Terran - TerraCorp - Argon, 21.92251550656224, 0.4105368290106105
    Yaki - Pirates - Strong Arms - Terran - TerraCorp - Argon, 23.89720901703243, 0.3766130175948733
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - TerraCorp - Argon, 23.807564349500964, 0.2940241974037436
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - TerraCorp - Argon, 13.549421032058078, 0.516627240635443
    Paranid - OTAS - Boron - Strong Arms - Split - Terran - TerraCorp - Argon, 16.363662240015167, 0.4277771013191917
    OTAS - Pirates - Duke's - Strong Arms - Terran - TerraCorp - Argon, 31.726841854798923, 0.2521524214925899
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - TerraCorp - Argon, 19.018802378391058, 0.3680568240171273
    Yaki - OTAS - Boron - Strong Arms - Terran - TerraCorp - Argon, 15.55845484657568, 0.5141898780366837
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - TerraCorp - Argon, 17.171284634760703, 0.4076573272700602
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - TerraCorp - Argon, 14.485104329720425, 0.48325506262577994
    Paranid - Yaki - OTAS - Strong Arms - Terran - TerraCorp - Argon, 18.40082336586277, 0.43476315385112657
    Yaki - OTAS - Pirates - Strong Arms - Terran - TerraCorp - Argon, 20.28128023869058, 0.3944524165066467
    Paranid - Pirates - Duke's - Strong Arms - Terran - TerraCorp - Argon, 31.01937346859626, 0.2579033392824368
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - TerraCorp - Argon, 16.446995603321934, 0.4256096474292334
    Paranid - Yaki - Duke's - Strong Arms - Terran - TerraCorp - Argon, 15.582465167159285, 0.5133975859519547
    Yaki - Pirates - Duke's - Strong Arms - Terran - TerraCorp - Argon, 11.231242590175139, 0.712298744842199
    Paranid - Yaki - Pirates - Strong Arms - Terran - TerraCorp - Argon, 15.287037918262506, 0.5233191703176768
    Paranid - OTAS - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 14.969191736136281, 0.4676271186440678
    Paranid - Yaki - OTAS - Boron - Strong Arms - Arteus - TerraCorp - Argon, 14.54012915875817, 0.4814262599437493
    Paranid - OTAS - Boron - Strong Arms - Arteus - Terran - TerraCorp - Argon, 17.40074062378113, 0.4022817276198742
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 13.126802204620946, 0.53326011094582
    Yaki - Pirates - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 19.543121147164012, 0.4093511952240502
    Yaki - Boron - Strong Arms - Arteus - Terran - TerraCorp - Argon, 14.18970545838003, 0.563789010523501
    Paranid - OTAS - Pirates - Boron - Strong Arms - Arteus - TerraCorp - Argon, 29.448318512222652, 0.23770457376351115
    Paranid - Yaki - Pirates - Boron - Strong Arms - Arteus - TerraCorp - Argon, 14.741735296937696, 0.47484233429792433
    Paranid - Yaki - Strong Arms - Terran - Arteus - TerraCorp - Argon, 15.062028577995836, 0.5311369553293256
    Yaki - Pirates - Strong Arms - Arteus - Terran - TerraCorp - Argon, 18.254289190120012, 0.43825316432096056
    Paranid - Pirates - Boron - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 13.126802204620946, 0.53326011094582
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 11.730066359451436, 0.5967570673084717
    Yaki - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp - Argon, 10.307551487414187, 0.6791137554391262
    Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp - Argon, 13.921620667482001, 0.5028150218422872
    Paranid - Pirates - Boron - Arteus - Strong Arms - Terran - TerraCorp - Argon, 17.617819424798018, 0.3973249941560377
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - TerraCorp - Argon, 23.80756434950096, 0.29402419740374364
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - TerraCorp - Argon, 13.866693077151627, 0.5048067308516414
    Yaki - OTAS - Duke's - Strong Arms - Terran - TerraCorp - Argon, 15.732847973758258, 0.5084902627511351
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Terran - TerraCorp - Argon, 8.42542264762066, 0.8308188553575766
    Paranid - OTAS - Pirates - Boron - Strong Arms - Terran - TerraCorp - Argon, 29.448318512222656, 0.23770457376351112
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Terran - TerraCorp - Argon, 8.380260758735199, 0.8352962039640022
    Paranid - OTAS - Pirates - Strong Arms - Split - Arteus - TerraCorp - Argon, 28.927773268446774, 0.24198198509925795
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - TerraCorp - Argon, 18.81443281319833, 0.3720547980106792
    Paranid - OTAS - Strong Arms - Split - Arteus - Terran - TerraCorp - Argon, 23.001219227749633, 0.30433169349366085
    Pirates - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp - Argon, 18.63082747587176, 0.3757213687403576
    Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - TerraCorp - Argon, 14.894887439727272, 0.46995991264289616
    Yaki - OTAS - Strong Arms - Split - Terran - TerraCorp - Argon, 18.37955769187134, 0.43526618725640664
    Paranid - Pirates - Strong Arms - Split - Arteus - Terran - TerraCorp - Argon, 18.592652899924776, 0.37649280270425106
    Paranid - Yaki - Pirates - Strong Arms - Split - Arteus - TerraCorp - Argon, 15.478181938727653, 0.45224949724136776
    Paranid - Yaki - Strong Arms - Split - Terran - TerraCorp - Argon, 13.70413872697924, 0.58376525218987
    Yaki - Pirates - Strong Arms - Split - Terran - TerraCorp - Argon, 16.176510553238323, 0.494544232742364
    Paranid - Pirates - Duke's - Strong Arms - Split - Arteus - TerraCorp - Argon, 14.02684357506647, 0.4990431355806168
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - TerraCorp - Argon, 11.833339504401515, 0.5915489872826084
    Yaki - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp - Argon, 14.894887439727272, 0.46995991264289616
    Yaki - Pirates - Duke's - Strong Arms - Split - Terran - TerraCorp - Argon, 9.525755071321644, 0.7348498830370189
    Paranid - Yaki - Pirates - Strong Arms - Split - Terran - TerraCorp - Argon, 8.69649430525567, 0.8049220472402996
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - TerraCorp - Argon, 12.91918691338992, 0.5418297642822199
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - TerraCorp - Argon, 16.17871128104869, 0.43266734157000575
    Paranid - OTAS - Duke's - Strong Arms - Split - Terran - TerraCorp - Argon, 20.382032903778025, 0.34343973601879896
    OTAS - Pirates - Duke's - Strong Arms - Split - Terran - TerraCorp - Argon, 14.545618985601617, 0.4812445594050788
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - TerraCorp - Argon, 11.813569427862387, 0.5925389479229242
    Yaki - OTAS - Duke's - Strong Arms - Split - Terran - TerraCorp - Argon, 11.813569427862385, 0.5925389479229243
    Paranid - OTAS - Pirates - Strong Arms - Split - Terran - TerraCorp - Argon, 17.333783184005053, 0.40383567312987567
    Paranid - Yaki - OTAS - Strong Arms - Split - Terran - TerraCorp - Argon, 9.44552894095676, 0.7410913717756237
    Yaki - OTAS - Pirates - Strong Arms - Split - Terran - TerraCorp - Argon, 11.498188651139667, 0.6087915420752973
    Paranid - Pirates - Duke's - Strong Arms - Split - Terran - TerraCorp - Argon, 14.562275285649408, 0.48069411288346164
    Paranid - Yaki - Duke's - Strong Arms - Split - Terran - TerraCorp - Argon, 11.833339504401513, 0.5915489872826085
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 23.347814979526795, 0.2998139228933479
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 19.38545388062873, 0.3610954916559822
    Paranid - OTAS - Duke's - Strong Arms - Arteus - Terran - TerraCorp - Argon, 24.890113608590195, 0.28123616107497906
    OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - TerraCorp - Argon, 16.889349146799415, 0.4144623892346096
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - TerraCorp - Argon, 13.583480208694429, 0.5153318510759477
    Yaki - OTAS - Strong Arms - Terran - Arteus - TerraCorp - Argon, 22.690070446943757, 0.3525771336279637
    Paranid - Yaki - OTAS - Strong Arms - Arteus - Terran - TerraCorp - Argon, 14.239997278709412, 0.4915731276484077
    Yaki - OTAS - Pirates - Strong Arms - Arteus - Terran - TerraCorp - Argon, 16.88934914679941, 0.41446238923460965
    Paranid - Pirates - Duke's - Strong Arms - Arteus - Terran - TerraCorp - Argon, 14.446263306762045, 0.4845543689296748
    Paranid - Yaki - Duke's - Strong Arms - Arteus - Terran - TerraCorp - Argon, 9.143692766258043, 0.765555031095459
    Yaki - Pirates - Duke's - Strong Arms - Arteus - Terran - TerraCorp - Argon, 7.733400228432645, 0.9051645839127499
    Paranid - Yaki - Pirates - Strong Arms - Arteus - Terran - TerraCorp - Argon, 12.43413474631804, 0.562966393948145
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Terran - TerraCorp - Argon, 20.382032903778025, 0.34343973601879896
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - TerraCorp - Argon, 16.17871128104869, 0.43266734157000575
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Terran - TerraCorp - Argon, 11.030339636366, 0.6346132785360166
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Terran - TerraCorp - Argon, 14.485104329720425, 0.48325506262577994
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Arteus - TerraCorp, 28.927773268446774, 0.24198198509925795
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Arteus - TerraCorp, 18.81443281319833, 0.3720547980106792
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - Terran - TerraCorp, 23.00121922774963, 0.3043316934936609
    Pirates - Boron - Duke's - Split - Strong Arms - Arteus - Terran - TerraCorp, 20.382032903778022, 0.34343973601879907
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - TerraCorp, 16.17871128104869, 0.43266734157000575
    Yaki - Boron - Strong Arms - Split - Arteus - Terran - TerraCorp, 28.060185678558955, 0.28510146339170067
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus - Terran - TerraCorp, 17.333783184005053, 0.40383567312987567
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Arteus - TerraCorp, 14.485104329720425, 0.48325506262577994
    Paranid - Yaki - Boron - Strong Arms - Split - Terran - TerraCorp, 13.704138726979242, 0.58376525218987
    Yaki - Pirates - Boron - Strong Arms - Split - Terran - TerraCorp, 18.498567344358655, 0.4324659229591469
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - TerraCorp, 12.91918691338992, 0.5418297642822199
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Arteus - TerraCorp, 16.178711281048688, 0.43266734157000586
    Paranid - Boron - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp, 20.382032903778022, 0.34343973601879907
    Yaki - Boron - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp, 16.17871128104869, 0.43266734157000575
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Terran - TerraCorp, 8.696494305255667, 0.8049220472402997
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Split - TerraCorp, 14.026843575066472, 0.4990431355806167
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Split - TerraCorp, 18.158344408581733, 0.3854976997072355
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Terran - TerraCorp, 23.131910971075516, 0.30261226617865267
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Terran - TerraCorp, 18.579294238481765, 0.37676350404642794
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Split - TerraCorp, 14.84938663015338, 0.47139994225658444
    Yaki - OTAS - Boron - Strong Arms - Split - Terran - TerraCorp, 25.589395295822754, 0.31262950560249975
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Terran - TerraCorp, 9.935575781204015, 0.7045389370631647
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Terran - TerraCorp, 13.914177158084579, 0.5030840070864541
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Terran - TerraCorp, 14.562275285649406, 0.4806941128834617
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Split - TerraCorp, 11.833339504401515, 0.5915489872826084
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Terran - TerraCorp, 11.833339504401513, 0.5915489872826085
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Terran - TerraCorp, 10.150012128001679, 0.6896543483616655
    OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 16.889349146799418, 0.4144623892346095
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - TerraCorp, 13.583480208694429, 0.5153318510759477
    Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 11.032765898597102, 0.6344737180447291
    Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - Terran - TerraCorp, 16.889349146799418, 0.4144623892346095
    Paranid - OTAS - Pirates - Boron - Strong Arms - Arteus - Terran - TerraCorp, 43.4738255639437, 0.16101642561232654
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - TerraCorp, 34.190429934346874, 0.20473565303043967
    Paranid - Yaki - OTAS - Boron - Strong Arms - Arteus - Terran - TerraCorp, 12.078130603346041, 0.5795598863669158
    Paranid - Yaki - Pirates - Boron - Strong Arms - Arteus - Terran - TerraCorp, 10.58310148759676, 0.6614318126122004
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Terran - TerraCorp, 10.6594477735905, 0.6566944318957096
    Paranid - OTAS - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp, 20.12905006446572, 0.34775610262688267
    Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - TerraCorp, 13.456431668931282, 0.5201973429673681
    Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp, 13.456431668931282, 0.5201973429673681
    OTAS - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp, 16.748014846659068, 0.41795998296457065
    Paranid - OTAS - Pirates - Strong Arms - Split - Arteus - Terran - TerraCorp, 24.443689380366962, 0.2863724821189375
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - TerraCorp, 20.129050064465716, 0.3477561026268827
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - Terran - TerraCorp, 11.158026907697819, 0.6273510592782999
    Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - Terran - TerraCorp, 16.74801484665907, 0.41795998296457054
    Paranid - Yaki - Duke's - Strong Arms - Split - Arteus - Terran - TerraCorp, 8.7733513517238, 0.797870701784288
    Paranid - OTAS - Pirates - Duke's - Strong Arms - Split - Terran - TerraCorp, 10.669847137670452, 0.6560543848173921
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Terran - TerraCorp, 8.773351351723802, 0.7978707017842878
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Arteus - Terran - TerraCorp, 9.818770641119608, 0.7129202072085278
    Paranid - OTAS - Pirates - Boron - Strong Arms - Split - Arteus - Argon, 13.902698282910876, 0.5034993824619184
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Arteus - Argon, 10.423405304316955, 0.6715655580524037
    Paranid - OTAS - Boron - Strong Arms - Split - Arteus - Terran - Argon, 16.363662240015167, 0.4277771013191917
    Pirates - Boron - Duke's - Split - Strong Arms - Arteus - Terran - Argon, 63.15756244853142, 0.11083391645623537
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - Argon, 19.797953964194374, 0.3535718899367007
    Yaki - OTAS - Boron - Strong Arms - Split - Terran - Argon, 18.789531246531535, 0.4257690037624949
    Paranid - Pirates - Boron - Split - Strong Arms - Arteus - Terran - Argon, 18.63479609197217, 0.37564135209483646
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Arteus - Argon, 11.59273088976216, 0.6038266622907533
    Paranid - Yaki - Boron - Strong Arms - Split - Arteus - Terran - Argon, 11.133306807403537, 0.6287440129957679
    Yaki - Pirates - Boron - Strong Arms - Split - Terran - Argon, 21.749723165697954, 0.3678207735819371
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - Argon, 16.38514724093087, 0.4272161792061087
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Argon, 13.196857952283954, 0.5304292904651993
    Yaki - Boron - Duke's - Strong Arms - Split - Arteus - Terran - Argon, 42.7391304347826, 0.16378433367243136
    Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Terran - Argon, 15.12175954276383, 0.4629090933633903
    Paranid - Yaki - Pirates - Boron - Strong Arms - Split - Terran - Argon, 9.375198316334789, 0.7466508722064701
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Terran - Argon, 23.497794936986992, 0.2979002931454459
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Argon, 13.196857952283954, 0.5304292904651993
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Terran - Argon, 15.12175954276383, 0.4629090933633903
    OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Terran - Argon, 18.89187854783761, 0.37052958932986735
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Split - Argon, 11.234137824566682, 0.6231007763401728
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Terran - Argon, 8.706567772302652, 0.8039907553776141
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Terran - Argon, 10.690536562493792, 0.6547847209613867
    Paranid - Pirates - Boron - Duke's - Strong Arms - Split - Terran - Argon, 23.497794936986992, 0.2979002931454459
    Paranid - Yaki - Boron - Duke's - Strong Arms - Split - Terran - Argon, 18.472463768115944, 0.3789424133061352
    Paranid - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Argon, 10.648398668798894, 0.5634650041400808
    Yaki - OTAS - Pirates - Boron - Duke's - Strong Arms - Arteus - Argon, 10.136127101563819, 0.6905990749583268
    Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - Terran - Argon, 11.274987008487788, 0.6208432874228959
    Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - Terran - Argon, 11.874323710076808, 0.5895072570793778
    Paranid - Yaki - OTAS - Pirates - Boron - Strong Arms - Arteus - Terran - Argon, 8.284280319733181, 0.7242632755567169
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Arteus - Terran - Argon, 6.632129865630645, 0.9046867479319879
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Terran - Argon, 10.832534549837604, 0.6462014930850085
    Paranid - OTAS - Pirates - Strong Arms - Split - Arteus - Terran - Argon, 18.592652899924772, 0.3764928027042511
    Paranid - Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - Argon, 12.974885081751172, 0.5395038149390096
    Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - Terran - Argon, 14.894887439727274, 0.4699599126428961
    Yaki - OTAS - Pirates - Strong Arms - Split - Arteus - Terran - Argon, 13.089477632793736, 0.5347806991520077
    Paranid - Yaki - OTAS - Strong Arms - Split - Arteus - Terran - Argon, 9.935575781204015, 0.7045389370631647
    Paranid - Yaki - Pirates - Duke's - Strong Arms - Split - Arteus - Terran - Argon, 6.254096175857257, 0.9593712394705174
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Split - Terran - Argon, 5.236661354619592, 1.1457681896323157
    Paranid - Yaki - OTAS - Pirates - Duke's - Strong Arms - Arteus - Terran - Argon, 6.7977160656262, 0.8826493990150625
    Paranid - OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Terran, 20.382032903778022, 0.34343973601879907
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Strong Arms - Split - Arteus, 6.106362073200688, 0.9825817611327889
    Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Arteus - Terran, 16.17871128104869, 0.43266734157000575
    Yaki - OTAS - Pirates - Boron - Strong Arms - Split - Arteus - Terran, 14.485104329720425, 0.48325506262577994
    Paranid - Yaki - OTAS - Boron - Strong Arms - Split - Arteus - Terran, 9.44552894095676, 0.7410913717756237
    Paranid - Yaki - Pirates - Boron - Duke's - Strong Arms - Split - Arteus - Terran, 5.887618762375414, 1.0190877232647524
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Split - Terran, 9.274596986986053, 0.7547497761705736
    Paranid - Yaki - OTAS - Boron - Duke's - Strong Arms - Arteus - Terran, 9.136866494410334, 0.7661269872206619
    Paranid - Yaki - OTAS - Duke's - Strong Arms - Split - Arteus - Terran, 8.7733513517238, 0.797870701784288
    Paranid - Pirates - Boron - Duke's - Split - Arteus - TerraCorp - Argon, 13.020876620983616, 0.5375982127592889
    Paranid - Yaki - OTAS - Boron - Split - Arteus - TerraCorp - Argon, 11.070303568687418, 0.6323223167790669
    Paranid - OTAS - Boron - Split - Arteus - Terran - TerraCorp - Argon, 10.749143222481841, 0.6512146926612248
    Pirates - Boron - Duke's - Split - Arteus - Terran - TerraCorp - Argon, 14.176604584863664, 0.49377126646206154
    Yaki - Pirates - Boron - Duke's - Split - Arteus - TerraCorp - Argon, 15.12175954276383, 0.4629090933633903
    Yaki - Boron - Split - Arteus - Terran - TerraCorp - Argon, 15.137069635407974, 0.5285038777443918
    Paranid - Pirates - Boron - Split - Arteus - Terran - TerraCorp - Argon, 12.417600221755839, 0.563716005910376
    Paranid - Yaki - OTAS - Pirates - Boron - Split - Arteus - TerraCorp - Argon, 9.124227054818313, 0.6575899486007997
    Paranid - Yaki - Boron - Split - Terran - TerraCorp - Argon, 16.605789839487123, 0.4817596800470578
    Yaki - Pirates - Boron - Split - Terran - TerraCorp - Argon, 17.24338053480403, 0.4639461492978598
    Paranid - Pirates - Boron - Duke's - Split - Terran - TerraCorp - Argon, 19.018802378391058, 0.3680568240171273
    Paranid - Yaki - Pirates - Boron - Duke's - Split - TerraCorp - Argon, 26.143385753931536, 0.2677541488270055
    Yaki - Boron - Duke's - Split - Arteus - Terran - TerraCorp - Argon, 11.841694537346712, 0.5911316136320843
    Yaki - Pirates - Boron - Duke's - Split - Terran - TerraCorp - Argon, 12.692182077975097, 0.5515206098522009
    Paranid - Yaki - Pirates - Boron - Split - Terran - TerraCorp - Argon, 10.534916964473407, 0.664457064408376
    OTAS - Pirates - Boron - Duke's - Split - Terran - TerraCorp - Argon, 13.298696686787196, 0.5263673700412154
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Split - TerraCorp - Argon, 10.23913043478261, 0.5859872611464968
    Yaki - OTAS - Boron - Split - Terran - TerraCorp - Argon, 14.028802793233627, 0.5702553609106659
    Yaki - OTAS - Pirates - Boron - Split - Terran - TerraCorp - Argon, 10.116088621798937, 0.691967049884859
    Paranid - Yaki - OTAS - Boron - Split - Terran - TerraCorp - Argon, 9.04648380826493, 0.7737812998244413
    Paranid - Yaki - Boron - Duke's - Split - Terran - TerraCorp - Argon, 15.907507018970898, 0.4400438102370141
    OTAS - Pirates - Boron - Duke's - Arteus - Terran - TerraCorp - Argon, 9.21412884576127, 0.7597028560350744
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Arteus - TerraCorp - Argon, 7.223666517256836, 0.83060312732688
    Yaki - OTAS - Boron - Duke's - Arteus - Terran - TerraCorp - Argon, 6.908320824445441, 1.0132708335186387
    Yaki - OTAS - Pirates - Boron - Arteus - Terran - TerraCorp - Argon, 9.21412884576127, 0.7597028560350744
    Paranid - Yaki - OTAS - Boron - Arteus - Terran - TerraCorp - Argon, 7.850041505145832, 0.8917150304761299
    Paranid - Yaki - Boron - Duke's - Arteus - Terran - TerraCorp - Argon, 7.4501208558383825, 0.939582073291383
    Paranid - Yaki - OTAS - Boron - Duke's - Terran - TerraCorp - Argon, 9.882811911989766, 0.7083004373995668
    Paranid - OTAS - Pirates - Duke's - Split - Arteus - Terran - TerraCorp - Argon, 8.926203730322595, 0.6721782497096511
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Arteus - TerraCorp - Argon, 10.007340757985697, 0.5995598776040575
    Yaki - OTAS - Duke's - Split - Arteus - Terran - TerraCorp - Argon, 11.002346861397198, 0.6362278964827204
    Yaki - OTAS - Pirates - Split - Arteus - Terran - TerraCorp - Argon, 13.04386047925789, 0.5366509409642393
    Paranid - Yaki - OTAS - Split - Arteus - Terran - TerraCorp - Argon, 10.832219633460108, 0.6462202795793948
    Paranid - Yaki - Pirates - Duke's - Split - Arteus - Terran - TerraCorp - Argon, 6.797716065626199, 0.8826493990150626
    Paranid - Yaki - OTAS - Duke's - Split - Terran - TerraCorp - Argon, 11.030339636365998, 0.6346132785360167
    Paranid - Yaki - OTAS - Duke's - Arteus - Terran - TerraCorp - Argon, 9.658221475454196, 0.7247711204169515
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Arteus - Terran - TerraCorp, 8.116246160773152, 0.7392580117885977
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Split - Arteus - TerraCorp, 8.601703248736854, 0.6975362700266474
    Yaki - OTAS - Boron - Duke's - Split - Arteus - Terran - TerraCorp, 11.590604843163756, 0.6039374212751859
    Yaki - OTAS - Pirates - Boron - Split - Arteus - Terran - TerraCorp, 13.896922970845004, 0.5037086277793741
    Paranid - Yaki - OTAS - Boron - Split - Arteus - Terran - TerraCorp, 9.777849198441706, 0.7159038616708866
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Arteus - Terran - TerraCorp, 6.033775138530048, 0.994402320644273
    Paranid - Yaki - OTAS - Boron - Duke's - Split - Terran - TerraCorp, 10.6594477735905, 0.6566944318957096
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Arteus - Terran - TerraCorp, 6.008156180501107, 0.9986424819435326
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Arteus - Terran - TerraCorp, 6.4151235436046035, 0.9352898598471341
    Paranid - OTAS - Pirates - Boron - Duke's - Split - Arteus - Terran - Argon, 8.284280319733181, 0.7242632755567169
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Split - Arteus - Argon, 7.1081445192896515, 0.8441021399772562
    Yaki - OTAS - Boron - Duke's - Split - Arteus - Terran - Argon, 11.841694537346712, 0.5911316136320843
    Yaki - OTAS - Pirates - Boron - Split - Arteus - Terran - Argon, 10.452418846747804, 0.6697014444822024
    Paranid - Yaki - OTAS - Boron - Split - Arteus - Terran - Argon, 8.326619076763992, 0.8406773428045947
    Paranid - Yaki - Pirates - Boron - Duke's - Split - Arteus - Terran - Argon, 7.777298373713906, 0.7714761234156958
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Split - Terran - Argon, 6.932497494928758, 0.8654889532075711
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Arteus - Terran - Argon, 6.1327955931536495, 0.9783466461360792
    Paranid - Yaki - OTAS - Pirates - Duke's - Split - Arteus - Terran - Argon, 6.7977160656262, 0.8826493990150625
    Paranid - Yaki - OTAS - Boron - Duke's - Pirates - Split - Arteus - Terran, 6.033775138530049, 0.9944023206442729


Note that the despite total number gets bigger (since you can now target Argon, Boron, Goner), the options of least enemies gets fewer since Goner exploit is not used. However, the toatal workload and efficiency gets a little higher, also because we don't have to suffer from the side effect of Goner exploit any more. After all, since the Goner exploit does not lower the number of enemies but adds difficulty, we will not consider it unless there's a specific combo you want achieve as listed above.

3 enemies option are listed below.


```python
parsed_least_enemy_set_list = []
for least_enemy_set in least_enemy_set_list:
    if len(list(least_enemy_set)) == 3:
        workload = sum(get_X(list(set(all_races) - least_enemy_set)))
        efficiency = (len(all_races) - len(list(least_enemy_set)))/workload
        item = " - ".join(list(least_enemy_set)) + ", " + str(workload) + ", " + str(efficiency)
        print(item)
        parsed_least_enemy_set_list += [item]
```

    Terran - Paranid - Yaki, 82.5459352322271, 0.14537360278541045
    Terran - Pirates - Yaki, 85.82881902339327, 0.1398131785633601


And with 4 enemies, difficulty lowers significantly.


```python
parsed_least_enemy_set_list = []
for least_enemy_set in least_enemy_set_list:
    if len(list(least_enemy_set)) == 4:
        workload = sum(get_X(list(set(all_races) - least_enemy_set)))
        efficiency = (len(all_races) - len(list(least_enemy_set)))/workload
        item = " - ".join(list(least_enemy_set)) + ", " + str(workload) + ", " + str(efficiency)
        print(item)
        parsed_least_enemy_set_list += [item]
```

    Arteus - Paranid - Terran - Yaki, 35.236630370332534, 0.3121751394611627
    Arteus - Pirates - Terran - Yaki, 51.070866881961976, 0.2153869842355301
    Terran - OTAS - Duke's - Yaki, 74.95096743102711, 0.14676261530743606
    Terran - Paranid - OTAS - Yaki, 45.85731953596932, 0.23987446521752934
    Terran - OTAS - Pirates - Yaki, 55.976158239538634, 0.19651223567233264
    Terran - Paranid - Duke's - Yaki, 62.50956326037024, 0.1759730739788062
    Terran - Pirates - Duke's - Yaki, 29.970950403601996, 0.3670220614251188
    Terran - Paranid - Pirates - Yaki, 29.044273921030808, 0.3787321394195693
    Split - Paranid - Terran - Yaki, 50.401375412268266, 0.21824801228187268
    Split - Pirates - Terran - Yaki, 53.26729548048723, 0.20650569736602262
    Terran - Paranid - Boron - Yaki, 45.732148368752426, 0.24053101357285045
    Pirates - Boron - Terran - Yaki, 48.89364099591666, 0.22497813163308214
    Terran - OTAS - Boron - Yaki, 88.81007384601443, 0.12385982269390548
    Terran - Paranid - Argon - Yaki, 67.54098818275885, 0.1628640666351394
    Terran - Argon - Pirates - Yaki, 56.98896447693796, 0.19301982587262892
    Terran - OTAS - Argon - Yaki, 92.05261490380018, 0.11949687699252844
    Terran - Argon - TerraCorp - Yaki, 157.97854747268636, 0.06962970717211994
    Terran - Paranid - TerraCorp - Yaki, 45.81087467240295, 0.24011765936934923
    Terran - Pirates - TerraCorp - Yaki, 53.27692036839961, 0.20646839051388718
    Strong Arms - Paranid - Terran - Yaki, 40.52498529967644, 0.271437482793802
    Strong Arms - Pirates - Terran - Yaki, 52.148737618505336, 0.21093511563924366
    Terran - Paranid - Yaki - NMMC, 76.12231085408021, 0.14450428365326473
    Terran - Pirates - Yaki - NMMC, 67.18924030150454, 0.16371668961635338
    Terran - Paranid - Teladi - Yaki, 82.2155413275132, 0.13379465515139632
    Terran - Pirates - Teladi - Yaki, 85.76569881120207, 0.12825640264664015


## Conclusion

- A simple tool is developed
- Goner approach is tested and comprared with normal approach
- All possible combos are given with total workload and efficiency
- Arteus - OTAS - Yaki might be the best solution if want to be friend with Terran, at a great cost of 535.0506351864673, efficiency of 0.022427783859779837


```python

```
