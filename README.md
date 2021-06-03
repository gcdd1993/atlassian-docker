# **[atlassian-docker](https://github.com/gcdd1993/atlassian-docker)**

## 编译

### jira

```bash
docker build -f jira/Dockerfile -t gcdd1993/jira-software:8.16 .
docker push gcdd1993/jira-software:8.16
```

### confluence

```bash
docker build -f confluence/Dockerfile -t  gcdd1993/confluence-server:7-adoptopenjdk11 .
docker push gcdd1993/confluence-server:7-adoptopenjdk11
```

## 运行

> 这里演示下如何安装，实际安装建议采用外部数据库，并使用k8s部署

```bash
docker run -p 8091:8080 gcdd1993/jira-software:8.16
...
2021-06-03 07:37:12,909+0000 JIRA-Bootstrap INFO      [c.a.jira.startup.LauncherContextListener] Startup is complete. Jira is ready to serve.
2021-06-03 07:37:12,911+0000 JIRA-Bootstrap INFO      [c.a.jira.startup.LauncherContextListener] Memory Usage:
    ---------------------------------------------------------------------------------
      Heap memory     :  Used:  267 MiB.  Committed:  910 MiB.  Max: 2019 MiB
      Non-heap memory :  Used:   77 MiB.  Committed:   90 MiB.  Max: 1536 MiB
    ---------------------------------------------------------------------------------
      TOTAL           :  Used:  343 MiB.  Committed:  999 MiB.  Max: 3555 MiB
    ---------------------------------------------------------------------------------
```

浏览器打开http://localhost:8091/

1、切换语言到中文，选择“我将设置它自己”

![](https://i.loli.net/2021/06/03/KtznIgjs9HV7S1G.png)

2、设置为内置数据库，仅作为演示

![](https://i.loli.net/2021/06/03/ZTF4IvVMJu8ctCE.png)

3、设置应用程序的属性，点击下一步即可

![](https://i.loli.net/2021/06/03/ETrIVmdaoHC5luX.png)

4、设置许可证

![image-20210603154622375](C:\Users\reborn\AppData\Roaming\Typora\typora-user-images\image-20210603154622375.png)

```bash\
java -jar atlassian-agent.jar -d -m gaochen@olxin.cn -n BAT -p 'jira' -o http://localhost:8091 -s ${服务器ID}
====================================================
=======        Atlassian Crack Agent         =======
=======           https://zhile.io           =======
=======          QQ Group: 30347511          =======
====================================================

Your license code(Don't copy this line!!!):

AAABow0ODAoPeJyNkk+PmzAQxe98CqSezRqSTbKRLDUBVLEiUBV2D705ziS4cmxkm3TTT18TWHX/R
FElX2zNe37zm/lSN53/2EkfT/zwfjl1B/txVfsRjkLvoAFko9oWdJBzBtJAfW6hoEcgcbnZpD/ib
JV7sQZquZIJtUB6IcIzhCfeDUkChmne9iryJAU/cgs7XwwCf3v2G2tbs7y7+9NwAQFX3oZyaUFSy
SB9abk+j78tHhCeu+P94pq+pkx3fLAu8myT1WniFd1xC7rcPxnQhqDwNdwNr1arXcds0F+QUXv7m
2oIPhndqKXM8hMQqzt4x/Lt+w25S0VjcF3roXTE8+w+7puLvKrb/sN4KUlPVHSXYZA9FWa0/2hU6
gOV3Ax1PWkHWihGRaOMXS7wQ+jFSloXM3XYBTlQxRqQX5V44TJgcnC9TuI/e6ss1X2eIeU4jCwhe
ZZUaYHycBZFczybTPF0fv9uttfWqQJ9Au3k68ciR0VZPqN8HX9Di+zn6toWf96P751mDTXwcYffi
i8EW83N2J4LSq6EHdFdMq5X9V/tNSn+MCwCFHoEs7FEyB8GJDD3qwVt2sJSxVl5AhRQUDDbL+DiN
ADCGu072KZdjN77tQ==X02k8
```

将此许可证填入即可

5、设置管理员账户，Enjoy！

![](https://i.loli.net/2021/06/03/e8Q4VL2YIqbuoFh.png)

