title: 时间转换功能类似strtotime
id: .nan
categories:
  - PHP
date: 2015-08-27 11:06:41
tags:
---

$date_str = "2015-08-27 17:00:00";

echo $time_str = str_format_time($date_str);

function str_format_time($timestamp = '')

{   

if (preg_match("/[0-9]{4}-[0-9]{1,2}-[0-9]{1,2} (0[0-9]|1[0-9]|2[0-3]):([0-5][0-9]):([0-5][0-9])/i", $timestamp)) 

{

list($date,$time)=explode(" ",$timestamp);

list($year,$month,$day)=explode("-",$date);

    list($hour,$minute,$seconds )=explode(":",$time);

  $timestamp=gmmktime($hour,$minute,$seconds,$month,$day,$year);

}

else

{

$timestamp=time();

}

return $timestamp;

}

echo '&lt;br /&gt;';

echo date("Y-m-d H:i:s", $time_str);