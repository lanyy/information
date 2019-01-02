# js 基本例子，偶尔使用
- [canvas图片转换及压缩](#canvas图片转换及压缩) 


## canvas图片转换及压缩

```javascript
/**
     * 压缩图片
     * @param src 图片url
     * @param quality 图片质量
     */
    imgCompress:function(src,quality){
       return  new Promise(function(resolve, reject){
           var canvas = document.createElement('canvas');
           var context = canvas.getContext('2d');
           var img=new Image();
           img.onload=function(){
               var w=this.width,h=this.height;
               canvas.width = w;
               canvas.height = h;
               // 清除画布
               context.clearRect(0, 0, w, h);
               context.drawImage(img, 0, 0, w, h);
               var base64 = canvas.toDataURL('image/jpeg',quality);
               resolve(base64);
           }
           img.src = src;
       });

    },
```


