查找文件内容
```
grep '15678312659' ecp_sms_sender.log.2019-03-13.log
```

查找文件内容显示行号
```
cat ecp_sms_sender.log.2019-03-13.log | grep -n '15578220878' #-n
```

显示内容往后100行
```
grep -A 100 'http://133.0.77.11:7080/open/proxy/scxt/yinzhang.NoVerification.SynReq?app_id=000000001000110010&app_secret=4097ff19-1a09-4466-a1eb-0925a9d7950f&MsgId=2019031315541815678312659' ecp_sms_sender.log.2019-03-13.log
```
