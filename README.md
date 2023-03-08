# Email
本项目通过get请求高德地图API获取天气信息

[详细参考](https://lbs.amap.com/?ref=https://console.amap.com/dev/key/app)
 * 开发过程
     * 先通过API获取天气的详细情况
       * 注意：
         * key需要去官网申请
         * city对应邮编
         * ext表示extensions，填写all，以保障获取全部信息
       *  通过`doHttpGetRequest`发送http的get请求
       * `rlt, err := doHttpGetRequest(url + "key=" + key + "&city=" + city + "&extensions=" + ext) //请求接口`拼接参数，因为get请求不能设置requestBody，所以拼接成字符串
     * `main`方法进行方法调用`sendEmain(weather, demo)`方法
     * 在`sendEmail`中配置邮件信息。
 ```
   e := email.NewEmail()
   e.From = "582044998@qq.com<582044998@qq.com>"
   e.To = []string{"582044998@qq.com"}//注意这里我才用的是数组切片，保障可以发送多个人。
   e.Subject = "每日天气" 
   ```
进行账号的验证，注意一点的是应该采用smpt密码，并非账号密码并且注意端口号。
> 	err := e.Send("smtp.qq.com:587", smtp.PlainAuth("", "1592622761@qq.com", "//注意不是密码", "smtp.qq.com"))



   



