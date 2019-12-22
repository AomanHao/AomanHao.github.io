<style type="text/css">
    
    .header-inner{
         display: none;
    }
    .sidebar{
        display: none;
    }
    .content{
        margin-bottom: 360px;
    }
    .content-wrap{
       width: 100%;
       // box-sizing: content-box;
       padding: initial !important;
       background:url('https://s2.ax1x.com/2019/09/07/nlL4pR.jpg');
    }
    
	.main-inner{
		width: 100%;
	}
	.main {
        padding-bottom: 150px;
        margin-top: 0px;
        background:url('https://s2.ax1x.com/2019/09/07/nlL4pR.jpg');
	}
	.main-inner{
		margin-top: unset;
	}
	.page-post-detail .post-meta{
		display: none;
	}
	body {
		background-image: unset;
		background-attachment: unset;
		background-size: 100%;
		/*background-position: top left;*/
	}
	.header{
		background: rgba(28, 25, 25, 0.6);
		border-bottom: unset;
	}
	.menu .menu-item a{
		    font-weight: 300;
    		color: #e6eaed;
	}
	.footer-inner {
    	 padding-left: 0px;
    }
    
    img:hover {
        //opacity:0.8; /*透明度*/
        //filter:alpha(opacity=100); /* For IE8 and earlier */
    }

	.imgbox{
	    margin-top: 20px;
	    padding: 1px 10px;
        width: 100%;
        overflow: hidden;
        height: 250px;
	    border-right: 1px solid #bcbcbc;
	    background:url('https://s2.ax1x.com/2019/09/07/nlL4pR.jpg');
	}
	.box{
		visibility: visible;
		overflow: auto; 
		zoom: 1;
	}
	.box li{
        float: left;
        width: 25%;
        position: relative;
        overflow: hidden;
        text-align: center;
        list-style: none;
        margin: 0;
        /*display: inline;*/
        padding: 0;
        height: 360px;
	}
	.box li span{
        display: block;
        padding: 12% 7% 10% 7%;
        min-height: 80px;
        //background: #fff;
        color: #000080;
        font-size: 16px;
        font-weight: 600;
        line-height: 26px;
        -webkit-box-sizing: border-box;
        box-sizing: border-box;
	}

	img.imgitem{
		padding: unset;
		padding: unset;
		border: unset;
		position: relative;
		padding: 0px;
		height: auto;
		width: 100%;
	}

    div#posts.posts-expand {
        border: unset;
        padding: unset;
        margin-bottom: 10px;
    }
    .posts-expand .post-body img{
        padding: 0px !important;
    }
    .box p{
        margin-top: -25px;
        display: block;
        background: #121212;
        color: #000080;
        font-size: 14px;
        -webkit-box-sizing: border-box;
        box-sizing: border-box;
        text-align: center;
    }
    
    .box span strong{
        background: rgba(0,0,0,0.4);
        padding: 20px;
    }
    
    .posts-expand .post-title {
        display: none;
    }
    
    .title{
        margin: 10px auto;
        display: inline-block;
        vertical-align: middle;
        //background: url(/images/beichen.jpg);
        font: 85px/250px 'ChaletComprimeMilanSixty';
        //background-position: left bottom !important;
        background-position: center center !important;
        color: #fff;
        background-size: 100% auto !important; 
        -webkit-background-size: cover; 
        -moz-background-size: cover;
        -o-background-size: cover;
        width: 100%;
        text-align: center;
        border: unset;
        height: 560px;
        cursor: unset !important;
        -webkit-box-sizing: border-box;
        box-sizing: border-box;
    }

    @media (max-width: 767px){
        .box li {
            width: 98%;
        }
        .title {
            height: 200px;
        }
        
        .box span {
            min-height: 80px;
            border-right: unset;
            font-size: 17px;
        }
        .box p{
            border-right: unset;
            font-size: 12px;
          
        }
        .posts-expand {
            margin: unset;
        }
    
    }

    @media (min-width: 1600px){
    
        .container .main-inner{
            width: 100%;
        }
    }

</style>

<div id="box" class="box"></div>

<script type="text/javascript">
   
   // 相册json 最好1比4 或者8
   var json = 
    [
    	[
            {
                'title': '蓝湖',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2019-04-07_ZJU%20Blue%20Lake.jpg'
            },
            {
                'title': '老屋',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2019-04-07_ZJU%20OldHouse.jpg'
            },
            {
                'title': '蓝湖美女',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2019-04-07_ZJU%20Blue%20Lake2.jpg'
            },
            {
                'title': '乌镇小舟',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2019-04-05_WuZhen%20boat.jpg'
            },
            {
                'title': '古镇',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2019-04-05_GuTangBoat.jpg'
            },
            {
                'title': '乌镇彩灯',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2019-04-05_GuTang%20Lantern.jpg'
            },
            {
                'title': '喵的天空',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2019-03-31_ZJ%20WalkStreet.jpg'
            },
            {
                'title': '重庆解放碑',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2018-12-31_CQ%20JieFangBei.jpg'
            },
            {
                'title': '重庆夜景',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2018-12-30_CQ%20Night.jpg'
            }
    	],
    	
    	[
            {
                'title': '大秦岭',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2017-10-10_West%20Post%20Wangling.jpg'
            },
            {
                'title': '爱的牌子',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2019-01-01_love.jpg'
            },
            {
                'title': '路灯',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2018-11-28_gute%20nathe.jpg'
            },
            {
                'title': '生日蛋糕',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2018-11-28_birthday%20cake.jpg'
            },
            {
                'title': '音乐节-许巍',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2017-10-07_XuWei%20Music%20Festival%20Of%20QiXi.jpg'
            },
            {
                'title': '突然的自我',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2017-10-16_Me.jpg'
            },
            {
                'title': '蓝莲花',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2017-10-07_XuWei%20Music%20Festival%202.jpg'
            },
            {
                'title': '在桥上',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2016-05-22_On%20the%20bridge.jpg'
            },
            {
                'title': '图像处理',
                'url': 'https://img-blog.nos-eastchina1.126.net/process_photo/2017-06-02_Image%20Processing.jpg'
            }
    	]
    ]
    
    var content = json2Array(json);
        
    var wid = 250;
    if ((window.innerWidth) > 1200) {
        wid = (window.innerWidth*3)/18;
    }
    var box = document.getElementById('box');
    
    var i=0;
    for (var i = 0; i < content.length; i++) {
    	var conBox = document.createElement("div");
    	conBox.id = 'conBox'+i;
    	box.appendChild(conBox);
    	var item = document.createElement("div");
    	var title = content[i][0].title;
    	var url = content[i][0].url;
    	item.innerHTML = "<button class = 'title' style = 'background: url(" + url + ");'><span style = 'display: inline;'><strong style = 'color:#f0f3f6;' >" + title + "</strong></span></button>";
    	conBox.appendChild(item);
    
    	for (var j = 1; j < content[i].length ; j++) {
    		var _title = content[i][j].title;
    		var _url = content[i][j].url;
    		var item = document.createElement("li");
    		item.innerHTML="<div class = 'imgbox' id = 'imgbox' style = 'height: " + wid + "px;'><img class = 'imgitem' src='" + _url + "' alt='" + _url + "'></div><span>" + _title +"</span>";
    		conBox.appendChild(item);
    	}
    }
    
    //json转二维数组
    function json2Array(arr) {
        for (var i=0; i<arr.length; i++) {
            var tmpArr = []
            for (var attr in arr[i]) {
                tmpArr.push(arr[i][attr])
            }
            arr[i] = tmpArr
        }
        return arr
    }

</script>