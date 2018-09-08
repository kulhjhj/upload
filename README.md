<? php
require_once 'Dailymotion.php';
?>
<? php 
require_once 'sdk / Dailymotion.php';

// Thông tin xác thực API DATA
$ apikey = '0e1b4b3f8b3c49678cbd'; 
$ apisecret = '2b4b7c0dcd6cc60e0eb5cfbfef07cc7cb2f5ce5b'; 
$ user = 'Địa chỉ email người dùng của bạn'; 
$ password = 'Mật khẩu';


$ videotitle = "Tiêu đề của video"; 
// $ videofile = "Đường dẫn thực tế của video";
$ name = $ _FILES ["upload_file"] ["name"];
move_uploaded_file ($ _ FILES ["upload_file"] ["tmp_name"], "video /".$ tên);
$ videofile = "video /".$ tên;
$ videocategory = "Danh mục của video";
$ videotags = "Thẻ của video";
$ videodescription = "Mô tả video";
$ api = new Dailymotion ();
$ api-> setGrantType (Dailymotion :: GRANT_TYPE_PASSWORD, $ apikey, $ apisecret, mảng ('write', 'delete'), mảng ('username' => $ user, 'password' => $ password)); 
$ url = $ api-> uploadFile ($ videofile); 
$ result = $ api-> call ('video.create', mảng ('url' => $ url, 'title' => $ videotitle, 'channel' => $ videocategory, 'tags' => $ videotags, ' description '=> $ videodescription,' published '=> true)); 
$ videourl = 'http://www.dailymotion.com/video/'.$result['id'];

if ($ result) {
 ?> <a href="<?php echo $videourl; ?> "target =" _ blank "> Nhấp vào đây </a> <? php echo" nhấp vào đây để xem video này. "; 
 echo "Video được tải lên thành công trên dailymotion.com";
 }
?>
