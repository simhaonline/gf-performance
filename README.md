# gf-performance

Performance testing between `gf`, `gin`, `echo`, `iris` and `beego`.

## Environment:

    OS   : Ubuntu 18.04 amd64
    CPU  : AMD A8-6600K x 4
    MEM  : 32GB
    GO   : v1.13.4


    GF   : v1.12.2
    Gin  : v1.6.2
    Echo : v3.3.10
    Iris : v11.1.1
    Beego: v1.12.1

## Testing tool

`ab`: Apache HTTP server benchmarking tool.

Command:
```
ab -t 10 -c 100 http://127.0.0.1:3000/hello
ab -t 10 -c 100 http://127.0.0.1:3000/query?id=10000
ab -t 10 -c 100 http://127.0.0.1:3000/json
```
The concurrency starts from `100` to `10000`.

## Testing cases


Run `5` times for each case of each project and pick up the best testing result.

### 1. Hello World

<table>
<tr>
<th>Throughputs</th>
<th>Mean Latency</th>
<th>P99 Latency</th>
</tr>
<tr>
<td width="30%"><img src="http://gfcdn.johng.cn/images/performance/throughputs1.jpeg"></td>
<td width="30%"><img src="http://gfcdn.johng.cn/images/performance/meanlatency1.jpeg"></td>
<td width="30%"><img src="http://gfcdn.johng.cn/images/performance/p99latency1.jpeg"></td>
</tr>
</table>

#### 1). Throughputs

|       | 100   | 300   | 500   | 800   | 1000  | 3000  | 5000  | 8000  | 10000 |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| gf    | 14353 | 14315 | 14215 | 14165 | 14137 | 14333 | 14317 | 14352 | 14201 |
| gin   | 14647 | 14527 | 14348 | 14241 | 14132 | 14469 | 14534 | 14493 | 14410 |
| echo  | 14670 | 14361 | 14275 | 14130 | 14139 | 14302 | 14401 | 14045 | 13978 |
| iris  | 14279 | 14121 | 14095 | 14145 | 14008 | 14247 | 14095 | 13844 | 13652 |
| beego | 14515 | 14382 | 14114 | 14039 | 14121 | 14272 | 14127 | 13760 | 13672 |

#### 2). Mean Latency

|       | 100  | 300  | 500  | 800  | 1000 | 3000 | 5000 | 8000 | 10000 |
| ----- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ----- |
| gf    | 6    | 20   | 35   | 56   | 70   | 209  | 349  | 557  | 715   |
| gin   | 6    | 20   | 34   | 56   | 70   | 207  | 344  | 551  | 693   |
| echo  | 6    | 20   | 35   | 56   | 70   | 205  | 347  | 572  | 705   |
| iris  | 7    | 21   | 35   | 56   | 72   | 210  | 362  | 595  | 732   |
| beego | 6    | 20   | 35   | 56   | 70   | 209  | 353  | 581  | 724   |

#### 3). P99 Latency

|       | 100  | 300  | 500  | 800  | 1000 | 3000 | 5000 | 8000 | 10000 |
| ----- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ----- |
| gf    | 14   | 28   | 52   | 75   | 100  | 1208 | 1409 | 1621 | 1869  |
| gin   | 11   | 27   | 47   | 70   | 94   | 1192 | 1321 | 1531 | 1716  |
| echo  | 11   | 30   | 45   | 77   | 97   | 1090 | 1341 | 1540 | 1674  |
| iris  | 13   | 31   | 51   | 80   | 104  | 1191 | 1306 | 1553 | 1802  |
| beego | 13   | 31   | 56   | 85   | 110  | 1200 | 1480 | 1761 | 1911  |

### 2. Query Retrieving

> The same as hello world.


### 3. JSON Response.

<table>
<tr>
<th>Throughputs</th>
<th>Mean Latency</th>
<th>P99 Latency</th>
</tr>
<tr>
<td width="30%"><img src="http://gfcdn.johng.cn/images/performance/throughputs3.jpeg"></td>
<td width="30%"><img src="http://gfcdn.johng.cn/images/performance/meanlatency3.jpeg"></td>
<td width="30%"><img src="http://gfcdn.johng.cn/images/performance/p99latency3.jpeg"></td>
</tr>
</table>

#### 1). Throughputs

|       | 100   | 300   | 500   | 800   | 1000  | 3000  | 5000  | 8000  | 10000 |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| gf    | 14018 | 14201 | 14008 | 13794 | 13890 | 13619 | 13928 | 13354 | 13221 |
| gin   | 14602 | 14144 | 14083 | 14019 | 13946 | 14276 | 14129 | 13528 | 13443 |
| echo  | 14390 | 14186 | 14033 | 13890 | 14085 | 14248 | 14021 | 13640 | 13284 |
| iris  | 14304 | 13988 | 14032 | 13790 | 13825 | 13853 | 13674 | 13379 | 12594 |
| beego | 13996 | 14001 | 13980 | 13781 | 13661 | 13705 | 13675 | 13301 | 12422 |

#### 2). Mean Latency

|       | 100  | 300  | 500  | 800  | 1000 | 3000 | 5000 | 8000 | 10000 |
| ----- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ----- |
| gf    | 6    | 21   | 35   | 57   | 71   | 220  | 358  | 635  | 764   |
| gin   | 6    | 21   | 35   | 57   | 71   | 210  | 353  | 739  | 743   |
| echo  | 7    | 22   | 36   | 56   | 70   | 210  | 360  | 713  | 752   |
| iris  | 6    | 21   | 35   | 58   | 72   | 216  | 365  | 597  | 813   |
| beego | 7    | 22   | 36   | 56   | 73   | 218  | 361  | 689  | 805   |



#### 3). P99 Latency

|       | 100  | 300  | 500  | 800  | 1000 | 3000 | 5000 | 8000 | 10000 |
| ----- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ----- |
| gf    | 13   | 32   | 50   | 1045 | 1102 | 1215 | 1337 | 1766 | 1769  |
| gin   | 13   | 31   | 46   | 1048 | 1069 | 1162 | 1292 | 1859 | 1766  |
| echo  | 13   | 32   | 52   | 1052 | 1064 | 1156 | 1308 | 1811 | 1956  |
| iris  | 15   | 30   | 54   | 1054 | 1058 | 1310 | 1384 | 1747 | 1732  |
| beego | 16   | 38   | 55   | 1120 | 1089 | 1130 | 1329 | 1701 | 1789  |











