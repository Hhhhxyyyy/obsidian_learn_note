---

---
<%*
// 按照年-月-日的格式，得到今天日期的变量（例如2023-03-07）
let today = tp.date.now("YYYY-MM-DD")
// 获取输入到inputDate
let inputDate = await tp.system.prompt("输入示例："+today,today)
// 格式化变量titleName成年-月-日_周几
titleName = window.moment(inputDate, "YYYY-MM-DD", true).format("YYYY-MM-DD_ddd")
// 获取昨天的日期（文件名以日期命名）
before_date = window.moment(inputDate, "YYYY-MM-DD", true).add(-1,"days").format("YYYY-MM-DD_ddd")
// 获取明天的日期（文件名以日期命名）
after_date = window.moment(inputDate, "YYYY-MM-DD", true).add(1,"days").format("YYYY-MM-DD_ddd")
// 获取当前文件创建时间
let createTime = tp.file.creation_date()
// 获取当前文件修改时间
let modificationDate = tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss")
-%>
 
---

create time : <% createTime %>
modification date: <% modificationDate %>

---

<< [[<% before_date %>]] | [[<% after_date %>]] >>

#### 重点关注
-  ==早上 7 件事==
    - [ ] 花点时间回顾和反思
    - [ ] 查看邮件
    - [ ] 确定今日主要活动
    - [ ] 布置任务，拆分为小目标
    - [ ] 写下需要思考的东西
    - [ ] 忽略人际关系冲突
    - [ ] 屏幕时间4h内
- ==注意效率！==


## TODO List

#### 学习
- 项目1
	- [ ] 1
	- [ ] 2
- 项目2
	- [ ] 1
	- [ ] 2
- 项目3
	- [ ] 1
	- [ ] 2

#### 项目
- 项目1
	- [ ] 1
	- [ ] 2
- 项目1
	- [ ] 1
	- [ ] 2

#### 生活
- [ ] 1
- [ ] 2

## Daily Agenda
**这是 <% today %>的日计划，根据TODO制订**

### 上午
- [ ] 6:00
- [ ] 7:00
### 下午
- [ ] 13:00
- [ ] 14:00
### 晚上
- [ ] 19:00
- [ ] 22:30 睡觉

## 复盘和总结
- [ ] TODO all done
#### 写写你的感想吧：
