title: 经典抽奖算法
id: .nan
categories:
  - PHP
date: 2017-08-03 18:59:27
tags: lottery
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---
## 定义中奖概率数组
```php
private $innerRate = array(
'1' => 1,
'2' => 200,
'3' => 500,
'4' => 100000,
'5' => 300000,
'6' => 1693000,
);
```
### 调用函数

1.`$i = $this->getRand($this->innerRate)`;
2.根据返回的$i,处理当前返回逻辑，if和switch都可以。
```php
if($i==1)
{
	echo "一等奖";
}else{
	echo "二等奖";
}
```
### 基础函数
```php
private function getRand($proArr)
{
    $result = '';
    // 概率数组的总概率精度
    $proSum = array_sum($proArr);
    // 概率数组循环
    foreach ($proArr as $key => $proCur) {
        $randNum = mt_rand(1, $proSum); // 抽取随机数
        if ($randNum <= $proCur) {
            $result = $key; // 得出结果
            break;
        } else {
            $proSum -= $proCur;
        }
    }
    unset($proArr);
    return $result;
}
```






