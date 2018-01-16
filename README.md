# HousePricingOfBeijing

HousePricingOfBeijing是一个基于SOA架构的北京丝房价地理信息系统，提供北京市海量房源数据的位置信息和属性信息的空间可视化展示，房源位置、属性及其周边的查询筛选，包括每一处房源周边重要的基础设施（学校、公交车站、地铁站、医院、商业写字楼）等购房者最为关心的内容。
系统现托管至heroku上：https://secret-crag-96471.herokuapp.com/


### 面向用户(买房者、卖房者)


对于买家，在主页面通过空间位置和属性（房价、房型、房屋面积等）筛选出符合自己感兴趣条件的房屋，并且可以进入各个房屋的详细页面，应用通过各种可视化手段让用户从交通、教育、工作、交通、生活等方面对这套房子进行评估。
对于卖家，可以根据自己的房屋位置和各个属性情况做出合理的估价。


### 面向开发者（数据挖掘工程师，数据可视化分析师等）

如果你是面向地理位置的数据挖掘工程师，你可以不用编写与百度API交互的代码，直接运行这个应用后导入自己的房屋数据，应用会自动与百度API爬取周围的基础设施，获得的数据可用来作为学术研究和分析等。

请点击这里查看详细信息:http://blog.csdn.net/ppp8300885/article/details/77806852



### 系统开发说明
   
   1. 在房价网站上利用爬虫爬下当前所有房子的价格和基本信息（房型、面积、楼层、建造时间等）
  
   2. 利用 arcgis online service 将爬虫下来的数据发布生成图层服务（房屋图层、公交车站图层、地铁站图层、写字楼图层、医院图层、学校图层、商场图层）等，并使用美观的地图符号对各种地理实体进行标记。

   3. 在三维场景中对房屋信息进行可视化展示，丰富UI界面。
    
   4. 利用 arcgis online service 发布各种空间分析服务（如房屋查询、周边查询等），实现与房屋交易相关的主要数据分析功能。 

   5. 建立 rails 开发框架，设计系统主要架构和前端UI布局，并将 arcgis online service 集成到 rails 应用中。
  

## 开发

   1. 原始数据由[scrapy-hoursepricing](https://github.com/PENGZhaoqing/scrapy-hoursepricing)爬取，数据抓取后先存为CSV文件，然后导入到arcgis online service 云端数据库中发布成图层服务。
    
   2. 再arcgis online 云端，建立空间查询和数据分析等先关应用，并发布成服务。
    
   3. 运用 ruby on rails 框架建立web应用程序，设计系统界面和UI布局，并集成 arcgis online 云端的服务。
    
    
## 系统安装说明

本项目由rails框架开发，系统运行环境需要`ruby 2.2,rails 5.1,postgresql`

```
git clone your_forked_project
cd project_path
bundle install
rake db:migrate
rake db:seed
rails s
```

在浏览器中输入`localhost:3000`，即可访问主页


## 小组成员分工

#### 何天乐
    数据可视化展示，发布arcgis online 图层及地理信息可视化服务，数据查询分析服务，
    建立rails应用并集成地图和数据分析服务。


## 系统界面截图

### 系统主页，运用地图符号标识房源位置，颜色深浅标识房价高低，符号大小标识房屋面积大小

<img src="/image/indexpage.png" width="900">


### 房屋信息热力图展示

<img src="/image/heatmap.png" width="900">


### 房屋信息三维场景展示

<img src="/image/3d.png" width="900">


### 房屋及其周边购房者关心的地理实体展示

<img src="/image/geoinfo.png" width="900">


### 根据属性信息查询

<img src="/image/search.png" width="900">


### 周边查询，根据位置信息查询

<img src="/image/near.png" width="900">


### 底图切换（卫星图、矢量图、黑色主题图等）

<img src="/image/basemap.png" width="900">

<img src="/lib/screen1.png">

<img src="/lib/screen3.png">

<img src="/lib/screen4.png">

