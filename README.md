<?php

//دریافت تمامی ورودی ها
$var = file_get_contents("php://input");

//تبدیل ورودی ها به آرایه
$var = json_decode($var,true);

//دریافت شناسه چت
$chat_id = $var['message']['chat']['id'];

//دریافت پیام ارسال شده توسط کاربر
$text = $var['message']['text'];

//تعریف توکن ربات
$token = "2097981723:AAGfVNdY5g9As-cvC0mQAjd0zn20eHLlM20";


//این تابع یک پیام ساده ارسال میکنه
function sendMessage($chat_id,$text)
{
		global $token;
	    $api    = "https://api.telegram.org/bot$token/";
	    $method = "sendMessage";
	    $params = "?chat_id=$chat_id&text=" . urlencode($text);
	  
	  	$url = $api . $method . $params;
	    $result = file_get_contents($url);
	  	return $result;
}

if($text == "/start"){
	  sendMessage($chat_id,"به ربات خوش آمدید 🥳");
}
if($text == "سلام"){
	  sendMessage($chat_id,"علیک سلام ♥️");
}
if($text == "سازنده"){
	  sendMessage($chat_id,"سازنده من محمد مهدی اصلانی هست 🤩");
}



?>
