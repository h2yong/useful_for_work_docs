# Excel 技巧

## 统计汉字个数

举例：统计 A2 单元格汉字个数
`=LEN(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(A2,"，",""),"。",""),"：",""),"；",""),"！",""),"？","")," ",""))`

> 参考：https://www.163.com/dy/article/F6SH5I660516FBUT.html
