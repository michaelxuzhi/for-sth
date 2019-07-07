### 在行数(i)=列数(j)的范围内，求x[n,n]循环次数。
```js
var num = 0;
start:
for(var i = 0; i < 2; i++)
{
    for(var j = 0; j < 2; j++)
    {
        if(i = =1 && j == 1)
        {
            break start;
        }
    }
    num++;
}
alert(num);
```
两层循环：可以列出一个矩阵：<br>
因为for循环中的条件是i,j<2,所以 i有0,1   j有0,1 if中的条件是i,j==1,所以要找的是第i+1行，j+1列的数 <br>
即：求在2行2列矩阵中，找到第2行第2列这个数所要经历的次数。
```math
\left[
 \begin{matrix}
   0 & 1 
  \end{matrix}  
\right]  *  \left[
 \begin{matrix}
   0 & 1 
  \end{matrix}  
\right]  =  \left[
 \begin{matrix}
   (0,0) & (0,1) \\
   (1,0) & (1,1)
  \end{matrix}  
\right]
```
先从第一行第一列开始算，(0,0) num=1, (0,1) num=2 <br>
算完第一行接着第二行&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(1,0) num=3, (1,1) num=4<br>
所以找到第2行第2列这个数是在第4遍循环的时候菜找到。**但是num = 3，因为num是不包括最后一次循环。**


***
### 继续举例
```js
var num = 0;
start:
for(var i = 0; i < 4; i++)
{
    for(var j = 0; j < 4; j++)
    {
        if(i = =2 && j == 2)
        {
            break start;
        }
    }
    num++;
}
alert(num);
```

```math
\left[
 \begin{matrix}
   0 & 1 & 2 & 3 
  \end{matrix}  
\right]  *  \left[
 \begin{matrix}
   0 & 1 & 2 & 3
  \end{matrix}  
\right]  =  \left[
 \begin{matrix}
   (0,0) & (0,1) & (0,2) & (0,3)\\
   (1,0) & (1,1) & (1,2) & (1,3)\\
   (2,0) & (2,1) & (2,2) & (2,3)\\
   (3,0) & (3,1) & (3,2) & (3,3)
  \end{matrix}  
\right]
```

**num = 10** <br>

由上述的例子可以得出一条公式：<br>
在行数(i)=列数(j)的范围内，求x[n,n]循环次数**num = n·i+n**
