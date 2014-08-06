#使用 QGIS 做影像的幾何校正

這個教學示範如何將沒有幾何校正過的檔案使用線上地圖參照並校正、數化成向量檔
(白話文：把沒有地理座標資訊的影像檔加入地理座標資訊，並數化成向量檔)

## I. 影像幾何校正
    
1. 開啟 QGIS，並加入要做幾何校正的原始影像檔

![加入要幾何校正的影像檔](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/01_add_orig_raster.png)

2. 設定投影座標系統，這裡先使用 WGS84 pseudo Mercator (EPSG:3857) 座標系統

![設定投影座標系統](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/02_setup_proj.png)

3. 從主選單中的 Web / OpenLayers Plugin / Openstreetmap / Openstreemap 加入 Openstreetmap

![加入 openstreetmap](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/03_add_openstreetmap.png)

4. 從主選單中的影像(raster)/幾何校正(Georeferencer) 開啟「幾何校正」

![開啟幾何校正工具](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/04_georeference.png)

5. 用看圖軟體看一下要校正的參考控制點，因為原始檔為道路圖，所以比較好抓出特徵(pattern)的是圓環交叉口，
因此我把幾個圓環圈起來，當做候選參考控制點。此外，為了獲得最佳的校正效果，建議平均在圖面上的東西南北各找幾個候選參考控制點，
這樣結果會比較準確（當然點愈多愈好）

![確認原檔，及預先找出特徵](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/05_grep_candidates.png)

6. 開啟「幾何校正」對話框，按圖示列最左邊的「加入影像檔」，並選取我們要做校正的檔案。在幾何校正功能中，
中間的框是顯示原圖，可以放大縮小並加入參考控制點(georeference check points; GCPs)，加入的參考點會顯示在
下方的 GCP table 中

![開啟幾何校正對話框](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/06_open_georeferencer.png)

7. 載入原始影像檔

![載入原始影像檔](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/07_load_orig_raster.png)

8. 點取第一個候選參考控制點區域

![](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/08_check_ctrl_pts.png)

9. 點選後，會出現一個對話框，此時你可以輸入這個點在真實地圖上的座標，或是從圖中點選(from map canvas)。
在這裡我們選擇 from map canvas

![](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/09_pick_ref_pts.png)

![](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/10_pick_ref_pts_1.png)

10. 選完之後，比對一下附近圖徵是否相符？如果不符可以刪掉重選，一個區域可以多選幾個點，最好選擇容易辨識的交叉路口

![](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/11_find_another_ref_pts.png)

11. 確認第二個候選參考控制點區域

![](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/12_check_pattern_1.png)

![](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/13_check_pattern_2.png)

12. 確認第三個候選參考控制點區域，建議至少選四個點以上，愈多愈好

![](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/14_check_pattern_3.png)

13. 都選完之後，可以整體看一下大致參考控制點是否平均

![](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/15_overall_look.png)

14. 另存新檔，這裡選擇轉換的方法是 1 階多項式加上 cubic spline，還有選擇座標系統 EPSG:3857 (之後可以再透過 QGIS 轉換座標系統)

![](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/16_save_as.png)

15. 載入以校正過的影像檔案，調整透明度（在圖層選單中，選擇以校正過的影像檔，按右鍵選擇 properties）

![](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/17_opacity.png)

16. 和 openstreetmap 疊圖，看校正結果如何，若誤差較大，重複上述 7 至 15 的步驟，再重新選擇參考控制點

![](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/18_check_georeferenced.png)
![](https://raw.github.com/mutolisp/kh_pplines/master/tutorial/img/19_check_georeferenced_2.png)

## II. 數化(digitize)成向量檔
(TBD)
