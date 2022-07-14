# map&flatmap

## map

把数组流中的每一个值，使用所提供的函数执行一遍，一一对应。得到元素个数相同的数组流。  

![](https://raw.githubusercontent.com/1990frog/imagebed/default/1602318302_20190815104510622_1436046530.png)
## flatMap

flat是扁平的意思。它把数组流中的每一个值，使用所提供的函数执行一遍，一一对应。得到元素相同的数组流。只不过，里面的元素也是一个子数组流。把这些子数组合并成一个数组以后，元素个数大概率会和原数组流的个数不同。  

![](https://raw.githubusercontent.com/1990frog/imagebed/default/1602318302_20190815104551413_34240466.png)