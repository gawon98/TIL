# 관광객 데이터



## 읽어올때 옵션

```
kto_201001=pd.read_excel("./files/kto_201001.xlsx",
              header=1,
              usecols='A:G', #열 잘라내기
              #skiprows=3, 위에서 건너뛰는 기능
             skipfooter=4) #엑셀 헤더1번줄, 마지막 4행 빼버리기 

```



# is in

```
continents_list=['아시아주','미주','구주','대양주','아프리카주','기타대륙','교포소계']

kto_201001['국적'].isin(continents_list)

kto_201001[kto_201001['국적'].isin(continents_list)] #true만

kto_201001[kto_201001['국적'].isin(continents_list)==False] #F만
```

