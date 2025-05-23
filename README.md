# BeijingAirQualityVisualizationProject_for_competition
for No.25 China National College Students Statistics Modeling Competition
# 北京市空气质量数据可视化项目

本项目收集了北京市28个空气质量站点从2022年1月1日至2023年12月31日的每小时空气质量六项指标数据，并通过爬虫技术获取数据。我们绘制了一系列具有交互功能的可视化图表，包括时间序列图、热图、箱线图和相关性热图，以深入分析数据特征。

## 数据特征分析

1. **地点差异（各站点）**  
   数据涵盖了多个站点（如定陵站、1002A站）。不同站点的空气质量指标分布和变化存在显著差异，这可能与地理位置、污染源（如工业区、交通枢纽）等因素有关。

2. **时间差异（年、月、日、小时）**  
   数据时间跨度长（2022至2023年），需要捕捉长期趋势（年、月）和短期波动（日、小时）。不同时间尺度可能反映出季节性（如冬季PM2.5浓度较高）和日周期性（如O3白天浓度较高）等模式。

3. **多污染物指标**  
   数据包含多种污染物（AQI、PM2.5、PM10、SO2、O3、NO2、CO）。需要分析这些污染物之间的关系和变化，例如它们之间的相关性（如PM2.5与PM10）以及对AQI的贡献。

## 可视化图表设计

### 1. 时间序列图（捕捉时间趋势）
**目的**：展示单个或多个站点在不同时间尺度（年、月、日、小时）上的污染物浓度变化趋势。

**设计**：
- **单站点时间序列**：
  - X轴：时间（支持年/月/日/小时切换）。
  - Y轴：污染物浓度（如PM2.5、AQI）或多个污染物叠加。
  - 使用平滑曲线（如移动平均）突出趋势，减少小时级噪声。
  - 示例：定陵站2023年PM2.5逐月变化。
- **多站点比较**：
  - 多条曲线，每条代表一个站点，颜色区分。
  - 可选择单一污染物（如PM2.5）或AQI，突出站点差异。
  - 示例：所有站点2023年1月PM2.5每日变化对比。
- **时间聚合**：
  - 支持按年、月、日聚合（如月均值、小时均值），以观察季节性或日周期性。
  - 示例：所有站点PM2.5的月均值热图（X轴为月份，Y轴为年份）。

### 2. 热图（时间与污染物分布）
**目的**：展示污染物浓度在时间维度（小时、日、月）上的分布规律，突出周期性特征。

**设计**：
- **小时 - 日热图**：
  - X轴：小时（0 - 23）。
  - Y轴：日期或星期几。
  - 颜色：污染物浓度（如PM2.5）或AQI。
  - 示例：定陵站2023年1月PM2.5的日 - 小时分布，揭示白天/夜间差异。
- **月 - 年热图**：
  - X轴：月份（1 - 12）。
  - Y轴：年份（2022 - 2023）。
  - 颜色：污染物均值或AQI。
  - 示例：所有站点PM2.5的月均值，展示季节性。
- **多站点热图**：
  - 为每个站点生成单独热图，或用Facet图并排显示。
  - 示例：各站点2023年NO2小时分布对比。

**适合场景**：
- 发现时间周期性（如O3白天高，NO2夜间高）。
- 比较站点在时间维度上的污染模式差异。

### 3. 箱线图（污染物分布与站点比较）
**目的**：比较不同站点的污染物浓度分布，分析离散程度和异常值。

**设计**：
- **单污染物箱线图**：
  - X轴：站点代码。
  - Y轴：污染物浓度（如PM2.5）。
  - 示例：2023年各站点PM2.5分布，显示中位数、四分位距、异常值。
- **时间分层箱线图**：
  - 分组按月或小时，展示时间维度的分布变化。
  - 示例：各站点PM2.5按月份分组的箱线图，揭示季节性差异。
- **多污染物箱线图**：
  - 使用Facet或子图，比较多种污染物的分布。
  - 示例：各站点PM2.5、PM10、NO2的箱线图对比。

**适合场景**：
- 比较站点间的污染水平差异。
- 识别异常值（如某站点PM2.5突然飙升）。
- 分析污染物分布的稳定性。

### 4. 相关性矩阵热图（污染物关系）
**目的**：分析多种污染物之间的相关性，揭示潜在的污染来源或相互作用。

**设计**：
- **相关性热图**：
  - 矩阵元素：污染物间的皮尔逊相关系数（如PM2.5与PM10、NO2与CO）。
  - 颜色：相关系数大小（-1到1）。
  - 示例：定陵站2023年污染物相关性热图。
- **多站点比较**：
  - 为每个站点生成热图，或计算平均相关性。
  - 示例：各站点PM2.5与NO2的相关性差异。
- **时间分层**：
  - 按年或月计算相关性，观察相关性随时间的变化。
  - 示例：2022 vs 2023年污染物相关性变化。

**适合场景**：
- 分析污染物间的协同变化（如PM2.5与PM10高度相关）。
- 推测污染来源（如NO2与CO高相关可能与交通排放有关）。



###使用须知
**使用Plotly和Dash库进行可视化，运行代码后，进入http://127.0.0.1:8050/，在浏览器中进行交互**
