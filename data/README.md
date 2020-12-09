# SHMetro Dataset & HZMetro Dataset 

In this work, we focue on the metro ridership prediction from 5:30 - 23:30. Specifically, we utilize the metro ridership (inflow/outflow) of previous 4 time intervals (4*15m=60m) to predict the metro ridership (inflow/outflow) of future 4 time intervals (4*15m=60m) : 
```
5:30-6:30 -- forecast -> 6:30-7:30
5:45-6:45 -- forecast -> 6:45-7:45
...
21:15-22:15 -- forecast -> 22:15-23:15
21:30-22:30 -- forecast -> 22:30-23:30
```
Therefore, each day can be splitted to 66 time slices. 

#### Data Organization
For each dataset, we release six pkl fiels.
1. Metro Ridership
```
T = the sample numebr of time slices
N = the numebr of metro stations
n = the length of input sequence,  i.e, 4 time intervals in our work
m = the length of output sequence, i.e, 4 time intervals in our work
D = the data dimension of each station, i.e, 2 (inflow/outflow) in our work

train.pkl: the train set. It is a dict that consists of 4 ndarray: 
(1) x: the metro ridership (inflow/outflow) of previous four time intervals, thus its shape is [T, n, N, D]. 
(2) y: the metro ridership (inflow/outflow) of next     four time intervals, thus its shape is [T, m, N, D]. 
(3) xtime: the timestamps of x. Its shape is [T, n]. 
(4) ytime: the timestamps of y. Its shape is [T, m]. 

val.pkl: the val set. Its data organization is similar to that of the train set.
test.pkl: the test set. Its data organization is similar to that of the train set.
```
This means that we use x[i] to predict y[i].

2. Graph Information
```
graph_**_conn.pkl: the physical graph of metro
graph_**_sml.pkl : the similarity graph of metro  
graph_**_conn.pkl: the correlation graph of metro
```
