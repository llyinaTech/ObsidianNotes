**日期**：2026-01-04

**场景**：拷贝了别人项目的模块，启动项目时发现找不到启动类，报错信息如下：

``` text
找不到或无法加载主类 com.atguigu.account.SeataAccountMainApplication
原因: java.lang.ClassNotFoundException: com.atguigu.account.SeataAccountMainApplication
```

**解决方案**：

在项目的配置参数里面也需要将对应的包名改成自己的包名。

![[Pasted image 20260104205629.png]]