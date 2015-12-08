title: 纠结了半天的一个问题json_decode
id: .nan
categories:
  - PHP
date: 2015-08-26 08:52:19
tags:
---

1.  为什么json_decode（）之后仍然还是个对象，查手册之后，原来还有那么多参数，醉了。
2.  <span class="dc-title">json_decode(参数1，参数2，参数3，参数4)</span>

    1.  <span class="dc-title">对json格式的字符串进行编码</span>

        2.  <span class="dc-title">参数1带解码的json string格式的字符串</span>

        3.  <span class="dc-title">参数2当为true时将返回array而不是object</span>

        4.  <span class="dc-title">参数3(int $depth=512) 参数4默认将大整数设为浮动</span>
3.  <span class="dc-title">json_encode(参数1，参数2)</span>

    1.  <span class="dc-title">对变量进行json编码，成功返回一个一json形式便是的string，否侧返回false</span>

        2.  参数1待编码的value，除了resource类型之外的任何类型，只接受utf-8的编码数据

        3.  参数2由一下常量组成二进制掩码：

        4.  <span class="term">**`JSON_HEX_TAG`** (<span class="type">integer</span>)</span>

        5.  <span class="simpara">所有的 &lt; 和 &gt; 转换成 \u003C 和 \u003E。 自 PHP 5.3.0 起生效。</span>

        6.  <span class="term">**`JSON_HEX_AMP`** (<span class="type">integer</span>)</span>

        7.  <span class="simpara">所有的 &amp; 转换成 \u0026。 自 PHP 5.3.0 起生效。</span>

        8.  <span class="term">**`JSON_HEX_APOS`** (<span class="type">integer</span>)</span>

        9.  <span class="simpara">所有的 ' 转换成 \u0027。 自 PHP 5.3.0 起生效。</span>

        10.  <span class="term">**`JSON_HEX_QUOT`** (<span class="type">integer</span>)</span>

        11.  <span class="simpara">所有的 " 转换成 \u0022。 自 PHP 5.3.0 起生效。</span>

        12.  <span class="term">**`JSON_FORCE_OBJECT`** (<span class="type">integer</span>)</span>

        13.  <span class="simpara">使一个非关联数组输出一个类（Object）而非数组。 在数组为空而接受者需要一个类（Object）的时候尤其有用。 自 PHP 5.3.0 起生效。</span>

        14.  <span class="term">**`JSON_NUMERIC_CHECK`** (<span class="type">integer</span>)</span>

        15.  <span class="simpara">将所有数字字符串编码成数字（numbers）。 自 PHP 5.3.3 起生效。</span>

        16.  <span class="term">**`JSON_BIGINT_AS_STRING`** (<span class="type">integer</span>)</span>

        17.  <span class="simpara">将大数字编码成原始字符原来的值。 自 PHP 5.4.0 起生效。</span>

        18.  <span class="term">**`JSON_PRETTY_PRINT`** (<span class="type">integer</span>)</span>

        19.  <span class="simpara">用空白字符格式化返回的数据。 自 PHP 5.4.0 起生效。</span>

        20.  <span class="term">**`JSON_UNESCAPED_SLASHES`** (<span class="type">integer</span>)</span>

        21.  <span class="simpara">不要编码 _/_。 自 PHP 5.4.0 起生效。</span>

        22.  <span class="term">**`JSON_UNESCAPED_UNICODE`** (<span class="type">integer</span>)</span>

        23.  <span class="simpara">以字面编码多字节 Unicode 字符（默认是编码成 \uXXXX）。 自 PHP 5.4.0 起生效。</span>