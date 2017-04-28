# pytest
import numpy as np
from pandas import Series,DataFrame
import pandas as pd
obj2=Series([1,2,3,4],index=['a','b','c','d'])
print(obj2)
print(obj2['b'])
print(obj2[obj2>2])
print('c' in  obj2)

data={'state':['ohio','ohio','ohio','texas','texas'],
      'year':[2000,2001,2002,2001,2002],
      'pop':[1.4,1.7,3.6,2.4,2.9]}
frame=DataFrame(data)
print(frame)
print(frame.year)
print(frame['year'])
frame.index.name='index'
frame.columns.name='columns'
print(frame)
print(frame.values)
print(frame['year'])#获取一列series
print(frame[['year','state']])#同时获取两列
print(frame.year)#同样获取一列
print(frame.ix[2])#获取一行
print(frame.ix[[2,1]])#同时获取两行
print(frame.loc[2])#同样获取一行
print(frame.loc[[0,2,3]])#同时获取三行

fra3=frame.loc[1:4]#获取连续的四行（非三行）
print(fra3)
list1=[1,7,3,4,5]
print(frame.reindex(list1))#更新索引行
colu=['pop1','state','year']#更新索引列
print(frame.reindex(columns=colu))
'''
frame=DataFrame(np.arange(9).reshape(3,3),
                index  =['a','b','c'],
                columns=['111','222','333'])
print(frame)
'''

fra4=fra3.reindex(index=[1,2,3,6],#同时更新行列索引
        method='ffill',
        columns=colu)
print(fra4)
fra5=fra3.ix[[1,2,3,6],colu]#同时更新行列，不填补
print(fra5)
print(fra3.drop(2))#删除一行
print(fra3.drop([2,4]))#删除多行
print(fra3.drop('pop',axis=1))#删除一列
print(fra3.drop(['pop','year'],axis=1))#删除多列
