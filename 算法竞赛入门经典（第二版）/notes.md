# 第2章 循环结构程序设计

- 计时器

  - 头文件 `#include<time.h>`
  - 结果 `(double)clock()/CLOCKS_PRE_SEC`
  - 键盘输入的时间也被计算在内，可使用管道解决
    - Win：`echo 20 | abc` 20是参数 abc是程序名称
    - Linux：`echo 20 | ./abc` 

- `scanf`的返回值为成功输入的变量个数

- 输入输出重定向方式使用文件

  - 在main函数入口处加
    - `freopen("input.txt","r",stdin);`
    - `freopen("output.txt","w",stdout);`
  - `scanf`从文件`input.txt`读入，`printf`写入文件`output.txt`

- 不使用重定向方式读写文件数据

  - ```cpp
    #include<stdio.h>
    #define INF 1000000000
    
    int main()
    {
    	FILE *fin,*fout;
    	fin=fopen("data.in","rb");	// b表示二进制
    	fout=fopen("data.out","wb");
    	int x,n=0,min=INF,max=-INF,s=0;
    	while(fscanf(fin,"%d",&x)==1)
    	{
    		s+=x;
    		if(x<min)
    			min=x;
    		if(x>max)
    			max=x;
    		n++;
    	}
    	fprintf(fout,"%d %d %.3f\n",min,max,(double)s/n);
    	fclose(fin);
    	fclose(fout);
    	
    	return 0;
    }
    
    
    ```

# 第3章 数组和字符串

- 比较大的数组应尽量声明在main函数外，否则程序可能异常退出
- `memset(a,0,sizeof(a))`把数组a清零
- 头文件`ctype.h`
  - `isalpha`判断是否为字母
  - `isdigit`判断是否为数字
  - `toupper` `tolower` 转化

# 第4章 函数和递归

- 定义新类型

  - ```cpp
    typedef struct
    {
    	double x,y;
    }Point;
    ```

- 