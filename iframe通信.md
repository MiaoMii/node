 window.setIframeUrl = function(name) {
         console.log('setIframeUrl')
         const arr = [
          { title: "轨迹回放", id: "drag-a9m1bkqo8t3j"},
          { title: "相似轨迹", id: "drag-xg81ccl0i4e7"},
          { title: "轨迹预测", id: "drag-szmi78275oev"},
          { title: "二三维转换", id: "drag-ibt4axxudvpw"},
        ];
        const cookie = {
          set: function (key, val, time) {
            //设置cookie方法
            var date = new Date(); //获取当前时间
            var expiresDays = time; //将date设置为n天以后的时间
            date.setTime(date.getTime() + expiresDays * 24 * 3600 * 1000); //格式化为cookie识别的时间
            document.cookie =
              key + "=" + escape(val) + ";expires=" + date.toGMTString(); //设置cookie
          },
          get: function (key) {
            //获取cookie方法
            /*获取cookie参数*/
            var getCookie = document.cookie.replace(/[ ]/g, ""); //获取cookie，并且将获得的cookie格式化，去掉空格字符
            var arrCookie = getCookie.split(";"); //将获得的cookie以"分号"为标识 将cookie保存到arrCookie的数组中
            var tips; //声明变量tips
            for (var i = 0; i < arrCookie.length; i++) {
              //使用for循环查找cookie中的tips变量
              var arr = arrCookie[i].split("="); //将单条cookie用"等号"为标识，将单条cookie保存为arr数组
              if (key == arr[0]) {
                //匹配变量名称，其中arr[0]是指的cookie名称，如果该条变量为tips则执行判断语句中的赋值操作
                tips = arr[1]; //将cookie的值赋给变量tips
                break; //终止for循环遍历
              }
            }
            return unescape(tips);
          },
        };
        const username =
          cookie.get("lastLoginUser") !== "undefined" &&
          JSON.parse(cookie.get("lastLoginUser"));
        const userinfo = username
          ? cookie.get(username) !== "undefined" &&
            JSON.parse(cookie.get(username))
          : "";
        if (!name || !username || $(".iframe-content").attr('data-value') === name) return;
        let temp = arr.filter((it) => it.title === name)[0];
        let url = `http://${window.location.host}/appSite/#/appExt?appname=${name}&user=${username}&userid=${userinfo.userid}&autorun=true`;
        console.log(url);
        if (temp.endPos) url += `&endPos=${temp.endPos}`;
        $(".iframe-content")[0].src = url;
        $(".iframe-content").attr('data-url', url);
        $(".iframe-content").attr('data-value', name);
    }



iframe 

parent.setIframeUrl ()

