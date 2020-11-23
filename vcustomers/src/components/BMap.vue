<template>
  <div class="BMap container">
    <h1 class="page-header">当前位置</h1>
    <div id="allmap" v-bind:style="mapStyle"></div>
    <br>
  </div>
</template>

<script>

    export default {
        name: "BMap",
        data:function(){
            return{
                mapStyle:{
                    width:'100%',
                    height:this.mapHeight +'px'
                }
            }
        },
        props:{
            // 地图在该视图上的高度
            mapHeight:{
                type:Number,
                default:500
            },
            // 经度
            longitude:{
                type:Number,
                default:121.404
            }
            ,
            // 纬度
            latitude:{
                type:Number,
                default:29.915
            },
            description:{
                type:String,
                default:'天安门'
            }
        },
        // ready:function(){
        //     var map =new BMap.Map("allmap");
        //     var point =new BMap.Point(this.longitude,this.latitude);
        //     var marker =new BMap.Marker(point);
        //     map.addOverlay(marker);
        //     map.centerAndZoom(point,15);
        //     // 信息窗的配置信息
        //     var opts ={
        //         width :250,
        //         height:75,
        //         title :"地址：",
        //     }
        //     var infoWindow =newBMap.InfoWindow(this.description,opts);// 创建信息窗口对象
        //     marker.addEventListener("click",function(){
        //         map.openInfoWindow(infoWindow,point);
        //     });
        //     map.enableScrollWheelZoom(true);
        //     map.openInfoWindow(infoWindow,point);//开启信息窗口
        // },
        mounted(){
            var map = new BMap.Map("allmap");
            var geolocation = new BMap.Geolocation();
            geolocation.getCurrentPosition(function(r){
                // var point = new BMap.Point(r.point.lon,r.point.lat);
                var point = new BMap.Point(121.504, 29.915);
                // console.log(Point);
                map.centerAndZoom(point,12);

                var marker = new BMap.Marker(point);  // 创建标注
	            map.addOverlay(marker);               // 将标注添加到地图中
                // marker.setAnimation(BMAP_ANIMATION_BOUNCE); //跳动的动画

                var opts = {
                    width : 100,     // 信息窗口宽度
                    height: 60,     // 信息窗口高度
                    title : "波浪艇" , // 信息窗口标题
                    message:"坐标"
                }
                var infoWindow = new BMap.InfoWindow("位置", opts);  // 创建信息窗口对象 
                marker.addEventListener("click", function(){          
                    map.openInfoWindow(infoWindow, point); //开启信息窗口
                }); 
                // map.openInfoWindow(infoWindow, map.getCenter());      // 打开信息窗口
                
                map.enableScrollWheelZoom(true);     //开启鼠标滚轮缩放
                var scaleCtrl = new BMapGL.ScaleControl();
                map.addControl(scaleCtrl);
                var zoomCtrl = new BMapGL.ZoomControl();  // 添加比例尺控件
                map.addControl(zoomCtrl);

                if(this.getStatus() == BMAP_STATUS_SUCCESS){
                    var mk = new BMap.Marker(r.point);
                    map.addOverlay(mk);
                    map.panTo(r.point);

                    function myFun(result){
                        var cityName = result.name;
                        map.setCenter(cityName);
                        alert("当前定位城市:"+cityName);
                    }
                }

                else {
                    alert('failed'+this.getStatus());
                }
            });
        },

    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>


