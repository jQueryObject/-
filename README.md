# 从服务器获取时间并自动加1生成对应的时间
```
    $.ajax({
        url:"/systemSet/readDateTimeSet.do",
        type:"post",
        data:"",
        dataType:"json",
        success:function(data){
            var serverTime = data.nowTime.split(" ")[1],
                hours = serverTime.split(":")[0]-0,
                minutes = serverTime.split(":")[1]-0,
                seconds = serverTime.split(":")[2]-0;
            $("#hours").html(( hours < 10 ? "0":"" )+hours);
            $("#min").html(( minutes < 10 ? "0":"" )+minutes);
            $("#sec").html(( seconds < 10 ? "0":"" )+seconds);
            setInterval( function(){
                seconds += 1;
                if(seconds>59){
                    seconds = 0;
                    minutes +=1;
                    if(minutes>59){
                        minutes = 0;
                        hours +=1;
                        if(hours>23){
                            hours = 0;
                        }
                    }
                }
                $("#hours").html(( hours < 10 ? "0":"" )+hours);
                $("#min").html(( minutes < 10 ? "0":"" )+minutes);
                $("#sec").html(( seconds < 10 ? "0":"" )+seconds);
            },1000);
        }
    });
```

