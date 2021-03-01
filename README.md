# w3HexSchool 報名清單 API

> 此 API 是 w3HexSchool 全馬鐵人賽報名表單 json 檔，主要是方便開發者可以串接 AJAX 並製作一個前端頁面進行篩選及查詢等動作。

API 連結：[https://raw.githubusercontent.com/hexschool/w3hexschool-API/master/data.json](https://raw.githubusercontent.com/hexschool/w3hexschool-API/master/data.json)

## API 介紹

- ~~每三十分鐘自動更新。~~ 該功能已於 2021/03/01 功成身退。
- 撈取 Google 表單所建立的 Google Sheet。
- 採 GitHub Action 自動部署。

這隻 API 也有一些基本的過濾規則，基本上就是以下

- 缺少部落格網址
- 非 「<https://>」 開頭的網址
- 沒有依照欄位提示填寫

## API 規則

基本上如果您在報名 w3HexSchool 的時候，若「**您願意分享您的姓名(暱稱)在 OPEN API 上嗎？**」的欄位填寫的是 「**願意**」，此時系統就會自動帶上您的暱稱，結構如下：

```json
{
  "keyID": 0,
  "blogList": [ // 文章列表
    {
      "title": "PixiJS V5 教學 (0)", // 文章標題
      "url": "https://hsiangfeng.github.io/javascript/20200203/3949702627/" // 文章 URL
    },
    ...
  ],
  "updateTime": "2020/2/18 下午 7:49:36", // 表單更新時間
  "blogUrl": "https://hsiangfeng.github.io/", // 部落格網址
  "name": "Ray" // 若有勾選願意公開暱稱則會顯示暱稱
}
```

假設若你勾選的是 「**不願意**」，那麼結構就會如下：

```json
{
  "keyID": 0,
  "blogList": [ // 文章列表
    {
      "title": "PixiJS V5 教學 (0)", // 文章標題
      "url": "https://hsiangfeng.github.io/javascript/20200203/3949702627/" // 文章 URL
    },
    ...
  ],
  "updateTime": "2020/2/18 下午 7:49:36", // 表單更新時間
  "blogUrl": "https://hsiangfeng.github.io/", // 部落格網址
  "name": null // 若勾選不願意，暱稱則會變成 null
}
```

## 搜尋器列表

> 以下這邊是學員所製作的 w3HexSchool 搜尋器，你可以挑選一個自己喜歡的並加入我的最愛使用。

[搜尋器列表](/SEARCH.md)

## 其他 Q&A

Q：現在還可以參加挑戰嗎？  
A：~~可以哦~~

已經不行囉~

活動結束囉，但您可以觀看先前的活動連結了解

傳送連結：[https://www.hexschool.com/2019/11/14/2019-11-14-w3Hexschool-2020-challenge/](https://www.hexschool.com/2019/11/14/2019-11-14-w3Hexschool-2020-challenge/)

Q：這個 API 更新頻率是？為什麼我投稿後沒有看到？  
A：目前是設定為每 30 分鐘一次，所以報名後請稍等待 30 分鐘後就可以看到囉。

Q：為什麼我有投稿，但沒顯示在上面？  
A：我們有寫一些資料排錯，如果你滿足以下任一條件，就不會收納在 API 裡  
1.你還沒投稿  
2.你有投稿，但格式錯誤 (第一行為文章標題，第二行為文章網址)

Q：為什麼目前大部分 `name` 是 `null`？  
A：因為個資法的關係所以預設是關閉，挑戰者們可以在投稿表單第一頁可以設定為「願意」公開名字，那下次 API 更新就會顯示，如果覺得全名不方便，你也可以寫暱稱。
