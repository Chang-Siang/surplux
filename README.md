# surplux
 [AIdea 太陽能發電量預測競賽, ITRI, Surplux Energy](https://aidea-web.tw/topic/09679060-518a-4e6f-94db-53c7d8de8138)
 
## Todo

- [X] Data: train model by normalized power
- [X] Date: train model base on location group (若只依機組型號分類，特定群組會缺少冬季的訓練資料，對測試資料反應不佳)
- [ ] Date: train model base on location group, Add: C
- [ ] Ensemble: ML (50%) & Rule Base (50%)
- [ ] Data: train by full train data
- [ ] ~~DL Model: LSTM, GRU~~
- [X] ML Model: linear regression, SVM, XGBoost
- [X] Pre-process: remove outlier
- [ ] ~~Pre-process: fill missing value~~

## 簡介
淨零排放 (Net Zero Emissions) 已成為國際共識與全球目標，目前已累積逾136國參與，甚至部分國家已達初期設定標。近來台灣擬定4大策略，預計2050年實現淨零碳排，而提升太陽光電、風力發電等再生能源發電比例也是能源轉型的重要方向。

本議題透過太陽能發電歷史資料如日射量、裝置容量…等，以機器學習的方法預測各地的太陽能發電量，期望參賽者能掌握影響太陽能發電量的關鍵因素，並對於未來太陽能建置細節擬定能有相當程度的助益。

獲獎條件：在 Private Leaderboard 低於 baseline (RMSE < 260)

## 活動時間
議題進行時間以台灣時間（UTC+8小時）為主，其時程如下:
- 2022/04/20	開放報名及下載訓練資料集
- 2022/06/21 23:59:59	上傳答案截止
- 2022/06/23	公布Private Leaderboard，開始上傳報告
- 2022/06/30 23:59:59	上傳報告截止
- 2022/07/06	公布得獎名單

## 資料
本議題提供之資料如下：  
- 發電量訓練集，共 3,585 筆（檔案名稱：train.csv）
- 發電量測試集，共 1,540 筆（檔案名稱：test.csv）

| 欄位名稱     | 欄位說明                                             |
| ------------ | ---------------------------------------------------- |
| ID           | 資料編號                                             |
| Date         | 資料日期                                             |
| Temp         | 當日平均氣溫(°C)\[2\]                                |
| Temp_m       | 模溫計：模板溫度(°C)\[1\]                            |
| Irradiance   | 日射量(MJ/m²)\[2\]                                   |
| Irradiance_m | 日照計：日射量(Wh/m²)\[1\]                           |
| Generation   | 預測目標 - 發電量(kWh)                               |
| Capacity     | 裝置容量(kWp)                                        |
| Lat          | 緯度                                                 |
| Lon          | 經度                                                 |
| Angle        | 面向角度(0 為正南方，正值為偏向西方，負值為偏向東方) |
| Module       | 模組型號\[3\]                                        |

[1] 因於硬體限制，非所有型號皆有資料  
[2] 外部資料來源：農作物災害預警平台  
[3] 模組型號  

|                 | MM60-6RT-300 | SEC-6M-60A-295 | AUO PM060MW3 320W | AUO PM060MW3 325W |
| --------------- | ------------ | -------------- | ----------------- | ----------------- |
| 峰值輸出(Pmax)   | 300W           | 295W              | 320W              | 325W |
| 峰值電壓(Vmp)    | 32.61          | 31.6              | 33.48             | 33.66 |
| 峰值電流(Imp)    | 9.2            | 9.34              | 9.56              | 9.66 |
| 開路電壓(Voc)    | 38.97          | 39.4              | 40.9              | 41.1 |
| 短路電流(Isc)    | 9.68           | 9.85              | 10.24             | 10.35 |
| 模組效能(%)      | 18.44%         | 17.74%            | 19.2%             | 19.5% |

以官方公開資料為準。STC標準測試狀況︰1000W/m²，空氣大氣光程AM 1.5，25℃
