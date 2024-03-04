---

---
<%* 
let weatherUrl = 'https://restapi.amap.com/v3/weather/weatherInfo' 
let key = 'YOUR_KEY' 

let tencentIpUrl = 'https://apis.map.qq.com/ws/location/v1/ip'; 
let tencentKey = 'YOUR_KEY' 

let adcode = eval("(" + await request({url: tencentIpUrl + `?key=${tencentKey}`, method: "GET"}) + ")").result.ad_info.adcode console.log("adcode: " + adcode) 
let 位置 = '' 
let 天气 = '' 
let 温度 = '' 
let 风向 = '' 
await fetch(weatherUrl + `?key=${key}&city=${adcode}&extensions=all`) 
.then(res => res.json()) 
.then((data) => { 
	let info = data.forecasts[0] 
	console.log("info:" + info) 
	
	位置 = info.province + '-' + info.city 
	天气 = '🌅' + info.casts[0].dayweather + ' / 🌃' + info.casts[0].nightweather 
	温度 = '🌅' + info.casts[0].daytemp_float + '℃' + '/ 🌃' + info.casts[0].nighttemp_float + '℃' 
}) 
-%> 

--- 

🌻日期🌻: <% tp.file.creation_date("YYYY MM DD HH:mm:ss") %> 
🌙星期🌙: <% tp.file.creation_date("dddd") %> 
⌚️时间⌚️: <% tp.file.creation_date("HH:mm:ss") %> 
🌍位置🌍: <% 位置 %> 
☁️天气☁️: <% 天气 %> 
🌡️温度🌡️: <% 温度 %>

---