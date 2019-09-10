 ### 1. 首先需要下载image2这个plugin之后放在ckeditor的plugins下面。

### 2. 在ckeditor下的config.js中配置文件的上传地址:
	
	```
		config.filebrowserUploadUrl = '/ckeditorUpload?type=File';
		config.filebrowserImageUploadUrl = "/ckeditorUpload?type=image";
		config.filebrowserFlashUploadUrl = '/ckeditorUpload?type=Flash';
	```

***

### 3. 上传文件之后的返回值类型
	
	```
		"uploaded": 1,
		"fileName": "test.png",
		"url": "/upload/test.png",
		"error": "uploaded error!!"
	```
	

