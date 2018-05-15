# 从服务器获取时间并自动加1生成对应的时间
```
    $.ajax({
        url:"/systemSet/readDateTimeSet.do",
        type:"post",
        data:{},
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
若不需求从服务器获取：
```
    var monthNames = [ "January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December" ];
    var dayNames= ["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"];
    // Create a newDate() object
    var newDate = new Date();
    
    // Extract the current date from Date object
    newDate.setDate(newDate.getDate());
    
    // Output the day, date, month and year
    $('#date').html(dayNames[newDate.getDay()] + " " + newDate.getDate() + ' ' + monthNames[newDate.getMonth()] + ' ' + newDate.getFullYear());
    
    setInterval( function() {
    
        // Create a newDate() object and extract the seconds of the current time on the visitor's
        var seconds = new Date().getSeconds();
    
        // Add a leading zero to seconds value
        $("#sec").html(( seconds < 10 ? "0":"" ) + seconds);
    },1000);

    setInterval( function() {
    
        // Create a newDate() object and extract the minutes of the current time on the visitor's
        var minutes = new Date().getMinutes();
    
        // Add a leading zero to the minutes value
        $("#min").html(( minutes < 10 ? "0":"" ) + minutes);
    },1000);
    
    setInterval( function() {
    
        // Create a newDate() object and extract the hours of the current time on the visitor's
        var hours = new Date().getHours();
    
        // Add a leading zero to the hours value
        $("#hours").html(( hours < 10 ? "0" : "" ) + hours);
    }, 1000);

```
