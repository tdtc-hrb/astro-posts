---
layout: ../../layouts/MarkdownPostLayout.astro
title: "面包屑（breadcrumbs）"
description: "Bootstrap"
date: 2020-05-16
author: "tdtc"
---
在很多网站上都有一个导航记录栏 - 面包屑；

# 官方文档
[举例](https://v3.bootcss.com/components/#breadcrumbs)
```xml
<ol class="breadcrumb">
  <li><a href="#">Home</a></li>
  <li><a href="#">Library</a></li>
  <li class="active">Data</li>
</ol>
```

# php example
> CodeIgniter v2.2.x/3.x

建立一个php文件
breadcrumb.php
```php
<ol class="breadcrumb">
  <?php echo get_breadcrumb($breadData, $menu_prefix); ?>
  <li class="active">
  <?php echo empty($breadData) ?
  $this->Glossary_M->get_word('home', $this->data['lang_id']) :
  $body;
  ?>
  </li>
</ol>
```

在helper中建立如下方法：
```php
function get_breadcrumb($array, $prefix = NULL) {
	$str = '';
	if (count($array)) {
		foreach ($array as $item) {
			if ($item['homeFlag']) {
				// '<li><a href="http://'
				$str .= '<li><a href="' . $item['linkAddr'] . '">' . e($item['name']) . '</a></li>' . PHP_EOL;
			}
			else
			  $str .= '<li><a href="' . $prefix . $item['linkAddr'] . '">' . e($item['name']) . '</a></li>' . PHP_EOL;
		}
	}

	return $str;

}
```

实现效果：
![website info](https://gitee.com/xiaobin80/csdn/raw/master/images/20140113150326015.png)
