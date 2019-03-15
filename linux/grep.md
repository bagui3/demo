grep '15678312659' ecp_sms_sender.log.2019-03-13.log

cat ecp_sms_sender.log.2019-03-13.log | grep -n '15578220878' #-n

grep -A 100 'http://133.0.77.11:7080/open/proxy/scxt/yinzhang.NoVerification.SynReq?app_id=000000001000110010&app_secret=4097ff19-1a09-4466-a1eb-0925a9d7950f&MsgId=2019031315541815678312659' ecp_sms_sender.log.2019-03-13.log