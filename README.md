# 轉換經緯度

## 台灣
* 常見座標：TWD67、TWD97、WGS84，其中 TWD67、TWD97 分別是 1967 年與 1997 年的 Taiwan Datum，台灣才有的地圖座標；WGS84 是國際通用的經緯度座標
* 格式：經緯度、二分帶，其中經緯度係以地球的角度來計算，單位：度(D)、分(M)、秒(S)(1度=60分，1分=60秒)；二分帶座標以公尺為單位，格字都是 1000 公尺為單位(1000M=1KM)
<br>


## 類型簡介
* TWD67(部分地籍圖圖解數化成果)：用傳統天文觀測及三角測量的方式測定經緯度，因為受到地球重力分布不均等因素影響，測出來的經緯度只適合用在台灣附近的局部區域 ＝> EPSG:3821
* TWD97(國土測繪中心發佈全國性資料)：利用衛星打點定位測量的。衛星定位發明後，不僅精度更高，所測得的值更是全球統一的座標系統 ＝> EPSG:3824
* WGS84(全球性資料)：為 GPS 全球定位系统使用所建立的座標系統。通過遍佈世界的衛星觀測站所觀測到的座標建立 ＝> EPSG:4326
* 類型：TWD67 二分帶(如等高線圖)、TWD67 經緯度、TWD97 二分帶(少用)、TWD97 經緯度、WGS84 經緯度(如一般非登山GPS、智慧手機、Google Map)
* 註：TWD97、WGS84 極為相近(誤差很小)

<table border="1" width="15%">
    <tr>
        <th width="5%">類型</a>
        <th width="5%">坐標系統</a>
        <th width="5%">說明</a>
        <th width="5%">代碼</a>
    </tr>
    <tr>
        <td rowspan="5"> 橫麥卡托 (Transverse Mercator) 系 </td>
        <td> TM2 (TWD97，中央經線121度) </td>
        <td> 適用臺灣本島，民國87年之後施行迄今 </td>
        <td> EPSG:3826 </td>
    </tr>
    <tr>
        <td> TM2 (TWD97，中央經線119度) </td>
        <td> 適用澎湖金門馬祖，民國87年之後施行迄今 </td>
        <td>EPSG:3825 </td>
    </tr>
    <tr>
        <td> TM2 (TWD67，中央經線121度) </td>
        <td> 適用臺灣本島，民國69年之後施行 </td>
        <td> EPSG:3828 <a href="http://gis.rchss.sinica.edu.tw/qgis/?p=3542">(內建參數有誤，需自行修正)</a> </td>
    </tr>
    <tr>
        <td> TM3 (TWD67，中央經線121度) </td>
        <td> 適用澎湖金門馬祖，民國69年之後施行 </td>
        <td> EPSG:3827 </td>
    </tr>
    <tr>
        <td> TM2 (TWD97，中央經線119度) </td>
        <td> 適用臺灣本島及澎湖，民國58年之後短暫使用 </td>
        <td> 無EPSG代號 <a href="http://gis.rchss.sinica.edu.tw/qgis/?p=3542">(需自行定義)</a> </td>
    </tr>
    <tr>
        <td rowspan="4"> 經緯度 (Latitude-Longitud) 系 </td>
        <td> WGS84經緯度 </td>
        <td> 全球性資料，如：GPS、kml、geojson</td>
        <td> EPSG:4326 </td>
    </tr>
    <tr>
        <td> TWD97經緯度 </td>
        <td> 國土測繪中心發佈全國性資料 </td>
        <td> EPSG:3824 </td>
    </tr>
    <tr>
        <td> TWD67經緯度 </td>
        <td> 部分地籍圖圖解數化成果 </td>
        <td> EPSG:3821 </td>
    </tr>
    <tr>
        <td> 虎子山經緯度 </td>
        <td> 日治時期陸測地形圖 </td>
        <td> EPSG:4236 </td>
    </tr>
    <tr>
        <td rowspan="2"> 其他 </td>
        <td> Spherical Mercator </td>
        <td> 圖磚、WMS、WMTS等，如：Google Map </td>
        <td> EPSG:3857 </td>
    </tr>
    <tr>
        <td> 虎子山UTM zone 51N </td>
        <td> 中美合作軍用地形圖 </td>
        <td> EPSG:3829 </td>
    </tr>
    <tr>
        <td> 地籍坐標系 </td>
        <td> 地籍坐標 </td>
        <td> 地籍圖、河川地形圖、都市計畫地形圖使用 </td>
        <td> 無EPSG代號，需先轉換成TM2坐標再套圖，單位有分為「間」、「公尺」兩類 </td>
    </tr>
</table>
<br>


## 格式簡介
* 經緯度：由經度、緯度合稱組成一個座標系統，又稱為地理座標系統，它是一種利用三度空間的球面來定義地球上的空間球面座標系統，能夠標示地球上的任何一個位置
* 二分帶：將3D（地球圓球體）投影成平面2D，它將地表隔二度切為一個投影帶，因為切割更細所以其誤差也更小，台灣本島因較狹長所以都在同一投影帶內，不會造成使用上不便，成為國內製作各種圖籍標準

![二分帶](https://github.com/sueshow/Python_Latitude-and-Longitude/blob/master/picture/%E4%BA%8C%E5%88%86%E5%B8%B6_grid_02da.jpg)

![類型分帶](https://github.com/sueshow/Python_Latitude-and-Longitude/blob/master/picture/%E5%88%86%E5%B8%B6%E9%A1%9E%E5%9E%8B.JPG)
<br>


## 地址轉換經緯度
* 地址處理要點
  * 特殊字元，如逗號、句號、括號、+、-、{}、[]、()等
  * 換行符號
  * 郵政信箱、郵政郵箱
  * 體驗、測試、未定義(NA)
  * 地址異常短
  * 段需使用國字，號需使用數字
* 方法
  * 方法一：明確名稱，較準確
    ```
    g = geocoder.osm('國立政治大學')
    g.json["lat"], g.json["lng"]
    g.latlng
    ```
    <br>

  * 方法二：完整地址，會有些誤差
    ```
    h = geocoder.arcgis('臺北市中山區集英里權西路35號8樓')
    h.json['lat'], h.json['lng']
    h.latlng
    ```
    <br>

  * 方法三：呼叫 Google API
    * Google API設定：https://tutorials.webduino.io/zh-tw/docs/socket/useful/google-map-1.html
    * 範例：
      ```
      address = '你的地址'
      GOOGLE_PLACES_API_KEY = '你的 API KEY'

      def get_latitude_longtitude(address, GOOGLE_PLACES_API_KEY): 
          # decode url
          # address = urllib.quote(address)
          url = 'https://maps.googleapis.com/maps/api/geocode/json?address=' + address + '&key=' + GOOGLE_PLACES_API_KEY
    
          while True:
              res = requests.get(url)
              js = json.loads(res.text)
  
              if js['status'] != 'OVER_QUERY_LIMIT':   
                  time.sleep(1) 
                  break

          result = js['results'][0]['geometry']['location']
          lat = result['lat'] # 緯度
          lng = result['lng'] # 經度

          return address, lat, lng

      get_latitude_longtitude(address, GOOGLE_PLACES_API_KEY)
      ```
<br>

  * 方法四：內政部 TGOS
    * 比較差異：
      <table border="1" width="2%">
        <tr>
          <th width="2%">版本</a>
          <th width="10%">參數</a>
          <th width="10%">回傳結果</a>
        </tr>
        <tr>
          <td> V4.0 </td>
          <td> QueryAddr(oAPPId, oAPIKey, oAddress, oSRS, oFuzzyType, <br>
                         oResultDataType, oFuzzyBuffer, oIsOnlyFullMatch, oIsSupportPast, oIsShowCodeBase, <br>
                         oIsLockCounty, oIsLockTown, oIsLockVillage, oIsLockRoadSection, oIsLockLane, <br>
		                 oIsLockAlley, oIsLockArea, oIsSameNumber_SubNumber, oCanIgnoreVillage, oCanIgnoreNeighborhood, <br>
		                 oReturnMaxCount) </td>
          <td> ("期別", 完整地址", "縣市", "鄉鎮市區", "村里", <br>
                "鄰", "大道路街", "段", "巷", "弄", <br>
                "衖", "衕", "門牌號碼", "X坐標", "Y坐標", <br>
                "最小統計區", "一級統計區", "二級統計區") </td>
        </tr>
        <tr>
          <td> V3.0 </td>
          <td> QueryAddr(oAPPId, oAPIKey, oAddress, oSRS, oFuzzyType, <br>
                         oResultDataType, oFuzzyBuffer, oIsOnlyFullMatch, <br>
		                 oIsLockCounty, oIsLockTown, oIsLockVillage, oIsLockRoadSection, oIsLockLane, <br> 
		                 oIsLockAlley, oIsLockArea, oIsSameNumber_SubNumber, oCanIgnoreVillage, oCanIgnoreNeighborhood, <br> 
		                 oReturnMaxCount) </td>
          <td> (        完整地址", "縣市", "鄉鎮市區", "村里", <br>
                "鄰", "大道路街", "段", "巷", "弄", <br>
                "衖", "衕", "門牌號碼", "X坐標", "Y坐標") </td>
        </tr>
      </table>
      <br>
  
    * 建議設定值： 
      <table border="1" width="60%">
        <tr>
          <th width="5%">參數</a>
          <th width="10%">說明</a>
          <th width="5%">設定</a>
          <th width="5%">參數</a>
          <th width="10%">說明</a>
          <th width="5%">設定</a>
          <th width="5%">參數</a>
          <th width="10%">說明</a>
          <th width="5%">設定</a>
        </tr>
        <tr>
          <td> oAPPId </td>
          <td> 應用程式識別碼 </td>
          <td> AppID </td>
          <td> oAPIKey </td>
          <td> 應用程式介接驗證碼 </td>
          <td> APIKey </td>
          <td> oAddress </td>
          <td> 所要查詢的門牌位置 </td>
          <td> address </td>
	</tr>
        <tr>
          <td> oSRS </td>
          <td> 回傳的坐標系統 </td>
          <td> 'EPSG:3826' </td>
          <td> oFuzzyType </td>
          <td> 模糊比對的代碼 </td>
          <td> '2' </td>
	  <td> oResultDataType </td>
          <td> 回傳的資料格式 </td>
          <td> 'json' </td>
        </tr>
        <tr>      
          <td> oFuzzyBuffer </td>
          <td> 模糊比對回傳門牌號的許可誤差範圍 </td>
          <td> '0' </td>
          <td> oIsOnlyFullMatch </td>
          <td> 是否只進行完全比對 </td>
          <td> 'false' </td>
          <td> oIsSupportPast </td>
          <td>  </td>
          <td>  </td>
        </tr>
        <tr> 
          <td> oIsShowCodeBase </td>
          <td>  </td>
          <td>  </td>
          <td> oIsLockCounty </td>
          <td> 是否鎖定縣市 </td>
          <td> 'false' </td>
          <td> oIsLockTown </td>
          <td> 是否鎖定鄉鎮市區 </td>
          <td> 'false' </td>
	</tr>
        <tr> 
          <td> oIsLockVillage </td>
          <td> 是否鎖定村里 </td>
          <td> 'false' </td>
          <td> oIsLockRoadSection </td>
          <td> 是否鎖定路段 </td>
          <td> 'false' </td>
          <td> oIsLockLane </td>
          <td> 是否鎖定巷 </td>
          <td> 'false' </td>
        </tr>
        <tr>
          <td> oIsLockAlley </td>
          <td> 是否鎖定弄 </td>
          <td> 'false' </td>
          <td> oIsLockArea </td>
          <td> 是否鎖定地區 </td>
          <td> 'false' </td>
          <td> oIsSameNumber_SubNumber </td>
          <td> 號之、之號是否視為相同 </td>
          <td> 'false' </td>
	</tr>
        <tr>
          <td> oCanIgnoreVillage </td>
          <td> 找不時是否可忽略村里 </td>
          <td> 'false' </td>
          <td> oCanIgnoreNeighborhood </td>
          <td> 找不時是否可忽略鄰 </td>
          <td> 'false' </td>
          <td> oReturnMaxCount </td>
          <td> 如為多筆時，限制回傳最大筆數 </td>
          <td> 'false' </td>
        </tr>
      </table>
      <br>


## 距離
* 計算經緯度之間的距離：
  * 計算地球上經緯度之間的距離 d，已知地球上兩點的經度、緯度：(X1,Y1), (X2,Y2)，其中 X1、X2為經度，Y1、Y2為緯度，視計算程式需要轉化為弧度 (*3.1415926/180) 地球半徑為 R=6371.0 km，則兩點距離 
    * d = R*arcos[cos(Y1)*cos(Y2)*cos(X1-X2)+sin(Y1)*sin(Y2)]
    * C = sin(MLatA)*sin(MLatB)*cos(MLonA-MLonB) + cos(MLatA)*cos(MLatB) <br>
      Distance = R*Arccos(C)*Pi/180
* SQL
```
單位：公尺
round(6378.138*2*asin(sqrt(pow(sin( (lat1*pi()/180-lat2*pi()/180)/2),2)+cos(lat1*pi()/180)*cos(lat2*pi()/180)* pow(sin( (lng1*pi()/180-lng2*pi()/180)/2),2)))*1000)

第一點的經緯度：lng1 lat1  
第二點的經緯度：lng2 lat2
```
<br>

* Python
```
import math


# 計算距離
def getDistance(latA, lonA, latB, lonB):
    ra = 6378140  # 赤道半徑
    rb = 6356755  # 極半徑
    flatten = (ra - rb) / ra  # Partial rate of the earth
    # change angle to radians
    radLatA = math.radians(latA)
    radLonA = math.radians(lonA)
    radLatB = math.radians(latB)
    radLonB = math.radians(lonB)

    pA = math.atan(rb / ra * math.tan(radLatA))
    pB = math.atan(rb / ra * math.tan(radLatB))
    x = math.acos(math.sin(pA) * math.sin(pB) + math.cos(pA) * math.cos(pB) * math.cos(radLonA - radLonB))
    c1 = (math.sin(x) - x) * (math.sin(pA) + math.sin(pB)) ** 2 / math.cos(x / 2) ** 2
    c2 = (math.sin(x) + x) * (math.sin(pA) - math.sin(pB)) ** 2 / math.sin(x / 2) ** 2
    dr = flatten / 8 * (c1 - c2)
    distance = ra * (x + dr)
    distance = round(distance / 1000, 4)
    return f'{distance}km'
```
<br>
<br>


## 參考資料
* https://hiking.biji.co/index.php?q=news&act=info&id=11787
* http://gis.rchss.sinica.edu.tw/qgis/?p=2823
* [座標解讀](https://www.sunriver.com.tw/grid_tm2.htm)
* [經緯度距離](https://www.iteye.com/blog/mukeliang-2373903)
* [如何計算經緯度之間的距離](https://www.cherryknow.com/tech/1130502.html)
* [全國門牌地址定位服務](https://www.tgos.tw/tgos/Web/Address/TGOS_Address.aspx)
