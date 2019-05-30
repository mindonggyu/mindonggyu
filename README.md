# 서울시 자치구 범죄율 TOP 5

전기공학과 | 201724644 | 민동규
---- | ---- | ---- 
본인학과 |본인학번 |본인학성명


## 프로젝트 개요
자치구마다 범죄율이 상이하게 차이가 납니다. 범죄율 데이터를 분석해서 범죄의 취약한 지역에 인력보강과 cctv 확충하여 안전한 치안을 확보 할 수 있습니다. 

## 사용한 공공데이터 
[데이터보기]
[2014년 범죄율 데이터](https://github.com/mindonggyu/mindonggyu/blob/master/2014.csv)
[](https://github.com/mindonggyu/mindonggyu/blob/master/2015.csv)
[](https://github.com/mindonggyu/mindonggyu/blob/master/2016.csv)
[](https://github.com/mindonggyu/mindonggyu/blob/master/2017.csv)

## 소스
* [링크로 소스 내용 보기](https://github.com/cybermin/python2019/blob/master/tes.py) 

* 코드 삽입
~~~python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
#import matplotlib.ticker as ticker

from matplotlib import font_manager, rc
font_name = font_manager.FontProperties(fname="c:\windows\Fonts\malgun.ttf").get_name()
rc('font', family = font_name)

filename = input("연도를 입력하세요 (2014~2017)" )

df = pd.read_csv(filename + ".csv")

#print(df)

x = input("범죄를 선택 하세요 : 살인, 강도, 강간강제추행, 절도, 폭력")
df1 = df[x]
#print(df1)

#dfg1 = round(df.groupby('자치구')[x].mean(),2)
#print(dfg1)

y = list(df1)
z = list(df['자치구'])

#print(y)
#print(z)
w = dict(zip(z,y))
#print(w)

data_x = []
data_y = []


for i in range(1,6) :
    m = max(w, key=w.get)
    print(i,"위 ", m )
    data_x.append(m)
    data_y.append(w[m])
    del w[m]


print(data_x)
print(data_y)


ax = plt.axes()
#ax.yaxis.set_major_locator(ticker.MultipleLocator(1))
#plt.grid(axis='y')
plt.bar(data_x, data_y, label = filename, color = 'b')
plt.show()

~~~
