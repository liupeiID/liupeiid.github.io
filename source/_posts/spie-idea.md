title: spie-idea
date: 2014-12-20 19:25:58
tags:
---
<h2 id="protocol">Protocol</h2>
<ul>
<li><p>download ground truth data from <a href="http://data.ess.tsinghua.edu.cn/">fine resolution observation and monitoring-global landcover</a>.</p>
</li>
<li><p>dataset prepared</p>
<ul>
<li>14 April 2005 (ETM+ scan-line)<ul>
<li>09 April 2003 (local linear histogram matching)</li>
</ul>
</li>
<li>04 May 2007 (landsat TM)</li>
<li>03 May 2009 (landsat TM)</li>
<li>08 May 2008 (ALOS PALSAR,HH)</li>
</ul>
</li>
<li><p>methodology</p>
<ul>
<li>atwt-ihs fusion (2007 vs. 2008),(2009 vs. 2008)</li>
<li>SVM classifier (2005,2007,2007Fusion,2009,2009Fusion)</li>
<li>trend simulation (2009,2011)</li>
<li>confusion matrix (2007-2009),(2009-2011),()</li>
<li>landscape index (NP,PD,AREA_MN,SHAPE_MN, PR, SHDI)</li>
</ul>
</li>
</ul>
<hr>
<ul>
<li>数据集汇总</li>
</ul>
<h3 id="ajar-dataset"><center>AJAR dataset (E:\soilErosion)</center></h3>
<table>
<thead>
<tr>
<th>data</th>
<th>time</th>
</tr>
</thead>
<tbody>
<tr>
<td></td>
<td>20010403</td>
</tr>
<tr>
<td></td>
<td>20030501</td>
</tr>
<tr>
<td>Landsat</td>
<td>20050410</td>
</tr>
<tr>
<td></td>
<td>20070504</td>
</tr>
<tr>
<td></td>
<td>20090503</td>
</tr>
<tr>
<td></td>
<td>20110330</td>
</tr>
<tr>
<td>PALSAR_FBS</td>
<td>20070621</td>
</tr>
<tr>
<td>PALSAR_FBD</td>
<td>20090626</td>
</tr>
</tbody>
</table>
---
![soil_erosion](https://raw.githubusercontent.com/liupeiID/liupeiid.github.io/master/images/soilEro.GIF)

### 小概念
 **几何校正**，是利用地面控制点和几何校正数学模型来矫正非系统因素产生的误差，将图像投影到平面上使其符合地图投影系统的过程。由于校正过程中会将坐标系统赋予图像数据，所以此过程包括了地理编码*(geo-coding)*
 
 **图像配准**(Image Registration)就是将不同时间、不同传感器（成像设备）或不同条件下（天侯、照度、摄像位置和角度等）获取的两幅或多幅图像进行匹配、叠加的过程。
 
## 进展 2014.12.18
p121r036_20080127-FROMGLCaggV1 与2005,2007,2009配准