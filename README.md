42call-sms
==========

42call SMS Example

```javascript
var date = new Date();
date = new Date(date.valueOf());

var passMd5 = CryptoJS.MD5($('#password').val());
passMd5 = passMd5.toString();

var hash = CryptoJS.HmacSHA1(passMd5+"\n"+date, passMd5);
hash = hash.toString(CryptoJS.enc.Base64);

$.ajax({
    type:"POST",
    headers : {
        "x-date" : date,
        "x-authorization" : $('#username').val()+":"+hash,
}, 
    data: { act: "sendSms", phonenumbers : $('#to').val(), message : $('#textarea-a').val()},
    url: "https://login.42call.com/api/rest/v2/?sms"
}).done(function(data) {
    alert(data);
    $.mobile.loading('hide');
});
```
