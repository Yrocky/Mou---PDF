#CoreLocation&MKMapKit

`行业术语：`LBS Location Based Services 基于地理位置的网络服务  SoLoMo 索罗门
##CoreLocation

**CoreLocation框架的使用**
 
 - 导入框架 `CoreLocation.framework`
 - 导入头文件 `#improt <CoreLocation/CoreLocation.h>`
 - 该框架中的所有数据类型都是以`CL`开头的
 - 使用`CLLocationManager`来管理用户位置
 
**CLLocationManager的常用操作**

根据管理对象的判断是否定位可用，不可用直接返回空，可用才接着进行后面的定位操作

属性| 含义
----|----
CLLocationDistance `distanceFilter`| Double 类型 每隔多少米进行一次定位
CLLocationAccuracy `desiredAccuracy` | 枚举类型 定位的精确程度,越往下精确度越小
CLLocation *`location`|位置信息

- 方法：
`stratUpdatingLocation`和`stopUpdatingLocation`  在start之后会频繁的调用代理方法

**CLLocation**

用来表示某个位置的地理信息，比如海拔，经纬度，通过这个对象可以和`MPAnnotation`对象进行相关联，然后将位置转化成提示对象，最后通过提示对象添加到地图上

属性|涵义
----|----
CLLocationCoordinate2D    `coordinate` |经纬度 (结构体)  `latitude` 纬度  `longitude` 经度 
CLLocationDistance `altitude` |海拔
CLLocationDirection  `course` |路线航向
CLLocationSpeed  `speed` |行走速度  单位是m/s

**CLGeocoder**


`geocodeAddressString....`地理编码：根据给定的地名，获得具体的位置信息，经纬度和海拔


`recerseGeocodeLocation....`反地理编码：根据经纬度，海拔等获得具体的位置信息

- 当地理编码或者反编码之后就会调用CLGeocodeCompletionHandler方法,这是个block，里面装的是CLPlaceMark对象

**CLPlacemark**

字面意思是地标，封装详细的地址位置信息，在地理位置编码的时候返回的数据就是这个对象

属性| 含义
----|-----
CLLocation *`location` |地理位置
CLRegion *`region` |区域
NSDictionary *`addressDictionary` |详细的位置信息


##MapKit

**MapKit框架的使用**

- 导入框架`MapKit.framework`
- 导入头文件`#import <MapKit/MapKit.h>`
- MapKit框架的所有数据类型的前缀都是`MK`
- MapKit框架中有一个很重要的UI控件：`MKMapView`，专门用于地图显示

**userTrackingMode**

跟踪用户的位置,属性可以进行跟踪显示用户的当前位置信息

**mapViewType**

地图的类型,可以设置地图的类型：普通，卫星云图，普通地图覆盖于云图上面

**regin**

通过设置`centerCoordinate`(CL)和`span`(MK)可以设置地图的显示位置和区域

map.regin = MKCoordinateRegionMake(coordinate, span)

**annotation**

其实就是大头针

`MKPinAnnotationView`是`MKAnnotationView`的子类，只不过是多了两个属性：pinColor和animationDrop// 第一个是大头针的颜色，第二个是大头针第一次显示的时候是否从天而降