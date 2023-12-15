# 异质结

由两种或多种不同材料拼接而成，分成垂直和横向异质结，不同材料之间要求晶格失配度$<$ 5%。

- 以 GaAs/AlAs 为例（**晶格常数相近**）：

  1. 从数据库分别导入 GaAs 和 AlAs 体材料结构：在菜单中依次点击`文件`→`从在线数据库导入`→`选择对应元素并搜素`→`选择晶胞并载入`;
  2. 结构组合：在菜单栏中依次点击`建模`→`构建异质结构`→`依次添加结构`→`堆叠方向选c`（垂直搭建）→ 详细设置中选择新的晶格常数。

<table><tr>
    <td> 
        <center>
            <img src={require('./nested/qstudio_example_hetero1.png').default} alt="Drawing" />
            <font>构建异质结</font>
        </center>
    </td>
    <td> 
        <center>
            <img src={require('./nested/qstudio_example_hetero2.png').default} alt="Drawing" />
            <font>参数设置</font>
        </center>
    </td>
</tr></table>

- 以 Fe/TiC 共格界面为例（**晶格常数相差大**）：

  1. 从数据库分别导入 Fe 和 TiC 体材料结构：在菜单中依次点击`文件`→`从在线数据库导入`→`选择对应元素并搜素`→`选择晶胞并载入`;
  2. 计算晶格失配度：分别读取结构的晶格常数，例子中 Fe 为 a=b=c=2.840,TiC 为 a=b=c=4.336，晶格失配度为（4.336-2.840）/4.336 ≈ 35%；
  3. 扩胞：因晶格常数相差较大，较高失配度可以通过扩胞处理，寻找晶格常数的最小公倍数。在菜单栏中依次点击`建模`→`建立超胞`→`设置扩胞方向及大小`；

  | 扩胞大小 | Fe 超胞晶格常数                | TiC 超胞晶格常数               |
  | -------- | ------------------------------ | ------------------------------ |
  | 1×1×1    | 2.840                          | 4.336                          |
  | 2×2×2    | 5.680                          | <font color='red'>8.671</font> |
  | 3×3×3    | <font color='red'>8.520</font> | 13.008                         |
  | 4×4×4    | 11.360                         | 17.344                         |
  | 5×5×5    | 14.200                         | 21.680                         |

  4. 计算晶格失配度：扩胞发现 Fe 的 3×3×3 超胞和 TiC 的 2×2×2 超胞的晶格常数相近，晶格失配度为（8.671-8.520）/8.671 ≈ 1.7%；
  5. 结构组合：在菜单栏中依次点击`建模`→`构建异质结构`→`依次添加结构`→`异质结方向选c`（垂直搭建）→ 详细设置中选择新的晶格常数。

<table><tr>
    <td> 
        <center>
            <img src={require('./nested/qstudio_example_hetero3.png').default} alt="Drawing" />
            <font>构建异质结</font>
        </center>
    </td>
    <td> 
        <center>
            <img src={require('./nested/qstudio_example_hetero4.png').default} alt="Drawing" />
            <font>参数设置</font>
        </center>
    </td>
</tr></table>

- 以 MoS<sub>2</sub>/石墨烯层间二维异质结为例（**晶格常数相差大**）：

  1. 分别导入单层石墨烯和 MoS<sub>2</sub> 结构：可以从在线数据库中导入，并进行[二维材料建模](./qstudio_example_2d.md)，在菜单中依次点击`文件`→`从在线数据库导入`→`选择对应元素并搜素`→`选择晶胞并载入`;
  2. 计算晶格失配度：分别读取结构的晶格常数，例子中石墨烯为 a=b=2.468,MoS<sub>2</sub> 为 a=b=3.19，晶格失配度为（3.19-2.468）/3.19 ≈ 23%；
  3. 扩胞：因晶格常数相差较大，较高失配度可以通过扩胞处理，寻找晶格常数的最小公倍数。在菜单栏中依次点击`建模`→`建立超胞`→`设置扩胞方向及大小`；

  | 扩胞大小 | 石墨烯超胞晶格常数             | MoS<sub>2</sub>超胞晶格常数   |
  | -------- | ------------------------------ | ----------------------------- |
  | 1×1×1    | 2.468                          | 3.19                          |
  | 2×2×1    | 4.936                          | 6.38                          |
  | 3×3×1    | 7.404                          | <font color='red'>9.57</font> |
  | 4×4×1    | <font color='red'>9.872</font> | 12.76                         |
  | 5×5×1    | 12.340                         | 15.95                         |

  4. 计算晶格失配度：扩胞发现石墨烯的 4×4×1 超胞和 MoS<sub>2</sub> 的 3×3×1 超胞的晶格常数相近，晶格失配度为（9.872-9.57）/9.872 ≈ 3%；
  5. 结构组合：在菜单栏中依次点击`建模`→`构建异质结构`→`依次添加结构`→`异质结方向选c`（垂直搭建）→ 晶格匹配方式选择`保持厚度不变`→ 处理方式选择`二维材料`→ 将异质结构层间分开，需要设置真空层厚度，第 1 层为层间距离设置，第 2 层为晶胞间的距离 → 详细设置中选择新的晶格常数。

<table><tr>
    <td> 
        <center>
            <img src={require('./nested/qstudio_example_hetero5.png').default} alt="Drawing" />
            <font>构建异质结</font>
        </center>
    </td>
    <td> 
        <center>
            <img src={require('./nested/qstudio_example_hetero6.png').default} alt="Drawing" />
            <font>参数设置</font>
        </center>
    </td>
</tr></table>
